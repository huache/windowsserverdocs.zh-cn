---
title: bitsadmin 缓存和 deleteurl
description: '**Bitsadmin 缓存和 deleteurl**的 Windows 命令主题，用于删除给定 URL 的所有缓存条目。'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 70099e795d0f05d0fcf75fbf6b82f5466d1c0c55
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850930"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>bitsadmin 缓存和 deleteurl

删除给定 URL 的所有缓存条目。

## <a name="syntax"></a>语法

```
bitsadmin /deleteURL url
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| url | 标识远程文件的统一资源定位器。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将删除的所有缓存条目 `https://www.contoso.com/en/us/default.aspx`

```
C:\>bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx 
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)