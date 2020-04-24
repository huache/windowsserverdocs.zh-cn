---
title: 界面端口代理的 Netsh 命令
description: 使用 netsh interface portproxy 命令作为 IPv4 和 IPv6 网络与应用程序之间的代理。
ms.prod: windows-server
ms.technology: networking
ms.topic: article
manager: dougkim
ms.author: lizross
author: eross-msft
ms.date: 08/30/2018
ms.openlocfilehash: e9c4cff4d1424c244857cf75be41d445b299f1f2
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80853740"
---
# <a name="netsh-interface-portproxy-commands"></a>Netsh interface portproxy 命令

使用 netsh interface portproxy 命令作为 IPv4 和 IPv6 网络与应用程序之间的代理  。 可以通过以下方式使用这些命令建立代理服务：

-   发送到 IPv4 配置的其他计算机和应用程序的 IPv4 配置的计算机和应用程序消息。

-   发送到 IPv6 配置的计算机和应用程序的 IPv4 配置的计算机和应用程序消息。

-   发送到 IPv4 配置的计算机和应用程序的 IPv6 配置的计算机和应用程序消息。

-   发送到 IPv6 配置的其他计算机和应用程序的 IPv6 配置的计算机和应用程序消息。

使用这些命令编写批处理文件或脚本时，每个命令必须以 netsh interface portproxy 开头  。 例如，使用 delete v4tov6 命令指定 portproxy 服务器从服务器侦听的 IPv4 地址列表中删除 IPv4 端口和地址时，批处理文件或脚本必须使用以下语法  ：

```PowerShell
netsh interface portproxy delete v4tov6listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address| HostName}] [[protocol=]tcp]
```

可用的 netsh interface portproxy 命令包括：

