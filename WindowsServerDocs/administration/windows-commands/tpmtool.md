---
title: tpmtool
description: Tpmtool 的参考文章，可获取有关受信任的平台模块的信息。
ms.topic: article
author: ashleytqy
ms.author: ashleytqy
manager: ronaldai
ms.date: 05/07/2019
ms.openlocfilehash: f34e577a87acd79f343f06bb81486d50339cdb54
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87897134"
---
# <a name="tpmtool"></a>tpmtool

此实用程序可用于获取有关[受信任的平台模块 (TPM) ](/windows/security/information-protection/tpm/trusted-platform-module-overview)的信息。

>[!IMPORTANT]
>有些信息与预发布产品相关，这些产品在商业发行之前可能发生重大更改。 对于此处提供的信息，Microsoft 不作任何明示或暗示的担保。

有关如何使用此命令的示例，请参阅[示例](#tpmtool_examples)。

## <a name="syntax"></a>语法

```
tpmtool /parameter [<arguments>]
```
### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|getdeviceinformation|显示 TPM 的基本信息。 [此处](/windows/desktop/secprov/win32-tpm-isreadyinformation#parameters)提供信息标志值的含义。|
|gatherlogs [输出目录路径]|收集 TPM 日志，并将其放在指定的目录中。 如果该目录不存在，则创建它。 默认情况下，它们位于当前目录中。 生成的可能文件包括： </br>-TpmEvents .evtx</br>-TpmInformation.txt</br>-SRTMBoot</br>-SRTMResume</br>-DRTMBoot</br>-DRTMResume</br>|
|drivertracing [start/stop]|开始/停止收集 TPM 驱动程序跟踪。 将生成跟踪日志 TPMTRACE，并将其放入当前目录。|
|/?|在命令提示符下显示帮助。|

## <a name="examples"></a><a name=tpmtool_examples></a>示例

若要显示 TPM 的基本信息，请键入：
```
tpmtool getdeviceinformation
```
若要收集 TPM 日志并将其放在当前目录中，请键入：
```
tpmtool gatherlogs
```
若要收集 TPM 日志并将其放入 `C:\Users\Public` ，请键入：
```
tpmtool gatherlogs C:\Users\Public
```
若要收集 TPM 驱动程序跟踪，请键入：
```
tpmtool drivertracing start
# Run scenario
tpmtool drivertracing stop
```

## <a name="decoding-error-codes"></a>编码错误代码

[此处](/windows/desktop/com/com-error-codes-6)介绍了特定于 TPM 的错误代码。
