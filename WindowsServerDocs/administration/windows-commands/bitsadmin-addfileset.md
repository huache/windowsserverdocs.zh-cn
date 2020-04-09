---
title: bitsadmin addfileset
description: 适用于**bitsadmin addfileset**的 Windows 命令主题，它将一个或多个文件添加到指定的作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1c4cff7dc8439fe8e1c54d1f5d231d1b487dc70c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850970"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

将一个或多个文件添加到指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /addfileset <Job> <TextFile>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| TextFile | 一个文本文件，其中每行包含一个远程和一个本地文件名。 **注意：** 名称以空格分隔。 以 `#` 字符开头的行被视为注释。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

```
C:\>bitsadmin /addfileset files.txt
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)