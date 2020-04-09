---
title: bitsadmin nowrap
description: 适用于**bitsadmin nowrap**的 Windows 命令主题，它截断超出命令窗口最右边边缘的任何输出文本行。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f9f1db370d8a8917aa03a414a27623a1024df192
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850180"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

截断超出命令窗口最右边缘的任何输出文本行。 默认情况下，除**监视器**开关外，所有交换机都将输出换行。 在其他交换机之前指定**nowrap**开关。

## <a name="syntax"></a>语法

```
bitsadmin /nowrap
```

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将检索名为*myDownloadJob*的作业的状态，并且不会包装输出。

```
C:\>bitsadmin /nowrap /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)