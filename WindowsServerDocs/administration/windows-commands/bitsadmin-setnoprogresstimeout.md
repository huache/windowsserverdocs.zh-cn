---
title: bitsadmin setnoprogresstimeout
description: Bitsadmin setnoprogresstimeout 命令的参考文章，用于设置服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。
ms.topic: reference
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9ffe7280e6a27d1fbc8a95b6b4c8375a8df844f8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630800"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

设置在第一次发生暂时性错误后 BITS 尝试传输文件的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /setnoprogresstimeout <job> <timeoutvalue>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| timeoutvalue | 在第一个错误后 BITS 等待传输文件的时间长度（以秒为单位）。 |

### <a name="remarks"></a>备注

- 作业遇到第一个暂时性错误时，"无进度" 超时间隔就会开始。

- 成功传输字节的数据后，超时间隔将停止或重置。

- 如果 "无进度" 超时间隔超过 *timeoutvalue*，则作业将置于严重错误状态。

## <a name="examples"></a>示例

若要将名为 *myDownloadJob*的作业的 "无进度" 超时值设置为20秒，请执行以下操作：

```
bitsadmin /setnoprogresstimeout myDownloadJob 20
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
