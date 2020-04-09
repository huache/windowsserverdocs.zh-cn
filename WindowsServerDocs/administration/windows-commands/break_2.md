---
title: break
description: 适用于 break_2 的 Windows 命令主题，它将卷影副本卷与 VSS 解除相关，并使其作为常规卷进行访问。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: de2b6c95-1c2e-4a43-bec5-341a9014371b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6683c44c84f4baae5f016f7df62d5bd6591cff70
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80848250"
---
# <a name="break"></a>break

将卷影副本卷与 VSS 解除映射，并使其作为常规卷进行访问。 然后，可以使用驱动器号（如果已指定）或卷名访问该卷。 如果不使用参数， **break**将在命令提示符下显示帮助。

> [!NOTE]
> 此命令仅适用于导入后的硬件卷影副本。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
break [writable] <SetID>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|编写|启用对卷的读/写访问。|
|\<SetID >|指定卷影副本集的 ID。|

## <a name="remarks"></a>备注

-   公开的卷（例如它们源自的卷影副本）默认为只读。
-   可以在*SetID*参数中使用卷影副本 ID 的别名，该 ID 由**load metadata**命令存储为环境变量。

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要在操作系统中使用别名 Alias1 作为可写卷访问的卷影副本，请键入：
```
break writable %Alias1%
```

> [!NOTE]
> 对卷的访问直接对硬件提供程序进行，而不记录卷的卷影副本。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)