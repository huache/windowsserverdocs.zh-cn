---
title: wbadmin delete catalog
description: 用于 wbadmin delete catalog 的参考文章，用于删除存储在本地计算机上的备份目录。
ms.topic: reference
ms.assetid: d3041407-4577-4716-a39f-2c8ab48818d1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b238e43eac784607a8f42175023eca88e13f2bfd
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89022821"
---
# <a name="wbadmin-delete-catalog"></a>wbadmin delete catalog



删除存储在本地计算机上的备份目录。 当备份目录已损坏且无法使用 **wbadmin restore catalog**还原它时，请使用此命令。

若要使用此子命令删除备份目录，您必须是 **Backup Operators** 组或 **Administrators** 组的成员，或者您必须被委派了适当的权限。 此外，必须在提升的命令提示符下运行 **wbadmin** 。  (打开提升的命令提示符，右键单击 " **命令提示符**"，然后单击 "以 **管理员身份运行**"。 ) 

## <a name="syntax"></a>语法

```
wbadmin delete catalog
[-quiet]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|-quiet|对用户运行无提示的子命令。|

## <a name="remarks"></a>注解

如果删除计算机的备份目录，将无法使用 "Windows Server 备份" 管理单元访问该计算机创建的备份。 在这种情况下，如果可以访问其他备份位置，请使用 **wbadmin restore catalog** 从该位置还原备份目录。 删除备份目录后，应创建新的备份。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
-   [Backup](wbadmin.md)
-   [WBCatalog](/powershell/module/windowserverbackup/?view=winserver2012r2-ps)
