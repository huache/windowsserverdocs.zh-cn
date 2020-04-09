---
title: 展开 vdisk
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 272714372a35f7f205b5a2e70cb2f2669b3a0634
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844890"
---
# <a name="expand-vdisk"></a>展开 vdisk

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

将虚拟硬盘（VHD）扩展到指定的大小。
> [!NOTE]
> 此命令仅适用于 Windows 7 和 Windows Server 2008 R2。
> ## <a name="syntax"></a>语法
> ```
> expand vdisk maximum=<n>
> ```
> ### <a name="parameters"></a>参数
> 
> |  参数  |                      说明                      |
> |-------------|-------------------------------------------------------|
> | 最大值 =<n> | 指定 VHD 的新大小（以兆字节（MB）为单位）。 |
> 
> ## <a name="remarks"></a>备注
> - 必须选择并分离 VHD，此操作才能成功。 使用 "**选择 vdisk** " 命令选择卷并将焦点移动到该卷。
>   ## <a name="examples"></a><a name=BKMK_Examples></a>示例
>   若要将所选 VHD 扩展到 20 GB，请键入：
>   ```
>   expand vdisk maximum=20000
>   ```
>   ## <a name="additional-references"></a>其他参考
> - - [命令行语法项](command-line-syntax-key.md)
> - [附加 vdisk](attach-vdisk.md)
> - [compact vdisk](compact-vdisk.md)

-   [分离 vdisk](detach-vdisk.md)
-   [详细信息 vdisk](detail-vdisk.md)
-   [Merge vdisk](merge-vdisk.md)
-   [选择 vdisk](select-vdisk.md)
-   [list_1](list_1.md)
