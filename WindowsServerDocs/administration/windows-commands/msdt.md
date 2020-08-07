---
title: msdt
description: 适用于 msdt 命令的参考文章，此命令在命令行或自动脚本中调用疑难解答包，并启用其他选项，无需用户输入。
ms.topic: article
ms.assetid: ead1b672-a120-4e16-94aa-a8e13602c1d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e8ef856cd54b93c77d4e260a5e433c67407d9611
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87886208"
---
# <a name="msdt"></a>msdt

在命令行或自动脚本中调用疑难解答包，并启用其他选项，无需用户输入。

## <a name="syntax"></a>语法

```
msdt </id <name> | /path <name> | /cab < name>> <</parameter> [options] … <parameter> [options]>>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
| --------- | ----------- |
| /id`<packagename>` | 指定要运行的诊断包。 有关可用包的列表，请参阅[可用的疑难解答包](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/ee424379(v=ws.11)#available-troubleshooting-packs)。 |
| /path`<directory|.diagpkg file|.diagcfg file>` | 指定诊断包的完整路径。 如果指定目录，则该目录必须包含诊断程序包。 不能将 **/path**参数与 * */id * *、 **/dci**或 **/cab**参数一起使用。 |                                                                                   |
| /dci`<passkey>` | 预填充 "密钥" 字段。 仅当支持提供程序提供了密钥时，才使用此参数。 |
| /dt`<directory>` | 显示指定目录中的故障排除历史记录。 诊断结果存储在用户的 **%LOCALAPPDATA%\Diagnostics**或 **%LOCALAPPDATA%\ElevatedDiagnostics**目录中。 |
| /af`<answerfile>` | 指定 XML 格式的应答文件，该文件包含对一个或多个诊断交互的响应。 |
| /modal`<ownerHWND>` | 使疑难解答包模式向父控制台窗口指定的窗口处理 (HWND) （以十进制表示）。 此参数通常由启动疑难解答包的应用程序使用。 有关获取控制台窗口句柄的详细信息，请参阅[如何获取控制台窗口句柄 (HWND) ](https://support.microsoft.com/help/124103/how-to-obtain-a-console-window-handle-hwnd)。 |
| /moreoptions`<true|false>` | 启用 (true) 或取消显示询问用户是否要浏览其他选项的最终故障排除屏幕 () false。 当疑难解答包由不属于操作系统的疑难解答程序启动时，通常使用此参数。 |
| /param returns`<parameters>` | 在命令行中指定一组交互响应，类似于答案文件。 此参数通常不在使用 TSP 设计器创建的疑难解答包的上下文中使用。 有关开发自定义参数的详细信息，请参阅[Windows 故障排除平台](/previous-versions/windows/desktop/wintt/windows-troubleshooting-toolkit-portal)。 |
| /advanced | 启动疑难解答包时，默认展开 "欢迎" 页上的 "高级" 链接。 |
| /custom | 提示用户在应用前确认每个可能的解决方法。 |

### <a name="return-codes"></a>返回代码

排除包包括一组根本原因，其中每个原因都描述了特定的技术问题。 完成故障排除包任务后，每个根本原因都将返回已修复但未修复的状态，检测到 (但无法修复) 或找不到该状态。 除了在疑难解答用户界面中报告的特定结果，故障排除引擎还会在结果中返回一个代码，这些结果通常是由于疑难解答程序修复了原始问题。 这些代码为：

| 代码 | 说明 |
| ---- | ----------- |
| -1 | **中断：** 疑难解答任务完成之前关闭了疑难解答。 |
| 0 | 已**修复：** 疑难解答程序识别并修复至少一个根本原因，根本原因不会保留在 "未固定" 状态。 |
| 1 | **存在，但不是固定的：** 疑难解答程序识别出一个或多个不处于固定状态的根本原因。 即使已修复另一个根本原因，此代码也会返回。 |
| 2 | **找不到：** 疑难解答不能识别任何根本原因。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [可用的疑难解答包](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/ee424379(v=ws.11)#available-troubleshooting-packs)

- [TroubleshootingPack Powershell 参考](/powershell/module/troubleshootingpack/?view=win10-ps)
