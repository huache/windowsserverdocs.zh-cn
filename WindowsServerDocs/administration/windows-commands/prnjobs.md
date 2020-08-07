---
title: prnjobs
description: Prnjobs 命令的参考文章，用于暂停、恢复、取消和列出打印作业。
ms.topic: article
ms.assetid: 5ad34199-7a5a-40c1-8053-bccd5929df43
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: d955f50761e1229e0a1acf21a9f2179525bd7ee4
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884741"
---
# <a name="prnjobs"></a>prnjobs

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

暂停、恢复、取消和列出打印作业。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入**cscript** ，然后键入 prnjobs 文件的完整路径，或将目录更改为相应的文件夹。 例如： `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnjobs.vbs`。

## <a name="syntax"></a>语法

```
cscript prnjobs {-z | -m | -x | -l | -?} [-s <Servername>] [-p <Printername>] [-j <JobID>] [-u <Username>] [-w <password>]
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| -Z | 暂停由 **-j**参数指定的打印作业。 |
| -m | 恢复由 **-j**参数指定的打印作业。 |
| -X | 取消由 **-j**参数指定的打印作业。 |
| -l | 列出打印队列中的所有打印作业。 |
| -s`<Servername>` | 指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。 |
| -p`<Printername>` | 必需。 指定要管理的打印机的名称。 |
| -j`<JobID>` | 按 ID 号指定 () 要取消的打印作业。 |
| -u `<Username>` -w`<password>` | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来 (例如，"Computer Name" ) 。

### <a name="examples"></a>示例

若要将作业 ID 为27的打印作业暂停发送到名为 HRServer 的远程计算机进行打印，请在名为 colorprinter 的打印机上键入：

```
cscript prnjobs.vbs -z -s HRServer -p colorprinter -j 27
```

若要列出名为 colorprinter_2 的本地打印机的队列中的所有当前打印作业，请键入：

```
cscript prnjobs.vbs -l -p colorprinter_2
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
