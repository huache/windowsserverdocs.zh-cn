---
title: Sc create
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 59416460-0661-4fef-85cc-73e9d8f4beb4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c1596d3f58fd235039585283a7a6360d85201d7a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80835390"
---
# <a name="sc-create"></a>Sc create



为注册表中的服务和服务控制管理器数据库创建子项和项。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
sc [<ServerName>] create [<ServiceName>] [type= {own | share | kernel | filesys | rec | interact type= {own | share}}] [start= {boot | system | auto | demand | disabled | delayed-auto }] [error= {normal | severe | critical | ignore}] [binpath= <BinaryPathName>] [group= <LoadOrderGroup>] [tag= {yes | no}] [depend= <dependencies>] [obj= {<AccountName> | <ObjectName>}] [displayname= <DisplayName>] [password= <Password>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ServerName >|指定服务所在的远程服务器的名称。 名称必须使用通用命名约定（UNC）格式（例如 \\\\myserver）。 若要在本地运行 SC.EXE，请省略此参数。|
|\<ServiceName >|指定**getkeyname**操作返回的服务名称。|
|type = {自有 \| share \| 内核 \| filesys \| rec \| 交互类型 = {拥有 \| 共享}}|指定服务类型。 默认设置为 "**类型 = 拥有**"。</br>**拥有**-指定服务在其自己的进程中运行。 它不与其他服务共享可执行文件。 这是默认设置。</br>**共享**-指定服务以共享进程的形式运行。 它与其他服务共享可执行文件。</br>**内核**-指定驱动程序。</br>**filesys** -指定文件系统驱动程序。</br>**rec** -指定文件系统识别的驱动程序（标识计算机上使用的文件系统）。</br>**交互**-指定服务可与桌面交互，同时接收来自用户的输入。 交互式服务必须在 LocalSystem 帐户下运行。 此类型必须与**类型 = "拥有**" 或 "**类型" 为 "共享**" 结合使用。 使用**type = 自行交互**将生成无效的参数错误。|
|开始 = {启动 \| 系统 \| 自动 \| 需求 \| 禁用 \|-自动}|指定服务的启动类型。 默认设置为 "**开始 = 请求**"。</br>**启动**-指定由启动加载程序加载的设备驱动程序。</br>**系统**-指定在内核初始化过程中启动的设备驱动程序。</br>**自动**指定在每次重新启动计算机时自动启动的服务。 请注意，即使没有人登录到计算机，也会运行该服务。</br>**demand** -指定必须手动启动的服务。 如果未指定**start =** ，则此值为默认值。</br>**disabled** -指定无法启动的服务。 若要启动已禁用的服务，请将启动类型更改为其他某个值。</br>**延迟-自动**指定一项服务，该服务将在启动其他自动服务之后的短时间自动启动。|
|错误 = {正常 \| 严重 \| 严重 \| 忽略}|如果在计算机启动时服务失败，则指定错误的严重性。 默认设置为**error = normal**。</br>**normal** -指定记录错误。 将显示一个消息框，通知用户服务无法启动。 启动将继续。 这是默认设置。</br>**严重**-指定记录错误（如果可能）。 计算机尝试用最后一次正确的配置重新启动。 这可能会导致计算机能够重启，但仍可能无法运行该服务。</br>**严重**-指定记录错误（如果可能）。 计算机尝试用最后一次正确的配置重新启动。 如果最后一次已知的正确配置失败，则启动也会失败，并且启动过程将停止并出现停止错误。</br>**ignore** -指定已记录错误并继续启动。 超出事件日志中记录错误的用户不会提供通知。|
|binpath = \<BinaryPathName >|指定服务二进制文件的路径。 **Binpath =** 没有默认值，必须提供此字符串。|
|group = \<LoadOrderGroup >|指定此服务所属的组的名称。 组列表存储在注册表的**HKLM\System\CurrentControlSet\Control\ServiceGroupOrder**子项中。 默认值为 null。|
|标记 = {yes \| no}|指定是否要从 CreateService 调用中获取 TagID。 标记仅用于启动和系统启动驱动程序。|
|依赖关系 = \<依赖关系 >|指定启动此服务之前必须启动的服务或组的名称。 名称由正斜杠（/）分隔。|
|obj = {\<AccountName > \| \<ObjectName >}|指定服务将在其中运行的帐户的名称，或指定将在其中运行该驱动程序的 Windows 驱动程序对象的名称。|
|displayname = \<DisplayName >|指定可由用户界面程序用来标识服务的友好名称。|
|password = \<密码 >|指定密码。 如果使用除 LocalSystem 以外的帐户，则这是必需的。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   对于每个命令行选项，等号都是选项名称的一部分。
-   选项和其值之间需要空格（例如， **type =** an）。 如果省略此空间，则操作将失败。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例演示如何使用**sc create**命令：
```
sc \\myserver create NewService binpath= c:\windows\system32\NewServ.exe
sc create NewService binpath= c:\windows\system32\NewServ.exe type= share start= auto depend= +TDI NetBIOS
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
