---
title: bitsadmin setclientcertificatebyid
description: 适用于**bitsadmin setclientcertificatebyid**的 Windows 命令主题，它指定用于 HTTPS （SSL）请求中的客户端身份验证的客户端证书的标识符
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 376bb850664a5ed569488634029cb7384856f158
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123046"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid

指定在 HTTPS （SSL）请求中用于客户端身份验证的客户端证书的标识符。

## <a name="syntax"></a>语法

```
bitsadmin /setclientcertificatebyid <job> <store_location> <store_name> <hexadecimal_cert_id>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| store_location | 标识用于查找证书的系统存储区的位置，包括：<ul><li>CURRENT_USER</li><li>LOCAL_MACHINE</li><li>CURRENT_SERVICE</li><li>服务</li><li>用户</li><li>CURRENT_USER_GROUP_POLICY</li><li>LOCAL_MACHINE_GROUP_POLICY</li><li>LOCAL_MACHINE_ENTERPRISE。</li></ul> |
| store_name | 证书存储区的名称，包括：<ul><li>CA （证书颁发机构证书）</li><li>我的（个人证书）</li><li>根（根证书）</li><li>SPC （软件发行者证书）。</li></ul> |
| hexadecimal_cert_id | 表示证书哈希的十六进制数。 |

## <a name="examples"></a>示例

下面的示例在名为*myDownloadJob*的作业的 HTTPS （SSL）请求中指定要用于客户端身份验证的客户端证书的标识符。

```
C:\>bitsadmin /setclientcertificatebyid myDownloadJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)