---
title: bitsadmin setclientcertificatebyname
description: Bitsadmin setclientcertificatebyname 命令的参考文章，其中指定了用于 HTTPS (SSL) 请求中的客户端身份验证的客户端证书的使用者名称。
ms.topic: reference
ms.assetid: f308a6d9-d0da-48be-ae41-eced14b3cccb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f5a29448641d7d92594e229396146169c3f6a9f4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631044"
---
# <a name="bitsadmin-setclientcertificatebyname"></a>bitsadmin setclientcertificatebyname

指定客户端证书的使用者名称，以用于 HTTPS (SSL) 请求中的客户端身份验证。

## <a name="syntax"></a>语法

```
bitsadmin /setclientcertificatebyname <job> <store_location> <store_name> <subject_name>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| store_location | 标识用于查找证书的系统存储区的位置。 可能的值包括：<ul><li>1 (CURRENT_USER) </li><li>2 (LOCAL_MACHINE) </li><li>3 (CURRENT_SERVICE) </li><li>4 (SERVICES) </li><li>5 (用户) </li><li>6 (CURRENT_USER_GROUP_POLICY) </li><li>7 (LOCAL_MACHINE_GROUP_POLICY) </li><li>8 (LOCAL_MACHINE_ENTERPRISE) </li></ul> |
| store_name | 证书存储的名称。 可能的值包括：<ul><li>CA (证书颁发机构证书) </li><li>我的 (个人证书) </li><li>根证书 (根证书) </li><li>SPC (软件发行者证书) </li></ul> |
| subject_name | 证书的名称。 |

## <a name="examples"></a>示例

若要指定客户端证书 *myCertificate* 的名称以用于 HTTPS 中的客户端身份验证 (SSL) 请求名为 *myDownloadJob*的作业：

```
bitsadmin /setclientcertificatebyname myDownloadJob 1 MY myCertificate
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
