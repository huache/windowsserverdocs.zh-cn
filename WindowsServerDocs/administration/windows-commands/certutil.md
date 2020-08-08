---
title: certutil
description: Certutil 命令的参考文章，这是一个命令行程序，可将证书颁发机构转储并显示 (CA) 配置信息、配置证书服务、备份和还原 CA 组件以及验证证书、密钥对和证书链。
ms.topic: article
ms.assetid: c264ccf0-ba1e-412b-9dd3-d77dd9345ad9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: afaf0c75350cfb4121d0ebc664469f4494afe8c7
ms.sourcegitcommit: 68444968565667f86ee0586ed4c43da4ab24aaed
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87992951"
---
# <a name="certutil"></a>certutil

Certutil.exe 是命令行程序，作为证书服务的一部分进行安装。 你可以使用 certutil.exe 来转储和显示证书颁发机构 (CA) 配置信息、配置证书服务、备份和还原 CA 组件以及验证证书、密钥对和证书链。

如果 certutil 在没有其他参数的证书颁发机构上运行，则它将显示当前的证书颁发机构配置。 如果在非证书颁发机构上运行 certutil，则该命令默认为运行 `certutil [-dump]` 命令。

> [!IMPORTANT]
> 更早版本的 certutil 可能不提供本文档中所述的所有选项。 可以通过运行或查看 certutil 的特定版本提供的所有选项 `certutil -?` `certutil <parameter> -?` 。

## <a name="parameters"></a>parameters

### <a name="-dump"></a>-dump

转储配置信息或文件。

```
certutil [options] [-dump]
certutil [options] [-dump] file
```

```
[-f] [-silent] [-split] [-p password] [-t timeout]
```

### <a name="-asn"></a>-asn

分析一个 asn.1 文件。

```
certutil [options] -asn file [type]
```

`[type]`：数值 CRYPT_STRING_ * 解码类型

### <a name="-decodehex"></a>-decodehex

对十六进制编码的文件进行解码。

```
certutil [options] -decodehex infile outfile [type]
```

`[type]`： numeric CRYPT_STRING_ * 编码类型

```
[-f]
```

### <a name="-decode"></a>-解码

对 Base64 编码的文件进行解码。

```
certutil [options] -decode infile outfile
```

```
[-f]
```

### <a name="-encode"></a>-编码

将文件编码为 Base64。

```
certutil [options] -encode infile outfile
```

```
[-f] [-unicodetext]
```

### <a name="-deny"></a>-deny

拒绝挂起的请求。

```
certutil [options] -deny requestID
```

```
[-config Machine\CAName]
```

### <a name="-resubmit"></a>-重新提交

重新提交挂起的请求。

```
certutil [options] -resubmit requestId
```

```
[-config Machine\CAName]
```

### <a name="-setattributes"></a>-setattributes

设置挂起证书请求的属性。

```
certutil [options] -setattributes RequestID attributestring
```

其中：

- **requestID**是挂起请求的数值请求 ID。

- **attributestring**是请求属性的名称和值对。

