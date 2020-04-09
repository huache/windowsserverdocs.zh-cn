---
title: auditpol resourceSACL
description: 用于配置全局资源系统访问控制列表（Sacl）的**Auditpol resourceSACL**的 Windows 命令主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 28771ba7-967a-45e9-9bf0-b2a2673070f0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b004be6f21cd076fe20e73c45268731c35d654e5
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80851150"
---
# <a name="auditpol-resourcesacl"></a>auditpol resourceSACL

配置全局资源系统访问控制列表（Sacl）。

> [!NOTE]
> 仅适用于 Windows 7 和 Windows Server 2008 R2。

有关如何使用此命令的示例，请参阅[示例](#BKMK_Examples)。

## <a name="syntax"></a>语法

```
auditpol /resourceSACL
[/set /type:<resource> [/success] [/failure] /user:<user> [/access:<access flags>]]
[/remove /type:<resource> /user:<user> [/type:<resource>]]
[/clear [/type:<resource>]]
[/view [/user:<user>] [/type:<resource>]]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /set | 向指定的资源类型的资源 SACL 中添加或更新现有条目。 |
| /remove | 删除全局对象访问审核列表中给定用户的所有条目。 |
| /clear | 从全局对象访问审核列表中移除所有项。|
| /view | 列出资源 SACL 中的全局对象访问审核条目。 用户和资源类型是可选的。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="arguments"></a>参数

| Argument | 说明 |
| -------- | ----------- | 
| /type | 正在为其配置对象访问审核的资源。 支持的、区分大小写的参数值是文件（对于目录和文件）和密钥（对于注册表项）。 |
| /success | 指定成功审核。 |
| /failure | 指定失败的审核。 |
| /user | 使用以下形式之一指定用户：<ul><li> DomainName\Account （如 DOM\Administrators）</li><li>StandaloneServer\Group 帐户（请参阅[LookupAccountName 函数](https://msdn.microsoft.com/library/windows/desktop/aa379159(v=vs.85).aspx)）</li><li>{S-1-x-x x-x}（x 以十进制表示，整个 SID 必须括在大括号中）。 例如： {S-1-5-21-5624481-130208933-164394174-1001}<p>**注意：** 如果使用 SID 格式，则不执行检查来验证此帐户是否存在。</li></ul> |
| /access | 指定可以通过指定的权限掩码：<p>一般访问权限，包括：<ul><li>GA-一般全部</li><li>GR-通用读取</li><li>GW-泛型写入</li><li>GX-泛型执行</li></ul><p>文件的访问权限，包括：<ul><li>FA-文件所有访问权限</li><li>FR-文件一般读取</li><li>FW-文件一般写入</li><li>FX-文件一般执行</li></ul><p>注册表项的访问权限，包括：<ul><li>KA-密钥所有访问权限</li><li>KR-读取密钥</li><li>KW-密钥写入</li><li>KX-KEY EXECUTE</li></ul><p>例如： `/access:FRFW` 将启用审核事件以便进行读写操作。<p>表示访问掩码的十六进制值（如0x1200a9）<p>    当使用不属于安全描述符定义语言（SDDL）标准的特定于资源的位掩码时，这非常有用。 如果省略，则使用完全访问权限。 |

## <a name="remarks"></a>备注

对于 resourceSACL 操作，必须对安全描述符中的该对象集具有 "写入" 或 "完全控制" 权限。 还可以通过拥有 "**管理审核和安全日志**（SeSecurityPrivilege）" 用户权限来执行 resourceSACL 操作。 但是，此权限允许执行删除操作所不需要的其他访问权限。

## <a name="examples"></a><a name=BKMK_Examples></a>示例

将全局资源 SACL 设置为审核用户对注册表项的成功访问尝试：

```
auditpol /resourceSACL /set /type:Key /user:MYDOMAIN\myuser /success
```

若要将全局资源 SACL 设置为审核用户对文件或文件夹执行一般的读取和写入功能的成功和失败尝试：

```
auditpol /resourceSACL /set /type:File /user:MYDOMAIN\myuser /success /failure /access:FRFW
```

删除文件或文件夹的所有全局资源 SACL 条目：

```
auditpol /resourceSACL /type:File /clear
```

从文件或文件夹删除特定用户的所有全局资源 SACL 条目：

```
auditpol /resourceSACL /remove /type:File /user:{S-1-5-21-56248481-1302087933-1644394174-1001}
```

列出对文件或文件夹设置的全局对象访问审核条目：

```
auditpol /resourceSACL /type:File /view
```

列出对文件或文件夹设置的特定用户的全局对象访问审核条目：

```
auditpol /resourceSACL /type:File /view /user:MYDOMAIN\myuser
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)