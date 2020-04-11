---
title: 适用于移动宽带网络的 Netsh 命令 (MBN)
description: 使用 netsh mbn 查询和配置移动宽带设置与参数。
ms.prod: windows-server
ms.technology: networking
ms.topic: article
author: apdutta
ms.date: 02/20/2020
ms.openlocfilehash: 478f87db4d520a133b3d70c0ed2dbb4e91db60d9
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80853730"
---
# <a name="netsh-mbn-commands"></a>Netsh mbn 命令


使用 **netsh mbn** 查询和配置移动宽带设置与参数。

> [!TIP]
> 可以使用以下命令获取有关 netsh mbn 命令的帮助 
>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;netsh mbn /?

可用的 netsh mbn 命令为：

- [add](#add)
- [connect](#connect)
- [delete](#delete)
- [disconnect](#disconnect)
- [diagnose](#diagnose)
- [dump](#dump)
- [help](#help)
- [set](#set)
- [show](#show)

## <a name="add"></a>添加

将配置项添加到表中。

可用的 netsh mbn add 命令为：

- [dmprofile](#dmprofile)
- [profile](#profile)

### <a name="dmprofile"></a>dmprofile

在配置文件数据存储中添加 DM Config 配置文件。

**语法**

```powershell
add dmprofile [interface=]<string> [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 配置文件 XML 文件的名称。 它是包含配置文件数据的 XML 文件的名称。     | 必需 |


**示例**

```powershell
add dmprofile interface="Cellular" name="Profile1.xml"
```


### <a name="profile"></a>profile

在配置文件数据存储中添加网络配置文件。

**语法**

```powershell
add profile [interface=]<string> [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 配置文件 XML 文件的名称。 它是包含配置文件数据的 XML 文件的名称。     | 必需 |


**示例**

```powershell
add profile interface="Cellular" name="Profile1.xml"
```


## <a name="connect"></a>connect

连接到移动宽带网络。

**语法**

```powershell
connect [interface=]<string> [connmode=]tmp|name [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **connmode**  | 指定如何提供连接参数。 可以使用某个配置文件 XML，或者使用以前通过“netsh mbn add profile”命令存储在移动宽带配置文件数据存储中的配置文件 XML 的配置文件名称，来请求连接。 对于前一种情况，参数 connmode 应保留“tmp”作为值。 而对于后一种情况，值应为“name”                                       | 必需 |
| **name**      | 配置文件 XML 文件的名称。 它是包含配置文件数据的 XML 文件的名称。     | 必需 |


**示例**

```powershell
connect interface="Cellular" connmode=tmp name=d:\profile.xml
connect interface="Cellular" connmode=name name=MyProfileName
```


## <a name="delete"></a>“删除”

从表中删除配置项。

可用的 netsh mbn delete 命令为：

- [dmprofile](#dmprofile)
- [profile](#profile)

### <a name="dmprofile"></a>dmprofile

从配置文件数据存储中删除 DM Config 配置文件。

**语法**

```powershell
delete dmprofile [interface=]<string> [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 配置文件 XML 文件的名称。 它是包含配置文件数据的 XML 文件的名称。     | 必需 |

**示例**

```powershell
delete dmprofile interface="Cellular" name="myProfileName"
```

### <a name="profile"></a>profile

从配置文件数据存储中删除网络配置文件。

**语法**

```powershell
delete profile [interface=]<string> [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 配置文件 XML 文件的名称。 它是包含配置文件数据的 XML 文件的名称。     | 必需 |


**示例**

```powershell
delete profile interface="Cellular" name="myProfileName"
```

## <a name="diagnose"></a>diagnose

针对基本手机网络问题运行诊断。

**语法**

```powershell
diagnose [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
diagnose interface="Cellular"
```


## <a name="disconnect"></a>断开连接

从移动宽带网络断开连接。

**语法**

```powershell
disconnect [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
disconnect interface="Cellular"
```


## <a name="dump"></a>dump

显示配置脚本。 

创建包含当前配置的脚本。  如果将此脚本保存到某个文件，则可以使用此脚本来还原已更改的配置设置。

**语法**

```powershell
dump
```

## <a name="help"></a>help

显示命令列表。

**语法**

```powershell
help
```

## <a name="set"></a>设置

设置配置信息。

可用的 netsh mbn set 命令为：

- [acstate](#acstate)
- [dataenablement](#dataenablement)
- [dataroamcontrol](#dataroamcontrol)
- [enterpriseapnparams](#enterpriseapnparams)
- [highestconncategory](#highestconncategory)
- [powerstate](#powerstate)
- [profileparameter](#profileparameter)
- [slotmapping](#slotmapping)
- [tracing](#tracing)

### <a name="acstate"></a>acstate

设置给定接口的移动宽带数据自动连接状态。

**语法**

```powershell
set acstate [interface=]<string> [state=]autooff|autoon|manualoff|manualon
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 要设置的自动连接状态。 以下值之一：<br>autooff：自动连接标记关闭。<br>autoon：自动连接标记打开。<br>manualoff：手动连接标记关闭。<br>manualon：手动连接标记打开。 | 必需 |


**示例**

```powershell
set acstate interface="Cellular" state=autoon
```


### <a name="dataenablement"></a>dataenablement

对给定的配置文件集和接口打开或关闭移动宽带数据。

**语法**

```powershell
set dataenablement [interface=]<string> [profileset=]internet|mms|all [mode=]yes|no
```

**Parameters**

|                |                                                                                               |          |
|----------------|-----------------------------------------------------------------------------------------------|----------|
| **interface**  | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **profileset** | 配置文件集的名称。                                                                      | 必需 |
| **mode**       | 以下值之一：<br>yes：启用目标配置文件集。<br>no：禁用目标配置文件集。| 必需 |


**示例**

```powershell
set dataenablement interface="Cellular" profileset=mms mode=yes
```


### <a name="dataroamcontrol"></a>dataroamcontrol

设置给定配置文件集和接口的移动宽带数据漫游控制状态。

**语法**

```powershell
set dataroamcontrol [interface=]<string> [profileset=]internet|mms|all [state=]none|partner|all
```

**Parameters**

|                |                                                                                               |          |
|----------------|-----------------------------------------------------------------------------------------------|----------|
| **interface**  | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **profileset** | 配置文件集的名称。                                                                      | 必需 |
| **mode**       | 以下值之一：<br>none：仅限本地运营商。<br>partner：仅限本地运营商与合作伙伴运营商。<br>all：本地、合作伙伴与漫游运营商。| 必需 |


**示例**

```powershell
set dataroamcontrol interface="Cellular" profileset=mms mode=partner
```


### <a name="enterpriseapnparams"></a>enterpriseapnparams

设置给定接口的移动宽带数据 enterpriseAPN 参数。

**语法**

```powershell
set enterpriseapnparams [interface=]<string> [allowusercontrol=]yes|no|nc [allowuserview=]yes|no|nc [profileaction=]add|delete|modify|nc
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **allowusercontrol** | 以下值之一：<br>yes：允许最终用户控制 enterpriseAPN。<br>no：禁止最终用户控制 enterpriseAPN。<br>nc：未更改。 | 必需 |
| **allowuserview** |以下值之一：<br>yes：允许最终用户查看 enterpriseAPN。<br>no：禁止最终用户查看 enterpriseAPN。<br>nc：未更改。 | 必需 |
| **profileaction** | 以下值之一：<br>add：刚刚添加了 enterpriseAPN 配置文件。<br>delete：刚刚删除了 enterpriseAPN 配置文件。<br>modify：刚刚修改了 enterpriseAPN 配置文件。<br>nc：未更改。 | 必需 |


**示例**

```powershell
set enterpriseapnparams interface="Cellular" profileset=mms mode=yes
```


### <a name="highestconncategory"></a>highestconncategory

设置给定接口的移动宽带数据最高连接类别。

**语法**

```powershell
set highestconncategory [interface=]<string> [highestcc=]admim|user|operator|device
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **highestcc** | 以下值之一：<br>admin：管理员预配的配置文件。<br>user：用户预配的配置文件。<br>operator：操作员预配的配置文件。<br>device：设备预配的配置文件。 | 必需 |


**示例**

```powershell
set highestconncategory interface="Cellular" highestcc=operator
```


### <a name="powerstate"></a>powerstate

对给定的接口打开或关闭移动宽带无线电。

**语法**

```powershell
set powerstate [interface=]<string> [state=]on|off
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **state**      | 以下值之一：<br>on：打开无线电收发器的电源。<br>off：关闭无线电收发器的电源。 | 必需 |


**示例**

```powershell
set powerstate interface="Cellular" state=on
```


### <a name="profileparameter"></a>profileparameter

在移动宽带网络配置文件中设置参数。

**语法**

```powershell
set profileparameter [name=]<string> [[interface=]<string>] [[cost]=default|unrestricted|fixed|variable]
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **name**      | 要修改的配置文件的名称。 如果指定了接口，则只修改该接口上的配置文件。 | 必需 |
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 可选 |
| **cost**      | 与配置文件关联的成本。                                                             | 可选 |


**备注**

必须在接口名称与成本之间至少指定一个参数。


**示例**

```powershell
set profileparameter name="profile 1" cost=default
```


### <a name="slotmapping"></a>slotmapping

设置给定接口的移动宽带调制解调器插槽映射。

**语法**

```powershell
set slotmapping [interface=]<string> [slotindex=]<integer>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **slotindex** | 要设置的插槽索引。                                                                         | 必需 |


**示例**

```powershell
set slotmapping interface="Cellular" slotindex=1
```


### <a name="tracing"></a>tracing

启用或禁用跟踪。

**语法**

```powershell
set tracing [mode=]yes|no
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **mode**      | 以下值之一：<br>yes：启用移动宽带跟踪。<br>no：禁用移动宽带跟踪。     | 必需 |


**示例**

```powershell
set tracing mode=yes
```

## <a name="show"></a>显示

显示移动宽带网络信息。

可用的 netsh mbn set 命令为：

- [acstate](#acstate)
- [capability](#capability)
- [connection](#connection)
- [dataenablement](#dataenablement)
- [dataroamcontrol](#dataroamcontrol)
- [dmprofiles](#dmprofiles)
- [enterpriseapnparams](#enterpriseapnparams)
- [highestconncategory](#highestconncategory)
- [homeprovider](#homeprovider)
- [interfaces](#interfaces)
- [netlteattachinfo](#netlteattachinfo)
- [pin](#pin)
- [pinlist](#pinlist)
- [preferredproviders](#preferredproviders)
- [profiles](#profiles)
- [profilestate](#profilestate)
- [provisionedcontexts](#provisionedcontexts)
- [purpose](#purpose)
- [radio](#radio)
- [readyinfo](#readyinfo)
- [signal](#signal)
- [slotmapping](#slotmapping)
- [slotstatus](#slotstatus)
- [smsconfig](#smsconfig)
- [tracing](#tracing)
- [visibleproviders](#visibleproviders)

### <a name="acstate"></a>acstate  

显示给定接口的移动宽带数据自动连接状态。

**语法**

```powershell
show acstate [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show acstate interface="Cellular"
```


### <a name="capability"></a>capability

显示给定接口的接口功能信息。

**语法**

```powershell
show capability [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show capability interface="Cellular"
```


### <a name="connection"></a>connection

显示给定接口的当前连接信息。

**语法**

```powershell
show connection [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show connection interface="Cellular"
```


### <a name="dataenablement"></a>dataenablement

显示给定接口的移动宽带数据启用状态。

**语法**

```powershell
show dataenablement [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show dataenablement interface="Cellular"
```


### <a name="dataroamcontrol"></a>dataroamcontrol

显示给定接口的移动宽带数据漫游控制状态。

**语法**

```powershell
show dataroamcontrol [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show dataroamcontrol interface="Cellular"
```


### <a name="dmprofiles"></a>dmprofiles

显示系统上配置的 DM Config 配置文件列表。

**语法**

```powershell
show dmprofiles [[name=]<string>] [[interface=]<string>]
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **name**      | 要显示的配置文件的名称。                                                               | 可选 |
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 可选 |

**备注**
    
显示配置文件数据或列出系统上的配置文件。

如果指定了配置文件名称，则会显示配置文件的内容。 否则会列出接口的配置文件。

如果指定了接口名称，则只会列出给定接口上的指定配置文件。 否则会显示第一个匹配的配置文件。

**示例**

```powershell
show dmprofiles name="profile 1" interface="Cellular"
show dmprofiles name="profile 2"
show dmprofiles
```


### <a name="enterpriseapnparams"></a>enterpriseapnparams

显示给定接口的移动宽带数据 enterpriseAPN 参数。

**语法**

```powershell
show enterpriseapnparams [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show enterpriseapnparams interface="Cellular"
```


### <a name="highestconncategory"></a>highestconncategory

显示给定接口的移动宽带数据最高连接类别。

**语法**

```powershell
show highestconncategory [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show highestconncategory interface="Cellular"
```


### <a name="homeprovider"></a>homeprovider

显示给定接口的本地提供商信息。

**语法**

```powershell
show homeprovider [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show homeprovider interface="Cellular"
```


### <a name="interfaces"></a>interfaces

显示系统上的移动宽带接口列表。 此命令没有参数。

**语法**

```powershell
show interfaces
```


### <a name="netlteattachinfo"></a>netlteattachinfo

显示给定接口的移动宽带网络 LTE 附加信息。

**语法**

```powershell
show netlteattachinfo [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show netlteattachinfo interface="Cellular"
```

### <a name="pin"></a>固定      

显示给定接口的引脚信息。

**语法**

```powershell
show pin [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show pin interface="Cellular"
```


### <a name="pinlist"></a>pinlist  

显示给定接口的引脚列表信息。

**语法**

```powershell
show pinlist [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show pinlist interface="Cellular"
```


### <a name="preferredproviders"></a>preferredproviders

显示给定接口的首选提供商列表。

**语法**

```powershell
show preferredproviders [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show preferredproviders interface="Cellular"
```


### <a name="profiles"></a>profiles 

显示系统上配置的配置文件列表。

**语法**

```powershell
show profiles [[name=]<string>] [[interface=]<string>] [[purpose=]<string>]
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **name**      | 要显示的配置文件的名称。                                                               | 可选 |
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 可选 |
| **purpose**   | 用途 | 可选 |

**备注**

如果指定了配置文件名称，则会显示配置文件的内容。 否则会列出接口的配置文件。

如果指定了接口名称，则只会列出给定接口上的指定配置文件。 否则会显示第一个匹配的配置文件。

如果提供了用途，则只会显示具有匹配用途 GUID 的配置文件。  否则不会按用途筛选配置文件。  字符串可以是带大括号的 GUID，或以下字符串之一：internet、supl、mms、ims 或 allhost。
    
**示例**

```powershell
show profiles interface="Cellular" purpose="{00000000-0000-0000-0000-000000000000}"
show profiles name="profile 1" interface="Cellular"
show profiles name="profile 2"
show profiles
```

### <a name="profilestate"></a>profilestate

显示给定接口的移动宽带配置文件状态。

**语法**

```powershell
show profilestate [interface=]<string> [name=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |
| **name**      | 配置文件的名称。 它是具有要显示状态的配置文件的名称。            | 必需 |

**示例**

```powershell
show profilestate interface="Cellular" name="myProfileName"
```

### <a name="provisionedcontexts"></a>provisionedcontexts

显示给定接口的预配上下文信息。

**语法**

```powershell
show provisionedcontexts [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show provisionedcontexts interface="Cellular"
```


### <a name="purpose"></a>purpose  

显示可用于在设备上筛选配置文件的用途组 GUID。 此命令没有参数。

**语法**

```powershell
show purpose
```


### <a name="radio"></a>radio    

显示给定接口的无线电状态信息。

**语法**

```powershell
show radio [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show radio interface="Cellular"
```


### <a name="readyinfo"></a>readyinfo

显示给定接口的就绪状态信息。

**语法**

```powershell
show readyinfo [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show readyinfo interface="Cellular"
```


### <a name="signal"></a>signal   

显示给定接口的信号信息。

**语法**

```powershell
show signal [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show signal interface="Cellular"
```


### <a name="slotmapping"></a>slotmapping

显示给定接口的移动宽带调制解调器插槽映射。

**语法**

```powershell
show slotmapping [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show slotmapping interface="Cellular"
```


### <a name="slotstatus"></a>slotstatus

显示给定接口的移动宽带调制解调器插槽状态。

**语法**

```powershell
show slotstatus [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show slotstatus interface="Cellular"
```


### <a name="smsconfig"></a>smsconfig

显示给定接口的短信配置信息。

**语法**

```powershell
show smsconfig [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show smsconfig interface="Cellular"
```


### <a name="tracing"></a>tracing  

显示是启用还是禁用了移动宽带跟踪。

**语法**

```powershell
show tracing 
```


### <a name="visibleproviders"></a>visibleproviders

显示给定接口的可视提供商列表。

**语法**

```powershell
show visibleproviders [interface=]<string>
```

**Parameters**

|               |                                                                                               |          |
|---------------|-----------------------------------------------------------------------------------------------|----------|
| **interface** | 接口名称。 它是“netsh mbn show interface”命令显示的接口名称之一。 | 必需 |


**示例**

```powershell
show visibleproviders interface="Cellular"
```
