---
title: ftp cd
description: Ftp cd 命令的参考文章，用于更改远程计算机上的工作目录。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a574855a-31b4-45c6-bce2-581c7231c99b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0676021eb923ef3f1c9225de624bb58e47a70c3c
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86957979"
---
# <a name="ftp-cd"></a>ftp cd

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

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

若要将远程计算机上的目录更改为*文档*，请键入：

```
cd Docs
```

若要将远程计算机上的目录更改为*可能的视频*，请键入：

```
cd  May Videos
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [其他 FTP 指南](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
