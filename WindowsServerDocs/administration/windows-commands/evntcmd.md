---
title: evntcmd
description: Evntcmd 命令的参考文章，它基于配置文件中的信息配置将事件转换为陷阱、陷阱目标或两者。
ms.topic: reference
ms.assetid: c1aabb74-76e7-4304-95a6-50ad87e92fd9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 173cb9c2f1528748986daf753a9d213c5060e5d4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035865"
---
# <a name="evntcmd"></a>evntcmd

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

基于配置文件中的信息，配置将事件转换为陷阱、陷阱目标或两者。

## <a name="syntax"></a>语法

```
evntcmd [/s <computername>] [/v <verbositylevel>] [/n] <filename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /s `<computername>` | 按名称指定要在其上配置事件转换的计算机和/或陷阱目标的计算机。 如果未指定计算机，则会在本地计算机上进行配置。 |
| /v `<verbositylevel>` | 指定哪些类型的状态消息会显示为陷阱，并配置陷阱目标。 此参数必须是一个介于0到10之间的整数。 如果指定10，则显示所有类型的消息，包括有关陷阱配置是否成功的跟踪消息和警告。 如果指定0，则不会显示任何消息。 |
| /n | 指定如果此计算机接收陷阱配置更改，则不应重新启动 SNMP 服务。 |
| `<filename>` | 按名称指定配置文件，该配置文件包含有关将事件转换为要配置的陷阱和陷阱目标的信息。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 如果要配置陷阱，而不是陷阱目标，则可以通过使用事件到陷阱转换器（一种图形实用程序）来创建有效的配置文件。 如果安装了 SNMP 服务，可以通过在命令提示符处键入 **evntwin** ，开始使用陷阱转换器事件。 定义所需的陷阱后，请单击 " **导出** " 以创建适用于 **evntcmd**的文件。 可以使用事件陷阱转换器轻松创建配置文件，然后在命令提示符下使用带有 **evntcmd** 的配置文件，在多台计算机上快速配置陷阱。

- 用于配置陷阱的语法如下所示：

  ```
  #pragma add <eventlogfile> <eventsource> <eventID> [<count> [<period>]]
  ```

  以下文本为 true：

    - **#pragma** 必须出现在文件中每个条目的开头。

    - " **添加** 参数" 指定要将事件添加到陷阱配置。

    - 参数 **eventlogfile**、 **eventsource**和 **eventID** 是必需的，其中 **eventlogfile** 指定记录事件的文件， **eventsource** 指定生成事件的应用程序， **eventID** 指定标识每个事件的唯一编号。

    若要确定与每个事件对应的值，请通过在命令提示符下键入 **evntwin** ，启动捕获转换器的事件。 单击 " **自定义**"，然后单击 " **编辑**"。 在 " **事件源**" 下浏览文件夹，直到找到要配置的事件，单击该事件，然后单击 " **添加**"。 有关事件源、事件日志文件和事件 ID 的信息分别显示在 " **源"、"日志**" 和 " **陷阱" 特定 id**下。

    - **Count**参数是可选的，它指定在发送陷阱消息之前事件必须发生的次数。 如果不使用此参数，则在事件发生一次后发送陷阱消息。

    - **Period**参数是可选的，但要求使用**count**参数。 **Period**参数指定 (的时间长度（以秒为单位）) 事件必须在发送陷阱消息之前，在该时间段内发生的次数与**count**参数一起指定。 如果不使用此参数，则在事件发生后，无论发生多少 ***次，都*** 将在事件发生后发送陷阱消息。

- 删除陷阱的语法如下所示：

  ```
  #pragma delete <eventlogfile> <eventsource> <eventID>
  ```

  以下文本为 true：

    - **#pragma** 必须出现在文件中每个条目的开头。

    - 参数 **delete** 指定要删除陷阱配置事件。

    - 参数 **eventlogfile**、 **eventsource**和 **eventID** 是必需的，其中 **eventlogfile** 指定记录事件的文件， **eventsource** 指定生成事件的应用程序， **eventID** 指定标识每个事件的唯一编号。

    若要确定与每个事件对应的值，请通过在命令提示符下键入 **evntwin** ，启动捕获转换器的事件。 单击 " **自定义**"，然后单击 " **编辑**"。 在 " **事件源**" 下浏览文件夹，直到找到要配置的事件，单击该事件，然后单击 " **添加**"。 有关事件源、事件日志文件和事件 ID 的信息分别显示在 " **源"、"日志**" 和 " **陷阱" 特定 id**下。

- 用于配置陷阱目标的语法如下所示：

  ```
  #pragma add_TRAP_DEST <communityname> <hostID>
  ```

  以下文本为 true：

    - **#pragma** 必须出现在文件中每个条目的开头。

    - 参数 **add_TRAP_DEST** 指定要将陷阱消息发送到社区中的指定主机。

    - 参数 **communityname** 按名称指定发送陷阱消息的团体。

    - 参数 **id** 按名称或 IP 地址指定要向其发送陷阱消息的主机。

- 删除陷阱目标的语法如下所示：

  ```
  #pragma delete_TRAP_DEST <communityname> <hostID>
  ```

  以下文本为 true：

    - **#pragma** 必须出现在文件中每个条目的开头。

    - 参数 **delete_TRAP_DEST** 指定你不希望将陷阱消息发送到社区中的指定主机。

    - 参数 **communityname** 按名称指定陷阱消息不应发送到的团体。

    - 参数 **id** 按名称或 IP 地址指定不想向其发送陷阱消息的主机。

### <a name="examples"></a>示例

下面的示例说明了 **evntcmd** 命令的配置文件中的条目。 它们的设计目的不是在命令提示符下键入。

若要在事件日志服务重新启动时发送陷阱消息，请键入：

```
#pragma add System Eventlog 2147489653
```

若要在三分钟内重启事件日志服务两次，请键入：

```
#pragma add System Eventlog 2147489653 2 180
```

若要在事件日志服务重新启动时停止发送陷阱消息，请键入：

```
#pragma delete System Eventlog 2147489653
```

若要将名为 " *公共* " 的社区中的陷阱消息发送到 IP 地址为 *192.168.100.100*的主机，请键入：

```
#pragma add_TRAP_DEST public 192.168.100.100
```

若要将名为 *Private* 的社区中的陷阱消息发送到名为 *Host1*的主机，请键入：

```
#pragma add_TRAP_DEST private Host1
```

若要停止将名为 *Private* 的社区中的陷阱消息发送到要配置陷阱目标的同一台计算机，请键入：

```
#pragma delete_TRAP_DEST private localhost
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
