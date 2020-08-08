---
title: 控制工具在解决方案中的可见性
description: '控制工具在解决方案中的可见性 Windows 管理中心 SDK (Project Honolulu) '
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: df939bb1a87c9ded77431661dcabd7faf607bb6e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87945000"
---
# <a name="control-your-tools-visibility-in-a-solution"></a>控制工具在解决方案中的可见性 #

>适用于：Windows Admin Center、Windows Admin Center 预览版

有时，你可能想要从 "可用工具" 列表中排除 (或隐藏) 你的扩展或工具。 例如，如果你的工具仅面向 Windows Server 2016 (不是旧版本) ，你可能不希望连接到 Windows Server 2012 R2 服务器的用户完全查看你的工具。  (假设用户体验-他们单击该体验，等待该工具加载，只会获得一条消息，指出其功能无法用于其连接。 ) 可以定义 (或隐藏在该工具的 manifest.js文件中) 功能的时间。

## <a name="options-for-deciding-when-to-show-a-tool"></a>用于决定何时显示工具的选项 ##

您可以使用三个不同的选项来确定是否应显示工具并使其可用于特定服务器或群集连接。

* localhost
* 清单 (属性的数组) 
* 脚本

### <a name="localhost"></a>主机 ###

条件对象的 localHost 属性包含一个布尔值，可对其进行评估，以推断连接节点是否是 localHost (在) 上安装了 Windows 管理中心的同一计算机上。 通过向属性传递一个值，可指示 (条件) 显示该工具的时间。 例如，如果你只希望在用户实际上连接到本地主机时显示该工具，请按如下所示进行设置：

``` json
"conditions": [
{
    "localhost": true
}]
```

或者，如果只希望在连接节点*不是*localhost 时显示工具：

``` json
"conditions": [
{
    "localhost": false
}]
```

下面是配置设置的外观，只是在连接节点不是 localhost 时显示工具：

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!windowsClients"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.windows-client"
        ],
        "conditions": [
        {
            "localhost": true
        }
        ]
    }
    ]
}
```

### <a name="inventory-properties"></a>清单属性 ###

SDK 包括一组预特选的清单属性，您可以使用这些属性来构建条件，确定何时可以使用您的工具。 "清单" 数组中有九个不同的属性：

| 属性名称 | 预期值类型 |
| ------------- | ------------------- |
| computerManufacturer | 字符串 |
| operatingSystemSKU | number |
| operatingSystemVersion | version_string (例如： "10.1. *" )  |
| productType | number |
| clusterFqdn | 字符串 |
| isHyperVRoleInstalled | boolean |
| isHyperVPowershellInstalled | boolean |
| isManagementToolsAvailable | boolean |
| isWmfInstalled | boolean |

清单数组中的每个对象都必须符合以下 json 结构：

``` json
"<property name>": {
    "type": "<expected type>",
    "operator": "<defined operator to use>",
    "value": "<expected value to evaluate using the operator>"
}
```

#### <a name="operator-values"></a>运算符值 ####

| 运算符 | 描述 |
| -------- | ----------- |
| gt | 大于 |
| ge | 大于等于 |
| lt | 小于 |
| le | 小于等于 |
| eq | 等于 |
| ne | 不等于 |
| is | 检查值是否为 true |
| not | 检查值是否为 false |
| contains | 字符串中存在项 |
| notContains | 字符串中不存在项 |

#### <a name="data-types"></a>数据类型 ####

"Type" 属性的可用选项：

| 类型 | 说明 |
| ---- | ----------- |
| 版本 | 版本号 (例如： 10.1. * )  |
| number | 一个数值 |
| 字符串 | 一个字符串值 |
| boolean | true 或 false |

#### <a name="value-types"></a>值类型 ####

"Value" 属性接受以下类型：

* 字符串
* 数字
* boolean

正确格式的清单条件集如下所示：

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!servers"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.server"
        ],
        "conditions": [
        {
            "inventory": {
            "operatingSystemVersion": {
                "type": "version",
                "operator": "gt",
                "value": "6.3"
            },
            "operatingSystemSKU": {
                "type": "number",
                "operator": "eq",
                "value": "8"
            }
            }
        }
        ]
    }
    ]
}
```

### <a name="script"></a>脚本 ###

最后，你可以运行自定义 PowerShell 脚本来确定节点的可用性和状态。 所有脚本都必须返回具有以下结构的对象：

