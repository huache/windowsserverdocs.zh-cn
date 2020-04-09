---
title: bitsadmin resume
description: '**Bitsadmin resume**的 Windows 命令主题，用于激活传输队列中的新作业或挂起的作业。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a3f464ba00c5cc233c42a40c063372dc0d584e9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849750"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume

激活传输队列中的新作业或挂起的作业。

## <a name="syntax"></a>语法

```
bitsadmin /resume <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例恢复名为*myDownloadJob*的作业。

```
C:\>bitsadmin /resume myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)