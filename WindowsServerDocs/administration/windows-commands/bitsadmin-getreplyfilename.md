---
title: bitsadmin getreplyfilename
description: Bitsadmin getreplyfilename 命令的参考文章，可获取包含该作业的服务器上传答复的文件的路径。
ms.topic: article
ms.assetid: 85447184-1732-4816-a365-2e3599551bf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 213df5c5dcef57db8f1cdc2b26c90dbdc124007c
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87893883"
---
# <a name="bitsadmin-getreplyfilename"></a>bitsadmin getreplyfilename

获取文件的路径，该文件包含作业的服务器上载答复。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getreplyfilename <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的上传-答复文件名：

```
bitsadmin /getreplyfilename myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
