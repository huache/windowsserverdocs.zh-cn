---
title: bitsadmin setcustomheaders
description: 适用于 bitsadmin setcustomheaders 的 Windows 命令主题，该主题将自定义 HTTP 标头添加到 GET 请求。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e5d97fae5f84637c80c3d1ef00aa36f09049bb17
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849610"
---
# <a name="bitsadmin-setcustomheaders"></a>bitsadmin setcustomheaders

向 GET 请求添加自定义 HTTP 标头。

## <a name="syntax"></a>语法

```
bitsadmin /SetCustomHeaders <Job> <Header1> <Header2> <. . .>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|Header1 .Header2。 . .|作业的自定义标头|

## <a name="remarks"></a>备注

-   此开关用于向发送到 HTTP 服务器的 GET 请求添加自定义 HTTP 标头。

## <a name="examples"></a><a name=BKMK_examples></a>示例

以下示例添加名为*myDownloadJob*的作业的自定义 HTTP 标头。
```
C:\>bitsadmin / SetCustomHeaders myDownloadJob Accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)