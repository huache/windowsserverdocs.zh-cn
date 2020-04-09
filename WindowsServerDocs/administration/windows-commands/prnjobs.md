---
title: prnjobs
description: 了解如何从命令行管理打印作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 5ad34199-7a5a-40c1-8053-bccd5929df43
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 231b8a7a9f4f8623b3d84cc789064d256883a733
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80837290"
---
# <a name="prnjobs"></a>prnjobs

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

暂停、恢复、取消和列出打印作业。

## <a name="syntax"></a>语法
```
cscript Prnjobs {-z | -m | -x | -l | -?} [-s <ServerName>] 
[-p <printerName>] [-j <JobID>] [-u <UserName>] [-w <Password>]
```

### <a name="parameters"></a>参数

|          参数           |                                                                                                                                                                                        说明                                                                                                                                                                                        |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              -z              |                                                                                                                                                                 暂停指定了 **-j**参数的打印作业。                                                                                                                                                                 |
|              -m              |                                                                                                                                                                恢复用 **-j**参数指定的打印作业。                                                                                                                                                                 |
|              -x              |                                                                                                                                                                取消用 **-j**参数指定的打印作业。                                                                                                                                                                 |
|              -l              |                                                                                                                                                                        列出打印队列中的所有打印作业。                                                                                                                                                                         |
|       -s \<ServerName >       |                                                                                                                  指定承载要管理的打印机的远程计算机的名称。 如果未指定计算机，则使用本地计算机。                                                                                                                  |
|      -p \<printerName >       |                                                                                                                                                           指定要管理的打印机的名称。 必需。                                                                                                                                                            |
|         -j \<JobID >          |                                                                                                                                                                指定要取消的打印作业（按 ID 号）。                                                                                                                                                                 |
| -u \<用户名 >-w <Password> | 指定有权连接到承载要管理的打印机的计算机的帐户。 目标计算机的本地管理员组的所有成员都具有这些权限，但也可以向其他用户授予权限。 如果未指定帐户，则必须使用具有这些权限的帐户登录，才能使命令正常工作。 |
|              /?              |                                                                                                                                                                           在命令提示符下显示帮助。                                                                                                                                                                            |

## <a name="remarks"></a>备注
-   **Prnjobs**命令是位于%windir%\system32\ printing_Admin_Scripts\\<language> 目录中的 Visual Basic 脚本。 若要使用此命令，请在命令提示符下键入**cscript** ，后跟 prnjobs 文件的完整路径，或将目录更改为相应的文件夹。 例如：
    ```
    cscript %WINdir%\System32\printing_Admin_Scripts\en-US\prnjobs.vbs
    ```
-   如果提供的信息包含空格，请使用引号将文本括起来（例如 `"computer Name"`）。

## <a name="examples"></a><a name="BKMK_examples"></a>示例
若要将作业 ID 为27的打印作业暂停发送到名为 HRServer 的远程计算机进行打印，请在名为 colorprinter 的打印机上键入：
```
cscript prnjobs.vbs -z -s HRServer -p colorprinter -j 27
```
若要列出名为 colorprinter_2 的本地打印机的队列中的所有当前打印作业，请键入：
```
cscript prnjobs.vbs -l -p colorprinter_2
```

## <a name="additional-references"></a>其他参考

-   - [命令行语法项](command-line-syntax-key.md)
-   [打印命令参考](print-command-reference.md)
