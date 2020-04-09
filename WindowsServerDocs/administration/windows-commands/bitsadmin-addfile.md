---
title: bitsadmin addfile
description: 适用于**bitsadmin addfile**的 Windows 命令主题，用于将文件添加到指定的作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 330e79eb2ba5a824cea54094f64ceb6f9cfd66b9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850960"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

将文件添加到指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /AddFile <Job> <RemoteURL> <LocalName>
```

#### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 | 作业的显示名称或 GUID。 |
| RemoteURL | 服务器上的文件的 URL。 |
| LocalName | 本地计算机上的文件的名称。 *LocalName*必须包含文件的绝对路径。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

将文件添加到作业。 对要添加的每个文件重复此调用。 如果多个作业使用 *myDownloadJob* 作为其名称，则必须替换 *myDownloadJob* 来唯一地标识该作业的作业的 guid。

```
C:\>bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

## <a name="additional-references"></a>其他参考

- [命令行语法键](command-line-syntax-key.md)&copy;