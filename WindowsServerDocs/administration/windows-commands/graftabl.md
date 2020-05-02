---
title: graftabl
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b08351d4-3d24-490c-86f6-1252da11d923
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b3815b85da163c03dea7bd2619d4647454d3ebd7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82724925"
---
# <a name="graftabl"></a>graftabl



使 Windows 操作系统能够在图形模式下显示扩展字符集。 如果在没有参数的情况下使用，则**graftabl**将显示前一个和当前代码页。



## <a name="syntax"></a>语法

```
graftabl <CodePage>
graftabl /status
```

### <a name="parameters"></a>参数

|参数|描述|
|---------|-----------|
|\<代码页>|指定一个代码页，用于定义图形模式下扩展字符的外观。</br>有效的代码页标识号为：</br>437：美国</br>850：多语言（拉丁语 I）</br>852：斯拉夫语（拉丁语 II）</br>855：西里尔语（俄语）</br>857：土耳其语</br>860：葡萄牙语</br>861：冰岛语</br>863：加拿大-法语</br>865：北欧</br>866：俄语</br>869：新式希腊语|
|/status|显示**graftabl**正在使用的当前代码页。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   **Graftabl**仅影响指定的代码页的扩展字符的监视器显示。 它不会更改实际的控制台输入代码页。 若要更改控制台输入代码页，请使用**模式**或**chcp**命令。
-   下表列出了每个退出代码以及它的简短说明。  
    |退出代码|描述|
    |---------|-----------|
    |0|已成功加载字符集。 未加载上一个代码页。|
    |1|指定的参数不正确。 未采取任何操作。|
    |2|出现文件错误。|
-   可以在批处理程序中使用 ERRORLEVEL 环境变量来处理**graftabl**返回的退出代码。

## <a name="examples"></a>示例

若要查看**graftabl**使用的当前代码页，请键入：
```
graftabl /status
```
若要将代码页437（美国）的图形字符集加载到内存中，请键入：
```
graftabl 437
```
若要将代码页850（多语言）的图形字符集加载到内存中，请键入：
```
graftabl 850
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

[Freedisk](freedisk.md)

[Chcp](chcp.md)