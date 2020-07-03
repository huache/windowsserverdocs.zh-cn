---
title: certreq
description: 用于从证书颁发机构（CA）请求证书、从证书颁发机构（CA）请求证书、从 .inf 文件创建新请求、接受并安装对请求的响应、从现有 CA 证书或请求构造交叉证书或合格的部属请求，以及签署交叉证书或合格的部属请求的 certreq 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7a04e51f-f395-4bff-b57a-0e9efcadf973
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 22fc496eddc17f4e6a1a5f02321c921009f9fd95
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85924817"
---
# <a name="certreq"></a>certreq

可以使用 certreq 命令从证书颁发机构（CA）请求证书，若要检索来自 CA 的以前请求的响应，请从 .inf 文件中创建新请求，以根据现有的 CA 证书或请求构造交叉证书或合格的部属请求，并对交叉证书或合格的部属请求进行签名。

> [!IMPORTANT]
> 更早版本的 certreq 命令可能不提供此处所述的所有选项。 若要查看基于特定版本的 certreq 支持的选项，请运行命令行帮助选项 `certreq -v -?` 。
>
> 在 CEP/CES 环境中时，certreq 命令不支持基于密钥证明模板创建新的证书请求。

> [!WARNING]
> 本主题的内容基于 Windows Server 的默认设置;例如，将密钥长度设置为2048，选择 Microsoft 软件密钥存储提供程序作为 CSP，并使用安全哈希算法1（SHA1）。 根据公司的安全策略要求评估这些选择。

## <a name="syntax"></a>语法

