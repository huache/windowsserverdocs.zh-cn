---
title: bitsadmin setclientcertificatebyid
description: 适用于 bitsadmin setclientcertificatebyid 的 Windows 命令主题，它指定用于 HTTPS （SSL）请求中的客户端身份验证的客户端证书的标识符
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8585a7a1-7472-437b-b04a-a11925782a3a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80c97b21194c773d1b21aab2ee31794624da671c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849660"
---
# <a name="bitsadmin-setclientcertificatebyid"></a>bitsadmin setclientcertificatebyid

指定在 HTTPS （SSL）请求中用于客户端身份验证的客户端证书的标识符。

## <a name="syntax"></a>语法

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> hexa-decimal_cert_id>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Store_location|标识用于查找证书的系统存储区的位置。 可能的值包括：</br>1（CURRENT_USER）</br>2（LOCAL_MACHINE）</br>3（CURRENT_SERVICE）</br>4（服务）</br>5（用户）</br>6（CURRENT_USER_GROUP_POLICY）</br>7（LOCAL_MACHINE_GROUP_POLICY）</br>8（LOCAL_MACHINE_ENTERPRISE）|
|Store_name|证书存储的名称。 可能的值包括：</br>CA （证书颁发机构证书）</br>我的（个人证书）</br>根（根证书）</br>SPC （软件发行者证书）|
|Hexadecimal_cert_id|表示证书哈希的十六进制数|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例在名为*myJob*的作业的 HTTPS （SSL）请求中指定要用于客户端身份验证的客户端证书的标识符。
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByID myJob BG_CERT_STORE_LOCATION_CURRENT_USER MY A106B52356D3FBCD1853A41B619358BD 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)