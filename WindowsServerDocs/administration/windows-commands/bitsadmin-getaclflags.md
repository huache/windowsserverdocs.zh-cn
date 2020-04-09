---
title: bitsadmin getaclflags
description: 用于**bitsadmin getaclflags**的 Windows 命令主题，它检索访问控制列表（ACL）传播标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 99266def-7479-4430-a61c-98ec433fa88b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d53018e2fa5c659c8cf4b0ec985beda848a8c1af
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850790"
---
# <a name="bitsadmin-getaclflags"></a>bitsadmin getaclflags

检索访问控制列表（ACL）传播标志，以反映子对象是否继承项。

## <a name="syntax"></a>语法

```
bitsadmin /getaclflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

将显示一个或多个以下的标志值︰

- **o** -将所有者信息复制到文件。

- **g** -复制组信息和文件。

- **d** -使用文件复制随机访问控制列表（DACL）信息。

- **s** -使用文件复制系统访问控制列表（SACL）信息。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的访问控制列表传播标志 *myDownloadJob*。

```
C:\>bitsadmin /getaclflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)