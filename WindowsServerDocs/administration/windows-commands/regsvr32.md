---
title: regsvr32
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d3b775b0c49e4191a9fee6dc9e2e91f968142085
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836210"
---
# <a name="regsvr32"></a>regsvr32



将 .dll 文件注册为注册表中的命令组件。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <DllName>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/u|注销服务器。|
|/s|运行**Regsvr32**而不显示消息。|
|/n|在不调用**DllRegisterServer**的情况下运行**Regsvr32** 。 （需要 **/i**参数。）|
|/i：\<cmdline >|将可选的命令行字符串（*cmdline*）传递给**DllInstall**。 如果将此参数与 **/u**参数一起使用，则它将调用**DllUninstall**。|
|\<DllName >|要注册的 .dll 文件的名称。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要为 Active Directory 架构注册 .dll，请键入：
```
regsvr32 schmmgmt.dll
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)