```
[-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 名称和值必须用冒号分隔，而多个名称、值对必须以换行符分隔。 例如： `CertificateTemplate:User\nEMail:User@Domain.com` `\n` 序列转换为换行符的位置。

### <a name="-setextension"></a>-setextension

设置挂起证书请求的扩展。

```
certutil [options] -setextension requestID extensionname flags {long | date | string | \@infile}
```

其中：

- **requestID**是挂起请求的数值请求 ID。

- **extensionname**是扩展的 ObjectId 字符串。

- **flags**设置扩展的优先级。 `0`建议将 `1` 扩展设置为 "严重"， `2` 禁用扩展，并 `3` 同时执行这两个扩展。

```
[-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 如果最后一个参数是数值，则将其视为一个**长整型值**。

- 如果最后一个参数可以分析为日期，则该参数将被视为一个**日期**。

- 如果最后一个参数以开头 `\@` ，则会将该标记的其余部分当作带有二进制数据的文件名或 ascii 文本十六进制转储。

- 如果最后一个参数是其他参数，则将其视为字符串。

### <a name="-revoke"></a>-revoke

吊销证书。

```
certutil [options] -revoke serialnumber [reason]
```

其中：

- **serialnumber**是要吊销的证书序列号的逗号分隔列表。

- **原因**是吊销原因的数字或符号表示形式，其中包括：

  - **0. CRL_REASON_UNSPECIFIED**未指定的 (默认) 

  - **1. CRL_REASON_KEY_COMPROMISE**密钥泄露

  - **2. CRL_REASON_CA_COMPROMISE**证书颁发机构泄露

  - **3. CRL_REASON_AFFILIATION_CHANGED**从属关系已更改

  - **4. CRL_REASON_SUPERSEDED**取代

  - **5.** 操作的 CRL_REASON_CESSATION_OF_OPERATION 哈

  - **6. CRL_REASON_CERTIFICATE_HOLD**证书保留

  - **8. CRL_REASON_REMOVE_FROM_CRL** -从 CRL 中删除

  - **1. 解除**吊销-解除吊销

```
[-config Machine\CAName]
```

### <a name="-isvalid"></a>-isvalid

显示当前证书的处置。

```
certutil [options] -isvalid serialnumber | certhash
```

```
[-config Machine\CAName]
```

### <a name="-getconfig"></a>-getconfig

获取默认配置字符串。

```
certutil [options] -getconfig
```

```
[-config Machine\CAName]
```

### <a name="-ping"></a>-ping

尝试联系 Active Directory 的证书服务请求接口。

```
certutil [options] -ping [maxsecondstowait | camachinelist]
```

其中：

- **camachinelist**是以逗号分隔的 CA 计算机名称的列表。 对于单台计算机，使用终止逗号。 此选项还显示每个 CA 计算机的站点成本。

```
[-config Machine\CAName]
```

### <a name="-cainfo"></a>-cainfo

显示有关证书颁发机构的信息。

```
certutil [options] -cainfo [infoname [index | errorcode]]
```

其中：

- **infoname**根据以下 infoname 参数语法，指示要显示的 CA 属性：

  - **文件**文件版本

  - **产品**-产品版本

  - **exitcount** -退出模块计数

  - **退出 `[index]` **-退出模块说明

  - **策略**-策略模块说明

  - **名称**-CA 名称

  - **sanitizedname** -净化的 CA 名称

  - **dsname** -净化了 CA 短名称 (DS 名称) 

  - **共享文件夹**-共享文件夹

  - **error1**错误消息文本

  - **error2**错误消息文本和错误代码

  - **类型**-CA 类型

  - **信息**-CA 信息

  - **父**-父 CA

  - **certcount** -CA 证书计数

  - **xchgcount** -CA exchange 证书计数

  - **kracount** -KRA 证书计数

  - **kraused** -KRA cert 使用计数

  - **propidmax** -最大 CA PropId

  - **certstate `[index]` **-CA 证书

  - **certversion `[index]` **-CA 证书版本

  - **certstatuscode `[index]` **-CA 证书验证状态

  - **crlstate `[index]` **-CRL

  - **krastate `[index]` **-KRA 证书

  - **crossstate + `[index]` **-转发交叉证书

  - **crossstate- `[index]` **-后向交叉证书

  - **证书 `[index]` **-CA 证书

  - **certchain `[index]` **-CA 证书链

  - **certcrlchain `[index]` **-带有 Crl 的 CA 证书链

  - **xchg `[index]` **-CA exchange 证书

  - **xchgchain `[index]` **-CA exchange 证书链

  - **xchgcrlchain `[index]` **-带有 Crl 的 CA exchange 证书链

  - **kra `[index]` **-KRA 证书

  - **交叉 + `[index]` **-转发交叉证书

  - **跨 `[index]` **-后向交叉证书

  - **CRL `[index]` **-基本 CRL

  - **deltacrl `[index]` **-增量 CRL

  - **crlstatus `[index]` **-CRL 发布状态

  - **deltacrlstatus `[index]` **-增量 CRL 发布状态

  - **dns** -dns 名称

  - **角色**-角色分隔

  - **广告**-高级服务器

  - **模板**-模板

  - **csp `[index]` **-OCSP Url

  - **aia `[index]` **-AIA Url

  - **cdp `[index]` **-CDP Url

  - **localename** -CA 区域设置名称

  - **subjecttemplateoids** -使用者模板 oid

  - **&#42;** -显示所有属性

- **index**是从零开始的可选属性索引。

- **错误代码是数字**错误代码。

```
[-f] [-split] [-config Machine\CAName]
```

### <a name="-cacert"></a>-ca. cert

检索证书颁发机构的证书。

```
certutil [options] -ca.cert outcacertfile [index]
```

其中：

- **outcacertfile**是输出文件。

- **index**是 CA 证书续订索引 (默认为最近) 。

```
[-f] [-split] [-config Machine\CAName]
```

### <a name="-cachain"></a>-ca。

检索证书颁发机构的证书链。

```
certutil [options] -ca.chain outcacertchainfile [index]
```

其中：

- **outcacertchainfile**是输出文件。

- **index**是 CA 证书续订索引 (默认为最近) 。

```
[-f] [-split] [-config Machine\CAName]
```

### <a name="-getcrl"></a>-getcrl

获取 (CRL) 的证书吊销列表。

certutil [options]-getcrl outfile [index] [delta]

其中：

- **index**是 (默认为 crl 进行最新密钥) 的 crl 索引或密钥索引。

- **增量**是 (默认为基本 crl) 的增量 crl。

```
[-f] [-split] [-config Machine\CAName]
```

### <a name="-crl"></a>-crl

 (Crl) 或增量 Crl 发布新的证书吊销列表。

```
certutil [options] -crl [dd:hh | republish] [delta]
```

其中：

- **dd： hh**是新的 CRL 有效期（以天和小时为单位）。

- 重新**发布**重新发布最新的 crl。

- **delta**仅发布增量 crl (默认为基本和增量 crl) 。

```
[-split] [-config Machine\CAName]
```

### <a name="-shutdown"></a>-shutdown

关闭 Active Directory 证书服务。

```
certutil [options] -shutdown
```

```
[-config Machine\CAName]
```

### <a name="-installcert"></a>-installcert

安装证书颁发机构证书。

```
certutil [options] -installcert [cacertfile]
```

```
[-f] [-silent] [-config Machine\CAName]
```

### <a name="-renewcert"></a>-renewcert

续订证书颁发机构证书。

```
certutil [options] -renewcert [reusekeys] [Machine\ParentCAName]
```

- 使用 `-f` 忽略未完成的续订请求，并生成新的请求。

```
[-f] [-silent] [-config Machine\CAName]
```

### <a name="-schema"></a>-架构

转储证书的架构。

```
certutil [options] -schema [ext | attrib | cRL]
```
其中：

- 该命令默认为请求和证书表。

- **ext**是扩展表。

- **attribute**是属性表。

- **crl**是 crl 表。

```
[-split] [-config Machine\CAName]
```

### <a name="-view"></a>-view

转储证书视图。

```
certutil [options] -view [queue | log | logfail | revoked | ext | attrib | crl] [csv]
```

其中：

- **队列**转储特定请求队列。

- **日志**转储已颁发或已吊销的证书，以及任何失败的请求。

- **logfail**转储失败的请求。

- 已**吊销**转储吊销的证书。

- **ext**会转储扩展表。

- **属性**转储属性表。

- **crl**将转储 crl 表。

- **csv**使用逗号分隔值提供输出。

```
[-silent] [-split] [-config Machine\CAName] [-restrict RestrictionList] [-out ColumnList]
```

#### <a name="remarks"></a>备注

- 若要显示所有条目的**StatusCode**列，请键入`-out StatusCode`

- 若要显示最后一个条目的所有列，请键入：`-restrict RequestId==$`

- 若要显示三个请求的**RequestID**和**处置**，请键入：`-restrict requestID>37,requestID<40 -out requestID,disposition`

- 若要显示所有基本 Crl 的行 Id**行 id**和**CRL 号**，请键入：`-restrict crlminbase=0 -out crlrowID,crlnumber crl`

- 若要显示，请键入：`-v -restrict crlminbase=0,crlnumber=3 -out crlrawcrl crl`

- 若要显示整个 CRL 表，请键入：`CRL`

- 用于 `Date[+|-dd:hh]` 日期限制。

- 用于 `now+dd:hh` 相对于当前时间的日期。

### <a name="-db"></a>-db

转储原始数据库。

```
certutil [options] -db
```

```
[-config Machine\CAName] [-restrict RestrictionList] [-out ColumnList]
```

### <a name="-deleterow"></a>-deleterow

从服务器数据库中删除行。

```
certutil [options] -deleterow rowID | date [request | cert | ext | attrib | crl]
```

其中：

- **请求**会根据提交日期删除失败和挂起的请求。

- **cert**会根据过期日期删除过期和吊销的证书。

- **ext**删除扩展表。

- **属性**删除属性表。

- **crl**删除 crl 表。

```
[-f] [-config Machine\CAName]
```

#### <a name="examples"></a>示例

- 若要删除在2001年1月22日提交的失败和挂起的请求，请键入：`1/22/2001 request`

- 若要删除所有已在2001年1月22日过期的证书，请键入：`1/22/2001 cert`

- 若要删除 RequestID 37 的证书行、属性和扩展，请键入：`37`

- 若要删除由2001年1月22日过期的 Crl，请键入：`1/22/2001 crl`

### <a name="-backup"></a>-backup

备份 Active Directory 证书服务。

```
certutil [options] -backup backupdirectory [incremental] [keeplog]
```

其中：

- **backupdirectory**是用于存储备份数据的目录。

- **增量**备份仅执行增量备份 (默认为完整备份) 。

- **keeplog**保留数据库日志文件 (默认情况下) 截断日志文件。

```
[-f] [-config Machine\CAName] [-p Password]
```

### <a name="-backupdb"></a>-backupdb

备份 Active Directory 证书服务数据库。

```
certutil [options] -backupdb backupdirectory [incremental] [keeplog]
```

其中：

- **backupdirectory**是用于存储备份数据库文件的目录。

- **增量**备份仅执行增量备份 (默认为完整备份) 。

- **keeplog**保留数据库日志文件 (默认情况下) 截断日志文件。

```
[-f] [-config Machine\CAName]
```

### <a name="-backupkey"></a>-backupkey

备份 Active Directory 证书服务证书和私钥。

```
certutil [options] -backupkey backupdirectory
```

其中：

- **backupdirectory**是用于存储备份的 PFX 文件的目录。

```
[-f] [-config Machine\CAName] [-p password] [-t timeout]
```

### <a name="-restore"></a>-restore

还原 Active Directory 证书服务。

```
certutil [options] -restore backupdirectory
```

其中：

- **backupdirectory**是包含要还原的数据的目录。

```
[-f] [-config Machine\CAName] [-p password]
```

### <a name="-restoredb"></a>-restoredb

还原 Active Directory 证书服务数据库。

```
certutil [options] -restoredb backupdirectory
```

其中：

- **backupdirectory**是包含要还原的数据库文件的目录。

```
[-f] [-config Machine\CAName]
```

### <a name="-restorekey"></a>-restorekey

还原 Active Directory 证书服务证书和私钥。

```
certutil [options] -restorekey backupdirectory | pfxfile
```

其中：

- **backupdirectory**是包含要还原的 PFX 文件的目录。

```
[-f] [-config Machine\CAName] [-p password]
```

### <a name="-importpfx"></a>-importpfx

导入证书和私钥。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -importpfx [certificatestorename] pfxfile [modifiers]
```

其中：

- **certificatestorename**是证书存储的名称。

- **修饰符**是逗号分隔的列表，其中可以包含以下一项或多项：

  1. **AT_SIGNATURE** -将 keyspec 更改为签名

  2. **AT_KEYEXCHANGE** -将 keyspec 更改为密钥交换

  3. **NoExport** -使私钥不可导出

  4. **NoCert** -不导入证书

  5. **NoChain** -不导入证书链

  6. **NoRoot** -不导入根证书

  7. **保护**-通过使用密码保护密钥

  8. **NoProtect** -不使用密码保护密钥

```
[-f] [-user] [-p password] [-csp provider]
```

#### <a name="remarks"></a>备注

- 默认为 "个人计算机存储"。

### <a name="-dynamicfilelist"></a>-dynamicfilelist

显示动态文件列表。

```
certutil [options] -dynamicfilelist
```

```
[-config Machine\CAName]
```

### <a name="-databaselocations"></a>-databaselocations

显示数据库位置。

```
certutil [options] -databaselocations
```

```
[-config Machine\CAName]
```

### <a name="-hashfile"></a>-hashfile

生成并显示文件的加密哈希。

```
certutil [options] -hashfile infile [hashalgorithm]
```

### <a name="-store"></a>-存储

转储证书存储区。

```
certutil [options] -store [certificatestorename [certID [outputfile]]]
```

其中：

- **certificatestorename**是证书存储区名称。 例如：

  - `My, CA (default), Root,`

  - `ldap:///CN=Certification Authorities,CN=Public Key Services,CN=Services,CN=Configuration,DC=cpandl,DC=com?cACertificate?one?objectClass=certificationAuthority (View Root Certificates)`

  - `ldap:///CN=CAName,CN=Certification Authorities,CN=Public Key Services,CN=Services,CN=Configuration,DC=cpandl,DC=com?cACertificate?base?objectClass=certificationAuthority (Modify Root Certificates)`

  - `ldap:///CN=CAName,CN=MachineName,CN=CDP,CN=Public Key Services,CN=Services,CN=Configuration,DC=cpandl,DC=com?certificateRevocationList?base?objectClass=cRLDistributionPoint (View CRLs)`

  - `ldap:///CN=NTAuthCertificates,CN=Public Key Services,CN=Services,CN=Configuration,DC=cpandl,DC=com?cACertificate?base?objectClass=certificationAuthority (Enterprise CA Certificates)`

  - `ldap: (AD computer object certificates)`

  - `-user ldap: (AD user object certificates)`

- **证书 id**是证书或 CRL 匹配令牌。 这可以是序列号、SHA-1 证书、CRL、CTL 或公钥哈希、数字证书索引 (0、1等等) 、数字 CRL 索引 ( .0、.1 等) 、数字 CTL 索引 (。0、.。1等) 、公钥、签名或扩展 ObjectId、证书使用者公用名、电子邮件地址、UPN 或 DNS 名称、密钥容器名称或 CSP 名称、模板名称、ObjectId、EKU 或应用程序策略 ObjectId 或 CRL 颁发者公用名。 其中许多项可能会导致多个匹配项。

- **outputfile**是用于保存匹配证书的文件。

```
[-f] [-user] [-enterprise] [-service] [-grouppolicy] [-silent] [-split] [-dc DCName]
```

#### <a name="options"></a>选项

- `-user`选项访问用户存储而不是计算机存储。

- `-enterprise`选项访问计算机企业应用商店。

- `-service`选项访问计算机服务存储。

- `-grouppolicy`选项访问计算机组策略存储。

例如：

- `-enterprise NTAuth`

- `-enterprise Root 37`

- `-user My 26e0aaaf000000000004`

- `CA .11`

### <a name="-addstore"></a>-addstore

向存储区添加证书。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -addstore certificatestorename infile
```

其中：

- **certificatestorename**是证书存储区名称。

- **infile**是要添加到存储中的证书或 CRL 文件。

```
[-f] [-user] [-enterprise] [-grouppolicy] [-dc DCName]
```

### <a name="-delstore"></a>-delstore

从存储区中删除证书。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -delstore certificatestorename certID
```

其中：

- **certificatestorename**是证书存储区名称。

- **证书 id**是证书或 CRL 匹配令牌。

```
[-enterprise] [-user] [-grouppolicy] [-dc DCName]
```

### <a name="-verifystore"></a>-verifystore

验证存储区中的证书。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -verifystore certificatestorename [certID]
```

其中：

- **certificatestorename**是证书存储区名称。

- **证书 id**是证书或 CRL 匹配令牌。

```
[-enterprise] [-user] [-grouppolicy] [-silent] [-split] [-dc DCName] [-t timeout]
```

### <a name="-repairstore"></a>-repairstore

修复密钥关联或更新证书属性或密钥安全描述符。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -repairstore certificatestorename certIDlist [propertyinffile | SDDLsecuritydescriptor]
```

其中：

- **certificatestorename**是证书存储区名称。

- **certIDlist**是以逗号分隔的证书或 CRL 匹配令牌列表。 有关详细信息，请参阅 `-store certID` 本文中的说明。

- **propertyinffile**是包含外部属性的 INF 文件，其中包括：

  ```
  [Properties]
      19 = Empty ; Add archived property, OR:
      19 =       ; Remove archived property

      11 = {text}Friendly Name ; Add friendly name property

      127 = {hex} ; Add custom hexadecimal property
          _continue_ = 00 01 02 03 04 05 06 07 08 09 0a 0b 0c 0d 0e 0f
          _continue_ = 10 11 12 13 14 15 16 17 18 19 1a 1b 1c 1d 1e 1f

      2 = {text} ; Add Key Provider Information property
        _continue_ = Container=Container Name&
        _continue_ = Provider=Microsoft Strong Cryptographic Provider&
        _continue_ = ProviderType=1&
        _continue_ = Flags=0&
        _continue_ = KeySpec=2

      9 = {text} ; Add Enhanced Key Usage property
        _continue_ = 1.3.6.1.5.5.7.3.2,
        _continue_ = 1.3.6.1.5.5.7.3.1,
  ```

```
[-f] [-enterprise] [-user] [-grouppolicy] [-silent] [-split] [-csp provider]
```

### <a name="-viewstore"></a>-viewstore

转储证书存储区。 有关详细信息，请参阅 `-store` 本文中的参数。

```
certutil [options] -viewstore [certificatestorename [certID [outputfile]]]
```

其中：

- **certificatestorename**是证书存储区名称。

- **证书 id**是证书或 CRL 匹配令牌。

- **outputfile**是用于保存匹配证书的文件。

```
[-f] [-user] [-enterprise] [-service] [-grouppolicy] [-dc DCName]
```

#### <a name="options"></a>选项

- `-user`选项访问用户存储而不是计算机存储。

- `-enterprise`选项访问计算机企业应用商店。

- `-service`选项访问计算机服务存储。

- `-grouppolicy`选项访问计算机组策略存储。

例如：

- `-enterprise NTAuth`

- `-enterprise Root 37`

- `-user My 26e0aaaf000000000004`

- `CA .11`

### <a name="-viewdelstore"></a>-viewdelstore

从存储区中删除证书。

```
certutil [options] -viewdelstore [certificatestorename [certID [outputfile]]]
```

其中：

- **certificatestorename**是证书存储区名称。

- **证书 id**是证书或 CRL 匹配令牌。

- **outputfile**是用于保存匹配证书的文件。

```
[-f] [-user] [-enterprise] [-service] [-grouppolicy] [-dc DCName]
```

#### <a name="options"></a>选项

- `-user`选项访问用户存储而不是计算机存储。

- `-enterprise`选项访问计算机企业应用商店。

- `-service`选项访问计算机服务存储。

- `-grouppolicy`选项访问计算机组策略存储。

例如：

- `-enterprise NTAuth`

- `-enterprise Root 37`

- `-user My 26e0aaaf000000000004`

- `CA .11`

### <a name="-dspublish"></a>-dspublish

将 (CRL) 的证书或证书吊销列表发布到 Active Directory。

```
certutil [options] -dspublish certfile [NTAuthCA | RootCA | SubCA | CrossCA | KRA | User | Machine]
```

```
certutil [options] -dspublish CRLfile [DSCDPContainer [DSCDPCN]]
```

其中：

- **certfile**是要发布的证书文件的名称。

- **NTAuthCA**会将证书发布到 DS 企业应用商店。

- **Rootca.cer**会将证书发布到 DS 受信任的根存储。

- **SubCA**将 CA 证书发布到 DS CA 对象。

- **CrossCA**会将交叉证书发布到 DS CA 对象。

- **KRA**将证书发布到 DS 密钥恢复代理对象。

- **用户**将证书发布到用户 DS 对象。

- **计算机**会将证书发布到计算机 DS 对象。

- **CRLfile**是要发布的 CRL 文件的名称。

- **DSCDPContainer**是 DS CDP 容器 CN，通常是 CA 计算机的名称。

- **DSCDPCN**是 DS CDP 对象 CN，通常基于净化的 CA 短名称和密钥索引。

- 使用 `-f` 创建新的 DS 对象。

```
[-f] [-user] [-dc DCName]
```

### <a name="-adtemplate"></a>-adtemplate

显示 Active Directory 模板。

```
certutil [options] -adtemplate [template]
```

```
[-f] [-user] [-ut] [-mt] [-dc DCName]
```

### <a name="-template"></a>-template

显示证书模板。

```
certutil [options] -template [template]
```

```
[-f] [-user] [-silent] [-policyserver URLorID] [-anonymous] [-kerberos] [-clientcertificate clientcertID] [-username username] [-p password]
```

### <a name="-templatecas"></a>-templatecas

显示证书模板 (Ca) 的证书颁发机构。

```
certutil [options] -templatecas template
```

```
[-f] [-user] [-dc DCName]
```

### <a name="-catemplates"></a>-catemplates.txt

显示证书颁发机构的模板。

```
certutil [options] -catemplates [template]
```

```
[-f] [-user] [-ut] [-mt] [-config Machine\CAName] [-dc DCName]
```

### <a name="-setcasites"></a>-setcasites

管理站点名称，包括设置、验证和删除证书颁发机构站点名称

```
certutil [options] -setcasites [set] [sitename]
certutil [options] -setcasites verify [sitename]
certutil [options] -setcasites delete
```

其中：

- 仅当以单个证书颁发机构为目标时才允许**sitename** 。

```
[-f] [-config Machine\CAName] [-dc DCName]
```

#### <a name="remarks"></a>备注

- `-config`选项以单个证书颁发机构为目标 (默认值为 "所有 ca) "。

- `-f`选项可用于重写指定**sitename**的验证错误或删除所有 CA sitenames 引用。

> [!NOTE]
> 有关为 Active Directory 域服务 (配置 Ca 的详细信息 AD DS) 站点感知，请参阅[AD DS 站点感知 AD CS 和 PKI 客户端](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11))。

### <a name="-enrollmentserverurl"></a>-enrollmentserverURL

显示、添加或删除与 CA 关联的注册服务器 Url。

```
certutil [options] -enrollmentServerURL [URL authenticationtype [priority] [modifiers]]
certutil [options] -enrollmentserverURL URL delete
```

其中：

- **authenticationtype**指定以下客户端身份验证方法之一，同时添加 URL：

  1. **kerberos** -使用 kerberos SSL 凭据。

  2. **用户名**-使用命名帐户作为 SSL 凭据。

  3. **clientcertificate**：-使用 X.509 证书 SSL 凭据。

  4. **匿名**-使用匿名 SSL 凭据。

- **删除**删除与 CA 关联的指定 URL。

- **priority** `1` 如果添加 URL 时未指定，则优先级默认值为。

- **修饰符**是逗号分隔的列表，其中包括以下一项或多项：

1. **allowrenewalsonly** -只能通过此 URL 将续订请求提交到此 CA。

2. **allowkeybasedrenewal** -允许使用在 AD 中没有关联帐户的证书。 这仅适用于 clientcertificate 和 allowrenewalsonly 模式

```
[-config Machine\CAName] [-dc DCName]
```

### <a name="-adca"></a>-adca

显示 Active Directory 证书颁发机构。

```
certutil [options] -adca [CAName]
```

```
[-f] [-split] [-dc DCName]
```

### <a name="-ca"></a>-ca

显示注册策略证书颁发机构。

```
certutil [options] -CA [CAName | templatename]
```

```
[-f] [-user] [-silent] [-split] [-policyserver URLorID] [-anonymous] [-kerberos] [-clientcertificate clientcertID] [-username username] [-p password]
```

### <a name="-policy"></a>-policy

显示注册策略。

```
[-f] [-user] [-silent] [-split] [-policyserver URLorID] [-anonymous] [-kerberos] [-clientcertificate clientcertID] [-username username] [-p password]
```

### <a name="-policycache"></a>-policycache

显示或删除注册策略缓存条目。

```
certutil [options] -policycache [delete]
```

其中：

- **删除**删除策略服务器缓存条目。

- **-f**删除所有缓存项

```
[-f] [-user] [-policyserver URLorID]
```

### <a name="-credstore"></a>-credstore

显示、添加或删除凭据存储项。

```
certutil [options] -credstore [URL]
certutil [options] -credstore URL add
certutil [options] -credstore URL delete
```

其中：

- **Url**是目标 url。 你还可以使用 `*` 匹配所有条目或 `https://machine*` 匹配 URL 前缀。

- **添加**"添加凭据存储项"。 使用此选项还需要使用 SSL 凭据。

- **删除**删除凭据存储条目。

- **-f**将覆盖单个项或删除多个项。

```
[-f] [-user] [-silent] [-anonymous] [-kerberos] [-clientcertificate clientcertID] [-username username] [-p password]
```

### <a name="-installdefaulttemplates"></a>-installdefaulttemplates

安装默认证书模板。

```
certutil [options] -installdefaulttemplates
```

```
[-dc DCName]
```

### <a name="-urlcache"></a>-URLcache

显示或删除 URL 缓存条目。

```
certutil [options] -URLcache [URL | CRL | * [delete]]
```

其中：

- **Url**是缓存的 url。

- **Crl**仅在所有缓存的 CRL url 上运行。

- **&#42;** 对所有缓存的 url 进行操作。

- **删除**从当前用户的本地缓存中删除相关的 url。

- **-f**强制提取特定 URL 并更新缓存。

```
[-f] [-split]
```

### <a name="-pulse"></a>-脉冲

脉冲自动注册事件。

```
certutil [options] -pulse
```

```
[-user]
```

### <a name="-machineinfo"></a>-machineinfo

显示 Active Directory 计算机对象的相关信息。

```
certutil [options] -machineinfo domainname\machinename$
```

### <a name="-dcinfo"></a>-DCInfo

显示有关域控制器的信息。 默认显示 DC 证书，无需验证。

```
certutil [options] -DCInfo [domain] [verify | deletebad | deleteall]
```

```
[-f] [-user] [-urlfetch] [-dc DCName] [-t timeout]
```

> [!TIP]
> 能够指定 Active Directory 域服务 (AD DS) 域 **[域]** ，并指定在 Windows Server 2012 中添加 (**dc**) 的域控制器。 若要成功运行此命令，你必须使用属于**Domain admins**或**Enterprise admins**成员的帐户。 此命令的行为修改如下：<ol><li>1. 如果未指定域并且未指定特定的域控制器，则此选项将返回要从默认域控制器处理的域控制器的列表。</li><li>2. 如果未指定域，但指定了域控制器，则会生成指定域控制器上的证书报表。</li><li>3. 如果指定了域，但未指定域控制器，则会在列表中的每个域控制器的证书上生成域控制器的列表。</li><li>4. 如果指定了域和域控制器，则会从目标域控制器生成域控制器的列表。 还会生成列表中每个域控制器的证书报表。</li></ol>
>
>例如，假设有一个名为 CPANDL 的域，其中包含名为 CPANDL-DC1 的域控制器。 可以运行以下命令，从 CPANDL-DC1 检索域控制器及其证书的列表：`certutil -dc cpandl-dc1 -DCInfo cpandl`

### <a name="-entinfo"></a>-entinfo

显示有关企业证书颁发机构的信息。

```
certutil [options] -entinfo domainname\machinename$
```

```
[-f] [-user]
```

### <a name="-tcainfo"></a>-tcainfo

显示有关证书颁发机构的信息。

```
certutil [options] -tcainfo [domainDN | -]
```

```
[-f] [-enterprise] [-user] [-urlfetch] [-dc DCName] [-t timeout]
```

### <a name="-scinfo"></a>-scinfo

显示有关智能卡的信息。

```
certutil [options] -scinfo [readername [CRYPT_DELETEKEYSET]]
```

其中：

- **CRYPT_DELETEKEYSET**删除智能卡上的所有密钥。

```
[-silent] [-split] [-urlfetch] [-t timeout]
```

### <a name="-scroots"></a>-scroots

管理智能卡根证书。

```
certutil [options] -scroots update [+][inputrootfile] [readername]
certutil [options] -scroots save \@in\\outputrootfile [readername]
certutil [options] -scroots view [inputrootfile | readername]
certutil [options] -scroots delete [readername]
```

```
[-f] [-split] [-p Password]
```

### <a name="-verifykeys"></a>-verifykeys

验证公钥或私钥集。

```
certutil [options] -verifykeys [keycontainername cacertfile]
```

其中：

- **cspparameters.keycontainername**是要验证的密钥的密钥容器名称。 此选项默认为 "计算机密钥"。 若要切换到用户密钥，请使用 `-user` 。

- **cacertfile**签名或加密证书文件。

```
[-f] [-user] [-silent] [-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 如果未指定任何参数，则将根据其私钥验证每个签名 CA 证书。

- 只能对本地 CA 或本地密钥执行此操作。

### <a name="-verify"></a>-验证

验证证书、证书吊销列表 (CRL) 或证书链。

```
certutil [options] -verify certfile [applicationpolicylist | - [issuancepolicylist]]
certutil [options] -verify certfile [cacertfile [crossedcacertfile]]
certutil [options] -verify CRLfile cacertfile [issuedcertfile]
certutil [options] -verify CRLfile cacertfile [deltaCRLfile]
```

其中：

- **certfile**是要验证的证书的名称。

- **applicationpolicylist**是可选的以逗号分隔的所需应用程序策略 ObjectIds 列表。

- **issuancepolicylist**是可选的以逗号分隔的所需颁发策略 ObjectIds 列表。

- **cacertfile**是要根据其进行验证的可选发证 CA 证书。

- **crossedcacertfile**是由**certfile**交叉认证的可选证书。

- **CRLfile**是用于验证**cacertfile**的 CRL 文件。

- **issuedcertfile**是 CRLfile 涵盖的可选颁发证书。

- **deltaCRLfile**是可选的增量 CRL 文件。

```
[-f] [-enterprise] [-user] [-silent] [-split] [-urlfetch] [-t timeout]
```

#### <a name="remarks"></a>备注

- 使用**applicationpolicylist**会将生成限制为仅对指定的应用程序策略使用有效的链。

- 使用**issuancepolicylist**会将生成限制为仅限指定的颁发策略的证书链。

- 使用**cacertfile**将根据**certfile**或**CRLfile**验证文件中的字段。

- 使用**issuedcertfile**将根据**CRLfile**验证文件中的字段。

- 使用 deltaCRLfile 将根据**certfile**验证文件中的字段。

- 如果未指定**cacertfile** ，则将针对**certfile**生成并验证整个链。

- 如果同时指定了**cacertfile**和**crossedcacertfile** ，则会对照**certfile**来验证这两个文件中的字段。

### <a name="-verifyctl"></a>-verifyCTL

验证 AuthRoot 或不允许的证书 CTL。

```
certutil [options] -verifyCTL CTLobject [certdir] [certfile]
```

其中：

- **CTLobject**标识要验证的 CTL，其中包括：

  - **AuthRootWU** -从 URL 缓存读取 AuthRoot CAB 和匹配的证书。 使用 `-f` 从 Windows 更新下载。

  - **DisallowedWU** -从 URL 缓存读取不允许的证书 CAB 和不允许的证书存储文件。 使用 `-f` 从 Windows 更新下载。

  - **AuthRoot** -读取注册表缓存的 AuthRoot CTL。 使用 with `-f` 和不受信任的**certfile**来强制注册表缓存的 AuthRoot 和不允许的证书 ctl 更新。

  - 不**允许**-读取注册表缓存的不允许证书 CTL。 使用 with `-f` 和不受信任的**certfile**来强制注册表缓存的 AuthRoot 和不允许的证书 ctl 更新。

- **CTLfilename**指定 CTL 或 CAB 文件的文件或 http 路径。

- **certdir**指定包含与 CTL 条目匹配的证书的文件夹。 默认为与**CTLobject**相同的文件夹或网站。 使用 http 文件夹路径时需要路径分隔符。 如果未指定 " **AuthRoot** " 或 "不**允许**"，则将在多个位置搜索匹配的证书，包括本地证书存储、crypt32.dll 资源和本地 URL 缓存。 `-f`根据需要使用从 Windows 更新下载。

- **certfile**指定要验证的) 证书 (。 证书与 CTL 条目匹配，并显示结果。 此选项将取消大多数默认输出。

```
[-f] [-user] [-split]
```

### <a name="-sign"></a>-sign

 (CRL) 或证书重新签署证书吊销列表。

```
certutil [options] -sign infilelist | serialnumber | CRL outfilelist [startdate+dd:hh] [+serialnumberlist | -serialnumberlist | -objectIDlist | \@extensionfile]
certutil [options] -sign infilelist | serialnumber | CRL outfilelist [#hashalgorithm] [+alternatesignaturealgorithm | -alternatesignaturealgorithm]
```

其中：

- **infilelist**是要修改和重新签名的证书或 CRL 文件的逗号分隔列表。

- **serialnumber**是要创建的证书的序列号。 有效期和其他选项不能出现。

- **Crl**创建空 CRL。 有效期和其他选项不能出现。

- **outfilelist**是以逗号分隔的已修改证书或 CRL 输出文件的列表。 文件数量必须与 infilelist 匹配。

- 开始时间 **+ dd： hh**是证书或 CRL 文件的新有效期，其中包括：

  - 可选日期加

  - 可选日期和小时有效期

  如果两者都指定，则必须使用加号 (+) 分隔符。 使用从 `now[+dd:hh]` 当前时间开始。 使用 `never` 将 (仅) crl 的到期日期。

- **serialnumberlist**是要添加或删除的文件的逗号分隔序列号列表。

- **objectIDlist**是要删除的文件的逗号分隔扩展 ObjectId 列表。

- ** \@ extensionfile**是包含要更新或删除的扩展的 INF 文件。 例如：

  ```
  [Extensions]
      2.5.29.31 = ; Remove CRL Distribution Points extension
      2.5.29.15 = {hex} ; Update Key Usage extension
      _continue_=03 02 01 86
  ```

- **hashalgorithm**是哈希算法的名称。 这必须是前面带有符号的文本 `#` 。

- **内容: alternatesignaturealgorithm**是备用签名算法说明符。

```
[-nullsign] [-f] [-silent] [-cert certID]
```

#### <a name="remarks"></a>备注

- 使用减号 (-) 删除序列号和扩展。

- 使用加号 (+) 将序列号添加到 CRL。

- 可以使用列表同时从 CRL 中删除序列号和 ObjectIDs。

- 使用**内容: alternatesignaturealgorithm**之前的减号允许使用旧的签名格式。 使用加号可以使用其他签名格式。 如果未指定**内容: alternatesignaturealgorithm**，则使用证书或 CRL 中的签名格式。

### <a name="-vroot"></a>-vroot

创建或删除 web 虚拟根和文件共享。

```
certutil [options] -vroot [delete]
```

### <a name="-vocsproot"></a>-vocsproot

创建或删除 OCSP web 代理的 web 虚拟根。

```
certutil [options] -vocsproot [delete]
```

### <a name="-addenrollmentserver"></a>-addenrollmentserver

为指定的证书颁发机构添加注册服务器应用程序和应用程序池（如有必要）。 此命令不安装二进制文件或包。

```
certutil [options] -addenrollmentserver kerberos | username | clientcertificate [allowrenewalsonly] [allowkeybasedrenewal]
```

其中：

- **addenrollmentserver**要求使用身份验证方法进行与证书注册服务器的客户端连接，其中包括：

  - **kerberos**使用 kerberos SSL 凭据。

  - **username**使用命名帐户作为 SSL 凭据。

  - **clientcertificate**使用 X.509 证书 SSL 凭据。

- **allowrenewalsonly**仅允许通过 URL 向证书颁发机构提交续订请求。

- **allowkeybasedrenewal**允许在 Active Directory 中使用没有关联帐户的证书。 这适用于与**clientcertificate**和**allowrenewalsonly**模式结合使用的情况。

```
[-config Machine\CAName]
```

### <a name="-deleteenrollmentserver"></a>-deleteenrollmentserver

为指定的证书颁发机构删除注册服务器应用程序和应用程序池（如有必要）。 此命令不安装二进制文件或包。

```
certutil [options] -deleteenrollmentserver kerberos | username | clientcertificate
```

其中：

- **deleteenrollmentserver**要求使用身份验证方法进行与证书注册服务器的客户端连接，其中包括：

  - **kerberos**使用 kerberos SSL 凭据。

  - **username**使用命名帐户作为 SSL 凭据。

  - **clientcertificate**使用 X.509 证书 SSL 凭据。

```
[-config Machine\CAName]
```

### <a name="-addpolicyserver"></a>-addpolicyserver

如有必要，请添加策略服务器应用程序和应用程序池。 此命令不安装二进制文件或包。

```
certutil [options] -addpolicyserver kerberos | username | clientcertificate [keybasedrenewal]
```

其中：

- **addpolicyserver**要求使用身份验证方法进行与证书策略服务器的客户端连接，其中包括：

  - **kerberos**使用 kerberos SSL 凭据。

  - **username**使用命名帐户作为 SSL 凭据。

  - **clientcertificate**使用 X.509 证书 SSL 凭据。

- **keybasedrenewal**允许使用返回到包含 keybasedrenewal 模板的客户端的策略。 此选项仅适用于**username**和**clientcertificate** authentication。

### <a name="-deletepolicyserver"></a>-deletepolicyserver

如有必要，删除策略服务器应用程序和应用程序池。 此命令不删除二进制文件或包。

certutil [options]-deletePolicyServer kerberos |用户名 |clientcertificate [keybasedrenewal]

其中：

- **deletepolicyserver**要求使用身份验证方法进行与证书策略服务器的客户端连接，其中包括：

  - **kerberos**使用 kerberos SSL 凭据。

  - **username**使用命名帐户作为 SSL 凭据。

  - **clientcertificate**使用 X.509 证书 SSL 凭据。

- **keybasedrenewal**允许使用 keybasedrenewal 策略服务器。

### <a name="-oid"></a>-oid

显示对象标识符或设置显示名称。

```
certutil [options] -oid objectID [displayname | delete [languageID [type]]]
certutil [options] -oid groupID
certutil [options] -oid agID | algorithmname [groupID]
```

其中：

- **objectID**显示或添加显示名称。

- **groupid**是 objectIDs 枚举 (decimal) 的 groupid 号。

- **algID**是 objectID 查找的十六进制 ID。

- **algorithmname**是 objectID 查找的算法名称。

- **displayname**显示要存储在 DS 中的名称。

- **删除**删除显示名称。

- **LanguageId**是 (默认为当前的语言 ID 值： 1033) 。

- **Type**是要创建的 DS 对象的类型，包括：

  - `1`-Template (默认值) 

  - `2`-颁发策略

  - `3`-应用程序策略

- `-f`创建 DS 对象。

### <a name="-error"></a>-错误

显示与错误代码关联的消息文本。

```
certutil [options] -error errorcode
```

### <a name="-getreg"></a>-getreg

显示注册表值。

```
certutil [options] -getreg [{ca | restore | policy | exit | template | enroll |chain | policyservers}\[progID\]][registryvaluename]
```

其中：

- **ca**使用证书颁发机构的注册表项。

- **restore**使用证书颁发机构的还原注册表项。

- **策略**使用策略模块的注册表项。

- **exit**使用第一个退出模块的注册表项。

- **模板**使用模板注册表项 (用于 `-user`) 用户模板。

- **注册**使用注册注册表项 (用于 `-user` 用户上下文) 。

- **链**使用链配置注册表项。

- **policyservers**使用策略服务器注册表项。

- **progID**使用策略或退出模块的 progID (注册表子项名称) 。

- **registryvaluename**使用注册表值名称 (使用 `Name*`) 前缀匹配。

- **值**使用新的数字、字符串或日期注册表值或文件名。 如果数字值以或开头 `+` ，则在 `-` 现有注册表值中设置或清除在新值中指定的位。

```
[-f] [-user] [-grouppolicy] [-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 如果字符串值以或开头 `+` `-` ，并且现有值为 `REG_MULTI_SZ` 值，则会将该字符串添加到现有注册表值或从中删除。 若要强制创建 `REG_MULTI_SZ` 值，请将添加 `\n` 到字符串值的末尾。

- 如果值以开头 `\@` ，则值的剩余部分是包含二进制值的十六进制文本表示形式的文件的名称。 如果未引用有效的文件，则将其分析为 `[Date][+|-][dd:hh]` -可选的日期加上或减去可选的日期和小时。 如果同时指定两者，则使用加号 (+) 或减号 ( ) 分隔符。 用于 `now+dd:hh` 相对于当前时间的日期。

- 使用 `chain\chaincacheresyncfiletime \@now` 有效刷新缓存的 crl。

### <a name="-setreg"></a>-setreg

设置注册表值。

```
certutil [options] -setreg [{ca | restore | policy | exit | template | enroll |chain | policyservers}\[progID\]]registryvaluename value
```

其中：

- **ca**使用证书颁发机构的注册表项。

- **restore**使用证书颁发机构的还原注册表项。

- **策略**使用策略模块的注册表项。

- **exit**使用第一个退出模块的注册表项。

- **模板**使用模板注册表项 (用于 `-user`) 用户模板。

- **注册**使用注册注册表项 (用于 `-user` 用户上下文) 。

- **链**使用链配置注册表项。

- **policyservers**使用策略服务器注册表项。

- **progID**使用策略或退出模块的 progID (注册表子项名称) 。

- **registryvaluename**使用注册表值名称 (使用 `Name*`) 前缀匹配。

- **值**使用新的数字、字符串或日期注册表值或文件名。 如果数字值以或开头 `+` ，则在 `-` 现有注册表值中设置或清除在新值中指定的位。

```
[-f] [-user] [-grouppolicy] [-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 如果字符串值以或开头 `+` `-` ，并且现有值为 `REG_MULTI_SZ` 值，则会将该字符串添加到现有注册表值或从中删除。 若要强制创建 `REG_MULTI_SZ` 值，请将添加 `\n` 到字符串值的末尾。

- 如果值以开头 `\@` ，则值的剩余部分是包含二进制值的十六进制文本表示形式的文件的名称。 如果未引用有效的文件，则将其分析为 `[Date][+|-][dd:hh]` -可选的日期加上或减去可选的日期和小时。 如果同时指定两者，则使用加号 (+) 或减号 ( ) 分隔符。 用于 `now+dd:hh` 相对于当前时间的日期。

- 使用 `chain\chaincacheresyncfiletime \@now` 有效刷新缓存的 crl。

### <a name="-delreg"></a>-delreg

删除注册表值。

```
certutil [options] -delreg [{ca | restore | policy | exit | template | enroll |chain | policyservers}\[progID\]][registryvaluename]
```

其中：

- **ca**使用证书颁发机构的注册表项。

- **restore**使用证书颁发机构的还原注册表项。

- **策略**使用策略模块的注册表项。

- **exit**使用第一个退出模块的注册表项。

- **模板**使用模板注册表项 (用于 `-user`) 用户模板。

- **注册**使用注册注册表项 (用于 `-user` 用户上下文) 。

- **链**使用链配置注册表项。

- **policyservers**使用策略服务器注册表项。

- **progID**使用策略或退出模块的 progID (注册表子项名称) 。

- **registryvaluename**使用注册表值名称 (使用 `Name*`) 前缀匹配。

- **值**使用新的数字、字符串或日期注册表值或文件名。 如果数字值以或开头 `+` ，则在 `-` 现有注册表值中设置或清除在新值中指定的位。

```
[-f] [-user] [-grouppolicy] [-config Machine\CAName]
```

#### <a name="remarks"></a>备注

- 如果字符串值以或开头 `+` `-` ，并且现有值为 `REG_MULTI_SZ` 值，则会将该字符串添加到现有注册表值或从中删除。 若要强制创建 `REG_MULTI_SZ` 值，请将添加 `\n` 到字符串值的末尾。

- 如果值以开头 `\@` ，则值的剩余部分是包含二进制值的十六进制文本表示形式的文件的名称。 如果未引用有效的文件，则将其分析为 `[Date][+|-][dd:hh]` -可选的日期加上或减去可选的日期和小时。 如果同时指定两者，则使用加号 (+) 或减号 ( ) 分隔符。 用于 `now+dd:hh` 相对于当前时间的日期。

- 使用 `chain\chaincacheresyncfiletime \@now` 有效刷新缓存的 crl。

### <a name="-importkms"></a>-importKMS

将用户密钥和证书导入到服务器数据库以进行密钥存档。

```
certutil [options] -importKMS userkeyandcertfile [certID]
```

其中：

- **userkeyandcertfile**是一个数据文件，其中包含要存档的用户私钥和证书。 此文件可以是：

  -  (KMS) 导出文件的 Exchange 密钥管理服务器。

  - PFX 文件。

- 证书 id 是 KMS 导出文件解密证书匹配令牌。 有关详细信息，请参阅 `-store` 本文中的参数。

- `-f`导入证书颁发机构未颁发的证书。

```
[-f] [-silent] [-split] [-config Machine\CAName] [-p password] [-symkeyalg symmetrickeyalgorithm[,keylength]]
```

### <a name="-importcert"></a>-importcert

将证书文件导入到数据库中。

```
certutil [options] -importcert certfile [existingrow]
```

其中：

- **existingrow**导入证书，以代替对同一密钥的挂起的请求。

- `-f`导入证书颁发机构未颁发的证书。

```
[-f] [-config Machine\CAName]
```

#### <a name="remarks"></a>备注

证书颁发机构可能还需要配置为支持外部证书。 为此，请键入 `import - certutil -setreg ca\KRAFlags +KRAF_ENABLEFOREIGN` 。

### <a name="-getkey"></a>-getkey

检索存档的私钥恢复 blob、生成恢复脚本或恢复已存档的密钥。

```
certutil [options] -getkey searchtoken [recoverybloboutfile]
certutil [options] -getkey searchtoken script outputscriptfile
certutil [options] -getkey searchtoken retrieve | recover outputfilebasename
```

其中：

- 如果找到多个匹配的恢复候选项，或者如果未) 指定输出文件，则**脚本**将生成用于检索和恢复密钥 (默认行为的脚本。

- 如果找到了恰好一个匹配的恢复候选项，**检索**将检索一个或多个密钥恢复 blob (默认行为; 如果指定了输出文件) 则检索。 使用此选项会截断任何扩展，并为每个密钥恢复 blob 追加特定于证书的字符串和 rec 扩展名。  每个文件都包含一个证书链和一个关联的私钥，仍加密为一个或多个密钥恢复代理证书。

- **恢复** (需要密钥恢复代理证书和私钥) ，在一个步骤中检索和恢复私钥。 使用此选项会截断任何扩展，并追加 p12 扩展名。  每个文件都包含已恢复的证书链和关联的私钥，作为 PFX 文件存储。

- **searchtoken**选择要恢复的密钥和证书，包括：

  - 1. 证书公用名

  - 2. 证书序列号

  - 3. 证书 SHA-1 哈希 (指纹) 

  - 4. 证书 KeyId SHA-1 哈希 (使用者密钥标识符) 

  - 5. 申请人姓名 (domain\user) 

  - 6. UPN (用户 \@ 域) 

- **recoverybloboutfile**输出带有证书链和私钥的文件，仍加密为一个或多个密钥恢复代理证书。

- **outputscriptfile**输出带有批处理脚本的文件以检索和恢复私钥。

- **outputfilebasename**输出文件基名称。

```
[-f] [-unicodetext] [-silent] [-config Machine\CAName] [-p password] [-protectto SAMnameandSIDlist] [-csp provider]
```

### <a name="-recoverkey"></a>-recoverkey

恢复存档的私钥。

```
certutil [options] -recoverkey recoveryblobinfile [PFXoutfile [recipientindex]]
```

```
[-f] [-user] [-silent] [-split] [-p password] [-protectto SAMnameandSIDlist] [-csp provider] [-t timeout]
```

### <a name="-mergepfx"></a>-mergePFX

合并 PFX 文件。

```
certutil [options] -mergePFX PFXinfilelist PFXoutfile [extendedproperties]
```

其中：

- **PFXinfilelist**是以逗号分隔的 PFX 输入文件列表。

- **PFXoutfile**是 PFX 输出文件的名称。

- **extendedproperties**包含任何扩展属性。

```
[-f] [-user] [-split] [-p password] [-protectto SAMnameAndSIDlist] [-csp provider]
```

#### <a name="remarks"></a>备注

- 在命令行中指定的密码必须是以逗号分隔的密码列表。

- 如果指定了多个密码，则将最后一个密码用于输出文件。 如果只提供了一个密码或最后一个密码为 `*` ，则系统将提示用户输入输出文件密码。

### <a name="-convertepf"></a>-convertEPF

将 PFX 文件转换为 EPF 文件。

```
certutil [options] -convertEPF PFXinfilelist PFXoutfile [cast | cast-] [V3CAcertID][,salt]
```

其中：


- **PFXinfilelist**是以逗号分隔的 PFX 输入文件列表。

- **PFXoutfile**是 PFX 输出文件的名称。

- **EPF**是 EPF 输出文件的名称。

- **cast**使用强制转换64加密。

- **cast-** 使用强制转换64加密 (导出) 

- **V3CAcertID**是 V3 CA 证书匹配令牌。 有关详细信息，请参阅 `-store` 本文中的参数。

- **salt**是 EPF 的输出文件 salt 字符串。

```
[-f] [-silent] [-split] [-dc DCName] [-p password] [-csp provider]
```

#### <a name="remarks"></a>备注

- 在命令行中指定的密码必须是以逗号分隔的密码列表。

- 如果指定了多个密码，则将最后一个密码用于输出文件。 如果只提供了一个密码或最后一个密码为 `*` ，则系统将提示用户输入输出文件密码。

### <a name="-"></a>-?

显示参数列表。

```
certutil -?
certutil <name_of_parameter> -?
certutil -? -v
```

其中：

- **-?** 显示参数的完整列表

- **-`<name_of_parameter>` -?** 显示指定参数的帮助内容。

- **-?-v**显示参数和选项的完整列表。

## <a name="options"></a>选项

本部分根据命令定义你能够指定的所有选项。 每个参数都包含有关有效选项的信息。

| 选项 | 描述 |
| ------- | ----------- |
| -nullsign | 使用数据哈希作为签名。 |
| -f | 强制覆盖。 |
| -enterprise | 使用本地计算机企业注册表证书存储区。 |
| -user | 使用 "HKEY_CURRENT_USER 密钥" 或 "证书存储"。 |
| -Microsoft-windows-grouppolicy | 使用组策略证书存储区。 |
| -未 | 显示用户模板。 |
| -mt | 显示计算机模板。 |
| -Unicode | 以 Unicode 编写重定向的输出。 |
| -UnicodeText | 用 Unicode 写入输出文件。 |
| -gmt | 使用 GMT 显示时间。 |
| -秒 | 使用秒和毫秒显示时间。 |
| -silent | 使用 `silent` 标志获取 dm-crypt 上下文。 |
| -split | 拆分嵌入的 node.js 元素，并保存到文件。 |
| -v | 提供更详细的 (详细) 信息。 |
| -privatekey.ppk | 显示密码和私钥数据。 |
| -pin PIN | 智能卡 PIN。 |
| -urlfetch | 检索并验证 AIA 证书和 CDP Crl。 |
| -config Machine\CAName | 证书颁发机构和计算机名字符串。 |
| -policyserver URLorID | 策略服务器 URL 或 ID。 对于选择 U/I，请使用 `-policyserver` 。 对于所有策略服务器，使用`-policyserver *`|
| -anonymous | 使用匿名 SSL 凭据。 |
| -kerberos | 使用 Kerberos SSL 凭据。 |
| -clientcertificate clientcertID | 使用 x.509 证书 SSL 凭据。 对于选择 U/I，请使用 `-clientcertificate` 。 |
| -用户名用户名 | 使用命名帐户作为 SSL 凭据。 对于选择 U/I，请使用 `-username` 。 |
| -cert 证书 id | 签名证书。 |
| -dc DCName | 以特定的域控制器为目标。 |
| -限制 restrictionlist | 以逗号分隔的限制列表。 每个限制都包含列名称、关系运算符和常量整数、字符串或日期。 一个列名前面可能有一个加号或减号，用来指示排序顺序。 例如，`requestID = 47`、`+requestername >= a, requestername` 或 `-requestername > DOMAIN, Disposition = 21` |
| -out columnlist | 逗号分隔的列列表。 |
| -p 密码 | 密码 |
| -protectto SAMnameandSIDlist | 以逗号分隔的 SAM 名称/SID 列表。 |
| -csp 提供程序 | 提供程序 |
| -t 超时 | URL 提取超时（毫秒）。 |
| -symkeyalg symmetrickeyalgorithm [，keylength] | 具有可选密钥长度的对称密钥算法的名称。 例如：`AES,128` 或 `3DES` |

### <a name="additional-references"></a>其他参考

有关如何使用此命令的更多示例，请参阅

- [Active Directory 证书服务 (AD CS)](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831740(v=ws.11))

- [用于管理证书的 Certutil 任务](/previous-versions/orphan-topics/ws.10/cc772898(v=ws.10))

- [certutil 命令](certutil.md)