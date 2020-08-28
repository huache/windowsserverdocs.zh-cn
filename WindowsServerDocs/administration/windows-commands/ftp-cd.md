---
title: ftp cd
description: Ftp cd 命令的参考文章，用于更改远程计算机上的工作目录。
ms.topic: reference
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7ab8992bfcbd10d487b5a460ecd25a0dad349ffc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037305"
---
# <a name="ftp-cd"></a>ftp cd

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改远程计算机上的工作目录。

## <a name="syntax"></a>语法

```
cd <remotedirectory>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| <remotedirectory> | 指定要更改的远程计算机上的目录。 |

### <a name="examples"></a>示例

若要将远程计算机上的目录更改为 *文档*，请键入：

```
cd Docs
```

若要将远程计算机上的目录更改为 *可能的视频*，请键入：

```
cd  May Videos
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