```
certreq [-submit] [options] [requestfilein [certfileout [certchainfileout [fullresponsefileOut]]]]
certreq -retrieve [options] requestid [certfileout [certchainfileout [fullresponsefileOut]]]
certreq -new [options] [policyfilein [requestfileout]]
certreq -accept [options] [certchainfilein | fullresponsefilein | certfilein]
certreq -sign [options] [requestfilein [requestfileout]]
certreq –enroll [options] templatename
certreq –enroll –cert certId [options] renew [reusekeys]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------- | ----------- |
| -提交 | 向证书颁发机构提交请求。 |
| -检索`<requestid>` | 检索对来自证书颁发机构的以前请求的响应。 |
| -new | 基于 .inf 文件创建新的请求。 |
| -accept | 接受并安装对证书请求的响应。 |
| -policy | 为请求设置策略。 |
| -sign | 对交叉证书或合格的部属请求进行签名。 |
| -注册 | 注册或续订证书。 |
| -? | 显示 certreq 语法、选项和说明的列表。 |
| `<parameter>` -? | 显示指定参数的帮助。 |
| -v-？ | 显示 certreq 语法、选项和说明的详细列表。 |

## <a name="examples"></a>示例

### <a name="certreq--submit"></a>certreq-提交

提交简单证书请求：

```
certreq –submit certrequest.req certnew.cer certnew.pfx
```

#### <a name="remarks"></a>备注

- 这是默认的 certreq.exe 参数。 如果在命令行提示符处未指定任何选项，certreq.exe 将尝试向证书颁发机构提交证书申请。 使用 **– submit**选项时，必须指定证书请求文件。 如果省略此参数，则会出现一个公共的**文件打开**窗口，让你选择适当的证书请求文件。

- 若要通过指定 SAN 属性请求证书，请参阅 Microsoft 知识库文章 931351[如何将使用者可选名称添加到安全 LDAP 证书](https://support.microsoft.com/kb/931351)中，了解*如何使用 certreq.exe 实用程序来创建和提交证书请求*部分。

### <a name="certreq--retrieve"></a>certreq-检索

若要检索证书 ID 20 并创建名为*MyCertificate*的证书文件（.cer），请执行以下操作：

```
certreq -retrieve 20 MyCertificate.cer
```

#### <a name="remarks"></a>备注

- 使用*certreq 检索证书*颁发机构颁发的证书。 *Requestid* PKC 可以是具有0x 前缀的十进制或十六进制，它可以是不带0x 前缀的证书序列号。 你还可以使用它来检索证书颁发机构曾经颁发的任何证书，包括吊销或过期证书，而不考虑证书的请求是否曾处于挂起状态。

- 如果向证书颁发机构提交请求，证书颁发机构的策略模块可能会使请求处于挂起状态，并将*requestid*返回给 certreq 调用方进行显示。 最终，证书颁发机构的管理员将颁发证书或拒绝请求。

### <a name="certreq--new"></a>certreq-新建

若要创建新请求：

```
[newrequest]
; At least one value must be set in this section
subject = CN=W2K8-BO-DC.contoso2.com
```

下面是可能会添加到 INF 文件中的部分可能的部分：

#### <a name="newrequest"></a>[newrequest]

INF 文件的此区域对于任何新的证书请求模板都是必需的，并且必须包含至少一个具有值的参数。

| 键<sup>1</sup> | 说明 | 值<sup>2</sup> | 示例 |
| --- | ---------- | ----- | ------- |
| 使用者 | 几个应用依赖证书中的主题信息。 建议为此项指定一个值。 如果未在此处设置主题，建议你将使用者名称作为使用者备用名称证书扩展的一部分。 | 相对可分辨名称字符串值 | Subject = CN = computer1 Subject = John Smith，CN = Users，DC = Contoso，DC = com |
| Exportable | 如果设置为 TRUE，则可以连同证书一起导出私钥。 若要确保安全级别较高，私钥应是不可导出的;但是，在某些情况下，如果多台计算机或用户必须共享相同的私钥，则可能需要该参数。 | `true | false` | `Exportable = TRUE`. CNG 密钥可以区分此和纯文本导出。 CAPI1 密钥不能。 |
| ExportableEncrypted | 指定私钥是否应设置为可导出。 | `true | false` | `ExportableEncrypted = true`<p>**提示：** 并非所有公共密钥大小和算法都适用于所有哈希算法。 指定的 CSP 还必须支持指定的哈希算法。 若要查看受支持的哈希算法的列表，可以运行以下命令：`certutil -oid 1 | findstr pwszCNGAlgid | findstr /v CryptOIDInfo` |
| HashAlgorithm | 要用于此请求的哈希算法。 | `Sha256, sha384, sha512, sha1, md5, md4, md2` | `HashAlgorithm = sha1`. 若要查看支持的哈希算法的列表，请使用： certutil-oid 1 | findstr pwszCNGAlgid | findstr/v CryptOIDInfo|
| KeyAlgorithm| 服务提供程序将用于生成公钥和私钥对的算法。| `RSA, DH, DSA, ECDH_P256, ECDH_P521, ECDSA_P256, ECDSA_P384, ECDSA_P521` | `KeyAlgorithm = RSA` |
| KeyContainer | 对于生成新密钥材料的新请求，不建议设置此参数。 密钥容器由系统自动生成和维护。<p>对于应使用现有密钥材料的请求，可以将此值设置为现有密钥的密钥容器名称。 使用 `certutil –key` 命令显示计算机上下文的可用密钥容器的列表。 `certutil –key –user`为当前用户的上下文使用命令。| 随机字符串值<p>**提示：** 用双引号将任何具有空格或特殊字符的 INF 密钥值括起来，以避免潜在的 INF 分析问题。 | `KeyContainer = {C347BD28-7F69-4090-AA16-BC58CF4D749C}` |
| KeyLength | 定义公钥和私钥的长度。 密钥长度会影响证书的安全级别。 较大的密钥长度通常提供较高的安全级别;但是，某些应用程序可能有关于密钥长度的限制。 | 加密服务提供程序支持的任何有效密钥长度。 | `KeyLength = 2048` |
| KeySpec | 确定密钥是否可用于签名，适用于 Exchange （加密），或同时用于两者。 | `AT_NONE, AT_SIGNATURE, AT_KEYEXCHANGE` | `KeySpec = AT_KEYEXCHANGE` |
| 密钥用法 | 定义证书密钥的用途。 | <ul><li>`CERT_DIGITAL_SIGNATURE_KEY_USAGE -- 80 (128)`</li><li>`CERT_NON_REPUDIATION_KEY_USAGE -- 40 (64)`</li><li>`CERT_KEY_ENCIPHERMENT_KEY_USAGE -- 20 (32)`</li><li>`CERT_DATA_ENCIPHERMENT_KEY_USAGE -- 10 (16)`</li><li>`CERT_KEY_AGREEMENT_KEY_USAGE -- 8`</li><li>`CERT_KEY_CERT_SIGN_KEY_USAGE -- 4`</li><li>`CERT_OFFLINE_CRL_SIGN_KEY_USAGE -- 2`</li><li>`CERT_CRL_SIGN_KEY_USAGE -- 2`</li><li>`CERT_ENCIPHER_ONLY_KEY_USAGE -- 1`</li><li>`CERT_DECIPHER_ONLY_KEY_USAGE -- 8000 (32768)`</li></ul> | `KeyUsage = CERT_DIGITAL_SIGNATURE_KEY_USAGE | CERT_KEY_ENCIPHERMENT_KEY_USAGE`<p>**提示：** 多个值使用竖线（|）符号分隔符。 请确保在使用多个值时使用双引号，以避免出现 INF 分析问题。 显示的值是每个位定义的十六进制值（十进制）。 还可以使用旧语法：设置了多个位的单个十六进制值，而不是符号表示形式。 例如，`KeyUsage = 0xa0`。 |
| KeyUsageProperty | 检索一个值，该值标识可以对其使用私钥的特定目的。 | <ul><li>`NCRYPT_ALLOW_DECRYPT_FLAG -- 1`</li><li>`NCRYPT_ALLOW_SIGNING_FLAG -- 2`</li><li>`NCRYPT_ALLOW_KEY_AGREEMENT_FLAG -- 4`</li><li>`NCRYPT_ALLOW_ALL_USAGES -- ffffff (16777215)`</li></ul> | `KeyUsageProperty = NCRYPT_ALLOW_DECRYPT_FLAG | NCRYPT_ALLOW_SIGNING_FLAG` |
| MachineKeySet | 当你需要创建由计算机拥有的证书而不是用户时，此密钥非常重要。 生成的密钥材料将保留在已创建请求的安全主体（用户或计算机帐户）的安全上下文中。 当管理员代表计算机创建证书申请时，必须在计算机的安全上下文中创建密钥材料，而不是管理员的安全上下文。 否则，计算机无法访问其私钥，因为它将位于管理员的安全上下文中。 | `true | false`. 默认值为 false。 | `MachineKeySet = true` |
| NotBefore | 指定日期或日期和时间，在该日期和时间之前无法发出请求。 `NotBefore`可与和一起 `ValidityPeriod` 使用 `ValidityPeriodUnits` 。 | 日期或日期和时间 | `NotBefore = 7/24/2012 10:31 AM`<p>**提示：** `NotBefore`和 `NotAfter` 仅适用于 R `equestType=cert` 。 日期分析尝试区分区域设置。 使用月份名称将消除歧义，并应在每个区域设置中使用。 |
| NotAfter | 指定日期或日期和时间，在此时间之后无法发出请求。 `NotAfter`不能与或一起使用 `ValidityPeriod` `ValidityPeriodUnits` 。 | 日期或日期和时间 | `NotAfter = 9/23/2014 10:31 AM`<p>**提示：** `NotBefore`和 `NotAfter` 仅适用于 `RequestType=cert` 。 日期分析尝试区分区域设置。 使用月份名称将消除歧义，并应在每个区域设置中使用。 |
| PrivateKeyArchive | 仅当相应的 RequestType 设置为 CMC 时，PrivateKeyArchive 设置才起作用，因为只有证书管理消息 over CMS （CMC）请求格式才允许安全地将请求者的私钥传输到 CA 进行密钥存档。 | `true | false` | `PrivateKeyArchive = true` |
| EncryptionAlgorithm | 要使用的加密算法。 | 可能的选项会有所不同，具体取决于操作系统版本和已安装的加密提供程序集。 若要查看可用算法的列表，请运行命令： `certutil -oid 2 | findstr pwszCNGAlgid` 。 使用的指定 CSP 还必须支持指定的对称加密算法和长度。 | `EncryptionAlgorithm = 3des` |
| EncryptionLength | 要使用的加密算法的长度。 | 指定的 EncryptionAlgorithm 允许的任何长度。 | `EncryptionLength = 128` |
| ProviderName | 提供程序名称是 CSP 的显示名称。 | 如果你不知道所使用的 CSP 的提供程序名称，请 `certutil –csplist` 从命令行运行。 命令将显示本地系统上可用的所有 Csp 的名称 | `ProviderName = Microsoft RSA SChannel Cryptographic Provider` |
| ProviderType | 提供程序类型用于根据特定算法功能（如 RSA Full）选择特定的提供程序。 | 如果你不知道所使用的 CSP 的提供程序类型，请 `certutil –csplist` 从命令行提示符运行。 此命令会显示本地系统上所有可用 Csp 的提供程序类型。 | `ProviderType = 1` |
| RenewalCert | 如果需要续订在生成证书请求的系统上存在的证书，则必须将其证书哈希指定为此密钥的值。 | 在其中创建证书请求的计算机上可用的任何证书的证书哈希。 如果你不知道证书哈希，请使用 "证书" MMC 管理单元，并查看应续订的证书。 打开证书属性并查看证书的 `Thumbprint` 属性。 证书续订需要 `PKCS#7` 或 `CMC` 请求格式。 | `RenewalCert = 4EDF274BD2919C6E9EC6A522F0F3B153E9B1582D` |
| RequesterName | 发出请求以代表其他用户请求进行注册。该请求还必须使用注册代理证书进行签名，否则 CA 将拒绝该请求。 使用 `-cert` 选项来指定注册代理证书。 如果设置为或，则可以为证书请求指定请求者名称 `RequestType` `PKCS#7` `CMC` 。 如果 `RequestType` 设置为，则 `PKCS#10` 将忽略此键。 `Requestername`只能设置为请求的一部分。 不能 `Requestername` 在挂起的请求中操作。 | `Domain\User` | `Requestername = Contoso\BSmith` |
| RequestType | 确定用于生成和发送证书请求的标准。 | <ul><li>`PKCS10 -- 1`</li><li>`PKCS7 -- 2`</li><li>`CMC -- 3`</li><li>`Cert -- 4`</li><li>`SCEP -- fd00 (64768)`</li></ul>**提示：** 此选项表示自签名或自行颁发的证书。 它不会生成请求，而是生成新证书，然后安装证书。 自签名为默认值。 使用– cert 选项指定一个签名证书，以创建自签名证书（不是自签名证书）。 | `RequestType = CMC` |
| SecurityDescriptor | 包含与安全对象关联的安全信息。 对于大多数安全对象，可以在创建对象的函数调用中指定对象的安全描述符。基于[安全描述符定义语言](https://msdn.microsoft.com/library/aa379567(v=vs.85).aspx)的字符串。<p>**提示：** 这仅适用于计算机上下文非智能卡密钥。 | `SecurityDescriptor = D:P(A;;GA;;;SY)(A;;GA;;;BA)` |
| 内容： alternatesignaturealgorithm | 指定并检索一个布尔值，该值指示 PKCS # 10 请求或证书签名的签名算法对象标识符（OID）是离散的还是组合的。 | `true | false` | `AlternateSignatureAlgorithm = false`<p>对于 RSA 签名， `false` 指示 `Pkcs1 v1.5` ，而 `true` 指示 `v2.1` 签名。 |
| 无提示 | 默认情况下，此选项允许 CSP 访问交互式用户桌面并向用户请求诸如智能卡 PIN 之类的信息。 如果将此项设置为 TRUE，则 CSP 不得与桌面交互，将阻止向用户显示任何用户界面。 | `true | false` | `Silent = true` |
| SMIME | 如果将此参数设置为 TRUE，则会将具有对象标识符值 "1.2.840.113549.1.9.15" 的扩展添加到请求中。 对象标识符的数量取决于安装的操作系统版本和 CSP 功能，这是指安全多用途 Internet 邮件扩展（S/MIME）应用程序（如 Outlook）可以使用的对称加密算法。 | `true | false` | `SMIME = true` |
| UseExistingKeySet | 此参数用于指定在生成证书请求时应使用现有的密钥对。 如果将此项设置为 TRUE，则还必须为 RenewalCert 项或 KeyContainer 名称指定值。 你不能设置可导出的密钥，因为你无法更改现有密钥的属性。 在这种情况下，生成证书请求时不会生成密钥材料。 | `true | false` | `UseExistingKeySet = true` |
| KeyProtection | 指定一个值，该值指示在使用之前私钥的保护方式。 | <ul><li>`XCN_NCRYPT_UI_NO_PROTCTION_FLAG -- 0`</li><li>`XCN_NCRYPT_UI_PROTECT_KEY_FLAG -- 1`</li><li>`XCN_NCRYPT_UI_FORCE_HIGH_PROTECTION_FLAG -- 2`</li></ul> | `KeyProtection = NCRYPT_UI_FORCE_HIGH_PROTECTION_FLAG` |
| SuppressDefaults | 指定一个布尔值，该值指示是否在请求中包含默认扩展和属性。 默认值由它们的对象标识符（Oid）表示。 | `true | false` | `SuppressDefaults = true` |
| FriendlyName | 新证书的友好名称。 | Text | `FriendlyName = Server1` |
| ValidityPeriodUnits | 指定要用于 ValidityPeriod 的单位数。 注意：仅当时才使用 `request type=cert` 。 | Numeric | `ValidityPeriodUnits = 3` |
| ValidityPeriod | ValidityPeriod 必须是美国英语复数时间段。 注意：仅当请求类型 = cert 时才使用此类型。 | `Years |  Months | Weeks | Days | Hours | Minutes | Seconds` | `ValidityPeriod = Years` |

<sup>1</sup>等号（=）左侧的参数

<sup>2</sup>等号（=）右侧的参数

#### <a name="extensions"></a>扩展名

本部分是可选的。

| 扩展 OID | 定义 | 示例 |
| ------------- | ---------- | ----- | ------- |
| 2.5.29.17 | | 2.5.29.17 = {text} |
| *continue* | | `continue = UPN=User@Domain.com&` |
| *continue* | | `continue = EMail=User@Domain.com&` |
| *continue* | | `continue = DNS=host.domain.com&` |
| *continue* | | `continue = DirectoryName=CN=Name,DC=Domain,DC=com&` |
| *continue* | | `continue = URL=<http://host.domain.com/default.html&>` |
| *continue* | | `continue = IPAddress=10.0.0.1&` |
| *continue* | | `continue = RegisteredId=1.2.3.4.5&` |
| *continue* | | `continue = 1.2.3.4.6.1={utf8}String&` |
| *continue* | | `continue = 1.2.3.4.6.2={octet}AAECAwQFBgc=&` |
| *continue* | | `continue = 1.2.3.4.6.2={octet}{hex}00 01 02 03 04 05 06 07&` |
| *continue* | | `continue = 1.2.3.4.6.3={asn}BAgAAQIDBAUGBw==&` |
| *continue* | | `continue = 1.2.3.4.6.3={hex}04 08 00 01 02 03 04 05 06 07` |
| 2.5.29.37 | | `2.5.29.37={text}` |
| *continue* | | `continue = 1.3.6.1.5.5.7` |
| *continue* | | `continue = 1.3.6.1.5.5.7.3.1` |
| 2.5.29.19 | | `{text}ca=0pathlength=3` |
| 严重 | | `Critical=2.5.29.19` |
| KeySpec | | <ul><li>`AT_NONE -- 0`</li><li>`AT_SIGNATURE -- 2`</li><li>`AT_KEYEXCHANGE -- 1`</ul></li> |
| RequestType | | <ul><li>`PKCS10 -- 1`</li><li>`PKCS7 -- 2`</li><li>`CMC -- 3`</li><li>`Cert -- 4`</li><li>`SCEP -- fd00 (64768)`</li></ul> |
| 密钥用法 | | <ul><li>`CERT_DIGITAL_SIGNATURE_KEY_USAGE -- 80 (128)`</li><li>`CERT_NON_REPUDIATION_KEY_USAGE -- 40 (64)`</li><li>`CERT_KEY_ENCIPHERMENT_KEY_USAGE -- 20 (32)`</li><li>`CERT_DATA_ENCIPHERMENT_KEY_USAGE -- 10 (16)`</li><li>`CERT_KEY_AGREEMENT_KEY_USAGE -- 8`</li><li>`CERT_KEY_CERT_SIGN_KEY_USAGE -- 4`</li><li>`CERT_OFFLINE_CRL_SIGN_KEY_USAGE -- 2`</li><li>`CERT_CRL_SIGN_KEY_USAGE -- 2`</li><li>`CERT_ENCIPHER_ONLY_KEY_USAGE -- 1`</li><li>`CERT_DECIPHER_ONLY_KEY_USAGE -- 8000 (32768)`</li></ul> |
| KeyUsageProperty | | <ul><li>`NCRYPT_ALLOW_DECRYPT_FLAG -- 1`</li><li>`NCRYPT_ALLOW_SIGNING_FLAG -- 2`</li><li>`NCRYPT_ALLOW_KEY_AGREEMENT_FLAG -- 4`</li><li>`NCRYPT_ALLOW_ALL_USAGES -- ffffff (16777215)`</li></ul> |
| KeyProtection | | <ul><li>`NCRYPT_UI_NO_PROTECTION_FLAG -- 0`</li><li>`NCRYPT_UI_PROTECT_KEY_FLAG -- 1`</li><li>`NCRYPT_UI_FORCE_HIGH_PROTECTION_FLAG -- 2`</li></ul> |
| SubjectNameFlags | template | <ul><li>`CT_FLAG_SUBJECT_REQUIRE_COMMON_NAME -- 40000000 (1073741824)`</li><li>`CT_FLAG_SUBJECT_REQUIRE_DIRECTORY_PATH -- 80000000 (2147483648)`</li><li>`CT_FLAG_SUBJECT_REQUIRE_DNS_AS_CN -- 10000000 (268435456)`</li><li>`CT_FLAG_SUBJECT_REQUIRE_EMAIL -- 20000000 (536870912)`</li><li>`CT_FLAG_OLD_CERT_SUPPLIES_SUBJECT_AND_ALT_NAME -- 8`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_DIRECTORY_GUID -- 1000000 (16777216)`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_DNS -- 8000000 (134217728)`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_DOMAIN_DNS -- 400000 (4194304)`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_EMAIL -- 4000000 (67108864)`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_SPN -- 800000 (8388608)`</li><li>`CT_FLAG_SUBJECT_ALT_REQUIRE_UPN -- 2000000 (33554432)`</li></ul> |
| X500NameFlags | | <ul><li>`CERT_NAME_STR_NONE -- 0`</li><li>`CERT_OID_NAME_STR -- 2`</li><li>`CERT_X500_NAME_STR -- 3`</li><li>`CERT_NAME_STR_SEMICOLON_FLAG -- 40000000 (1073741824)`</li><li>`CERT_NAME_STR_NO_PLUS_FLAG -- 20000000 (536870912)`</li><li>`CERT_NAME_STR_NO_QUOTING_FLAG -- 10000000 (268435456)`</li><li>`CERT_NAME_STR_CRLF_FLAG -- 8000000 (134217728)`</li><li>`CERT_NAME_STR_COMMA_FLAG -- 4000000 (67108864)`</li><li>`CERT_NAME_STR_REVERSE_FLAG -- 2000000 (33554432)`</li><li>`CERT_NAME_STR_FORWARD_FLAG -- 1000000 (16777216)`</li><li>`CERT_NAME_STR_DISABLE_IE4_UTF8_FLAG -- 10000 (65536)`</li><li>`CERT_NAME_STR_ENABLE_T61_UNICODE_FLAG -- 20000 (131072)`</li><li>`CERT_NAME_STR_ENABLE_UTF8_UNICODE_FLAG -- 40000 (262144)`</li><li>`CERT_NAME_STR_FORCE_UTF8_DIR_STR_FLAG -- 80000 (524288)`</li><li>`CERT_NAME_STR_DISABLE_UTF8_DIR_STR_FLAG -- 100000 (1048576)`</li><li>`CERT_NAME_STR_ENABLE_PUNYCODE_FLAG -- 200000 (2097152)`</li></ul> |

> [!NOTE]
> `SubjectNameFlags`允许 INF 文件根据当前用户或当前计算机属性，指定应由 certreq 自动填充哪些**Subject**和**SubjectAltName**扩展字段： DNS 名称、UPN 等。 使用文本模板意味着改为使用模板名称标志。 这允许在多个上下文中使用单个 INF 文件，以生成具有特定于上下文的主题信息的请求。
>
> `X500NameFlags`指定在将 `CertStrToName` 值转换为一个名为 "node.js `Subject INF keys` 编码的可分辨**名称**" 时，将直接传递给 API 的标志。

#### <a name="example"></a>示例

在记事本中创建策略文件（.inf），并将其另存为*requestconfig*：

```
[NewRequest]
Subject = CN=<FQDN of computer you are creating the certificate>
Exportable = TRUE
KeyLength = 2048
KeySpec = 1
KeyUsage = 0xf0
MachineKeySet = TRUE
[RequestAttributes]
CertificateTemplate=WebServer
[Extensions]
OID = 1.3.6.1.5.5.7.3.1
OID = 1.3.6.1.5.5.7.3.2
```

在请求证书的计算机上：

```
certreq –new requestconfig.inf certrequest.req
```

如果为，则对 Oid 使用 [String] 部分语法，其他难以解释数据。 用于 EKU 扩展的新 {text} 语法示例，它使用以逗号分隔的 Oid 列表：

```
[Version]
Signature=$Windows NT$

[Strings]
szOID_ENHANCED_KEY_USAGE = 2.5.29.37
szOID_PKIX_KP_SERVER_AUTH = 1.3.6.1.5.5.7.3.1
szOID_PKIX_KP_CLIENT_AUTH = 1.3.6.1.5.5.7.3.2

[NewRequest]
Subject = CN=TestSelfSignedCert
Requesttype = Cert

[Extensions]
%szOID_ENHANCED_KEY_USAGE%={text}%szOID_PKIX_KP_SERVER_AUTH%,
_continue_ = %szOID_PKIX_KP_CLIENT_AUTH%
```

### <a name="certreq--accept"></a>certreq-accept

`–accept`参数使用已颁发的证书链接以前生成的私钥，并从请求证书的系统中删除挂起的证书请求（如果存在匹配的请求）。

手动接受证书的步骤：

```
certreq -accept certnew.cer
```

> [!WARNING]
> 将 `-accept` 参数与 `-user` 和选项一起使用 `–machine` 可指示是否应在**用户**或**计算机**上下文中安装安装证书。 如果在与要安装的公钥相匹配的上下文中存在未完成的请求，则不需要这些选项。 如果没有未完成的请求，则必须指定其中一个。

### <a name="certreq--policy"></a>certreq-策略

策略 .inf 文件是一个配置文件，用于定义在定义合格的部属时应用于 CA 证书的约束。

若要生成交叉证书请求：

```
certreq -policy certsrv.req policy.inf newcertsrv.req
```

使用 `certreq -policy` 不带任何其他参数的将打开一个对话框窗口，使你可以选择请求的文件（. 请求，.，.txt，。 选择所请求的文件并单击 "**打开**" 后，将打开另一个对话框窗口，允许您选择策略 .inf 文件。

#### <a name="examples"></a>示例

查找[Capolicy.inf 语法](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/prepare-the-capolicy-inf-file)中的策略 .inf 文件的示例。

### <a name="certreq--sign"></a>certreq-sign

若要创建新的证书请求，请对其进行签名并提交：

```
certreq -new policyfile.inf myrequest.req
certreq -sign myrequest.req myrequest.req
certreq -submit myrequest_sign.req myrequest_cert.cer
```

#### <a name="remarks"></a>备注

- `certreq -sign`如果不使用任何其他参数，它将打开一个对话框窗口，以便你可以选择请求的文件（请求、cmc、txt、der、cer 或 crt）。

- 对合格的部属请求进行签名可能需要**企业管理员**凭据。 这是为合格的部属颁发签名证书的最佳做法。

- 用于对合格的部属请求进行签名的证书使用合格的部属模板。 企业管理员将必须签署请求，或者向用户授予对证书签名的权限。

- 你可能需要让其他人员在你之后对 CMC 请求进行签名。 这将取决于与合格的部属关联的保障级别。

- 如果正在安装的合格从属 CA 的父 CA 处于脱机状态，则必须从脱机父 ca 获取合格从属 CA 的 CA 证书。 如果父 CA 处于联机状态，请在**证书服务安装**向导中指定合格从属 CA 的 ca 证书。

### <a name="certreq--enroll"></a>certreq-注册

可以使用此注释来注册或续订证书。

#### <a name="examples"></a>示例

若要注册证书，请使用*web*服务器模板，并通过使用 U/I 选择策略服务器：

```
certreq -enroll –machine –policyserver * WebServer
```

使用序列号续订证书：

```
certreq –enroll -machine –cert 61 2d 3c fe 00 00 00 00 00 05 renew
```

只能续订有效证书。 无法续订过期的证书，必须将其替换为新证书。

## <a name="options"></a>选项

| 选项 | 说明 |
| ------- | ----------- |
| -any | `Force ICertRequest::Submit`确定编码类型。|
| -attrib`<attributestring>` | 指定**名称**和**值**字符串对，并以冒号分隔。<p>使用**Name** **Value** `\n` （例如，Name1： Value1\nName2： Value2）分隔名称和值字符串对。 |
| -二进制 | 将输出文件的格式设置为二进制格式，而不是 base64 编码格式。 |
| -policyserver`<policyserver>` | ldap`<path>`<br>插入运行证书注册策略 web 服务的计算机的 URI 或唯一 ID。<p>若要指定要通过浏览使用请求文件，只需对使用减号（-） `<policyserver>` 。 |
| -config`<ConfigString>` | 使用在配置字符串中指定的 CA （ **CAHostName\CAName**）来处理操作。 对于 https： \\ \ 连接，请指定注册服务器 URI。 对于本地计算机存储区 CA，使用减号（-）符号。 |
| -anonymous | 将匿名凭据用于证书注册 web 服务。 |
| -kerberos | 将 Kerberos （域）凭据用于证书注册 web 服务。 |
| -clientcertificate`<ClientCertId>` | 您可以 `<ClientCertId>` 使用证书指纹、CN、EKU、模板、电子邮件、UPN 或新 `name=value` 语法替换。 |
| -username`<username>` | 用于证书注册 web 服务。 可以用 `<username>` SAM 名称或**域 \ 用户**值来替换。 此选项与选项一起使用 `-p` 。 |
| -p`<password>` | 用于证书注册 web 服务。 替换 `<password>` 为实际用户的密码。 此选项与选项一起使用 `-username` 。 |
| -user | `-user`为新证书请求配置上下文或指定证书接受的上下文。 如果在 INF 或模板中未指定任何内容，则这是默认上下文。 |
| -计算机 | 配置新的证书申请或为计算机上下文的证书指定上下文。 对于新请求，它必须与 MachineKeyset INF 密钥和模板上下文一致。 如果未指定此选项，并且模板未设置上下文，则默认为用户上下文。 |
| -crl | 将输出中的证书吊销列表（Crl）包括到由指定的 base64 编码的 PKCS #7 文件 `certchainfileout` 或由指定的 base64 编码文件中 `requestfileout` 。 |
| -rpc | 指示 Active Directory 证书服务（AD CS）使用远程过程调用（RPC）服务器连接而不是分布式 COM。 |
| -adminforcemachine | 使用密钥服务或模拟从本地系统上下文提交请求。 要求调用此选项的用户是本地管理员的成员。 |
| -renewonbehalfof | 代表签名证书中标识的使用者提交续订。 这会在调用[ICertRequest：： Submit 方法](https://docs.microsoft.com/windows/win32/api/certcli/nf-certcli-icertrequest-submit)时设置 CR_IN_ROBO |
| -f | 强制覆盖现有文件。 这也会绕过缓存模板和策略。 |
| -q | 使用静默模式;禁止显示所有交互式提示。 |
| -unicode | 将标准输出重定向到另一个命令（在从 Windows PowerShell 脚本中调用此命令时）时，写入 Unicode 输出。 |
| -unicodetext | 将 base64 文本编码的数据 blob 写入文件时，发送 Unicode 输出。 |

## <a name="formats"></a>格式

| 格式 | 说明 |
| ------- | ----------- |
| requestfilein | Base64 编码的或二进制输入文件名： PKCS #10 证书请求、CMS 证书请求、PKCS #7 证书续订请求、要交叉验证的 x.509 证书，或 Ssh-keygen 标记格式的证书请求。 |
| requestfileout | Base64 编码的输出文件名。 |
| certfileout | Base64 编码的 X-509 文件名。 |
| PKCS10fileout | 仅与参数一起使用 `certreq -policy` 。 Base64 编码的 PKCS10 输出文件名。 |
| certchainfileout | Base64 编码的 PKCS #7 文件名。 |
| fullresponsefileout | Base64 编码的完整响应文件名。 |
| policyfilein | 仅与参数一起使用 `certreq -policy` 。 INF 文件，其中包含用于限定请求的扩展的文本表示形式。 |

## <a name="additional-resources"></a>其他资源

以下文章包含 certreq 用法的示例：

- [如何向安全的 LDAP 证书添加使用者可选名称](https://support.microsoft.com/help/931351/how-to-add-a-subject-alternative-name-to-a-secure-ldap-certificate)

- [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831348(v=ws.11))

- [附录3： Certreq.exe 语法](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736326(v=ws.10))

- [如何手动创建 web 服务器 SSL 证书](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-create-a-web-server-ssl-certificate-manually/ba-p/1128529)

- [使用 Windows Server 2008 CA 请求 AMT 设置证书](https://social.technet.microsoft.com/wiki/contents/articles/548.request-an-amt-provisioning-certificate-using-a-windows-server-2008-ca.aspx)

- [System Center Operations Manager 代理的证书注册](https://social.technet.microsoft.com/wiki/contents/articles/2017.certificate-enrollment-for-system-center-operations-manager-agent.aspx)

- [AD CS 循序渐进指南：双层 PKI 层次结构部署](https://social.technet.microsoft.com/wiki/contents/articles/15037.ad-cs-step-by-step-guide-two-tier-pki-hierarchy-deployment.aspx)

- [如何使用第三方证书颁发机构启用 LDAP over SSL](https://support.microsoft.com/help/321051/how-to-enable-ldap-over-ssl-with-a-third-party-certification-authority)
