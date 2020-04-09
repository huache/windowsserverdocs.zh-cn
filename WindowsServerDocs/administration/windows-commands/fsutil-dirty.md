---
ms.assetid: 385a2a7c-d6bd-4f11-9c18-fca0413f9e97
title: Fsutil 脏
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: cf3685bae9ed76ede4da6df244139437d92250c0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80844330"
---
# <a name="fsutil-dirty"></a>Fsutil 脏
>适用于： Windows Server （半年频道），Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8，Windows Server 2008 R2，Windows 7

查询或设置卷的未更新位。 如果设置了卷的未更新位，则在下次重新启动计算机时， **autochk**会自动检查卷中是否存在错误。

有关如何使用此命令的示例，请参阅[示例](#BKMK_examples)。

## <a name="syntax"></a>语法

```
fsutil dirty {query | set} <VolumePath>
```

### <a name="parameters"></a>参数

|   参数   |                                                 说明                                                  |
|---------------|--------------------------------------------------------------------------------------------------------------|
|     query     |                                  查询指定卷的已更新位。                                   |
|      set      |                                    设置指定卷的未更新位。                                    |
| \<VolumePath > | 用以下格式指定驱动器名称后跟冒号或 GUID： **Volume {** <em>GUID</em> **}** 。 |

## <a name="remarks"></a>备注

-   卷的未更新位表示文件系统可能处于不一致的状态。 可以设置脏位，因为：

    -   卷处于联机状态，它有未完成的更改。

    -   对卷进行了更改，并且计算机在将更改提交到磁盘之前已关闭。

    -   在卷上检测到损坏。

-   如果在计算机重新启动时设置了脏位， **chkdsk**将运行以验证文件系统的完整性，并尝试修复卷的任何问题。

## <a name="examples"></a><a name="BKMK_examples"></a>示例
若要查询驱动器 C 上的脏位，请键入：

```
fsutil dirty query c:
```

-   如果卷处于脏区，则会显示以下输出：

    `Volume C: is dirty`

-   如果卷未更新，则会显示以下输出：

    `Volume C: is not dirty`

若要设置驱动器 C 上的脏位，请键入：

```
fsutil dirty set C:
```

## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

[Fsutil](Fsutil.md)


