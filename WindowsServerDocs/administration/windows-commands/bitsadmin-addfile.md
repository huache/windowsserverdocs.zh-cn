---
title: bitsadmin addfile
description: Bitsadmin addfile 命令的参考文章，可将文件添加到指定的作业。
ms.topic: article
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c9bc00f1b63c559d048c9ae590df29f7421e42ec
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87894940"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

将文件添加到指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /addfile <job> <remoteURL> <localname>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| remoteURL | 服务器上的文件的 URL。 |
| localname | 本地计算机上的文件的名称。 *Localname*必须包含文件的绝对路径。 |

## <a name="examples"></a>示例

若要将文件添加到作业：

```
bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

对要添加的每个文件重复此调用。 如果多个作业使用 *myDownloadJob* 作为其名称，则必须替换 *myDownloadJob* 来唯一地标识该作业的作业的 guid。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
