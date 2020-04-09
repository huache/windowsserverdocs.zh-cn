---
title: bitsadmin getproxyusage
description: 适用于**bitsadmin getproxyusage**的 Windows 命令主题，它检索指定作业的代理使用情况设置。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: f940a70e-3b02-497e-a47f-b37b905c299e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 01c9bb9a1d413fa847482f652e18eed30ad76109
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850510"
---
# <a name="bitsadmin-getproxyusage"></a>bitsadmin getproxyusage

检索指定作业的代理使用情况设置。

## <a name="syntax"></a>语法

```
bitsadmin /getproxyusage <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

代理使用值包括：

- **预配置**-使用所有者的 Internet Explorer 默认值。

- **No_Proxy** -不使用代理服务器。

- **替代**-使用显式代理列表。

- 自动**检测-自动**检测代理设置。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的代理使用情况。

```
C:\>bitsadmin /getproxyusage myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)