``` ps
@{
    State = 'Available' | 'NotSupported' | 'NotConfigured';
    Message = '<Message to explain the reason of state such as not supported and not configured.>';
    Properties =
        @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' },
        @{Name='Prop2'; Value = 12345678; Type='number'; };
}
```
"状态" 属性是一个重要值，用于控制在 "工具" 列表中显示或隐藏扩展的决定。  允许的值为：

| “值” | 描述 |
| ---- | ----------- |
| 可用 | 该扩展应显示在 "工具" 列表中。 |
| NotSupported | 不应在 "工具" 列表中显示该扩展。 |
| NotConfigured | 这是未来工作的占位符值，将在工具可用之前提示用户进行其他配置。  当前此值将导致工具显示，并且其功能等效于 "可用"。 |

例如，如果我们希望仅在远程服务器安装了 BitLocker 的情况下加载工具，该脚本将如下所示：

``` ps
$response = @{
    State = 'NotSupported';
    Message = 'Not executed';
    Properties = @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' },
        @{Name='Prop2'; Value = 12345678; Type='number'; };
}

if (Get-Module -ListAvailable -Name servermanager) {
    Import-module servermanager;
    $isInstalled = (Get-WindowsFeature -name bitlocker).Installed;
    $isGood = $isInstalled;
}

if($isGood) {
    $response.State = 'Available';
    $response.Message = 'Everything should work.';
}

$response
```

使用脚本选项的入口点配置如下所示：

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
        "msft.sme.server-manager!windowsClients"
        ],
        "connectionTypes": [
        "msft.sme.connection-type.windows-client"
        ],
        "conditions": [
        {
            "localhost": true,
            "inventory": {
            "operatingSystemVersion": {
                "type": "version",
                "operator": "eq",
                "value": "10.0.*"
            },
            "operatingSystemSKU": {
                "type": "number",
                "operator": "eq",
                "value": "4"
            }
            },
            "script": "$response = @{ State = 'NotSupported'; Message = 'Not executed'; Properties = @{ Name = 'Prop1'; Value = 'prop1 data'; Type = 'string' }, @{Name='Prop2'; Value = 12345678; Type='number'; }; }; if (Get-Module -ListAvailable -Name servermanager) { Import-module servermanager; $isInstalled = (Get-WindowsFeature -name bitlocker).Installed; $isGood = $isInstalled; }; if($isGood) { $response.State = 'Available'; $response.Message = 'Everything should work.'; }; $response"
        }
        ]
    }
    ]
}
```

## <a name="supporting-multiple-requirement-sets"></a>支持多个需求集 ##

通过定义多个 "要求" 块，你可以使用多组要求来确定何时显示你的工具。

例如，若要在 "方案 A" 或 "方案 B" 为 true 时显示你的工具，请定义两个要求块;如果任一条件为 true (即满足要求块中的所有条件) ，则会显示该工具。

``` json
"entryPoints": [
{
    "requirements": [
    {
        "solutionIds": [
            …"scenario A"…
        ],
        "connectionTypes": [
            …"scenario A"…
        ],
        "conditions": [
            …"scenario A"…
        ]
    },
    {
        "solutionIds": [
            …"scenario B"…
        ],
        "connectionTypes": [
            …"scenario B"…
        ],
        "conditions": [
            …"scenario B"…
        ]
    }
    ]
}

```

## <a name="supporting-condition-ranges"></a>支持条件范围 ##

还可以通过使用相同的属性定义多个 "条件" 块，但使用不同的运算符来定义条件范围。

如果用不同的运算符定义了同一个属性，则只要这两个条件之间的值，就会显示该工具。

例如，只要操作系统是6.3.0 和10.0.0 之间的版本，就会显示此工具：

``` json
"entryPoints": [
{
    "entryPointType": "tool",
    "name": "main",
    "urlName": "processes",
    "displayName": "resources:strings:displayName",
    "description": "resources:strings:description",
    "icon": "sme-icon:icon-win-serverProcesses",
    "path": "",
    "requirements": [
    {
        "solutionIds": [
             "msft.sme.server-manager!servers"
        ],
        "connectionTypes": [
             "msft.sme.connection-type.server"
        ],
        "conditions": [
        {
            "inventory": {
                "operatingSystemVersion": {
                    "type": "version",
                    "operator": "gt",
                    "value": "6.3.0"
                },
            }
        },
        {
            "inventory": {
                "operatingSystemVersion": {
                    "type": "version",
                    "operator": "lt",
                    "value": "10.0.0"
                }
            }
        }
        ]
    }
    ]
}

```
