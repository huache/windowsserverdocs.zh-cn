---
title: pubprn
description: Pubprn 命令的参考文章，用于将打印机发布到 Active Directory 域服务。
ms.topic: article
ms.assetid: 0bc7f7e3-84e1-4359-b477-7b1a1a0bd639
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 33905fbfe06887ee8b8721ed9c91eed5701ed3f5
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87884604"
---
# <a name="pubprn"></a>pubprn

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将打印机发布到 Active Directory 域服务。 此命令是位于目录中的 Visual Basic 脚本 `%WINdir%\System32\printing_Admin_Scripts\<language>` 。 若要在命令提示符下使用此命令，请键入**cscript** ，然后键入 pubprn 文件的完整路径，或将目录更改为相应的文件夹。 例如： `cscript %WINdir%\System32\printing_Admin_Scripts\en-US\pubprn`。

## <a name="syntax"></a>语法

```
cscript pubprn {<servername> | <UNCprinterpath>} LDAP://CN=<container>,DC=<container>
```

### <a name="parameters"></a>参数

| 参数 | 描述 |
|--|--|
| `<servername>` | 指定承载要发布的打印机的 Windows 服务器的名称。 如果未指定计算机，则使用本地计算机。 |
| `<UNCprinterpath>` | 通用命名约定 (要发布的共享打印机的 UNC) 路径。 |
| `LDAP://CN=<Container>,DC=<Container>` | 指定要在其中发布打印机 Active Directory 域服务容器的路径。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 如果提供的信息包含空格，请使用引号将文本括起来 (例如，"Computer Name" ) 。

### <a name="examples"></a>示例

若要将 Server1 计算机上的所有打印机发布 \\ 到 MyDomain.company.com 域中的 MyContainer 容器，请键入：

```
cscript pubprn Server1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```

若要将 \Server1 服务器上的 Laserprinter1 打印机发布 \\ 到 MyDomain.company.com 域中的 MyContainer 容器，请键入：

```
cscript pubprn \\Server1\Laserprinter1 LDAP://CN=MyContainer,DC=MyDomain,DC=company,DC=Com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [打印命令参考](print-command-reference.md)
