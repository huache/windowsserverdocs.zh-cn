---
title: bitsadmin replaceremoteprefix
description: '**Bitsadmin replaceremoteprefix**的 Windows 命令主题，根据需要将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d0e0abb1-bdb4-4c74-abbc-16c809f5fd81
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0cea0108a292815e31e893e91dc4079305c1da9a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849810"
---
# <a name="bitsadmin-replaceremoteprefix"></a>bitsadmin replaceremoteprefix

必要时，将作业中所有文件的远程 URL 从*oldprefix*更改为*newprefix*。

## <a name="syntax"></a>语法

```
bitsadmin /replaceremoteprefix <job> <oldprefix> <newprefix>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |
| oldprefix | 现有的 URL 前缀。 |
| newprefix | 新的 URL 前缀。 |

## <a name="examples"></a>示例

下面的示例将名为*myDownloadJob*的作业中的所有文件的远程 URL 从 *http://stageserver* 更改为 *http://prodserver* 。

```
C:\>bitsadmin /replaceremoteprefix myDownloadJob http://stageserver http://prodserver
```

## <a name="additional-information"></a>其他信息

- [命令行语法项](command-line-syntax-key.md)