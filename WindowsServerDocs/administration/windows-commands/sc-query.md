---
title: Sc.exe 查询
description: 了解如何使用 sc.exe 实用程序获取有关服务、驱动程序、服务类型或驱动程序类型的信息
ms.topic: reference
ms.assetid: ac365f89-4b20-4de6-a582-b204c5e7d0eb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e961badf867237c0725441e138bf4f0ea948155f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637044"
---
# <a name="scexe-query"></a>Sc.exe 查询

获取并显示有关指定服务、驱动程序、服务类型或驱动程序类型的信息。

## <a name="syntax"></a>语法

```
sc.exe [<ServerName>] query [<ServiceName>] [type= {driver | service | all}] [type= {own | share | interact | kernel | filesys | rec | adapt}] [state= {active | inactive | all}] [bufsize= <BufferSize>] [ri= <ResumeIndex>] [group= <GroupName>]
```

### <a name="parameters"></a>参数

|       参数        |                                                                                                                          说明                                                                                                                          |
|------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     \<ServerName>      |                       指定服务所在的远程服务器的名称。 名称必须使用通用命名约定 (UNC) 格式 (例如， \\ \\ myserver) 。 若要在本地运行 SC.exe，请省略此参数。                        |
|     \<ServiceName>     |                                      指定 **getkeyname** 操作返回的服务名称。 此**查询**参数不与*ServerName*) 以外 (其他**查询**参数一起使用。                                      |
|     type = {driver      |                                                                                                                            服务                                                                                                                            |
|       type = {自有       |                                                                                                                             共享                                                                                                                             |
|     state = {active     |                                                                                                                           非活跃                                                                                                                            |
| bufsize = \<BufferSize> |                     指定枚举缓冲区) 大小 (（以字节为单位）。 默认缓冲区大小为1024个字节。 当查询生成的显示超过1024个字节时，应增加枚举缓冲区的大小。                      |
|   ri = \<ResumeIndex>   | 指定枚举开始或恢复的索引号。 默认值为 **0** (零) 。 当查询返回的详细信息超过默认缓冲区可显示的信息时，请将此参数与 **bufsize =** 参数一起使用。 |
|  组 = \<GroupName>   |                                                                             指定要枚举的服务组。 默认情况下，将 ( * * group = * * ) 枚举所有组。                                                                              |
|           /?           |                                                                                                             在命令提示符下显示帮助。                                                                                                              |

## <a name="remarks"></a>备注

- 如果参数与其值之间没有空格 (即， **type = 自有**，not **type =**) ，则操作将失败。
- **查询**操作显示有关服务的下列信息： SERVICE_NAME (服务的注册表子项名称) 、类型、状态 (以及不可用) 、WIN32_EXIT_B、SERVICE_EXIT_B、检查点和 WAIT_HINT 的状态。
- 在某些情况下， **type =** 参数可以使用两次。 **Type =** 参数的第一种外观指定是否查询服务、驱动程序，或者两者都** (都**) 。 **Type =** 参数的第二个外观从**create**操作指定一个类型，以进一步缩小查询范围。
- 当 **查询** 命令所产生的显示超出枚举缓冲区的大小时，将显示一条类似于以下内容的消息：
  ```
  Enum: more data, need 1822 bytes start resume at index 79
  ```
  若要显示剩余的 **查询** 信息，请重新运行 **查询**，将 **bufsize =** 设置为字节数，并将 **ri =** 设置为指定索引。 例如，在命令提示符下键入以下内容，将显示剩余的输出：
  ```
  sc.exe query bufsize= 1822 ri= 79
  ```

## <a name="examples"></a>示例

若要仅显示活动服务的信息，请键入以下命令之一：
```
sc.exe query
sc.exe query type= service
```
若要显示活动服务的信息，并指定缓冲区大小（2000字节），请键入：
```
sc.exe query type= all bufsize= 2000
```
若要显示 WUAUSERV 服务的信息，请键入：
```
sc.exe query wuauserv
```
若要显示所有服务 (活动和非活动) 的信息，请键入：
```
sc.exe query state= all
```
若要显示所有服务的信息 (活动和非活动) ，从第56行开始，键入：
```
sc.exe query state= all ri= 56
```
若要显示交互式服务的信息，请键入：
```
sc.exe query type= service type= interact
```
若要仅显示驱动程序的信息，请键入：
```
sc.exe query type= driver
```
若要在网络驱动程序接口规范 (NDIS) 组中显示驱动程序的信息，请键入：
```
sc.exe query type= driver group= ndis
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
