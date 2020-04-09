---
title: bitsadmin getcustomheaders
description: 适用于**bitsadmin getcustomheaders**的 Windows 命令主题，用于从作业中检索自定义 HTTP 标头。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 80a3d1230fd541f0b986434ce373da4c8bb0c761
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850730"
---
# <a name="bitsadmin-getcustomheaders"></a>bitsadmin getcustomheaders

从作业检索自定义 HTTP 标头。

## <a name="syntax"></a>语法

```
bitsadmin /getcustomheaders <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例获取名为*myDownloadJob*的作业的自定义标头。

```
C:\>bitsadmin /getcustomheaders myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)