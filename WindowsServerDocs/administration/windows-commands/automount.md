---
title: automount
description: 用于启用或禁用自动装载功能的自动装载命令的参考文章。
ms.topic: reference
ms.assetid: 4635fc91-a477-4f17-8dcc-aa08854bfe45
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 92fa9f66db510d887af793882a2400b31a1517c4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031635"
---
# <a name="automount"></a>automount

适用于：Windows Server（半年频道）、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

- [命令行语法项](command-line-syntax-key.md)

> [!IMPORTANT]
> 在存储区域网络 (SAN) 配置中，禁用自动装载会阻止 Windows 自动将驱动器号装入或分配给系统可以看到的任何新基本卷。

## <a name="syntax"></a>语法

自动装载 [{enable | disable | 推移}] [noerr]

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| enable | 使 Windows 能够自动挂载添加到系统的新基本卷和动态卷，并为其分配驱动器号。 |
| disable | 阻止 Windows 自动安装添加到系统中的任何新基本卷和动态卷。<p>**注意**：禁用自动装载可能导致故障转移群集无法通过验证配置向导的存储部分。 |
| scrub | 删除不再位于系统中的卷的卷装入点目录和注册表设置。 该操作防止自动装入已经位于系统中的卷，并防止在其重新添加到系统时给定以前的卷装入点。 |
| noerr | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="examples"></a>示例

若要查看是否已启用自动装载功能，请在 diskpart 命令中键入以下命令：

```
automount
```

若要启用自动装载功能，请键入：

```
automount enable
```

若要禁用自动装载功能，请键入：

```
automount disable
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [diskpart 命令](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/cc770877(v%3dws.11))
