---
title: 加载元数据
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2c535487-668b-44fc-babb-ff59cf7d190e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b8db98611fd78c6e30070901effafddd6e678c16
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80841020"
---
# <a name="load-metadata"></a>加载元数据



在导入可传送的卷影副本之前加载元数据 .cab 文件，或者在还原时加载写入器元数据。 如果在没有参数的情况下使用，**加载元数据**将在命令提示符下显示帮助。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
load metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[\<驱动器 >：][<Path>]|指定元数据文件的位置。|
|MetaData .cab|指定要加载的元数据 .cab 文件。|

## <a name="remarks"></a>备注

-   您可以使用 "**导入**" 命令根据**负载元数据**指定的元数据导入可传送的卷影副本。
-   此命令在 "**开始还原**" 命令之前需要，以便加载所选编写器和组件以进行还原。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要从默认位置加载名为元文件的元数据文件，请键入：
```
load metadata metafile.cab
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)