---
title: bitsadmin setaclflag
description: 适用于 bitsadmin setaclflag 的 Windows 命令主题，用于设置访问控制列表传播标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4ac47e554dde6a555e891d89668cd12fec3179d4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849670"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

为作业设置访问控制列表（ACL）传播标志。 标志指示你希望在要下载的文件中维护所有者和 ACL 信息。 例如，若要通过文件维护所有者和组，请将 **Flags** 设置为 `OG`。

## <a name="syntax"></a>语法

```
bitsadmin /SetAclFlags <Job> <Flags>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Flags|指定以下一个或多个标志值：</br>-O：将所有者信息复制到文件。</br>-G：用文件复制组信息。</br>-D：将 DACL 信息复制到文件。</br>-S：复制具有文件的 SACL 信息。|

## <a name="remarks"></a>备注

当作业从 Windows （SMB）共享下载数据时，SetAclFlags 开关用于维护所有者和访问控制列表信息。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例设置名为*myDownloadJob*的作业的访问控制列表传播标志，以使用下载的文件维护所有者和组信息。
```
C:\>bitsadmin /setaclflags myDownloadJob OG
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)