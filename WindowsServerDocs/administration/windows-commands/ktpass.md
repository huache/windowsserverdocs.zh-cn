---
title: ktpass
description: Ktpass 命令的参考文章，该命令为 AD DS 中的主机或服务配置服务器主体名称，并生成 keytab 文件，其中包含服务的共享密钥。
ms.topic: article
ms.assetid: 47087676-311e-41f1-8414-199740d01444
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3bb523d35a1bbf2d15895201855a58e96ebb7772
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87887639"
---
# <a name="ktpass"></a>ktpass

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

Active Directory 域服务 () AD DS 中为主机或服务配置服务器主体名称，并生成一个包含服务共享密钥的 keytab 文件。 .Keytab 文件基于麻省理工学院 (MIT) 对 Kerberos 身份验证协议的实现。 Ktpass 命令行工具允许支持 Kerberos 身份验证的非 Windows 服务使用 Kerberos 密钥发行中心 (KDC) 服务提供的互操作性功能。

## <a name="syntax"></a>语法

```
ktpass
[/out <filename>]
[/princ <principalname>]
[/mapuser <useraccount>]
[/mapop {add|set}] [{-|+}desonly] [/in <filename>]
[/pass {password|*|{-|+}rndpass}]
[/minpass]
[/maxpass]
[/crypto {DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}]
[/itercount]
[/ptype {KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}]
[/kvno <keyversionnum>]
[/answer {-|+}]
[/target]
[/rawsalt] [{-|+}dumpsalt] [{-|+}setupn] [{-|+}setpass <password>]  [/?|/h|/help]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ------------|
| /out`<filename>` | 指定要生成的 Kerberos 版本 keytab 文件的名称。 **注意：** 这是传输到未运行 Windows 操作系统的计算机上的 keytab 文件，然后将其替换或合并为你的现有 keytab 文件 */Etc/Krb5.keytab*。 |
| /princ `<principalname>` | 指定窗体中的主体名称 host/computer.contoso.com@CONTOSO.COM 。 **警告：** 此参数区分大小写。 |
| /mapuser `<useraccount>` | 将由**princ**参数指定的 Kerberos 主体的名称映射到指定的域帐户。 |
| /mapop`{add|set}` | 指定如何设置映射属性。<ul><li>**添加**-添加指定的本地用户名的值。 这是默认设置。</li><li>**Set** -为指定的本地用户名设置数据加密标准 (DES 仅) 加密的值。</li></ul> |
| `{-|+}`desonly | 默认情况下，设置为仅 DES 加密。<ul><li>**+** 为仅 DES 加密设置帐户。</li><li>**-** 针对仅 DES 加密的帐户释放限制。 **重要提示：** 默认情况下，Windows 不支持 DES。</li></ul> |
| /in`<filename>` | 指定要从运行 Windows 操作系统的主计算机读取的 keytab 文件。 |
| /pass`{password|*|{-|+}rndpass}` | 指定由**princ**参数指定的主体用户名的密码。 使用 `*` 提示输入密码。 |
| /minpass | 将随机密码的最小长度设置为15个字符。 |
| /maxpass | 将随机密码的最大长度设置为256个字符。 |
| /crypto`{DES-CBC-CRC|DES-CBC-MD5|RC4-HMAC-NT|AES256-SHA1|AES128-SHA1|All}` | 指定在 keytab 文件中生成的密钥：<ul><li>**DES-CBC-CRC** -用于实现兼容性。</li><li>**DES-CBC-MD5** -更密切地遵从 MIT 实现，并用于兼容性。</li><li>**RC4-HMAC-NT** -采用128位加密。</li><li>**AES256** ---------------------96-96</li><li>   **AES128** ---------------------96-96</li><li>**所有**-可以使用所有受支持的加密类型。</li></ul><p>**注意：** 由于默认设置基于较旧的 MIT 版本，因此应始终使用 `/crypto` 参数。 |
| /itercount | 指定用于 AES 加密的迭代次数。 默认情况下，将忽略非 AES 加密的**itercount** ，并将 AES 加密设置为4096。 |
| /ptype`{KRB5_NT_PRINCIPAL|KRB5_NT_SRV_INST|KRB5_NT_SRV_HST}` | 指定主体类型。<ul><li>**KRB5_NT_PRINCIPAL** - (建议) 的常规主体类型。</li><li>**KRB5_NT_SRV_INST** -用户服务实例</li><li>  **KRB5_NT_SRV_HST** -主机服务实例</li></ul> |
| /kvno`<keyversionnum>` | 指定密钥版本号。 默认值为 1。 |
| /answer`{-|+}` | 设置背景应答模式：<ul><li>**-** 应答自动重置密码提示，**无**。</li><li>**+** 回答 **"是"** 时自动重置密码提示。</li></ul> |
| /target | 设置要使用的域控制器。 默认情况下，将基于主体名称检测域控制器。 如果域控制器名称未解析，则会出现一个对话框，提示输入有效的域控制器。 |
| /rawsalt | 强制 ktpass 在生成密钥时使用 rawsalt 算法。 此参数是可选的。 |
| `{-|+}dumpsalt` | 此参数的输出显示了用于生成密钥的 MIT 盐算法。 |
| `{-|+}setupn` | 将用户主体名称 (UPN) 除 (SPN) 以外的其他服务主体名称。 默认情况下，在 keytab 文件中设置。 |
| `{-|+}setpass <password>` | 在提供时设置用户的密码。 如果使用了 rndpass，则改为生成随机密码。 |
| /? | 显示此命令的帮助。 |

#### <a name="remarks"></a>备注

- 在未运行 Windows 操作系统的系统上运行的服务可以在 AD DS 中配置服务实例帐户。 这允许任何 Kerberos 客户端使用 Windows Kdc 对未运行 Windows 操作系统的服务进行身份验证。

- **/Princ**参数不由 ktpass 计算，并按提供的方式使用。 在生成 Keytab 文件时，不会检查该参数是否与**userPrincipalName**特性值的准确大小写相匹配。 如果没有完全匹配大小写，则使用此 Keytab 文件的区分大小写的 Kerberos 分发可能会出现问题，甚至可能会在预身份验证过程中失败。 从 LDifDE 导出文件中检查和检索正确的**userPrincipalName**属性值。 例如：

    ```
    ldifde /f keytab_user.ldf /d CN=Keytab User,OU=UserAccounts,DC=contoso,DC=corp,DC=microsoft,DC=com /p base /l samaccountname,userprincipalname
    ````

### <a name="examples"></a>示例

若要为未运行 Windows 操作系统的主计算机创建 keytab 文件，必须将该主体映射到该帐户，并设置主机主体密码。

1. 使用 active directory**用户和计算机**管理单元为未运行 Windows 操作系统的计算机上的服务创建用户帐户。 例如，创建名为*User1*的帐户。

2. 使用**ktpass**命令通过键入以下内容设置用户帐户的标识映射：

    ```
    ktpass /princ host/User1.contoso.com@CONTOSO.COM /mapuser User1 /pass MyPas$w0rd /out machine.keytab /crypto all /ptype KRB5_NT_PRINCIPAL /mapop set
    ```

    > [!NOTE]
    > 不能将多个服务实例映射到同一个用户帐户。

3. 将 keytab 文件与未运行 Windows 操作系统的主计算机上的 */Etc/Krb5.keytab*文件合并。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
