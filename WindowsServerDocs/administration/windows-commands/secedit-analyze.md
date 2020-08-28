---
title: secedit：分析
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 3430cf9d-1411-48b1-b5a9-2e47701dc87f
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b24a2a60163d7a7a368b18119fe2db199525b372
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037465"
---
# <a name="seceditanalyze"></a>secedit：分析



允许你针对存储在数据库中的基线设置分析当前系统设置。

## <a name="syntax"></a>语法

```
Secedit /analyze /db <database file name> [/cfg <configuration file name>] [/overwrite] [/log <log file name>] [/quiet}]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|db|必需。</br>指定数据库的路径和文件名，该数据库包含将对其执行分析的存储配置。</br>如果文件名指定的数据库没有安全模板 (如关联的配置文件) 所表示的，则 `/cfg \<configuration file name>` 还必须指定命令行选项。|
|cfg|可选。</br>指定将导入到数据库中进行分析的安全模板的路径和文件名。</br>此/cfg 选项仅在与参数一起使用时才有效 `/db \<database file name>` 。 如果未指定此项，则对已存储在数据库中的任何配置执行分析。|
|overwrite|可选。</br>指定/cfg 参数中的安全模板是否应覆盖数据库中存储的任何模板或复合模板，而不是将结果追加到存储的模板。</br>此命令行选项仅在使用参数时才有效 `/cfg \<configuration file name>` 。 如果未指定此参数，则将/cfg 参数中的模板追加到存储的模板。|
|log|可选。</br>指定要在进程中使用的日志文件的路径和文件名。|
|quiet|可选。</br>禁止屏幕输出。 你仍可以通过使用 "安全配置和分析" 管理单元 (MMC) 来查看分析结果。|

## <a name="remarks"></a>注解

分析结果存储在数据库的一个独立区域中，可以在 MMC 的 "安全配置和分析" 管理单元中查看。

如果未提供日志文件的路径，则使用默认的日志文件 (*systemroot*\Documents and Settings \* 用户帐户<em>\My Documents\Security\Logs \* DatabaseName</em>) 。

在 Windows Server 2008 中，已 `Secedit /refreshpolicy` 替换为 `gpupdate` 。 有关如何刷新安全设置的信息，请参阅 [Gpupdate](gpupdate.md)。

## <a name="examples"></a>示例

对安全数据库 SecDbContoso （使用 "安全配置和分析" 管理单元创建）的安全参数执行分析。 通过提示将输出定向到文件 SecAnalysisContosoFY11，以便可以验证命令是否正常运行。
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /log C:\Security\FY11\SecAnalysisContosoFY11.log
```
假设分析显示了一些 inadequacies，因此修改了安全模板 SecContoso。 再次运行该命令以合并更改，将输出定向到现有文件 SecAnalysisContosoFY11，而不会出现提示。
```
Secedit /analyze /db C:\Security\FY11\SecDbContoso.sdb /cfg SecContoso.inf /overwrite /log C:\Security\FY11\SecAnalysisContosoFY11.xml /quiet
```

## <a name="additional-references"></a>其他参考

-   [Secedit](secedit.md)
- [命令行语法项](command-line-syntax-key.md)