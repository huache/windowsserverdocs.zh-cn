---
title: bitsadmin geterrorcount
description: 适用于 bitsadmin geterrorcount 的 Windows 命令主题，它检索指定作业生成暂时性错误的次数的计数。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1711781dd416311e45874b7c611f3f8f42a06854
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850690"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount

检索指定的作业生成的暂时性错误的次数计数。

## <a name="syntax"></a>语法

```
bitsadmin /geterrorcount <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的错误计数信息 *myDownloadJob*。

```
C:\>bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)