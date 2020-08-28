---
title: change port
description: "\"更改端口\" 命令的参考文章，此命令可列出或更改 COM 端口映射，使其与 MS-DOS 应用程序兼容。"
ms.topic: article
ms.assetid: 3d772c90-e849-4e74-b9ec-b6cae1159336 Lizap
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8014ba67b2c4383aa56a6fce5eb486bbccfba7e7
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031155"
---
# <a name="change-port"></a>change port

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

列出或更改要与 MS-DOS 应用程序兼容的 COM 端口映射。

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 [Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
change port [<portX>=<portY| /d <portX | /query]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|-----------------|----------------------------------------|
| <portX>=<portY> | 将 COM 映射 `<*portX*>` 到 `<*portY*>` |
| /d <portX> | 删除 COM 的映射 `<*portX*>` |
| /query | 显示当前端口映射。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>注解

- 大多数 MS-DOS 应用程序仅支持 COM1 到 COM4 串行端口。 " **更改端口** " 命令将串行端口映射到不同的端口号，允许不支持高编号 COM 端口的应用访问串行端口。 重新映射仅适用于当前会话，如果从会话中注销然后重新登录，则不会保留。

- 使用不带任何参数的 **change 端口** 显示可用 COM 端口及其当前映射。

## <a name="examples"></a>示例

- 若要将 COM12 映射到 COM1 以供基于 MS-DOS 的应用程序使用，请键入：

  ```
  change port com12=com1
  ```

- 若要显示当前端口映射，请键入：

  ```
  change port /query
  ```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [change 命令](change.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
