---
title: Vssadmin 调整大小 shadowstorage
description: Vssadmin resize shadowstorage 命令的说明。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 03/05/2020
ms.localizationpriority: medium
ms.openlocfilehash: e32fe419899c0f553f36976ecee95fb3a922f1a6
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2020
ms.locfileid: "83436622"
---
# <a name="vssadmin-resize-shadowstorage"></a>Vssadmin 调整大小 shadowstorage

> 适用于： Windows 10，Windows 8.1，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2，Windows Server 2008

调整可用于卷影副本存储的最大存储空间量。

可以使用**MinDiffAreaFileSize**注册表值指定可用于卷影副本存储的最小存储空间量。 有关详细信息，请参阅[MinDiffAreaFileSize](https://docs.microsoft.com/windows/win32/backup/registry-keys-for-backup-and-restore#mindiffareafilesize)。

> [!WARNING]
> 调整存储关联的大小可能会导致卷影副本消失。

## <a name="syntax"></a>语法

```cmd
vssadmin resize shadowstorage /for=<ForVolumeSpec> /on=<OnVolumeSpec> [/maxsize=<MaxSizeSpec>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---|---|
`/for=<ForVolumeSpec>`  | 指定要调整其最大存储空间量的卷。
`/on=<OnVolumeSpec>` | 指定存储卷。
`[/maxsize=<MaxSizeSpec>]` |  指定可用于存储卷影副本的最大空间量。 如果没有为/maxsize 指定任何值，则可以使用的存储空间量没有限制。  <br> <br> MaxSizeSpec 值必须为 1 MB 或更大，且必须以下列单位之一表示： KB、MB、GB、TB、PB 或 EB。 如果未指定单位，则默认情况下 MaxSizeSpec 使用字节。

## <a name="examples"></a>示例

```cmd
vssadmin Resize ShadowStorage /For=C: /On=D: /MaxSize=900MB
vssadmin Resize ShadowStorage /For=C: /On=D: /MaxSize=UNBOUNDED
vssadmin Resize ShadowStorage /For=C: /On=C: /MaxSize=20%
```

## <a name="additional-references"></a>其他参考

* [命令行语法关键字](https://docs.microsoft.com/windows-server/administration/windows-commands/command-line-syntax-key)
* [List](vssadmin.md)
