---
title: ktpass
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 47087676-311e-41f1-8414-199740d01444
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09f0a715c8addf8694eb75d17f9b8089cad72e56
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724535"
---
# <a name="ktpass"></a>ktpass

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

在 active directory 域服务（AD DS）中为主机或服务配置服务器主体名称，并生成一个包含服务共享密钥的 keytab 文件。 .Keytab 文件基于麻省理工学院 (MIT) 对 Kerberos 身份验证协议的实现。 Ktpass 命令行工具允许支持 Kerberos 身份验证的非 Windows 服务使用 Kerberos 密钥发行中心（KDC）服务提供的互操作性功能。 本主题适用于本主题开头的 "**适用**于" 列表中指定的操作系统版本。  

## <a name="syntax"></a>语法  
```  
ktpass  
[/out <FileName>]   
[/princ <PrincipalName>]   
[/mapuser <UserAccount>]   
[/mapop {add|set}] [{-|+}desonly] [/in <FileName>]  
[/pass {Password|*|{-|+}rndpass}]  
[/minpass]  
[/maxpass]  
[/crypto {DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}]  
[/itercount]  
[/ptype {KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}]  
[/kvno <KeyversionNum>]  
[/answer {-|+}]  
[/target]  
[/rawsalt] [{-|+}dumpsalt] [{-|+}setupn] [{-|+}setpass <Password>]  [/?|/h|/help]  
```  
### <a name="parameters"></a>参数  

