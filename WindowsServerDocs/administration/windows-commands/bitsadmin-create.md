---
title: bitsadmin create
description: Bitsadmin create 命令的参考文章，用于创建具有给定显示名称的传输作业。
ms.topic: article
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ca651705955826ab3b65bd95aa90c98170bdb935
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894599"
---
# <a name="bitsadmin-create"></a>bitsadmin create

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建给定的显示名的传输作业。

> [!NOTE]
> **/Upload**   BITS 1.2 和更早版本不支持/Upload 和 **/Upload-Reply**参数类型。

## <a name="syntax"></a>语法

```
bitsadmin /create [type] displayname
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| type | 有三种类型的作业：<ul><li>**下载.** 将数据从服务器传输到本地文件。</li><li>**上.** 将数据从本地文件传输到服务器。</li><li>**/Upload-Reply.** 将数据从本地文件传输到服务器，并从服务器接收回复文件。</li></ul>如果未指定此参数，则此参数的默认值为 **/Download** 。 |
| displayname | 分配给新创建的作业的显示名称。 |

## <a name="examples"></a>示例

若要创建名为*myDownloadJob*的下载作业：

```
bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin resume 命令](bitsadmin-resume.md)

- [bitsadmin 命令](bitsadmin.md)
