---
title: bitsadmin setaclflag
description: 适用于**bitsadmin setaclflag**的 Windows 命令主题，用于设置访问控制列表（ACL）传播标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f0aae550e94d04db518edccafb1d6bcf46d0320b
ms.sourcegitcommit: 141f2d83f70cb467eee59191197cdb9446d8ef31
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2020
ms.locfileid: "81123066"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

为作业设置访问控制列表（ACL）传播标志。 标志指示你希望在要下载的文件中维护所有者和 ACL 信息。 例如，若要维护文件的所有者和组，请将 **flags**参数设置为 `og`。

## <a name="syntax"></a>语法

```
bitsadmin /setaclflag <job> <flags>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| flags | 指定一个或多个值，包括：<ul><li>**o** -将所有者信息复制到文件。</li><li>**g** -复制组信息和文件。</li><li>**d** -使用文件复制随机访问控制列表（DACL）信息。</li><li>**s** -使用文件复制系统访问控制列表（SACL）信息。</li></ul> |

## <a name="remarks"></a>备注

当作业从 Windows （SMB）共享下载数据时，/setaclflag 开关用于维护所有者和访问控制列表信息。

## <a name="examples"></a>示例

下面的示例设置名为*myDownloadJob*的作业的访问控制列表传播标志，以使用下载的文件维护所有者和组信息。

```
C:\>bitsadmin /setaclflags myDownloadJob og
```

## <a name="additional-references"></a>其他参考

[命令行语法关键字](command-line-syntax-key.md)&reg;"    