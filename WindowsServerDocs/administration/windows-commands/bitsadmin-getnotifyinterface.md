---
title: bitsadmin getnotifyinterface
description: 适用于**bitsadmin getnotifyinterface**的 Windows 命令主题，它确定其他程序是否已为指定作业注册 COM 回调接口。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5eb5aee42446c70f16fd6785a3645f42c1987e4d
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850570"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

确定其他程序是否已为指定作业注册 COM 回调接口（通知接口）。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifyinterface <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

#### <a name="output"></a>Output

此命令的输出将显示 "**已注册**" 或 "已**注销**"。

> [!NOTE]
> 不能确定注册的回调接口的程序。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为的作业的通知接口 *myDownloadJob*。

```
C:\>bitsadmin /getnotifyinterface myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)