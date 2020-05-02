---
title: bitsadmin getnotifyinterface
description: Bitsadmin getnotifyinterface 命令的参考主题，它确定其他程序是否已为指定作业注册 COM 回调接口。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2158759067010292ca213f97014857354247b9c7
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82717740"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

确定其他程序是否已为指定作业注册 COM 回调接口（通知接口）。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifyinterface <job>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

此命令的输出将显示 "**已注册**" 或 "已**注销**"。

> [!NOTE]
> 不能确定注册了回调接口的程序。

## <a name="examples"></a>示例

若要检索名为*myDownloadJob*的作业的通知接口，请执行以下操作：

```
bitsadmin /getnotifyinterface myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
