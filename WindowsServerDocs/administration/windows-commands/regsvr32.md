---
title: regsvr32
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3345e964-7d3e-42b8-abeb-42ed6edfe2b2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: beadc9e9e614e2fe4cffad5dc263cfb1d4aecf67
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722479"
---
# <a name="regsvr32"></a>regsvr32



将 .dll 文件注册为注册表中的命令组件。



## <a name="syntax"></a>语法

```
regsvr32 [/u] [/s] [/n] [/i[:cmdline]] <DllName>
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|/U|注销服务器。|
|/s|运行**Regsvr32**而不显示消息。|
|/n|在不调用**DllRegisterServer**的情况下运行**Regsvr32** 。 （需要 **/i**参数。）|
|/i：\<cmdline>|将可选的命令行字符串（*cmdline*）传递给**DllInstall**。 如果将此参数与 **/u**参数一起使用，则它将调用**DllUninstall**。|
|\<DllName>|要注册的 .dll 文件的名称。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a>示例

若要为 Active Directory 架构注册 .dll，请键入：
```
regsvr32 schmmgmt.dll
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)