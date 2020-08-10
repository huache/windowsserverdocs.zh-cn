---
ms.assetid: f964d056-11bf-4d9b-b5ab-dceaad8bfbc3
title: Windows Server 2016 功能级别
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 10/29/2018
ms.topic: article
ms.custom: it-pro
ms.reviewer: maheshu
ms.openlocfilehash: 75ba30502c7de1b0a88886f42c3a8ef9a84a7e18
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87938626"
---
# <a name="forest-and-domain-functional-levels"></a>林和域功能级别

>适用于：Windows Server

功能级别决定了可用的 Active Directory 域服务 (AD DS) 域或林功能。 功能级别还决定了你可以在域或林中的域控制器上运行哪些 Windows Server 操作系统。 但是，功能级别不会影响你可以在已加入域或林的工作站和成员服务器上运行哪些操作系统。

部署 AD DS 时，请将域和林功能级别设置为环境可以支持的最高值。 这样一来，你就可以尽可能使用多项 AD DS 功能。 部署新的林时，系统会提示你设置林功能级别，然后设置域功能级别。 可以将域功能级别设置为高于林功能级别的值，但不能将域功能级别设置为低于林功能级别的值。

随着 Windows 2003 生存期的结束，Windows 2003 域控制器 (DC) 需更新到 Windows Server 2008、2008R2、2012、2012R2、2016 或 2019。 因此，应从域中删除任何运行 Windows Server 2003 的域控制器。

在 Windows Server 2008 及更高的域功能级别，分布式文件服务 (DFS) 复制用于在域控制器之间复制 SYSVOL 文件夹内容。 如果在 Windows Server 2008 或更高的域功能级别创建新的域，系统会自动使用 DFS 复制来复制 SYSVOL。 如果在较低的功能级别创建域，则在复制 SYSVOL 时，需从使用 FRS 复制迁移到使用 DFS 复制。 有关迁移步骤，可以参阅 [TechNet 上的过程](../../storage/dfs-replication/migrate-sysvol-to-dfsr.md)，也可参阅[存储团队文件柜博客上的简化步骤集](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)。

## <a name="windows-server-2019"></a>Windows Server Standard 2012 R2

此版本没有新增的林或域功能级别。

若要添加 Windows Server 2019 域控制器，最低要求是 Windows Server 2008 功能级别。 该域还需使用 DFS-R 作为引擎来复制 SYSVOL。

## <a name="windows-server-2016"></a>Windows Server 2016

支持的域控制器操作系统：

* Windows Server Standard 2012 R2
* Windows Server 2016

### <a name="windows-server-2016-forest-functional-level-features"></a>Windows Server 2016 林功能级别功能

