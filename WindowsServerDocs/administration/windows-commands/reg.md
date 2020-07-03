---
title: reg
description: 用于对注册表项中的注册表子项信息和值执行操作的 reg 命令的参考文章。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c97496b2-d1ff-4887-b5d2-6e1524be465a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47ceea315b3d172c766e749e3447f56907eab945
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85931024"
---
# <a name="reg"></a>reg

对注册表项中的注册表子项信息和值执行操作。

某些操作使你可以查看或配置本地或远程计算机上的注册表项，其他一些操作允许你仅配置本地计算机。 使用**reg**配置远程计算机的注册表限制了可在某些操作中使用的参数。 检查每个操作的语法和参数，验证它们是否可用于远程计算机。

> [!CAUTION]
> 不要直接编辑注册表，除非没有替代方法。 注册表编辑器会绕过标准安全措施，同时允许可能降低性能的设置、损坏系统，甚至要求你重新安装 Windows。 可以通过使用 "控制面板" 或 "Microsoft 管理控制台（MMC）" 中的 "程序" 来安全地更改大多数注册表设置。 如果必须直接编辑注册表，请首先对其进行备份。

## <a name="syntax"></a>语法

```
reg add
reg compare
reg copy
reg delete
reg export
reg import
reg load
reg query
reg restore
reg save
reg unload
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| [reg add](reg-add.md) | 向注册表中添加新的子项或条目。 |
| [reg compare](reg-compare.md) | 比较指定的注册表子项或条目。 |
| [reg copy](reg-copy.md) | 将注册表项复制到本地或远程计算机上的指定位置。 |
| [reg delete](reg-delete.md) | 删除注册表中的一个或一些项。 |
| [reg export](reg-export.md) | 将本地计算机的指定子项、项和值复制到文件中，以便传输到其他服务器。 |
| [reg import](reg-import.md) | 将包含导出的注册表子项、项和值的文件的内容复制到本地计算机的注册表中。 |
| [reg load](reg-load.md) | 将保存的子项和项写入注册表中的不同子项。 |
| [reg query](reg-query.md) | 返回位于注册表中指定子项下的子子项和条目的列表。 |
| [reg restore](reg-restore.md) | 将保存的子项和项写入注册表。 |
| [reg save](reg-save.md) | 在指定的文件中保存指定子项、项和注册表值的副本。 |
| [reg unload](reg-unload.md) | 删除使用**reg load**操作加载的注册表部分。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
