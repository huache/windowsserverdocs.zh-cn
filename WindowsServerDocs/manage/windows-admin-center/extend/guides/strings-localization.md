---
title: Windows 管理中心中的字符串和本地化
description: '了解如何在 Windows 管理中心 SDK 中准备好用于本地化的字符串 (项目 Honolulu) '
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 06/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 565e4da69466549538c380457269304c7f1cdd5a
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87944917"
---
# <a name="strings-and-localization-in-windows-admin-center"></a>Windows 管理中心中的字符串和本地化 #

>适用于：Windows Admin Center、Windows Admin Center 预览版

让我们更深入地了解 Windows 管理中心扩展 SDK，并讨论字符串和本地化。

若要对呈现层上呈现的所有字符串启用本地化，请利用/src/resources/strings 下的 resjson 文件-它已设置好。 如果需要将新字符串添加到扩展，请将其作为新条目添加到此 resjson 文件。 现有结构的格式如下所示：

``` ts
"<YourExtensionName>_<Component>_<Accessor>": "Your string value goes here.",
```

你可以使用你喜欢的任意格式作为字符串，但请注意，生成过程 (采用 resjson 的进程，并输出可用的 TypeScript 类) 将下划线 (_) 转换为 ( ) 。

例如，以下条目：
``` ts
"HelloWorld_cim_title": "CIM Component",
```
生成以下访问器结构：
``` ts
MsftSme.resourcesStrings<Strings>().HelloWorld.cim.title;
```

## <a name="add-other-languages-for-localization"></a>添加其他本地化语言 ##

对于其他语言的本地化，需要为每种语言创建 resjson 文件。 需要将这些文件放在中 ```\loc\output\{!ExtensionName}\{!LanguageFolder}\strings.resjson``` 。 具有相应文件夹的可用语言包括：

| 语言      | 文件夹      |
| ------------- |-------------|
| Čeština | cs-CZ |
| Deutsch | de-DE |
| 英语 | en-US |
| Español | es-ES |
| Français | fr-FR |
| Magyar | hu-HU |
| Italiano | it-IT |
| 日本語 | ja-JP |
| 한국어 | ko-KR |
| Nederlands | nl-NL |
| Polski | pl-PL |
| Português (Brasil) | pt-BR |
| Português (Portugal) | pt-PT |
| Русский | ru-RU |
| Svenska | sv-SE |
| Türkçe    | tr-TR |
| 中文 (简体)  | zh-CN |
| 中文 (繁體)  | zh-TW |
> [!NOTE]
> 如果文件结构需要在 "位置"/"输出" 内有所不同，则需要调整 gulpfile.js 中 gulp 任务 "" 的 localeOffset。 此偏移量是位置文件夹中应开始搜索 resjson 文件的深度。

每个 resjson 文件的格式设置方式与本指南顶部提及的格式相同。

例如，若要包括西班牙语的本地化，请在中包含此项 ```\loc\output\HelloWorld\es-ES\strings.resjson``` ：
```json
"HelloWorld_cim_title": "CIM Componente",
```
无论何时添加本地化字符串，都必须重新运行 gulp 才能使其显示。 运行：
``` cmd
gulp generate
```

若要确认已生成字符串，请导航到 ```\src\app\assets\strings\{!LanguageFolder}\strings.resjson``` 。 新添加的条目将显示在此文件中。
现在，如果切换 Windows 管理中心中的 "语言" 选项，则可以在扩展中看到本地化的字符串。
