---
title: bitsadmin setclientcertificatebyname
description: 适用于 bitsadmin setclientcertificatebyname 的 Windows 命令主题，它指定用于 HTTPS （SSL）请求中客户端身份验证的客户端证书的使用者名称。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f308a6d9-d0da-48be-ae41-eced14b3cccb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 08ec6fd8c941234de36f14cd71ffa51c3b428acb
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849650"
---
# <a name="bitsadmin-setclientcertificatebyname"></a>bitsadmin setclientcertificatebyname

指定在 HTTPS （SSL）请求中用于客户端身份验证的客户端证书的使用者名称。

## <a name="syntax"></a>语法

```
bitsadmin /SetClientCertificateByID <Job> <store_location> <store_name> <subject_name>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Store_location|标识用于查找证书的系统存储区的位置。 可能的值包括：</br>1（CURRENT_USER）</br>2（LOCAL_MACHINE）</br>3（CURRENT_SERVICE）</br>4（服务）</br>5（用户）</br>6（CURRENT_USER_GROUP_POLICY）</br>7（LOCAL_MACHINE_GROUP_POLICY）</br>8（LOCAL_MACHINE_ENTERPRISE）|
|Store_name|证书存储的名称。 可能的值包括：</br>CA （证书颁发机构证书）</br>我的（个人证书）</br>根（根证书）</br>SPC （软件发行者证书）|
|Subject_name|证书的名称|

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例在名为*myJob*的作业的 HTTPS （SSL）请求中指定要用于客户端身份验证的客户端证书*myCertificate*的名称。
```
C:\>bitsadmin Bitsadmin /SetClientCertificateByName myJob 1 MY myCertificate 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)