* 提供 Windows Server 2012R2 林功能级别可用的所有功能，以及下列功能：
   * [使用 Microsoft 标识管理器 (MIM) 的特权访问管理 (PAM)](../whats-new-active-directory-domain-services.md#privileged-access-management)

### <a name="windows-server-2016-domain-functional-level-features"></a>Windows Server 2016 域功能级别功能

* 所有默认的 Active Directory 功能、所有来自 Windows Server 2012R2 域功能级别的功能，以及下列功能：
   * DC 可以支持在已配置为需要 PKI 身份验证的用户帐户上自动推出 NTLM 和其他基于密码的机密。 此配置也称为“交互式登录需要智能卡”
   * 当用户只能使用特定的加入域的设备时，DC 支持为其启用网络 NTLM。
   * 成功使用 PKInit Freshness Extension进行身份验证的 Kerberos 客户端会获取新的公钥标识 SID。

    有关详细信息，请参阅 [Kerberos 身份验证的新增功能](../../security/kerberos/whats-new-in-kerberos-authentication.md)和[凭据保护的新增功能](../../security/credentials-protection-and-management/whats-new-in-credential-protection.md)

## <a name="windows-server-2012r2"></a>Windows Server 2012R2

支持的域控制器操作系统：

* Windows Server Standard 2012 R2
* Windows Server 2016
* Windows Server 2012 R2

### <a name="windows-server-2012r2-forest-functional-level-features"></a>Windows Server 2012R2 林功能级别功能

* Windows Server 2012 林功能级别可用的所有功能，而不是任何其他功能。

### <a name="windows-server-2012r2-domain-functional-level-features"></a>Windows Server 2012R2 域功能级别功能

* 所有默认的 Active Directory 功能、所有来自 Windows Server 2012 域功能级别的功能，以及下列功能：
   * 针对受保护用户的 DC 端保护。 向 Windows Server 2012 R2 域进行身份验证的受保护用户再也不能执行以下操作：
      * 使用 NTLM 身份验证进行验证
      * 在 Kerberos 预身份验证中使用 DES 或 RC4 密码套件
      * 使用不受约束的或受约束的委派进行委派
      * 在超出最初的 4 小时生存期后续订用户票证 (TGT)
   * 身份验证策略
      * 新的基于林的 Active Directory 策略，这些策略可以应用到 Windows Server 2012 R2 域中的帐户，用于控制一个帐户可以从哪些主机登录，并将身份验证的访问控制条件应用到作为帐户运行的服务。
   * 身份验证策略接收器
      * 新的基于林的 Active Directory 对象，可以在用户、托管服务和计算机，以及帐户（用于对帐户分类，以便实施身份验证策略或进行身份验证隔离）之间创建关系。

## <a name="windows-server-2012"></a>Windows Server 2012

支持的域控制器操作系统：

* Windows Server Standard 2012 R2
* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012

### <a name="windows-server-2012-forest-functional-level-features"></a>Windows Server 2012 林功能级别功能

* Windows Server 2008 R2 林功能级别可用的所有功能，而不是任何其他功能。

### <a name="windows-server-2012-domain-functional-level-features"></a>Windows Server 2012 域功能级别功能

* 所有默认的 Active Directory 功能、所有来自 Windows Server 2008R2 域功能级别的功能，以及下列功能：
   * KDC 对声明、复合身份验证和 Kerberos 保护的支持 KDC 管理模板策略的两个设置（“始终提供声明”和“拒绝未保护身份验证请求”）需要 Windows Server 2012 域功能级别。 有关详细信息，请参阅 [Kerberos 身份验证的新增功能](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831747(v=ws.11))

## <a name="windows-server-2008r2"></a>Windows Server 2008R2

支持的域控制器操作系统：

* Windows Server Standard 2012 R2
* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012
* Windows Server 2008 R2

### <a name="windows-server-2008r2-forest-functional-level-features"></a>Windows Server 2008R2 林功能级别功能

* Windows Server 2003 林功能级别上可用的所有功能，以及下列功能：
   * Active Directory 回收站，提供在运行 AD DS 时还原整个已删除对象的功能。

### <a name="windows-server-2008r2-domain-functional-level-features"></a>Windows Server 2008R2 域功能级别功能

* 所有默认的 Active Directory 功能、所有来自 Windows Server 2008 域功能级别的功能，以及下列功能：
   * 身份验证机制保证，将对域用户进行身份验证所用的登录方法类型（智能卡或用户名/密码）的相关信息封装在每个用户的 Kerberos 令牌中。 如果在已部署联合身份管理基础结构（如 Active Directory 联合身份验证服务 (AD FS)）的网络环境中启用此功能，则每当用户尝试访问已开发为根据用户登录方法确定是否授权的声明感知应用程序时，都可以提取令牌中的信息。
   * 当计算机帐户的名称或 DNS 主机名更改时，针对在特定计算机上运行且处于“托管服务帐户”上下文中的服务自动进行 SPN 管理。 有关托管服务帐户的详细信息，请参阅 [Service Accounts Step-by-Step Guide](https://go.microsoft.com/fwlink/?LinkId=180401)（服务帐户分步指南）。

## <a name="windows-server-2008"></a>Windows 2008 Server

支持的域控制器操作系统：

* Windows Server Standard 2012 R2
* Windows Server 2016
* Windows Server 2012 R2
* Windows Server 2012
* Windows Server 2008 R2
* Windows Server 2008

### <a name="windows-server-2008-forest-functional-level-features"></a>Windows Server 2008 林功能级别功能

* 提供 Windows Server 2003 林功能级别可用的所有功能，而不是任何其他功能。

### <a name="windows-server-2008-domain-functional-level-features"></a>Windows Server 2008 域功能级别功能

* 提供所有默认的 AD DS 功能、所有来自 Windows Server 2003 域功能级别的功能，以及下列功能：
  * 针对 Windows Server 2003 系统卷 (SYSVOL) 的分布式文件系统 (DFS) 复制支持
    * DFS 复制支持提供 SYSVOL 内容的更稳健且更详细的复制。

      > [!NOTE]
      > 文件复制服务 (FRS) 从 Windows Server 2012 R2 开始弃用。 在至少运行 Windows Server 2012 R2 的域控制器上创建的新域必须设置为 Windows Server 2008 域功能级别或更高级别。

  * 在 Windows Server 2008 模式下运行的基于域的 DFS 命名空间，支持基于访问的枚举和增强的可伸缩性。 在 Windows Server 2008 模式下的基于域的命名空间还要求林使用 Windows Server 2003 林功能级别。 有关详细信息，请参阅 [Choose a Namespace Type](https://go.microsoft.com/fwlink/?LinkId=180400)（选择命名空间类型）。
  * 针对 Kerberos 协议的高级加密标准（AES 128 和 AES 256）支持。 若要使用 AES 来颁发 TGT，域功能级别必须为 Windows Server 2008 或更高版本，且域密码需要更改。
    * 有关详细信息，请参阅 [Kerberos Enhancements](/previous-versions/windows/it-pro/windows-vista/cc749438(v=ws.10))（Kerberos 增强功能）。

      > [!NOTE]
      >如果已将域功能级别提升到 Windows Server 2008 或更高版本，但此时域控制器已复制 DFL 更改但尚未刷新 krbtgt 密码，则可能会在域控制器上出现身份验证错误。 在这种情况下，在域控制器上重启 KDC 服务会触发内存对新 krbtgt 密码的刷新，解决相关的身份验证错误。

  * [上次交互式登录](https://go.microsoft.com/fwlink/?LinkId=180387)信息会显示以下信息：
     * 在加入域的 Windows Server 2008 服务器或 Windows Vista 工作站上尝试登录失败的总次数
     * 在成功登录到 Windows Server 2008 服务器或 Windows Vista 工作站后又尝试登录的失败总次数
     * 在 Windows Server 2008 或 Windows Vista 工作站上最后一次尝试登录失败的时间
     * 在 Windows Server 2008 服务器或 Windows Vista 工作站上最后一次尝试登录成功的时间
  * 严格的密码策略，这可以为域中的用户和全局安全组指定密码和帐户锁定策略。 有关详细信息，请参阅[有关细化密码和帐户锁定策略配置的分步指南](https://go.microsoft.com/fwlink/?LinkID=91477)。
  * 个人虚拟桌面
     * 若要使用“Active Directory 用户和计算机”内“用户帐户属性”对话框中“个人虚拟桌面”选项卡提供的新增功能，必须扩展 Windows Server 2008 R2（架构对象版本 = 47）的 AD DS 架构。 有关详细信息，请参阅 [Deploying Personal Virtual Desktops by Using RemoteApp and Desktop Connection Step-by-Step Guide](https://go.microsoft.com/fwlink/?LinkId=183552)（使用 RemoteApp 和桌面连接分步指南部署个人虚拟桌面）。

## <a name="windows-server-2003"></a>Windows Server 2003

支持的域控制器操作系统：

* Windows Server 2012 R2
* Windows Server 2012
* Windows Server 2008 R2
* Windows Server 2008
* Windows Server 2003

### <a name="windows-server-2003-forest-functional-level-features"></a>Windows Server 2003 林功能级别功能

* 提供所有默认的 AD DS 功能及以下功能：
   * 林信任
   * 域重命名
   * 链接值复制
      - 有了链接值复制功能，就可以更改组成员身份，为各个成员存储并复制值，而不需以单个单位形式复制整个成员身份。 在复制期间存储和复制单个成员的值使用的网络带宽和处理器循环都较少，这样，当你以并发方式在不同的域控制器中添加或删除多个成员时，就不会丢失更新。
   * 部署只读域控制器 (RODC) 的功能
   * 改进的知识一致性检查器 (KCC) 的算法和可伸缩性
      - 站点间拓扑生成器 (ISTG) 使用改进的算法，可通过缩放支持多个林，其中的站点数目大于 AD DS 在 Windows 2000 林功能级别能够支持的站点数量。 改进的 ISTG 选择算法是一种在 Windows 2000 林功能级别选择 ISTG 的入侵性较小的机制。
   * 在域目录分区中创建动态辅助类（名为 **dynamicObject**）的实例的功能
   * 将 **inetOrgPerson** 对象实例转换为 **User** 对象实例以及完成反向转换的功能
   * 创建新组类型的实例以支持基于角色的授权的功能。
      - 这些类型称为应用程序基本组和 LDAP 查询组。
   * 在架构中停用并重新定义属性和类别。 以下属性可以重用：ldapDisplayName、schemaIdGuid、OID、mapiID。
   * 在 Windows Server 2008 模式下运行的基于域的 DFS 命名空间，支持基于访问的枚举和增强的可伸缩性。 有关详细信息，请参阅 [Choose a Namespace Type](https://go.microsoft.com/fwlink/?LinkId=180400)（选择命名空间类型）。

### <a name="windows-server-2003-domain-functional-level-features"></a>Windows Server 2003 域功能级别功能

* 提供所有默认的 AD DS 功能、所有在 Windows 2000 本机域功能级别可用的功能，以及下列功能：
   * 域管理工具 Netdom.exe，有了它就可以重命名域控制器。
   * 登录时间戳更新
      * 使用用户或计算机的上次登录时间来更新 lastLogonTimestamp 属性  。 可以在域内复制该属性。
   * 在 **inetOrgPerson** 和用户对象上将 **userPassword** 属性设置为有效密码的功能
   * 重定向用户和计算机容器的功能
      * 默认情况下，已提供了两个已知的容器，用于容纳计算机和用户帐户，即：cn=Computers,<domain root> 和 cn=Users,<domain root>。 该功能可用于定义这些帐户新的已知位置。
   * 授权管理器的功能，可以将其授权策略存储在 AD DS 中
   * 约束的委派
      * 受限制的委派使得应用程序可通过基于 Kerberos 的身份验证充分利用用户凭据的安全委派。
      * 可以将委派限制为仅允许特定的目标服务。
   * 选择性身份验证
      * 有了选择性的身份验证，就可以从受信任林指定允许对信任林中资源服务进行身份验证的用户和组。

## <a name="windows-2000"></a>Windows 2000

支持的域控制器操作系统：

* Windows Server 2008 R2
* Windows Server 2008
* Windows Server 2003
* Windows 2000

### <a name="windows-2000-native-forest-functional-level-features"></a>Windows 2000 本机林功能级别功能

* 提供所有默认的 AD DS 功能。

### <a name="windows-2000-native-domain-functional-level-features"></a>Windows 2000 本机域功能级别功能

* 提供所有默认的 AD DS 功能及以下目录功能：
   * 与分发和安全组对应的通用组。
   * 组嵌套
   * 组转换，允许在安全组与分发组之间进行转换
   * 安全标识符 (SID) 历史记录

## <a name="next-steps"></a>后续步骤

* [提升域功能级别](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753104(v=ws.11))
* [提升林功能级别](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730985(v=ws.11))
