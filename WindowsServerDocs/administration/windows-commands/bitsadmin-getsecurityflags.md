---
title: bitsadmin getsecurityflags
description: 适用于**bitsadmin getsecurityflags**的 Windows 命令主题，用于报告传输过程中在服务器证书上执行的 URL 重定向和检查的 HTTP 安全标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 360f8d5514e5251dd9e4a6a6b60335dc34fe4415
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850470"
---
# <a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

报告在传输过程中对服务器证书执行的 URL 重定向和检查的 HTTP 安全标志。

## <a name="syntax"></a>语法

```
bitsadmin /getsecurityflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例从名为*myDownloadJob*的作业中检索安全标志。

```
C:\>bitsadmin /getsecurityflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)