---
title: HTTP 1.1/2 性能优化
description: 针对 HTTP 1.1/2 的性能优化建议
ms.topic: article
ms.author: ivanpash; gmonte
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: 362ceea398e13c5e537d1d828b86eec8b5d66a8f
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87896024"
---
# <a name="performance-tuning-http-112"></a>性能优化 HTTP 1.1/2

HTTP/2 旨在提高客户端的性能 (例如，浏览器) 上的页面加载时间。 在服务器上，这可能表示 CPU 开销略有增加。 服务器不再需要针对每个请求建立单个 TCP 连接，而其中的某些状态现在将保留在 HTTP 层中。 此外，HTTP/2 还具有标头压缩，表示额外的 CPU 负载。

某些情况下，需要 HTTP/1.1 回退 (重置 HTTP/2 连接，而是建立新的连接以使用 HTTP/1.1) 。 具体而言，TLS 重新协商和 HTTP 身份验证 (基本和摘要式) 不需要 HTTP/1.1 回退。 尽管这会增加开销，但这些操作已经意味着一些延迟，因此不会特别影响性能。

## <a name="additional-references"></a>其他参考
- [Web 服务器性能优化](index.md)
- [IIS 10.0 性能优化](tuning-iis-10.md)