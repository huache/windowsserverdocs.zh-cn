---
title: bcdedit
description: 用于创建新存储、修改现有存储以及添加启动菜单参数的 bcdedit 命令的参考文章。
ms.topic: reference
ms.assetid: ab2da47d-3aac-44a0-b7fd-bd9561d61553
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/27/2018
ms.openlocfilehash: b3cd41f3ba1980718a5e2c0a37df470a94f67657
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632972"
---
# <a name="bcdedit"></a>bcdedit

引导配置数据 (BCD) 文件提供用于描述启动应用程序和启动应用程序设置的存储。 存储中的对象和元素有效地替换 Boot.ini。

BCDEdit 是用于管理 BCD 存储的命令行工具。 它可用于多种用途，包括创建新存储、修改现有存储、添加启动菜单参数等等。 BCDEdit 的作用实质上与早期版本的 Windows Bootcfg.exe 相同，但有两个主要改进：

- 公开与 Bootcfg.exe 范围更广的启动参数。

- 提高了脚本支持。

> [!NOTE]
> 需要管理权限才能使用 BCDEdit 来修改 BCD。

BCDEdit 是编辑 Windows Vista 和更新版本的 Windows 的启动配置的主要工具。 该工具与 Windows Vista 分发一起包含在 %WINDIR%\System32 文件夹中。

BCDEdit 限制为标准数据类型，主要用于对 BCD 执行单个常见更改。 对于更复杂的操作或非标准的数据类型，请考虑使用 BCD Windows Management Instrumentation (WMI) 应用程序编程接口 (API) ，以创建功能更强大和更灵活的自定义工具。

## <a name="syntax"></a>语法

```
bcdedit /command [<argument1>] [<argument2>] ...
```

### <a name="parameters"></a>参数

### <a name="general-bcdedit-command-line-options"></a>常规 BCDEdit 命令行选项

| 选项 | 说明 |
| ------ | ----------- |
| /? | 显示 BCDEdit 命令的列表。 如果不使用参数运行此命令，则会显示可用命令的摘要。 若要显示特定命令的详细帮助，请运行 **bcdedit/？** `<command>`，其中 `<command>` 是要搜索的命令的名称。 例如， **bcdedit/？ createstore** 显示 createstore 命令的详细帮助。 |

#### <a name="parameters-that-operate-on-a-store"></a>在存储区上操作的参数

| 选项 | 说明 |
| ------ | ----------- |
| /createstore | 创建新的空启动配置数据存储。 创建的存储不是系统存储区。 |
| /export | 将系统存储的内容导出到文件。 稍后可以使用此文件来还原系统存储的状态。 此命令仅对系统存储有效。 |
| /import | 使用以前使用 **/export** 选项生成的备份数据文件还原系统存储的状态。 此命令将在执行导入之前删除系统存储中的所有现有条目。 此命令仅对系统存储有效。 |
| /store | 此选项可与大多数 BCDedit 命令结合使用，以指定要使用的存储。 如果未指定此选项，则 BCDEdit 将在系统存储区上操作。 自行运行 **bcdedit/store** 命令等效于运行 **bcdedit/enum active** 命令。 |

#### <a name="parameters-that-operate-on-entries-in-a-store"></a>对存储中的项进行操作的参数

| 参数 | 说明 |
| ------ | ----------- |
| /copy | 在同一系统存储中创建指定启动项的副本。 |
| /create | 在启动配置数据存储中创建新条目。 如果指定了众所周知的标识符，则不能指定 **/application**、 **/inherit**和 **/device** 参数。 如果未指定标识符或未指定标识符，则必须指定 **/application**、 **/inherit**或 **/device** 选项。 |
| /delete | 从指定的项中删除一个元素。 |

#### <a name="parameters-that-operate-on-entry-options"></a>操作项选项的参数

| 参数 | 说明 |
| ------ | ----------- |
| /deletevalue | 从启动项中删除指定的元素。 |
| /set | 设置输入选项值。 |

#### <a name="parameters-that-control-output"></a>控制输出的参数

| 参数 | 说明 |
| ------ | ----------- |
| /enum | 列出存储中的条目。 **/Enum**选项是 BCEdit 的默认值，因此，运行不带参数的**bcdedit**命令等效于运行**bcdedit/enum active**命令。 |
| /v | 详细模式。 通常，任何已知的条目标识符均由其友好速记形式表示。 将 **/v** 指定为命令行选项，将全部标识符全部显示。 自行运行 **bcdedit/v** 命令等效于运行 **bcdedit/enum active/v** 命令。 |

#### <a name="parameters-that-control-the-boot-manager"></a>控制启动管理器的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootsequence | 指定用于下一次启动的一次性显示顺序。 此命令类似于 **/displayorder** 选项，只不过它仅在计算机下次启动时使用。 之后，计算机将恢复为原始显示顺序。 |
| /默认27000 | 指定在超时过期时启动管理器选择的默认项。 |
| /displayorder | 指定启动管理器向用户显示启动参数时使用的显示顺序。 |
| /timeout | 指定在启动管理器选择默认条目之前等待的时间（秒）。 |
| /toolsdisplayorder | 指定在显示 " **工具** " 菜单时要使用的启动管理器的显示顺序。 |

#### <a name="parameters-that-control-emergency-management-services"></a>控制紧急管理服务的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootems | 启用或禁用指定条目 (EMS) 的紧急管理服务。 |
| /ems | 为指定的操作系统启动项启用或禁用 EMS。 |
| /emssettings | 设置计算机的全局 EMS 设置。 **/emssettings** 不会为任何特定的启动条目启用或禁用 EMS。 |

#### <a name="parameters-that-control-debugging"></a>控制调试的参数

| 参数 | 说明 |
| ------ | ----------- |
| /bootdebug | 启用或禁用指定启动项的启动调试器。 尽管此命令适用于任何启动条目，但它仅对启动应用程序有效。 |
| /dbgsettings | 指定或显示系统的全局调试器设置。 此命令不 enablepose。 若要设置单个全局调试器设置，请使用 **bcdedit/set** `<dbgsettings> <type> <value>` 命令。 |
| /debug | 启用或禁用指定启动项的内核调试器。 |

## <a name="additional-references"></a>其他参考

有关如何使用 BCDEdit 的示例，请参阅 [Bcdedit Options 参考](/windows-hardware/drivers/devtest/bcd-boot-options-reference) 文章。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
