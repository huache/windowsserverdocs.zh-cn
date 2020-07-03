---
title: bitsadmin setsecurityflags
description: Bitsadmin setsecurityflags 命令的参考文章，用于设置 HTTP 的安全标志，以确定 BITS 应检查证书吊销列表、忽略某些证书错误，并定义服务器重定向 HTTP 请求时要使用的策略。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0da5cbf5-5f7f-4833-bbbe-c4e8379a78ab
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f6030316396e64c9884d6df9b56d5489ec2c6318
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85927503"
---
# <a name="bitsadmin-setsecurityflags"></a>bitsadmin setsecurityflags

设置 HTTP 的安全标志，以确定 BITS 应检查证书吊销列表、忽略某些证书错误，并定义服务器重定向 HTTP 请求时要使用的策略。 该值是一个无符号整数。

## <a name="syntax"></a>语法

```
bitsadmin /setsecurityflags <job> <value>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 (job) | 作业的显示名称或 GUID。 |
| 值 | 可以包含以下一个或多个通知标志，其中包括：<ul><li>将最小有效位设置为启用 CRL 检查。</li><li>将第二个位设置为从右到忽略服务器证书中不正确的公用名。</li><li>将第三位设置为从右到忽略服务器证书中的错误日期。</li><li>将第四位设置为 "忽略服务器证书中的错误证书颁发机构"。</li><li>设置从右侧的第5位以忽略服务器证书的不正确用法。</li><li>设置从右侧开始的第9位到第11位以实现指定的重定向策略，包括：<ul><li>**0，0，0。** 自动允许重定向。</li><li>**0，0，1。** 如果发生重定向，则会更新**IBackgroundCopyFile**接口中的远程名称。</li><li>**0，1，0。** 如果发生重定向，则 BITS 会失败。</li></ul></li><li>将第12位设置为允许从 HTTPS 重定向到 HTTP。</li></ul> |

## <a name="examples"></a>示例

若要设置安全标志来启用对名为*myDownloadJob*的作业的 CRL 检查，请执行以下操作：

```
bitsadmin /setsecurityflags myDownloadJob 0x0001
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
