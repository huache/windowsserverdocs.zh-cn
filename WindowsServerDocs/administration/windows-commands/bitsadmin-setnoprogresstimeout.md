---
title: bitsadmin setnoprogresstimeout
description: Bitsadmin setnoprogresstimeout 命令的参考文章，用于设置服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。
ms.topic: reference
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc2559a963900234fd3111edb1a32e3f13b27e40
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027795"
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

### <a name="remarks"></a>注解

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
