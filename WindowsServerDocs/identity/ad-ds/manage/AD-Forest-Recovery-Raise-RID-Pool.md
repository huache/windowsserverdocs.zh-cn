---
title: AD 林恢复-引发 RID 池
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: c37bc129-a5e0-4219-9ba7-b4cf3a9fc9a4
ms.technology: identity-adds
ms.openlocfilehash: 308dce9be53194eb7db91944964ae5de03345ab6
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80823850"
---
# <a name="ad-forest-recovery---raising-the-value-of-available-rid-pools"></a>AD 林恢复-提高可用 RID 池的值 

>适用于： Windows Server 2016、Windows Server 2012 和 2012 R2、Windows Server 2008 和 2008 R2

使用以下过程来引发 RID 操作主机在该 DC 还原后将分配的相对 ID （RID）池的值。 通过提高可用 RID 池的值，你可以确保没有 DC 为在用于还原域的备份之后创建的安全主体分配 RID。 

## <a name="about-active-directory-rid-pools-and-ridavailablepool"></a>关于 Active Directory RID 池和 rIDAvailablePool

每个域都有一个对象**CN = RID Manager $，CN = System，DC**=<*domain_name*>。 此对象具有名为**rIDAvailablePool**的属性。 此属性值维护整个域的全局 RID 空间。 该值是一个大整数，其中包含上半部分和下半部分。 上半部分定义了可以为每个域分配的安全主体的数量（0x3FFFFFFF 或仅限1000000000）。 下半部分是已在域中分配的 Rid 的数目。 
  
> [!NOTE]
> 在 Windows Server 2016 和2012中，可分配的安全主体数量将增加到超过2000000000。 有关详细信息，请参阅[管理 RID 颁发](https://technet.microsoft.com/library/jj574229.aspx)。 
  
- 示例值：4611686014132422708  
- 低部分：2100（从下一个 RID 池开始分配）  
- 上半部分：1073741823（可在域中创建的 Rid 的总数）  
  
增大大整数的值时，会增加低部分的值。 例如，如果将100000的样本4611686014132422708值添加到4611686014132522708的总和，则新的低部分为102100。 这表示 RID 主机将分配的下一个 RID 池的开头为102100，而不是2100。 
  
### <a name="to-raise-the-value-of-available-rid-pools-using-adsiedit-and-the-calculator"></a>使用 adsiedit 和计算器提高可用 RID 池的值

1. 打开服务器管理器，单击 "**工具**"，然后单击 " **ADSI 编辑器**"。
2. 右键单击，选择 "**连接到**"，然后单击 **"确定"** 。
   ![ADSI 编辑器](media/AD-Forest-Recovery-Raise-RID-Pool/adsi1.png) 
3. 浏览到以下可分辨名称路径： **cn = RID Manager $，cn = System，DC =<domain name>** 。
   ![ADSI 编辑器](media/AD-Forest-Recovery-Raise-RID-Pool/adsi2.png) 
3. 右键单击并选择 "CN = RID Manager $" 的属性。 
4. 选择属性**rIDAvailablePool**，单击 "**编辑**"，然后将大整数值复制到剪贴板。
   ![ADSI 编辑器](media/AD-Forest-Recovery-Raise-RID-Pool/adsi3.png)  
5. 启动计算器，然后在 "**视图**" 菜单中选择 "**科学模式**"。 
6. 将100000添加到当前值。
   ![ADSI 编辑器](media/AD-Forest-Recovery-Raise-RID-Pool/adsi4.png) 
7. 使用 ctrl + c 或 "**编辑**" 菜单中的 "**复制**" 命令，将值复制到剪贴板。 
8. 在 adsiedit 的 "编辑" 对话框中，粘贴此新值。 
   ![ADSI 编辑器](media/AD-Forest-Recovery-Raise-RID-Pool/adsi5.png) 
9. 单击对话框中的 **"确定"** ，并在属性表中**应用**以更新**rIDAvailablePool**属性。 
  
### <a name="to-raise-the-value-of-available-rid-pools-using-ldp"></a>使用 LDP 提高可用 RID 池的值  
  
1. 在命令提示符下，键入以下命令，然后按 Enter：  
   **ldp.exe**  
2. 单击 "**连接**"，单击 "**连接**"，键入 RID 管理器的名称，然后单击 **"确定"** 。 
   ![LDP](media/AD-Forest-Recovery-Raise-RID-Pool/ldp1.png)
3. 依次单击 "**连接**"、"**绑定**"、"**绑定**" 和 "凭据"，然后单击 **"确定"** 。 
   ![LDP](media/AD-Forest-Recovery-Raise-RID-Pool/ldp2.png)
4. 单击 "**查看**"，单击 "**树**"，然后键入以下可分辨名称路径： cn = RID Manager $，CN = System，DC =*域名*  
   ![LDP](media/AD-Forest-Recovery-Raise-RID-Pool/ldp3.png)
5. 单击 "**浏览**"，然后单击 "**修改**"。 
6. 将100000添加到当前的**rIDAvailablePool**值，然后将 Sum 键入**值**。 
7. 在 " **Dn**" 中，键入 `cn=RID Manager$,cn=System,dc=` *< 域名\>* "。 
8. 在 "**编辑项属性**" 中，键入 `rIDAvailablePool`。 
9. 选择 "**替换**为操作"，然后单击 " **Enter**"。
   ![LDP](media/AD-Forest-Recovery-Raise-RID-Pool/ldp4.png) 
10. 单击 "**运行**" 以运行该操作。 单击 **“关闭”** 。
11. 若要验证更改，请单击 "**查看**"，单击 "**树**"，然后键入以下可分辨名称路径： cn = RID Manager $，CN = System，DC =*域名*。   检查**rIDAvailablePool**属性。 
   ![LDP](media/AD-Forest-Recovery-Raise-RID-Pool/ldp5.png)

## <a name="next-steps"></a>后续步骤

- [AD 林恢复指南](AD-Forest-Recovery-Guide.md)
- [AD 林恢复 - 过程](AD-Forest-Recovery-Procedures.md)
