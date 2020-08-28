---
title: uniqueid
description: 适用于 uniqueid 的参考文章，其中显示或设置 GUID 分区表 (GPT) 标识符或主启动记录 (MBR) 签名与具有焦点的磁盘相同。
ms.topic: reference
ms.assetid: 64235a4a-b91c-46da-b9b0-68ee90571c2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 42b3bcc50ad5f13a941a0ff81a7c74f40b45b48d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032192"
---
# <a name="uniqueid"></a>uniqueid

显示或设置 GUID 分区表 (GPT) 标识符或主启动记录 (MBR 的主) 签名。

> [!IMPORTANT]
> 在任何版本的 Windows Vista 中，此 DiskPart 命令均不可用。

## <a name="syntax"></a>语法

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

### <a name="parameters"></a>参数

|  参数   |                                                                                             说明                                                                                              |
|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id = {\<dword> |                                                                                               <GUID>}                                                                                                |
|    noerr     | 仅用于脚本。 出现错误时，DiskPart 继续处理命令，就像未发生错误一样。 如果没有此参数，则错误会导致 DiskPart 退出并出现错误代码。 |

## <a name="remarks"></a>注解

-   此命令适用于基本磁盘和动态磁盘。
-   必须选择磁盘才能使此命令成功。 使用 " **选择磁盘** " 命令选择磁盘，并将焦点移动到该磁盘。

## <a name="examples"></a>示例

若要显示具有焦点的 MBR 磁盘的签名，请键入：
```
uniqueid disk
```
若要将具有焦点的 MBR 磁盘的签名设置为5f1b2c36，请键入：
```
uniqueid disk id=5f1b2c36
```
若要将具有焦点的 GPT 磁盘的标识符设置为 baf784e7-6bbd-4cfb-aaac-e86c96e166ee，请键入：
```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

## <a name="additional-references"></a>其他参考

