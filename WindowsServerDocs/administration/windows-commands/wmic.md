---
title: wmic
description: 适用于 wmic 的参考文章，可在交互式命令行界面中显示 WMI 信息。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 76397c72-d06f-4cea-88cf-c7603315a983
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c14f877c226bdd376da39cfa6e8f11116d59fe56
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936111"
---
# <a name="wmic"></a>wmic



显示交互式命令行界面中的 WMI 信息。



## <a name="syntax"></a>语法

```
wmic </parameter>
```

## <a name="sub-commands"></a>子命令

以下子命令始终可用：

|子命令|说明|
|-----------|-----------|
|class|从 WMIC 的默认别名模式转义以直接访问 WMI 架构中的类。|
|path|从 WMIC 的默认别名模式进行转义，以直接访问 WMI 架构中的实例。|
|上下文|显示所有全局开关的当前值。|
|[退出 \| 退出]|退出 WMIC 命令行界面。|

## <a name="examples"></a>示例

若要显示所有全局开关的当前值，请键入：
```
wmic context
```
类似于以下内容的输出：
```
NAMESPACE    : root\cimv2
ROLE         : root\cli
NODE(S)      : BOBENTERPRISE
IMPLEVEL     : IMPERSONATE
[AUTHORITY   : N/A]
AUTHLEVEL    : PKTPRIVACY
LOCALE       : ms_409
PRIVILEGES   : ENABLE
TRACE        : OFF
RECORD       : N/A
INTERACTIVE  : OFF
FAILFAST     : OFF
OUTPUT       : STDOUT
APPEND       : STDOUT
USER         : N/A
AGGREGATE    : ON
```
若要将命令行使用的语言 ID 更改为英语（区域设置 ID 409），请键入：
```
wmic /locale:ms_409
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
