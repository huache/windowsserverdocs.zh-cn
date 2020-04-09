---
title: bitsadmin getpriority
description: 用于**bitsadmin getpriority**的 Windows 命令主题，它检索指定作业的优先级。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: b27829a0fb852abb88c88a65e61e8d7693ca2df2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850540"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

检索指定的作业的优先级。

## <a name="syntax"></a>语法

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

此命令的优先级可以是：

- **后台**

- **严重**

- **一般**

- **低级**

- **未知**

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的优先级 *myDownloadJob*。

```
C:\>bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
