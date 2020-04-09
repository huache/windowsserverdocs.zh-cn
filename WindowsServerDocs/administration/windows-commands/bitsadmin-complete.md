---
title: bitsadmin complete
description: 用于 bitsadmin 的 Windows 命令主题**完成**作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 847f6e298ff9701064ce4e577c785f7fc78ea22c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850820"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

完成作业。 使用此开关时，将下载的文件才可供您。 作业转到已转移的状态后，请使用此开关。 否则，只有那些已成功传输的文件是可用的。

## <a name="syntax"></a>语法

```
bitsadmin /complete <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

传输作业的状态，则 BITS 已成功传输作业中的所有文件。 但是，这些文件之前将不可用您使用 **/ 完成** 切换。 

如果多个作业使用 *myDownloadJob* 作为其名称，则必须替换 *myDownloadJob* 来唯一地标识该作业的作业的 guid。

```
C:\>bitsadmin /complete myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)