|                                             参数                                              |                                                                                                                                                                                                                                                                                                      描述                                                                                                                                                                                                                                                                                                       |
|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                          /out<FileName>                                           |                                                                                                                                                                        指定要生成的 Kerberos 版本 keytab 文件的名称。 **注意：** 这是你传输到未运行 Windows 操作系统的计算机的 keytab 文件，然后将其替换或合并到你的现有 keytab 文件/Etc/Krb5.keytab。                                                                                                                                                                        |
|                                       /princ<PrincipalName>                                       |                                                                                                                                                                                                                   指定窗体host/computer.contoso.com@CONTOSO.COM中的主体名称。 **警告：** 此参数区分大小写。 有关详细信息，请参阅 "[备注](#BKMK_remarks)"。                                                                                                                                                                                                                    |
|                                       /mapuser<UserAccount>                                       |                                                                                                                                                                                                                                                将由**princ**参数指定的 Kerberos 主体的名称映射到指定的域帐户。                                                                                                                                                                                                                                                |
|                                       /mapop {add&#124;set}                                        |                                                                                                                                                                             指定如何设置映射属性。<p>-   **添加添加**指定的本地用户名的值。 这是默认设置。<br />-   **设置**为指定的本地用户名设置仅限数据加密标准（DES）加密的值。                                                                                                                                                                             |
|                                         {-&#124;+} desonly                                          |                                                                                                                                                            默认情况下，设置为仅 DES 加密。<p>-   **+** 为仅 DES 加密设置帐户。<br />-   **-** 针对仅 DES 加密的帐户释放限制。 **重要提示：** 从 Windows 7 和 Windows Server 2008 R2 开始，默认情况下，Windows 不支持 DES。                                                                                                                                                            |
|                                           /in<FileName>                                           |                                                                                                                                                                                                                                                       指定要从运行 Windows 操作系统的主计算机读取的 keytab 文件。                                                                                                                                                                                                                                                        |
|                          /pass {Password&#124;\*&#124; {-&#124;+} rndpass}                           |                                                                                                                                                                                                                                           指定由**princ**参数指定的主体用户名的密码。 使用\*提示输入密码。                                                                                                                                                                                                                                            |
|                                              /minpass                                              |                                                                                                                                                                                                                                                                            将随机密码的最小长度设置为15个字符。                                                                                                                                                                                                                                                                            |
|                                              /maxpass                                              |                                                                                                                                                                                                                                                                           将随机密码的最大长度设置为256个字符。                                                                                                                                                                                                                                                                            |
| /crypto {DES-CBC&#124;DES-CBC&#124;RC4-HMAC&#124;AES256--SHA1&#124;&#124;AES128 | 指定在 keytab 文件中生成的密钥：<p>-   **DES-CBC**用于实现兼容性。<br />-   **DES-CBC**更密切地遵从 MIT 实现，并用于兼容性。<br />-   **RC4-HMAC-NT**采用128位加密。<br />-   **AES256-sha1**使用 AES256--HMAC-96-96-96。<br />-   **AES128-sha1**使用 AES128--HMAC-96-96-96。<br />-   所有支持的加密类型都可以使用的**所有**状态。 **注意：** 默认设置基于较旧的 MIT 版本。 因此， `/crypto`应始终指定。 |
|                                             /itercount                                             |                                                                                                                                                                                                                        指定用于 AES 加密的迭代次数。 默认情况下，将忽略非 AES 加密的**itercount** ，并将其设置为4096以进行 AES 加密。                                                                                                                                                                                                                         |
|               /ptype {KRB5_NT_PRINCIPAL&#124;KRB5_NT_SRV_INST&#124;KRB5_NT_SRV_HST}                |                                                                                                                                                                                         指定主体类型。<p>-   **KRB5_NT_PRINCIPAL**是一般的主体类型（推荐）。<br />-   **KRB5_NT_SRV_INST**是用户服务实例。<br />-   **KRB5_NT_SRV_HST**是主机服务实例。                                                                                                                                                                                         |
|                                       /kvno<KeyversionNum>                                        |                                                                                                                                                                                                                                                                               指定密钥版本号。 默认值为 1。                                                                                                                                                                                                                                                                                |
|                                         /answer {-&#124;+}                                         |                                                                                                                                                                                                                    设置背景应答模式：<p>**-** 应答自动重置密码提示，无。<p>**+** 回答 "是" 时自动重置密码提示。                                                                                                                                                                                                                     |
|                                              /target                                               |                                                                                                                                                                                           设置要使用的域控制器。 默认情况下，将基于主体名称检测域控制器。 如果域控制器名称未解析，则会出现一个对话框，提示输入有效的域控制器。                                                                                                                                                                                           |
|                                              /rawsalt                                              |                                                                                                                                                                                                                                                           强制 ktpass 在生成密钥时使用 rawsalt 算法。 此参数不是必需的。                                                                                                                                                                                                                                                            |
|                                         {-&#124;+} dumpsalt                                         |                                                                                                                                                                                                                                                           此参数的输出显示了用于生成密钥的 MIT 盐算法。                                                                                                                                                                                                                                                            |
|                                          {-&#124;+} setupn                                          |                                                                                                                                                                                                                                          除了服务主体名称（SPN）之外，还设置用户主体名称（UPN）。 默认情况下，在 keytab 文件中设置。                                                                                                                                                                                                                                           |
|                                    {-&#124;+} setpass<Password>                                    |                                                                                                                                                                                                                                                          在提供时设置用户的密码。 如果使用了 rndpass，则改为生成随机密码。                                                                                                                                                                                                                                                           |
|                                       /？ &#124;/h&#124;/help                                        |                                                                                                                                                                                                                                                                                         显示 ktpass 的命令行帮助。                                                                                                                                                                                                                                                                                         |

## <a name="remarks"></a><a name=BKMK_remarks></a>标记  
在未运行 Windows 操作系统的系统上运行的服务可以在 active directory 域服务中配置服务实例帐户。 这允许任何 Kerberos 客户端使用 Windows Kdc 对未运行 Windows 操作系统的服务进行身份验证。  
/Princ 参数不由 ktpass 计算，并按提供的方式使用。 生成 Keytab 文件时，不会进行检查以查看参数是否与**userPrincipalName**特性值的准确大小写匹配。 使用此 Keytab 文件的区分大小写的 Kerberos 分发在没有完全大小写匹配时可能会有问题，并且在预身份验证过程中可能会失败。 从 LDifDE 导出文件中检查并检索正确的**userPrincipalName**属性值。 例如：  
```  
ldifde /f keytab_user.ldf /d CN=Keytab User,OU=UserAccounts,DC=contoso,DC=corp,DC=microsoft,DC=com /p base /l samaccountname,userprincipalname  
```  
## <a name="examples"></a>示例  
为了说明如何在用户 Sample1 的当前目录中创建 keytab 文件 keytab。 （将此文件与未运行 Windows 操作系统的主计算机上的 Krb5.conf 文件合并。）将为常规主体类型的所有支持的加密类型创建 keytab 文件。  
若要为未运行 Windows 操作系统的主计算机生成 keytab 文件，请使用以下步骤将主体映射到该帐户并设置主机主体密码：  
1.  使用 active directory 用户和计算机管理单元为未运行 Windows 操作系统的计算机上的服务创建用户帐户。 例如，创建名为 Sample1 的帐户。  
2.  通过在命令提示符下键入以下内容，使用 ktpass 为用户帐户设置标识映射：  
    ```  
    ktpass /princ host/Sample1.contoso.com@CONTOSO.COM /mapuser Sample1 /pass MyPas$w0rd /out Sample1.keytab /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set   
    ```  

    > [!NOTE]  
    > 不能将多个服务实例映射到同一个用户帐户。  

3.  将 keytab 文件与未运行 Windows 操作系统的主计算机上的/Etc/Krb5.keytab 文件合并。 

## <a name="additional-references"></a>其他参考  
- [命令行语法项](command-line-syntax-key.md)  
