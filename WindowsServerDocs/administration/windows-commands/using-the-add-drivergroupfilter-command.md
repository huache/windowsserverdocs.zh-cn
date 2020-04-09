---
title: DriverGroupFilter
description: DriverGroupFilter 的 Windows 命令主题，用于向服务器上的驱动程序组添加筛选器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: a66c5e68-99ea-4e47-b68d-8109633ae336
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6a62baf85462d4340d61196bc154efd6d852f1f7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832110"
---
# <a name="add-drivergroupfilter"></a>DriverGroupFilter

向服务器上的驱动程序组添加筛选器。

## <a name="syntax"></a>语法

```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]
```

### <a name="parameters"></a>参数

|         参数          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                            说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /DriverGroup：\<组名称 > |                                                                                                                                                                                                                                                                                                                                                                                                                                                              指定驱动程序组的名称。                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|  [/Server：\<Server name >]  |                                                                                                                                                                                                                                                                                                                                                                                                               指定服务器的名称。 此名称可以是 NetBIOS 名称或 FQDN。 如果未指定服务器名称，则使用本地服务器。                                                                                                                                                                                                                                                                                                                                                                                                               |
| /FilterType：\<FilterType >  |                                                                                                                                                                                                   指定要添加到组的筛选器的类型。 可以在单个命令中指定多个筛选器类型。 每个筛选器类型都必须后跟 **/policy**并包含至少一个 **/Value**。 \<FilterType > 可以是**BiosVendor**、 **BiosVersion**、 **ChassisType**、 **Manufacturer**、 **Uuid**、 **OsVersion**、 **OsEdition**或**OsLanguage**。 有关获取所有其他筛选器类型的值的信息，请参阅[驱动程序组筛选器](https://go.microsoft.com/fwlink/?LinkID=155158)（<https://go.microsoft.com/fwlink/?LinkID=155158>）。                                                                                                                                                                                                    |
|     [/Policy： {Include      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             排除}]                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|     [/Value：\<值 >]      | 指定与 **/FilterType**对应的客户端值。 您可以为单个类型指定多个值。 请参阅以下列表，了解**ChassisType**的有效值。 有关获取所有其他筛选器类型的值的信息，请参阅[驱动程序组筛选器](https://go.microsoft.com/fwlink/?LinkID=155158)（<https://go.microsoft.com/fwlink/?LinkID=155158>）。</br>**以外**</br>**UnknownChassis**</br>**桌面**</br>**LowProfileDesktop**</br>**PizzaBox**</br>**MiniTower**</br>**指**</br>**机型**</br>**膝**</br>**笔记本**</br>**手持式**</br>**DockingStation**</br>**AllInOne**</br>**SubNotebook**</br>**SpaceSaving**</br>**LunchBox**</br>**MainSystemChassis**</br>**ExpansionChassis**</br>**SubChassis**</br>**BusExpansionChassis**</br>**PeripheralChassis**</br>**StorageChassis**</br>**RackMountChassis**</br>**SealedCaseComputer**</br>**MultiSystemChassis**</br>**CompactPci**</br>**AdvancedTca** |

## <a name="examples"></a><a name=BKMK_examples></a>示例

若要向驱动程序组添加筛选器，请键入下列内容之一：
```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /Value:Name2
```
```
WDSUTIL /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /FilterType:ChassisType /Policy:Exclude /Value:Tower /Value:MiniTower
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

