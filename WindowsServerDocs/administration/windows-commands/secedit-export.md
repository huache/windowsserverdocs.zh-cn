---
title: secedit： export
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 49a8b241-aa8c-45b7-844d-67a29fab708e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 04a03dd392fb333bb95bbd73a2694ce6bf548d9c
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037445"
---
# <a name="seceditexport"></a>secedit： export



导出使用安全模板配置的数据库中存储的安全设置。

## <a name="syntax"></a>语法

```
Secedit /export /db <database file name> [/mergedpolicy] /cfg <configuration file name> [/areas [securitypolicy | group_mgmt | user_rights | regkeys | filestore | services]] [/log <log file name>] [/quiet]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|db|必需。</br>指定数据库的路径和文件名，该数据库包含将对其执行分析的存储配置。</br>如果文件名指定的数据库没有安全模板 (如关联的配置文件) 所表示的，则 `/cfg \<configuration file name>` 还必须指定命令行选项。|
|mergedpolicy|可选。</br>合并和导出域和本地策略安全设置。|
|cfg|必需。</br>指定将导入到数据库中进行分析的安全模板的路径和文件名。</br>此/cfg 选项仅在与参数一起使用时才有效 `/db \<database file name>` 。 如果未指定此项，则对已存储在数据库中的任何配置执行分析。|
|区域|可选。</br>指定要应用于系统的安全区域。 如果未指定此参数，则会将数据库中定义的所有安全设置应用到系统。 若要配置多个区域，请用空格分隔每个区域。 支持以下安全区域：</br>-Ws-securitypolicy</br>    系统的本地策略和域策略，包括帐户策略、审核策略、安全选项等。</br>-Group_Mgmt</br>    在安全模板中指定的任何组的限制组设置。</br>-User_Rights</br>    用户登录权限和授予权限。</br>- RegKeys</br>    本地注册表项的安全性。</br>-%</br>    本地文件存储的安全性。</br>-服务</br>    所有已定义服务的安全性。|
|log|可选。</br>指定进程的日志文件的路径和文件名。|
|quiet|可选。</br>禁止显示屏幕和日志输出。 你仍可以通过使用 "安全配置和分析" 管理单元 (MMC) 来查看分析结果。|

## <a name="remarks"></a>注解

除了将设置导入另一台计算机之外，还可以使用此命令在本地计算机上备份安全策略。

如果未提供日志文件的路径，则使用默认的日志文件 (*systemroot*\Documents and Settings \* 用户帐户<em>\My Documents\Security\Logs \* DatabaseName</em>) 。

在 Windows Server 2008 中，已 `Secedit /refreshpolicy` 替换为 `gpupdate` 。 有关如何刷新安全设置的信息，请参阅 [Gpupdate](gpupdate.md)。

## <a name="examples"></a>示例

将安全数据库和域安全策略导出到一个 inf 文件，然后将该文件导入到另一个数据库，以便在另一台计算机上复制安全策略设置。
```
Secedit /export /db C:\Security\FY11\SecDbContoso.sdb /mergedpolicy /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY11.log /quiet
```
将该文件导入另一台计算机上的其他数据库。
```
Secedit /import /db C:\Security\FY12\SecDbContoso.sdb /cfg SecContoso.inf /log C:\Security\FY11\SecAnalysisContosoFY12.log /quiet
```

## <a name="additional-references"></a>其他参考

-   [Secedit:import](secedit-import.md)
-   [Secedit](secedit.md)
- [命令行语法项](command-line-syntax-key.md)