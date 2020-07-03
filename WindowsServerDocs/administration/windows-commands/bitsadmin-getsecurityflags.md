---
title: bitsadmin getsecurityflags
description: Bitsadmin getsecurityflags 命令的参考文章，用于报告传输过程中在服务器证书上执行的 URL 重定向和检查的 HTTP 安全标志。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8613f2bd293bdbf7680aa730ec6fc222ffcfe158
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85926683"
---
# <a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

报告在传输过程中对服务器证书执行的 URL 重定向和检查的 HTTP 安全标志。

## <a name="syntax"></a>语法

```
bitsadmin /getsecurityflags <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |

## <a name="examples"></a>示例

若要从名为*myDownloadJob*的作业中检索安全标志：

```
bitsadmin /getsecurityflags myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
