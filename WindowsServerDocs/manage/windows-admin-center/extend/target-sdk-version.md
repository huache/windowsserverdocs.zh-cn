---
title: 面向不同版本的 Windows 管理中心 SDK
description: '针对不同版本的 Windows 管理中心 SDK (Project Honolulu) '
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 96e17326bc289b4ad018da59b01344956586a198
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87964553"
---
# <a name="target-a-different-version-of-the-windows-admin-center-sdk"></a>面向不同版本的 Windows 管理中心 SDK

>适用于：Windows Admin Center、Windows Admin Center 预览版

通过 SDK 更改和平台更改，使扩展保持最新状态非常简单。  我们使用[NPM 标记](https://www.npmjs.com/package/@microsoft/windows-admin-center-sdk)将新功能的发布组织到 SDK 版本中。

有三个可供选择的 SDK 版本：

* ```latest```–此 SDK 包与当前的 Windows 管理中心版本
* ```insider```–此 SDK 包与当前在 Windows Server 有问必答 Preview 中提供的 Windows 管理中心 (预览版本一致) 
* ```next```–此 SDK 包包含最新功能

> [!NOTE]
> 详细了解可供下载的 Windows 管理中心的不同[版本](https://aka.ms/WACDownloadPage)。

## <a name="targeting-sdk-version-on-a-new-project"></a>面向新项目的 SDK 版本

创建新扩展时，可以包括 ```--version``` 参数以面向不同版本的 SDK：

```
wac create --company "{!Company Name}" --tool "{!Tool Name}" --version {!version}
```

| 值 | 说明 | 示例 |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | 你的公司名称 (带有空格)  | ```Contoso Inc``` |
| ```{!Tool Name}``` | 你的工具名称 (带有空格)  | ```Manage Foo Works``` |
| ```{!version}``` | SDK 版本 | ```latest``` |

下面是一个创建新扩展目标的示例 ```insider``` ：

```
wac create --company "Contoso Inc" --tool "Manage Foo Works" --version insider
```

## <a name="targeting-sdk-version-on-an-existing-project"></a>针对现有项目的 SDK 版本

若要修改现有项目以使其面向不同的 SDK 版本，请在中修改以下行 ```package.json``` ：

```
"@microsoft/windows-admin-center-sdk": "latest",
```
在此示例中，请 ```latest``` 将替换为所需的 SDK 版本，即 ```insider``` ：

```
"@microsoft/windows-admin-center-sdk": "insider",
```

然后运行 ```npm install``` 以更新整个项目中的引用。