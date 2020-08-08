---
title: 在 Azure 虚拟机上安装 Active Directory 域服务
description: 如何在虚拟机上创建新的 Active Directory 林中 (VM) 上的 Azure 虚拟机上。
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 04/11/2019
ms.topic: article
ms.openlocfilehash: 7272ddc3693816974df528e6c5e10671bbe4ffb7
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87943772"
---
# <a name="install-a-new-active-directory-forest-using-azure-cli"></a>使用 Azure CLI 安装新的 Active Directory 林

AD DS 可以在 Azure 虚拟机上运行 (VM) ，其方式与在许多本地实例中运行的方式相同。 本文逐步讲解如何使用 Azure 门户和 Azure CLI 在两个新的域控制器上部署新的 AD DS 林： Azure 可用性集。 许多客户在创建实验室或准备在 Azure 中部署域控制器时，会发现此指导很有用。

## <a name="components"></a>组件

* 要将所有内容放在其中的资源组。
* 允许 RDP 访问 Vm 的[Azure 虚拟网络](/azure/virtual-network/virtual-networks-overview.md)、子网、网络安全组和规则。
* Azure 虚拟机[可用性集](/azure/virtual-machines/windows/regions-and-availability#availability-sets)可将两个 Active Directory 域服务 (AD DS 在中) 域控制器。
* 要运行 AD DS 和 DNS 的两个 Azure 虚拟机。

### <a name="items-that-are-not-covered"></a>未覆盖的项

* 从本地位置[创建站点到站点 VPN 连接](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal.md)
* [保护 Azure 中的网络流量](/azure/security/azure-security-network-security-best-practices.md)
* [设计站点拓扑](../../plan/designing-the-site-topology.md)
* [规划操作主机角色放置](../../plan/planning-operations-master-role-placement.md)
* [部署 Azure AD Connect 以将标识同步到 Azure AD](/azure/active-directory/hybrid/how-to-connect-install-express)

## <a name="build-the-test-environment"></a>生成测试环境

我们使用[Azure 门户](https://portal.azure.com)和[Azure CLI](/cli/azure/overview?view=azure-cli-latest)来创建环境。

Azure CLI 用于从命令行或脚本创建和管理 Azure 资源。 本教程详细介绍了如何使用 Azure CLI 部署运行 Windows Server 2019 的虚拟机。 部署完成后，我们将连接到服务器并安装 AD DS。

如果还没有 Azure 订阅，可以在开始前[创建一个免费帐户](https://azure.microsoft.com/free)。

### <a name="using-azure-cli"></a>使用 Azure CLI

下面的脚本自动构建两个 Windows Server 2019 Vm 的过程，用于为 Azure 中的新 Active Directory 林生成域控制器。 管理员可以修改以下变量以满足其需求，然后作为一个操作完成。 此脚本将创建所需的资源组、包含远程桌面、虚拟网络和子网和可用性组的流量规则的网络安全组。 然后，每个 Vm 都是使用 20 GB 的数据磁盘生成的，并禁用缓存，以便将 AD DS 安装到。

下面的脚本可以直接从 Azure 门户运行。 如果选择在本地安装并使用 CLI，此快速入门教程要求运行 Azure CLI 2.0.4 版或更高版本。 运行 `az --version` 即可查找版本。 如果需要进行安装或升级，请参阅[安装 Azure CLI 2.0](/cli/azure/install-azure-cli?view=azure-cli-latest)。

| 变量名 | 目的 |
| :---: | :--- |
| AdminUsername | 要作为本地管理员在每个 VM 上配置的用户名。 |
| AdminPassword | 要在每个 VM 上配置为本地管理员密码的明文密码。 |
| ResourceGroupName | 用于资源组的名称。 不应复制现有名称。 |
| 位置 | 要部署到的 Azure 位置名称。 使用列出当前订阅支持的区域 `az account list-locations` 。 |
| VNetName | 分配给 Azure 虚拟网络的名称不应重复现有名称。 |
| VNetAddress | 用于 Azure 网络的 IP 作用域。 不应复制现有范围。 |
| SubnetName | 分配 IP 子网的名称。 不应复制现有名称。 |
| SubnetAddress | 域控制器的子网地址。 应为 VNet 内的子网。 |
| AvailabilitySet | 域控制器虚拟机将加入的可用性集的名称。 |
| VMSize | 部署的位置中可用的标准 Azure VM 大小。 |
| DataDiskSize | AD DS 安装的数据磁盘的大小（GB）。 |
| DomainController1 | 第一个域控制器的名称。 |
| DC1IP | 第一个域控制器的 IP 地址。 |
| DomainController2 | 第二个域控制器的名称。 |
| DC2IP | 第二个域控制器的 IP 地址。 |

```azurecli
#Update based on your organizational requirements
Location=westus2
ResourceGroupName=ADonAzureVMs
NetworkSecurityGroup=NSG-DomainControllers
VNetName=VNet-AzureVMsWestUS2
VNetAddress=10.10.0.0/16
SubnetName=Subnet-AzureDCsWestUS2
SubnetAddress=10.10.10.0/24
AvailabilitySet=DomainControllers
VMSize=Standard_DS1_v2
DataDiskSize=20
AdminUsername=azureuser
AdminPassword=ChangeMe123456
DomainController1=AZDC01
DC1IP=10.10.10.11
DomainController2=AZDC02
DC2IP=10.10.10.12

# Create a resource group.
az group create --name $ResourceGroupName \
                --location $Location

# Create a network security group
az network nsg create --name $NetworkSecurityGroup \
                      --resource-group $ResourceGroupName \
                      --location $Location

# Create a network security group rule for port 3389.
az network nsg rule create --name PermitRDP \
                           --nsg-name $NetworkSecurityGroup \
                           --priority 1000 \
                           --resource-group $ResourceGroupName \
                           --access Allow \
                           --source-address-prefixes "*" \
                           --source-port-ranges "*" \
                           --direction Inbound \
                           --destination-port-ranges 3389

# Create a virtual network.
az network vnet create --name $VNetName \
                       --resource-group $ResourceGroupName \
                       --address-prefixes $VNetAddress \
                       --location $Location \

# Create a subnet
az network vnet subnet create --address-prefix $SubnetAddress \
                              --name $SubnetName \
                              --resource-group $ResourceGroupName \
                              --vnet-name $VNetName \
                              --network-security-group $NetworkSecurityGroup

# Create an availability set.
az vm availability-set create --name $AvailabilitySet \
                              --resource-group $ResourceGroupName \
                              --location $Location

# Create two virtual machines.
az vm create \
    --resource-group $ResourceGroupName \
    --availability-set $AvailabilitySet \
    --name $DomainController1 \
    --size $VMSize \
    --image Win2019Datacenter \
    --admin-username $AdminUsername \
    --admin-password $AdminPassword \
    --data-disk-sizes-gb $DataDiskSize \
    --data-disk-caching None \
    --nsg $NetworkSecurityGroup \
    --private-ip-address $DC1IP \
    --no-wait

az vm create \
    --resource-group $ResourceGroupName \
    --availability-set $AvailabilitySet \
    --name $DomainController2 \
    --size $VMSize \
    --image Win2019Datacenter \
    --admin-username $AdminUsername \
    --admin-password $AdminPassword \
    --data-disk-sizes-gb $DataDiskSize \
    --data-disk-caching None \
    --nsg $NetworkSecurityGroup \
    --private-ip-address $DC2IP

```

## <a name="dns-and-active-directory"></a>DNS 和 Active Directory

如果在此过程中创建的 Azure 虚拟机将是现有本地 Active Directory 基础结构的扩展，则必须更改虚拟网络上的 DNS 设置，以在部署之前包含本地 DNS 服务器。 若要允许在 Azure 中新建的域控制器解析本地资源并允许进行复制，则必须执行此步骤。 有关 DNS、Azure 和如何配置设置的详细信息，请参阅[使用自己的 dns 服务器的名称解析](/azure/virtual-network/virtual-networks-name-resolution-for-vms-and-role-instances#name-resolution-that-uses-your-own-dns-server)部分。

升级 Azure 中的新域控制器后，需要将其设置为虚拟网络的主 DNS 服务器和辅助 DNS 服务器，并且任何本地 DNS 服务器都将降级为三级和更高版本。 有关更改 DNS 服务器的详细信息[，请参阅创建、更改或删除虚拟网络一](/azure/virtual-network/manage-virtual-network#change-dns-servers)文。

有关将本地网络扩展到 Azure 的信息，可参阅[创建站点到站点 VPN 连接](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)一文。

## <a name="configure-the-vms-and-install-active-directory-domain-services"></a>配置 Vm 并安装 Active Directory 域服务

脚本完成后，浏览到[Azure 门户](https://portal.azure.com)，然后浏览到 "**虚拟机**"。

### <a name="configure-the-first-domain-controller"></a>配置第一个域控制器

使用脚本中提供的凭据连接到 AZDC01。

* 将数据磁盘初始化并格式化为 F：
   * 打开 "开始" 菜单并浏览到 "**计算机管理**"
   * 浏览到**存储**  >  **磁盘管理**
   * 将磁盘初始化为 MBR
   * 创建新的简单卷并分配驱动器号 F：如果需要，可以提供卷标
* 使用服务器管理器安装 Active Directory 域服务
* 升级到新林中的第一个域控制器
   * 在 "域控制器选项" 页上选中 "保留域名系统 (DNS) 服务器" 和 "全局编录 (GC) "
   * 根据组织的要求指定目录服务还原模式密码
   * 将路径从 C：更改为指向我们在系统提示其位置时创建的 F：驱动器
   * 查看在向导中所做的选择，然后选择 "**下一步**"

> [!NOTE]
> "先决条件检查" 将向你发出警告：物理网络适配器没有 (es) 分配静态 IP 地址，你可以放心地忽略此情况，因为在 Azure 虚拟网络中分配了静态 ip。

* 选择**安装**

向导完成安装过程后，VM 将重新启动。

VM 重新启动完成后，使用以前使用的凭据重新登录，但这一次是创建的域的成员。

   > [!NOTE]
   > 升级到域控制器后首次登录的时间可能比平时长，这是正常的。 抓住一杯茶、咖啡、水或其他所选饮料。

[Azure 虚拟网络现在支持 ipv6](/azure/virtual-network/virtual-networks-faq#do-vnets-support-ipv6) ，但如果你想要将 vm 设置为首选 IPv4 over ipv6，则有关如何完成此任务的信息，请参阅在[Windows 中为高级用户配置 IPv6](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)的知识库文章。

### <a name="configure-the-second-domain-controller"></a>配置第二个域控制器

使用脚本中提供的凭据连接到 AZDC02。

* 将数据磁盘初始化并格式化为 F：
   * 打开 "开始" 菜单并浏览到 "**计算机管理**"
   * 浏览到**存储**  >  **磁盘管理**
   * 将磁盘初始化为 MBR
   * 创建新的简单卷并分配驱动器号 F： (如果需要，可以提供卷标) 
* 使用服务器管理器安装 Active Directory 域服务
* 提升域控制器
   * 向现有域添加域控制器-CONTOSO.com
   * 提供凭据以执行此操作
   * 将路径从 C：更改为指向我们在系统提示其位置时创建的 F：驱动器
   * 确保在 "域控制器选项" 页上选中 "域名系统 (DNS) 服务器" 和 "全局编录 (GC) "
   * 根据组织的要求指定目录服务还原模式密码
   * 查看在向导中所做的选择，然后选择 "**下一步**"

> [!NOTE]
> "先决条件检查" 将向你发出警告：物理网络适配器没有 (es) 分配静态 IP 地址。 可以放心地忽略此情况，因为在 Azure 虚拟网络中分配了静态 Ip。

* 选择**安装**

向导完成安装过程后，VM 将重新启动。

VM 重新启动完成后，使用以前使用的凭据重新登录，但这一次是 CONTOSO.com 域的成员

[Azure 虚拟网络现在支持 ipv6](/azure/virtual-network/virtual-networks-faq#do-vnets-support-ipv6) ，但如果你想要将 vm 设置为首选 IPv4 over ipv6，则有关如何完成此任务的信息，请参阅在[Windows 中为高级用户配置 IPv6](https://support.microsoft.com/help/929852/guidance-for-configuring-ipv6-in-windows-for-advanced-users)的知识库文章。

### <a name="configure-dns"></a>配置 DNS

升级 Azure 中的新域控制器后，需要将其设置为虚拟网络的主 DNS 服务器和辅助 DNS 服务器，并且任何本地 DNS 服务器都将降级为三级和更高版本。 有关更改 DNS 服务器的详细信息[，请参阅创建、更改或删除虚拟网络一](/azure/virtual-network/manage-virtual-network#change-dns-servers)文。

### <a name="wrap-up"></a>总结

此时，环境具有一对域控制器，并且我们配置了 Azure 虚拟网络，以便可以将其他服务器添加到该环境中。 应在此时完成 Active Directory 域服务的安装后任务，如配置站点和服务、审核、备份和保护内置管理员帐户。

## <a name="removing-the-environment"></a>删除环境

若要删除环境，在完成测试后，可以删除上面创建的资源组。 此步骤将删除属于该资源组的所有组件。

### <a name="remove-using-the-azure-portal"></a>使用 Azure 门户删除

在 Azure 门户中，浏览到 "**资源组**"，然后选择在此示例中创建的资源组 (ADonAzureVMs) ，然后选择 "**删除资源组**"。 进程在删除资源组内包含的所有资源之前要求确认。

### <a name="remove-using-the-azure-cli"></a>使用 Azure CLI 删除

从 Azure CLI 运行以下命令：

```azurecli
az group delete --name ADonAzureVMs
```

## <a name="next-steps"></a>后续步骤

* [安全地虚拟化 Active Directory 域服务 (AD DS)](../../Introduction-to-Active-Directory-Domain-Services-AD-DS-Virtualization-Level-100.md)
* [Azure AD Connect](/azure/active-directory/connect/active-directory-aadconnect-get-started-express)
* [备份和恢复](/azure/virtual-machines/windows/backup-recovery)
* [站点到站点 VPN 连接](/azure/vpn-gateway/vpn-gateway-howto-site-to-site-resource-manager-portal)
* [Monitoring](/azure/virtual-machines/windows/monitor)
* [安全和策略](/azure/virtual-machines/windows/security-policy)
* [维护和更新](/azure/virtual-machines/windows/maintenance-and-updates)
