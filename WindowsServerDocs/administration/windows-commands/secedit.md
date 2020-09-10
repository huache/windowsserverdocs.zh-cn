---
title: secedit
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 58ed57ed-08e3-403d-a363-0620b358637a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8a1e4e49c5fd9cef10f6b60d18511f3a38d0dea6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635499"
---
# <a name="secedit"></a>secedit



通过将当前配置与指定的安全模板进行比较，来配置和分析系统安全。

## <a name="syntax"></a>语法

```
secedit
[/analyze /db <database file name> /cfg <configuration file name> [/overwrite] /log <log file name> [/quiet]]
[/configure /db <database file name> [/cfg <configuration filename>] [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>]]
[/generaterollback /db <database file name> /cfg <configuration file name> /rbk <rollback file name> [/log <log file name>] [/quiet]]
[/import /db <database file name> /cfg <configuration file name> [/overwrite] [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]]
[/validate <configuration file name>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|[Secedit:analyze](secedit-analyze.md)|允许你针对存储在数据库中的基线设置分析当前系统设置。  分析结果存储在数据库的一个独立区域中，可以在 "安全配置和分析" 管理单元中查看。|
|[Secedit:configure](secedit-configure.md)|允许你配置存储在数据库中的安全设置的系统。|
|[Secedit:export](secedit-export.md)|允许您导出存储在数据库中的安全设置。|
|[Secedit:generaterollback](secedit-generaterollback.md)|允许你生成与配置模板相关的回滚模板。|
|[Secedit:import](secedit-import.md)|允许您将安全模板导入到数据库中，以便在模板中指定的设置可以应用于系统或针对系统进行分析。|
|[Secedit:validate](secedit-validate.md)|允许您验证安全模板的语法。|

## <a name="remarks"></a>备注

对于所有文件名，如果未指定路径，则使用当前目录。

当使用安全模板管理单元创建安全模板并运行 "安全配置和分析" 管理单元时，将创建以下文件：


|           文件           |                                                                                                                                                                                                                                                               说明                                                                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        Scesrv.dll        |                                                                                                                             **位置**：%windir%\security\logs</br>**创建者**：操作系统</br>**文件类型**：文本</br>**刷新频率**：在 secedit/analyze、/configure、/export 或/import 运行时被覆盖。</br>**Content**：包含按策略类型分组的分析结果。                                                                                                                             |
| *用户选择的名称*。 sdb |                                                                                    **位置**：% windir% \* 用户帐户 <em> \Documents\Security\Database</br></em>*创建者* <em> ：运行 "安全配置和分析" 管理单元</br></em>*文件类型* <em> ：专有</br></em>*刷新频率* <em> ：每当创建新安全模板时更新。</br></em>*内容* \* ：本地安全策略和用户创建的安全模板。                                                                                    |
| *用户选择的名称*.log | **位置**：用户定义，但默认为% windir% \* 用户帐户 <em> \Documents\Security\Logs</br></em>*创建者* <em> ：运行 "/analyze" 和 "/configure" 子命令 (或使用 "安全配置和分析" 管理单元) </br></em>*文件类型* <em> ：文本</br></em>*刷新频率* <em> ： (或使用 "安全配置和分析" 管理单元) ，运行 "/analyze" 和 "/configure" 子命令。</br></em>*内容* \* ：</br>1. 日志文件名称</br>2. 日期和时间</br>3. 分析或调查结果。 |
| *用户选择的名称*.inf |                                                                                     **位置**：% windir% \* 用户帐户 <em> \Documents\Security\Templates</br></em>*创建者* <em> ：运行安全模板管理单元</br></em>*文件类型* <em> ：文本</br></em>*刷新频率* <em> ：每次更新安全模板时</br></em>*内容* \* ：包含为使用管理单元选择的每个策略设置的模板信息。                                                                                     |

> [!NOTE]
> Microsoft 管理控制台 (MMC) 并且 "安全配置和分析" 管理单元在 "服务器核心" 上不可用。

## <a name="additional-references"></a>其他参考

有关如何使用此命令的示例，请参阅任何子命令文件中的 "示例" 部分。
- [命令行语法项](command-line-syntax-key.md)