-   [add v4tov4](#add-v4tov4)

-   [add v4tov6](#add-v4tov6)

-   [add v6tov4](#add-v6tov4)

-   [add v6tov6](#add-v6tov6)

-   [delete v4tov4](#delete-v4tov4)

-   [delete v4tov6](#delete-v4tov6)

-   [delete v6tov6](#delete-v6tov6)

-   [reset](#reset)

-   [set v4tov4](#set-v4tov4)

-   [set v4tov6](#set-v4tov6)

-   [setv6tov4](#set-v6tov4)

-   [set v6tov6](#set-v6tov6)

-   [show all](#show-all)

-   [show v4tov4](#show-v4tov4)

-   [show v4tov6](#show-v4tov6)

-   [show v6tov4](#show-v6tov4)

-   [show v6tov6](#show-v6tov6)


## <a name="add-v4tov4"></a>add v4tov4

Portproxy 服务器侦听发送到特定端口和 IPv4 地址的消息，并映射端口和 IPv4 地址以发送在建立单独的 TCP 连接后收到的消息。

### <a name="syntax"></a>语法

```PowerShell
add v4tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName}] [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName}] [[protocol=]tcp]
```

#### <a name="parameters"></a>参数


|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv4 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv4 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要侦听的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="add-v4tov6"></a>add v4tov6

Portproxy 服务器侦听发送到特定端口和 IPv4 地址的消息，并映射端口和 IPv6 地址以发送在建立单独的 TCP 连接后收到的消息。

### <a name="syntax"></a>语法

```PowerShell
add v4tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv4 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv6 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="add-v6tov4"></a>add v6tov4

Portproxy 服务器侦听发送到特定端口和 IPv6 地址的消息，并映射端口和 IPv4 地址以发送在建立单独的 TCP 连接后收到的消息。

### <a name="syntax"></a>语法

```PowerShell
add v6tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv6 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv4 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="add-v6tov6"></a>add v6tov6

Portproxy 服务器侦听发送到特定端口和 IPv6 地址的消息，并映射端口和 IPv6 地址以发送在建立单独的 TCP 连接后收到的消息。

### <a name="syntax"></a>语法

```PowerShell
add v6tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv6 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv6 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="delete-v4tov4"></a>delete v4tov4

Portproxy 服务器从服务器侦听的 IPv4 端口和地址列表中删除 IPv4 地址。

### <a name="syntax"></a>语法

```PowerShell
delete v4tov4 listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    指定要删除的 IPv4 端口。                                    |
| **listenaddress** | 指定要删除的 IPv4 地址。 如果未指定地址，则默认值为本地计算机。 |
|   **protocol**    |                                      指定要使用的协议。                                      |

## <a name="delete-v4tov6"></a>delete v4tov6

Portproxy 服务器从服务器侦听的 IPv4 地址列表中删除 IPv4 端口和地址。

### <a name="syntax"></a>语法

```PowerShell 
delete v4tov6 listenport= {Integer | ServiceName} [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    指定要删除的 IPv4 端口。                                    |
| **listenaddress** | 指定要删除的 IPv4 地址。 如果未指定地址，则默认值为本地计算机。 |
|   **protocol**    |                                      指定要使用的协议。                                      |

## <a name="delete-v6tov4"></a>delete v6tov4

Portproxy 服务器从服务器侦听的 IPv6 地址列表中删除 IPv6 端口和地址。

### <a name="syntax"></a>语法

```PowerShell
delete v6tov4 listenport= {Integer | ServiceName} [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    指定要删除的 IPv6 端口。                                    |
| **listenaddress** | 指定要删除的 IPv6 地址。 如果未指定地址，则默认值为本地计算机。 |
|   **protocol**    |                                      指定要使用的协议。                                      |

## <a name="delete-v6tov6"></a>delete v6tov6

Portproxy 服务器从服务器侦听的 IPv6 地址列表中删除 IPv6 地址。

### <a name="syntax"></a>语法

```PowerShell
delete v6tov6 listenport= {Integer | ServiceName} [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                   |                                                                                                          |
|-------------------|----------------------------------------------------------------------------------------------------------|
|  **listenport**   |                                    指定要删除的 IPv6 端口。                                    |
| **listenaddress** | 指定要删除的 IPv6 地址。 如果未指定地址，则默认值为本地计算机。 |
|   **protocol**    |                                      指定要使用的协议。                                      |

## <a name="reset"></a>reset

重置 IPv6 配置状态。

### <a name="syntax"></a>语法

`reset`

## <a name="set-v4tov4"></a>set v4tov4

修改使用 add v4tov4 命令创建的 portproxy 服务器上现有条目的参数值，或将新条目添加到映射端口/地址对的列表  。

### <a name="syntax"></a>语法

```PowerShell
set v4tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv4 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv4 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要侦听的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="set-v4tov6"></a>set v4tov6

修改使用 add v4tov6 命令创建的 portproxy 服务器上现有条目的参数值，或将新条目添加到映射端口/地址对的列表  。

### <a name="syntax"></a>语法

```PowerShell
set v4tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv4Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv4 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv6 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="set-v6tov4"></a>set v6tov4

修改使用 add v6tov4 命令创建的 portproxy 服务器上现有条目的参数值，或将新条目添加到映射端口/地址对的列表  。

### <a name="syntax"></a>语法

```PowerShell
set v6tov4 listenport= {Integer | ServiceName} [[connectaddress=] {IPv4Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                   |
|--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                           按端口号或服务名称指定要对其进行侦听的 IPv6 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv4 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|  **connectport**   |       按端口号或服务名称指定要连接的 IPv4 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|    **protocol**    |                                                                                  指定要使用的协议。                                                                                   |

## <a name="set-v6tov6"></a>set v6tov6

修改使用 add v6tov6 命令创建的 portproxy 服务器上现有条目的参数值，或将新条目添加到映射端口/地址对的列表  。

### <a name="syntax"></a>语法

```PowerShell 
set v6tov6 listenport= {Integer | ServiceName} [[connectaddress=] {IPv6Address | HostName} [[connectport=] {Integer | ServiceName}] [[listenaddress=] {IPv6Address | HostName} [[protocol=]tcp]
```

#### <a name="parameters"></a>参数

|                    |                                                                                                                                                                                                    |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **listenport**   |                                                            按端口号或服务名称指定要对其进行侦听的 IPv6 端口。                                                            |
| **connectaddress** | 指定要连接的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。  |
|  **connectport**   |        按端口号或服务名称指定要连接的 IPv6 端口。 如果未指定 connectport，则默认值为本地计算机上 listenport 的值   。        |
| **listenaddress**  | 指定要对其进行侦听的 IPv6 地址。 可接受的值为 IP 地址、计算机 NetBIOS 名称或计算机 DNS 名称。 如果未指定地址，则默认值为本地计算机。 |
|    **protocol**    |                                                                                   指定要使用的协议。                                                                                   |

## <a name="show-all"></a>显示所有

显示所有 portproxy 参数，包括 v4tov4、v4tov6、v6tov4 和 v6tov6 的端口/地址对。

### <a name="syntax"></a>语法

`show all`


## <a name="show-v4tov4"></a>show v4tov4

显示 v4tov4 portproxy 参数。

### <a name="syntax"></a>语法

`show v4tov4`

## <a name="show-v4tov6"></a>show v4tov6

显示 v4tov6 portproxy 参数。

### <a name="syntax"></a>语法

`show v4tov6`

## <a name="show-v6tov4"></a>show v6tov4

显示 v6tov4 portproxy 参数。

### <a name="syntax"></a>语法

`show v6tov4`


## <a name="show-v6tov6"></a>show v6tov6

显示 v6tov6 portproxy 参数。

### <a name="syntax"></a>语法

`show v6tov6`

---
