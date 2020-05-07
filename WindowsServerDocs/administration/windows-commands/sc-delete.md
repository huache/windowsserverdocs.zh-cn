---
title: Sc.exe delete
description: 了解如何使用 sc.exe 实用程序注销服务
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 284012cf6799df52832e62c3eea1b2f0fcd84805
ms.sourcegitcommit: 95b60384b0b070263465eaffb27b8e3bb052a4de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2020
ms.locfileid: "82850108"
---
# <a name="scexe-delete"></a>Sc.exe delete

从注册表中删除服务子项。 如果服务正在运行，或者如果另一个进程具有该服务的打开句柄，则该服务将标记为删除。

有关如何使用此命令的示例，请参阅[示例](#examples)。

## <a name="syntax"></a>语法

```
sc.exe [<ServerName>] delete [<ServiceName>]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<ServerName>|指定服务所在的远程服务器的名称。 名称必须使用通用命名约定（UNC）格式（例如， \\ \\myserver）。 若要在本地运行 SC.EXE，请省略此参数。|
|\<ServiceName>|指定**getkeyname**操作返回的服务名称。|
|?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

不建议使用 sc.exe 删除内置的操作系统服务，例如 DHCP、DNS 或 Internet Information Services。 若要安装、删除或重新配置操作系统角色、服务和组件，请参阅[安装或卸载角色、角色服务或功能](/WindowsServerDocs/administration/server-manager/install-or-uninstall-roles-role-services-or-features.md)

## <a name="examples"></a>示例

若要从本地计算机上的注册表中删除服务子项**NewServ** ，请键入：
```
sc.exe delete newserv
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
