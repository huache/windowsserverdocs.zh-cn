---
title: cmstp
description: 用于安装或删除连接管理器服务配置文件的 cmstp 的参考文章。
ms.topic: article
ms.assetid: 34aad544-11c3-4e85-8bbf-5bc5a971da93
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 36f07fd6215159c1b4e6384f93725e26e2d22ebc
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880051"
---
# <a name="cmstp"></a>cmstp

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

安装或删除连接管理器服务配置文件。 使用不带可选参数的， **cmstp**将使用适用于操作系统和用户权限的默认设置安装服务配置文件。

## <a name="syntax"></a>语法

语法 1-这是在自定义安装应用程序中使用的典型语法。 若要使用此语法，必须从包含该文件的目录中运行**cmstp** `<serviceprofilefilename>.exe` 。

```
<serviceprofilefilename>.exe /q:a /c:cmstp.exe <serviceprofilefilename>.inf [/nf] [/s] [/u]
```

语法2
```
cmstp.exe [/nf] [/s] [/u] [drive:][path]serviceprofilefilename.inf
```

#### <a name="parameters"></a>参数
| 参数 | 描述 |
| --------- | ----------- |
| `<serviceprofilefilename>.exe` | 按名称指定包含要安装的配置文件的安装包。<p>对于语法1是必需的，但对于语法2是无效的。 |
| /q： a | 指定在不提示用户的情况下安装配置文件。 安装已成功的验证消息仍将出现。<p>对于语法1是必需的，但对于语法2是无效的。 |
| [驱动器：]通道`<serviceprofilefilename>.inf` | 必需。 按名称指定配置文件的配置文件，该配置文件确定如何安装配置文件。<p>[驱动器：] [路径] 参数对于语法1无效。 |
| /nf | 指定不应安装支持文件。 |
| /s | 指定在不提示用户响应或显示验证消息) 的情况下，应以无提示方式安装或卸载服务配置文件 (。 这是可与 **/u**结合使用的唯一参数。|
| /U | 指定应卸载服务配置文件。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要在没有任何支持文件的情况下安装*小说*服务配置文件，请键入：

```
fiction.exe /c:cmstp.exe fiction.inf /nf
```

若要以无提示方式安装单个用户的*小说*服务配置文件，请键入：

```
fiction.exe /c:cmstp.exe fiction.inf /s /su
```

若要以无提示方式卸载*小说*服务配置文件，请键入：

```
fiction.exe /c:cmstp.exe fiction.inf /s /u
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
