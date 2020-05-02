---
title: bitsadmin replaceremoteprefix
description: Bitsadmin replaceremoteprefix 命令的参考主题，可根据需要将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 745d026513413db799e86df3422d5ee19c89274f
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717040"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

必要时，将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。

## <a name="syntax"></a>语法

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| oldprefix | 现有的 URL 前缀。 |
| newprefix | 新的 URL 前缀。 |

## <a name="examples"></a>示例

若要将名为*myDownloadJob*的作业中的所有文件的远程*http://stageserver* URL *http://prodserver*更改为，则为。

```
bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>其他信息

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
