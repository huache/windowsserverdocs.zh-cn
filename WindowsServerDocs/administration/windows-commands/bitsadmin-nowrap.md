---
title: bitsadmin nowrap
description: Bitsadmin nowrap 命令的参考文章，它截断超出命令窗口最右边边缘的任何输出文本行。
ms.topic: reference
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d2d0afe483a48e4e699c506c650cdec61076643b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026635"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

截断超出命令窗口最右边缘的任何输出文本行。 默认情况下，除 **监视器** 开关外，所有交换机都将输出换行。 在其他交换机之前指定 **nowrap** 开关。

## <a name="syntax"></a>语法

```
bitsadmin /nowrap
```

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob* 的作业的状态，但不包装输出：

```
bitsadmin /nowrap /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
