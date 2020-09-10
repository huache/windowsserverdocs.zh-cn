---
title: bitsadmin getreplyprogress
description: Bitsadmin getreplyprogress 命令的参考文章，用于检索服务器上传的大小和进度。
ms.topic: reference
ms.assetid: 7f7cb0b4-ad95-44fd-a35d-0ddf5fc0b0d0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7dffacb53044175b8c65d3832863d17d59853b3a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631697"
---
# <a name="bitsadmin-getreplyprogress"></a>bitsadmin getreplyprogress

检索服务器上传-答复的大小和进度。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getreplyprogress <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的上传应答进度：

```
bitsadmin /getreplyprogress myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
