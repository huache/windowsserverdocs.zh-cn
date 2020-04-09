---
title: ftp put
description: 用于 FTP 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 95cc1e3f-523d-4374-98b8-16e6c276b2ca vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/30/2020
ms.openlocfilehash: ecd579a313fe1cad1b8a5b4a622aaaec2d6a6d63
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80843130"
---
# <a name="ftp-put"></a>ftp： put

> 适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

使用当前文件传输类型将本地文件复制到远程计算机。
## <a name="syntax"></a>语法
```
put <LocalFile> [<remoteFile>]
```
#### <a name="parameters"></a>参数

|    参数     |                    说明                    |
|------------------|---------------------------------------------------|
|   `<LocalFile>`  |         指定要复制的本地文件。         |
| `[<remoteFile>]` | 指定要在远程计算机上使用的名称。 |

## <a name="remarks"></a>备注
- **Put**命令与**send**命令完全相同。
- 如果未指定*remoteFile* ，则会为该文件提供*LocalFile*名称。
  ## <a name="examples"></a><a name="BKMK_Examples"></a>示例
  复制本地文件**test.txt** ，并在远程计算机上将其命名为**test1。**
  ```
  put test.txt test1.txt
  ```
  将本地文件**setup.exe**复制到远程计算机。
  ```
  put program.exe
  ```
  ## <a name="additional-references"></a>其他参考
- [ftp： ascii](ftp-ascii.md)
- [ftp：二进制](ftp-binary.md)
- - [命令行语法项](command-line-syntax-key.md)
