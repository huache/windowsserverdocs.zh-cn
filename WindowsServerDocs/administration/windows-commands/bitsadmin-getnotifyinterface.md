---
title: bitsadmin getnotifyinterface
description: 用于确定其他程序是否已为指定作业注册 COM 回调接口的 bitsadmin getnotifyinterface 命令的参考文章。
ms.topic: reference
ms.assetid: 40bf9dd8-b167-406a-80a6-a5a6f1b8cf7f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1455975083ac6afb25a02dc19c6df282928af587
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027805"
---
# <a name="bitsadmin-getnotifyinterface"></a>bitsadmin getnotifyinterface

确定其他程序是否已将 COM 回调接口注册 (通知接口) 指定的作业。

## <a name="syntax"></a>语法

```
bitsadmin /getnotifyinterface <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

#### <a name="output"></a>输出

此命令的输出将显示 " **已注册** " 或 "已 **注销**"。

> [!NOTE]
> 不能确定注册了回调接口的程序。

## <a name="examples"></a>示例

若要检索名为 *myDownloadJob*的作业的通知接口，请执行以下操作：

```
bitsadmin /getnotifyinterface myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
