---
title: prnqctl
description: Prnqctl 命令的参考文章，用于打印测试页面，暂停或恢复打印机。
ms.topic: article
ms.assetid: 8df9dfa7-984c-4276-bb7d-e7675e7c399e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 9ab7c6e8302ebd2c94daee98d8bbef87ecfd4854
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884698"
---
# <a name="prnqctl"></a>prnqctl

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

打印测试页、暂停或恢复打印机以及清除打印机队列。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入**cscript** ，然后键入 prnqctl 文件的完整路径，或将目录更改为相应的文件夹。 例如： `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnqctl`。

## <a name="syntax"></a>语法

```
cscript Prnqctl {-z | -m | -e | -x | -?} [-s <Servername>] [-p <Printername>] [-u <Username>] [-w <password>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| -Z | 暂停 **-p**参数指定的打印机上的打印。 |
| -m | 在由 **-p**参数指定的打印机上恢复打印。 |
| -E | 打印由 **-p**参数指定的打印机上的测试页。 |
| -X | 取消由 **-p**参数指定的打印机上的所有打印作业。 |
| -s`<Servername>` | 指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。 |
| -p`<Printername>` | 必需。 指定要管理的打印机的名称。 |
| -u `<Username>` -w`<password>` | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来 (例如，"Computer Name" ) 。

### <a name="examples"></a>示例

若要在 Server1 计算机共享的 Laserprinter1 打印机上打印测试页 \\ ，请键入：

```
cscript prnqctl -e -s Server1 -p Laserprinter1
```

若要在本地计算机上的 Laserprinter1 打印机上暂停打印，请键入：

```
cscript prnqctl -z -p Laserprinter1
```

若要取消本地计算机上 Laserprinter1 打印机上的所有打印作业，请键入：

```
cscript prnqctl -x -p Laserprinter1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
