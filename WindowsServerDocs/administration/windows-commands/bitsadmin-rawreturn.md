---
title: bitsadmin rawreturn
description: 适用于**bitsadmin rawreturn**的 Windows 命令主题，它返回适合分析的数据。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: bbe97130-26f6-4cdd-84f1-baf530ce38b7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8cd84b6082b1fda8061ee7b324dd66991d3b206
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849880"
---
# <a name="bitsadmin-rawreturn"></a>bitsadmin rawreturn

返回适合解析的数据。 通常，将此命令与 **/create**和 **/get*** 开关一起使用以仅接收值。 必须在其他交换机之前指定此开关。

## <a name="syntax"></a>语法

```
bitsadmin /rawreturn
```

## <a name="remarks"></a>备注

- 从输出中去除换行符和格式设置。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的状态的原始数据。

```
C:\>bitsadmin /rawreturn /getstate myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)