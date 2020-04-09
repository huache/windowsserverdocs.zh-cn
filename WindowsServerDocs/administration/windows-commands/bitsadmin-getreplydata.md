---
title: bitsadmin getreplydata
description: 适用于**bitsadmin getreplydata**的 Windows 命令主题，它以十六进制格式为作业检索服务器的上载答复数据。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: fb83ca93f8e73445788d926e0d5e6db4c774d759
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850500"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

检索以十六进制格式用于作业的服务器的上载答复数据。

> [!NOTE]
> BITS 1.2 和更早版本不支持此命令。

## <a name="syntax"></a>语法

```
bitsadmin /getreplydata <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的上传回复数据。

```
C:\>bitsadmin /getreplydata myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)