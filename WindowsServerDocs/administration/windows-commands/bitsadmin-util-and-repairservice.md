---
title: bitsadmin util 和 repairservice
description: Windows 命令主题，适用于 bitsadmin util 和 repairservice，用于修复各种版本的 BITS 服务中的已知问题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2ac7baeb-4340-4186-bfcb-66478195378d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: aaaa6edab22031dc53d266984bb669634e3bb362
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848890"
---
# <a name="bitsadmin-util-and-repairservice"></a>bitsadmin util 和 repairservice

如果 BITS 无法启动，请使用此开关修复各种版本的 BITS 中的已知问题。

**BITSAdmin 1.5 及更早版本：**  不受支持。

## <a name="syntax"></a>语法

```
bitsadmin /Util /RepairService [/Force]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|Force|可选-删除并重新创建该服务。|

## <a name="remarks"></a>备注

此开关解决了与不正确的服务配置和 Windows 服务（如 LANManworkstation）和网络目录的依赖项相关的错误。 此开关生成一个输出，用于指示是否已解决问题。

> [!NOTE]
> 如果 BITS 重新创建服务，则可以在本地化系统中将服务说明字符串设置为英语。

> [!IMPORTANT]
> Windows Vista 不支持此命令。

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例修复 BITS 服务配置。
```
C:\>bitsadmin /Util /RepairService
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)