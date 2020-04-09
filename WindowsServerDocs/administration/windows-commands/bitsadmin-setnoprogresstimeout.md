---
title: bitsadmin setnoprogresstimeout
description: 适用于 bitsadmin setnoprogresstimeout 的 Windows 命令主题，用于设置服务在发生暂时性错误后尝试传输文件的时间长度（以秒为单位）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 544a6c73f29684bc4091ec05fa28016fbc718bb2
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849350"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

设置在第一次发生暂时性错误后 BITS 尝试传输文件的时间长度（以秒为单位）。

## <a name="syntax"></a>语法

```
bitsadmin /SetNoProgressTimeout <Job> <TimeOutvalue>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|TimeOutvalue|以秒表示的数字。|

## <a name="remarks"></a>备注

-   如果作业遇到暂时性错误，则不会开始任何进度超时时间间隔。
-   成功传输字节的数据后，超时间隔将停止或重置。
-   如果没有进度超时间隔超过*TimeOutvalue*，则作业将置于严重错误状态。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将名为*myDownloadJob*的作业的无进度超时值设置为20秒
```
C:\>bitsadmin /SetNoProgressTimeout myDownloadJob 20
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)