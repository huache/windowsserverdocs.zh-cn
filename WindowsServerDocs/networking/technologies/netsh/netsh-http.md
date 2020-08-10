---
title: 用于超文本传输协议 (HTTP) 的 Netsh 命令
description: 使用 netsh http 查询和配置 HTTP.sys 设置和参数。
ms.topic: article
manager: dougkim
ms.author: lizross
author: eross-msft
ms.openlocfilehash: a2bf580dff85463306767b6a129819b82f4fc85c
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87946981"
---
# <a name="netsh-http-commands"></a>Netsh http 命令


使用 netsh http 查询和配置 HTTP.sys 设置和参数  。

>[!TIP]
>如果在运行 Windows Server 2016 或 Windows 10 的计算机上使用 Windows PowerShell，请键入 netsh 并按 Enter  。 在 netsh 提示符下键入 http，然后按 Enter 获取 netsh http 提示符  。
>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;netsh http\>

可用的 netsh http 命令包括：

- [add iplisten](#add-iplisten)
- [add sslcert](#add-sslcert)
- [add timeout](#add-timeout)
- [add urlacl](#add-urlacl)
- [delete cache](#delete-cache)
- [delete iplisten](#delete-iplisten)
- [delete sslcert](#delete-sslcert)
- [delete timeout](#delete-timeout)
- [delete urlacl](#delete-urlacl)
- [flush logbuffer](#flush-logbuffer)
- [show cachestate](#show-cachestate)
- [show iplisten](#show-iplisten)
- [show servicestate](#show-servicestate)
- [show sslcert](#show-sslcert)
- [show timeout](#show-timeout)
- [show urlacl](#show-urlacl)

## <a name="add-iplisten"></a>add iplisten

向 IP 侦听列表添加新的 IP 地址（不包括端口号）。

**语法**

```powershell
add iplisten [ ipaddress= ] IPAddress
```

**Parameters**

|               |                                                                                                                                                                                                                          |          |
|---------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| **ipaddress** | 要添加到 IP 侦听列表的 IPv4 或 IPv6 地址。 IP 侦听列表用于确定 HTTP 服务绑定到的地址列表的范围。 “0.0.0.0”表示任何 IPv4 地址，“::”表示任何 IPv6 地址。 | 必需 |

---

**示例**

下面是 add iplisten 命令的四个示例  。

-   add iplisten ipaddress=fe80::1
-   add iplisten ipaddress=1.1.1.1
-   add iplisten ipaddress=0.0.0.0
-   add iplisten ipaddress=::

---

## <a name="add-sslcert"></a>add sslcert

为 IP 地址和端口添加新的 SSL 服务器证书绑定和相应的客户端证书策略。

**语法**

```powershell
add sslcert [ ipport= ] IPAddress:port [ certhash= ] CertHash [ appid= ] GUID [ [ certstorename= ] CertStoreName [ verifyclientcertrevocation= ] enable | disable [verifyrevocationwithcachedclientcertonly= ] enable | disable [ usagecheck= ] enable | disable [ revocationfreshnesstime= ] U-Int [ urlretrievaltimeout= ] U-Int [sslctlidentifier= ] SSLCTIdentifier [ sslctlstorename= ] SLCtStoreName [ dsmapperusage= ] enable | disable [ clientcertnegotiation= ] enable | disable ] ]
```

**Parameters**


|                                              |                                                                                                                                                                                          |          |
|----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
|                  **ipport**                  |                       指定绑定的 IP 地址和端口。 冒号字符 (:) 用作 IP 地址和端口号之间的分隔符。                        | 必需 |
|                 **certhash**                 |                                     指定证书的 SHA 哈希。 此哈希长度为 20 个字节，并指定为十六进制字符串。                                      | 必需 |
|                  **appid**                   |                                                                  指定用于标识所属应用程序的 GUID。                                                                  | 必需 |
|              **certstorename**               |                                  指定证书的存储名称。 默认情况下为 MY。 证书必须存储在本地计算机上下文中。                                  | 可选 |
|        **verifyclientcertrevocation**        |                                                      指定客户端证书吊销的打开/关闭验证。                                                       | 可选 |
| **verifyrevocationwithcachedclientcertonly** |                                      指定是启用还是禁用仅将缓存的客户端证书用于吊销检查。                                       | 可选 |
|                **usagecheck**                |                                                      指定是启用或禁用使用情况检查。 默认为启用。                                                       | 可选 |
|         **revocationfreshnesstime**          | 指定检查更新的证书吊销列表 (CRL) 的时间间隔（以秒为单位）。 如果此值为零，则仅当上一个 CRL 过期时才会更新新的 CRL。 | 可选 |
|           **urlretrievaltimeout**            |                            指定尝试检索远程 URL 的证书吊销列表后的超时间隔（以毫秒为单位）。                            | 可选 |
|             **sslctlidentifier**             |                指定可信任的证书颁发者的列表。 此列表可以是计算机信任的证书颁发者的子集。                 | 可选 |
|             **sslctlstorename**              |                                                指定存储 SslCtlIdentifier 的 LOCAL_MACHINE 下的证书存储名称。                                                | 可选 |
|              **dsmapperusage**               |                                                        指定是启用还是禁用 DS 映射器。 默认为禁用。                                                         | 可选 |
|          **clientcertnegotiation**           |                                              指定是启用还是禁用证书协商。 默认为禁用。                                               | 可选 |

---

**示例**

下面是 add sslcert 命令的示例  。

add sslcert ipport=1.1.1.1:443 certhash=0102030405060708090A0B0C0D0E0F1011121314 appid={00112233-4455-6677-8899- AABBCCDDEEFF}

---

## <a name="add-timeout"></a>add timeout

将全局超时添加到服务。

**语法**

```powershell
add timeout [ timeouttype= ] IdleConnectionTimeout | HeaderWaitTimeout [ value=] U-Short
```

**Parameters**

|                 |                                                                                                     |
|-----------------|-----------------------------------------------------------------------------------------------------|
| **timeouttype** |                                    设置的超时类型。                                     |
|    **value**    | 超时值（以秒为单位）。 如果该值采用十六进制表示法，则添加前缀 0x。 |

---

**示例**

下面是 add timeout 命令的两个示例  。

-   add timeout timeouttype=idleconnectiontimeout value=120
-   add timeout timeouttype=headerwaittimeout value=0x40

---

## <a name="add-urlacl"></a>add urlacl

添加统一资源定位器 (URL) 保留条目。 此命令保留非管理员用户和帐户的 URL。 可以通过将 NT 帐户名与侦听和委托参数一起使用或使用 SDDL 字符串来指定 DACL。

**语法**

```powershell
add urlacl [ url= ] URL [ [user=] User [ [ listen= ] yes | no [ delegate= ] yes | no ] | [ sddl= ] SDDL ]
```

**Parameters**

|              |                                                                                                                                                  |          |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------|----------|
|   **url**    |                                          指定完全限定的统一资源定位器 (URL)。                                           | 必需 |
|   **user**   |                                                      指定用户或用户组名称                                                       | 必需 |
|  **listen**  | 指定下列值之一，yes：允许用户注册 URL。 这是默认值。 no：拒绝用户注册 URL。 | 可选 |
| **delegate** |  指定下列值之一，yes：允许用户委托 URL。no：拒绝用户委托 URL。 这是默认值。  | 可选 |
|   **sddl**   |                                                指定描述 DACL 的 SDDL 字符串。                                                 | 可选 |

---

**示例**

下面是 add urlacl 命令的四个示例  。

- add urlacl url=https://+:80/MyUri user=DOMAIN\\ user
- add urlacl url=<https://www.contoso.com:80/MyUri> user=DOMAIN\\user listen=yes
- add urlacl url=<https://www.contoso.com:80/MyUri> user=DOMAIN\\user delegate=no
- add urlacl url=https://+:80/MyUri sddl=...

---

## <a name="delete-cache"></a>delete cache

从 HTTP 服务内核 URI 缓存中删除所有条目或指定的条目。

**语法**

```powershell
delete cache [ [ url= ] URL [ [recursive= ] yes | no ]
```

**Parameters**

|               |                                                                                                                              |          |
|---------------|------------------------------------------------------------------------------------------------------------------------------|----------|
|    **url**    |                    指定要删除的完全限定的统一资源定位器 (URL)。                     | 可选 |
| **recursive** | 指定是否删除 URL 缓存下的所有条目。 yes：删除所有条目。no：不删除所有条目   | 可选 |

---

**示例**

下面是 delete cache 命令的两个示例  。

- delete cache url=<https://www.contoso.com:80/myresource/> recursive=yes
- delete cache

---

## <a name="delete-iplisten"></a>delete iplisten

从 IP 侦听列表中删除 IP 地址。 IP 侦听列表用于确定 HTTP 服务绑定到的地址列表的范围。

**语法**

```powershell
delete iplisten [ ipaddress= ] IPAddress
```

**Parameters**

|               |                                                                                                                                                                                                                                                                     |          |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| **ipaddress** | 要从 IP 侦听列表删除的 IPv4 或 IPv6 地址。 IP 侦听列表用于确定 HTTP 服务绑定到的地址列表的范围。 “0.0.0.0”表示任何 IPv4 地址，“::”表示任何 IPv6 地址。 这不包括端口号。 | 必需 |

---


**示例**

下面是 delete iplisten 命令的四个示例  。

-   delete iplisten ipaddress=fe80::1
-   delete iplisten ipaddress=1.1.1.1
-   delete iplisten ipaddress=0.0.0.0
-   delete iplisten ipaddress=::

---

## <a name="delete-sslcert"></a>delete sslcert


删除 IP 地址和端口的 SSL 服务器证书绑定和相应的客户端证书策略。

**语法**

```powershell
delete sslcert [ ipport= ] IPAddress:port
```

**Parameters**

|            |                                                                                                                                                                                          |          |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| **ipport** | 指定要为其删除 SSL 证书绑定的 IPv4 或 IPv6 地址和端口。 冒号字符 (:) 用作 IP 地址和端口号之间的分隔符。 | 必需 |

---


**示例**

下面是 delete sslcert 命令的三个示例  。

- delete sslcert ipport=1.1.1.1:443
- delete sslcert ipport=0.0.0.0:443
- delete sslcert ipport=[::]:443

---

## <a name="delete-timeout"></a>delete timeout

删除全局超时，并将服务恢复为默认值。

**语法**

```powershell
delete timeout [ timeouttype= ] idleconnectiontimeout | headerwaittimeout
```

**Parameters**

|                 |                                        |          |
|-----------------|----------------------------------------|----------|
| **timeouttype** | 指定超时设置的类型。 | 必需 |

---


**示例**

下面是 delete timeout 命令的两个示例  。

-   delete timeout timeouttype=idleconnectiontimeout
-   delete timeout timeouttype=headerwaittimeout

---

## <a name="delete-urlacl"></a>delete urlacl

删除 URL 保留项。

**语法**

```powershell
delete urlacl [ url= ] URL
```

**Parameters**

|         |                                                                                       |          |
|---------|---------------------------------------------------------------------------------------|----------|
| **url** | 指定要删除的完全限定的统一资源定位器 (URL)。 | 必需 |

---


**示例**

下面是 delete urlacl 命令的两个示例  。

- delete urlacl url=https://+:80/MyUri
- delete urlacl url=<https://www.contoso.com:80/MyUri>

---

## <a name="flush-logbuffer"></a>flush logbuffer

刷新日志文件的内部缓冲区。

**语法**

```powershell
flush logbuffer
```

---

## <a name="show-cachestate"></a>show cachestate

列出缓存的 URI 资源及其相关属性。 此命令列出缓存在 HTTP 响应缓存中的所有资源及其相关属性，或显示单个资源及其相关属性。

**语法**

```powershell
show cachestate [ [url= ] URL]
```

**Parameters**

|         |                                                                                                                                                    |          |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| **url** | 指定要显示的完全限定的 URL。 如果未指定，则显示所有 URL。 该 URL 还可以是注册 URL 的前缀。 | 可选 |

---


**示例**

下面是 show cachestate 命令的两个示例  ：

- show cachestate url=<https://www.contoso.com:80/myresource>
- show cachestate

---

## <a name="show-iplisten"></a>show iplisten

在 IP 侦听列表中显示所有 IP 地址。 IP 侦听列表用于确定 HTTP 服务绑定到的地址列表的范围。 “0.0.0.0”表示任何 IPv4 地址，“::”表示任何 IPv6 地址。

**语法**

```powershell
show iplisten
```

---

## <a name="show-servicestate"></a>show servicestate

显示 HTTP 服务的屏幕截图。

**语法**
```powershell
show servicestate [ [ view= ] session | requestq ] [ [ verbose= ] yes | no ]
```

**Parameters**

|             |                                                                                                                      |          |
|-------------|----------------------------------------------------------------------------------------------------------------------|----------|
|  **查看**   | 指定是否基于服务器会话或请求队列查看 HTTP 服务状态的快照。 | 可选 |
| **Verbose** |                指定是否显示还显示属性信息的详细信息。                | 可选 |

---

**示例**

下面是 show servicestate 命令的两个示例  。

-   show servicestate view="session"
-   show servicestate view="requestq"

---

## <a name="show-sslcert"></a>show sslcert

显示 IP 地址和端口的安全套接字层 (SSL) 服务器证书绑定和相应的客户端证书策略。

**语法**

```powershell
show sslcert [ ipport= ] IPAddress:port
```

**Parameters**

|            |                                                                                                                                                                                                                                                |          |
|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
| **ipport** | 指定 SSL 证书绑定显示的 IPv4 或 IPv6 地址和端口。 冒号字符 (:) 用作 IP 地址和端口号之间的分隔符。 如果未指定 ipport，则会显示所有绑定。 | 必需 |

---


**示例**

下面是 show sslcert 命令的五个示例  。

-   show sslcert ipport=[fe80::1]:443
-   show sslcert ipport=1.1.1.1:443
-   show sslcert ipport=0.0.0.0:443
-   show sslcert ipport=[::]:443
-   show sslcert

---

## <a name="show-timeout"></a>show timeout

显示 HTTP 服务的超时值（以秒为单位）。

**语法**

```powershell
show timeout
```

---

## <a name="show-urlacl"></a>show urlacl

显示指定保留 URL 或所有保留 URL 的自由访问控制列表 (DACL)。

**语法**

```powershell
show urlacl [ [url= ] URL]
```

**Parameters**

|         |                                                                                                |          |
|---------|------------------------------------------------------------------------------------------------|----------|
| **url** | 指定要显示的完全限定的 URL。 如果未指定，则显示所有 URL。 | 可选 |

---


**示例**

下面是 show urlacl 命令的三个示例  。

- show urlacl url=https://+:80/MyUri
- show urlacl url=<https://www.contoso.com:80/MyUri>
- show urlacl

---