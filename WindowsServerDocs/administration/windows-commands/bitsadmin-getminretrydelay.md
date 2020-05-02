---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay 命令的参考主题，它检索在尝试传输文件之前服务遇到暂时性错误的时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a50b9d98fe0b873dc58b8e86dc672a8f4157208a
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717844"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

检索在尝试传输文件之前服务遇到暂时性错误后将等待的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的最小重试延迟时间：

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
