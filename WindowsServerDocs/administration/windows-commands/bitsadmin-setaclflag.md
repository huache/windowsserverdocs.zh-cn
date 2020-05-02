---
title: bitsadmin setaclflag
description: Bitsadmin setaclflag 命令的参考主题，用于设置访问控制列表（ACL）传播标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 6e3bcda0-827d-4dfd-8384-d1da018f3e10
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1852bd267fe22825d55f7522a81179e9290e2a00
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82716990"
---
# <a name="bitsadmin-setaclflag"></a>bitsadmin setaclflag

为作业设置访问控制列表（ACL）传播标志。 标志指示你希望在要下载的文件中维护所有者和 ACL 信息。 例如，若要维护文件的所有者和组，请将 **flags**参数设置为`og`。

## <a name="syntax"></a>语法

```
bitsadmin /setaclflag <job> <flags>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| flags | 指定一个或多个值，包括：<ul><li>**o** -将所有者信息复制到文件。</li><li>**g** -复制组信息和文件。</li><li>**d** -使用文件复制随机访问控制列表（DACL）信息。</li><li>**s** -使用文件复制系统访问控制列表（SACL）信息。</li></ul> |

## <a name="examples"></a>示例

若要设置名为*myDownloadJob*的作业的访问控制列表传播标志，使其与下载的文件一起维护所有者和组信息。

```
bitsadmin /setaclflags myDownloadJob og
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
