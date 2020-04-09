---
title: 注册导入
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0816297e837bbce91ca069e3506405cbdb53c51a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80836420"
---
# <a name="reg-import"></a>注册导入



将包含导出的注册表子项、项和值的文件的内容复制到本地计算机的注册表中。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
Reg import FileName
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<文件名 >|指定包含要复制到本地计算机的注册表中的内容的文件的名称和路径。 必须使用**reg export**提前创建此文件。|
|/?|在命令提示符下显示**reg import**的帮助。|

## <a name="remarks"></a>备注

下表列出了**reg import**操作的返回值。

|值|说明|
|-----|-----------|
|0|成功|
|1|失败|

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要从名为 AppBkUp 的文件中导入注册表项，请键入：
```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)