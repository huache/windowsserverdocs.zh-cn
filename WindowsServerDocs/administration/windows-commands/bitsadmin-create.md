---
title: bitsadmin create
description: '**Bitsadmin create**的 Windows 命令主题，它创建具有给定显示名称的传输作业。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4a922d9f15aff0a9bd064a7e987920adf3a9107d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850810"
---
# <a name="bitsadmin-create"></a>bitsadmin create

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

创建给定的显示名的传输作业。 下载作业：将数据从服务器传输到本地文件。 上载作业：将数据从本地文件传输到服务器。 上载-答复作业：将数据从本地文件传输到服务器，并从服务器接收回复文件。

使用[bitsadmin resume](bitsadmin-resume.md)开关激活传输队列中的作业。

## <a name="syntax"></a>语法

```
bitsadmin /create [type] displayname
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ------- | -------- |
| type | -  **/Download**将数据从服务器传输到本地文件。<p>-  **/Upload**将数据从本地文件传输到服务器。<p>-  **/Upload-Reply**将数据从本地文件传输到服务器，并从服务器接收回复文件。<p>如果未在命令行上指定，则此参数默认为 **/Download** 。 此外， **/Upload** 和 **/Upload-Reply** 类型在1.2 和更早版本中不可用。 |
| displayname | 分配给新创建的作业的显示名称。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

创建一个名为下载作业 *myDownloadJob*。

```
C:\>bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
