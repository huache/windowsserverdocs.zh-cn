---
title: pwlauncher
description: Pwlauncher 命令的参考文章，用于启用或禁用 Windows To 中转启动选项 (pwlauncher) 。
ms.topic: reference
ms.assetid: 0917bb7b-408a-40f7-a1c5-20e94c10d38b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0e59182378aa8277a0ff68b31be29c9c315b174b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028145"
---
# <a name="pwlauncher"></a>pwlauncher

启用或禁用 Windows To 中转启动选项 (pwlauncher) 。 使用 **pwlauncher** 命令行工具，可以将计算机配置为自动启动到 Windows to 中转工作区， (假设存在) ，而无需输入固件或更改启动选项。

Windows To boot 启动选项允许用户将其计算机配置为从 Windows 内部启动，而无需输入其固件，只要其固件支持从 USB 启动。 若要使系统始终从 USB 首次启动，则需要考虑一些问题。 例如，可能会无意中启动包含恶意软件的 USB 设备来危害系统，或插入多个 USB 驱动器，导致启动冲突。 出于此原因，默认配置将默认禁用 Windows To To Startup 选项。 此外，需要管理员特权才能配置 Windows To 中转启动选项。 如果使用 pwlauncher 命令行工具或 " **更改 Windows To To Boot 启动选项** " 应用程序启用 Windows to boot 启动选项，计算机将尝试从插入到计算机的任何 USB 设备启动，然后再启动该计算机。

## <a name="syntax"></a>语法

```
pwlauncher {/enable | /disable}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /enable | 启用 Windows To boot 选项，使计算机在出现时自动从 USB 设备启动。 |
| /disable | 禁用 Windows To 中转启动选项，因此除非在固件中手动配置，否则无法从 USB 设备启动计算机。 |
| /? | 在命令提示符下显示帮助。 |

### <a name="examples"></a>示例

若要从 USB 启用启动：

```
pwlauncher /enable
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
