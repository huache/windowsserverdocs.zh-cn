---
title: bitsadmin getcreationtime
description: 适用于**bitsadmin getcreationtime**的 Windows 命令主题，它检索指定作业的创建时间。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: be409cb5-ce72-41d9-aafa-edd4e230fd14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cd8f718e53cc44dc5f4c6f5ff09c9a5c201e0564
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850740"
---
# <a name="bitsadmin-getcreationtime"></a>bitsadmin getcreationtime

检索指定作业的创建时间。

## <a name="syntax"></a>语法

```
bitsadmin /getcreationtime <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的创建时间。

```
C:\>bitsadmin /getcreationtime myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)