---
title: AD FS 故障排除-AD FS 终结点
description: 本文档介绍如何对 AD FS 终结点进行故障排除
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/03/2017
ms.topic: article
ms.openlocfilehash: 7739093e483e8f797e87259c176ff3c92514903d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87954163"
---
# <a name="ad-fs-troubleshooting---ad-fs-metadata-endpoints"></a>AD FS 故障排除-AD FS 元数据终结点
终结点提供对 AD FS 的联合服务器功能的访问，如发布联合元数据。  若要验证 AD FS 服务器是否正在响应 web 请求，可以检查各种终结点。


## <a name="federation-metadata-test"></a>联合元数据测试
被动联合是指你的浏览器重新定向到 AD FS 登录页的方案。  通过测试元数据终结点，我们可以确定在这些被动方案中 AD FS 服务器是否响应 web 请求。  使用以下过程来测试终结点。

1.  使用 web 浏览器导航到 AD FS 联合元数据终结点。  例如：https://sts.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
2. 该 xml 文件应该在本地下载到您的计算机上。
3. 打开它并验证它是否包含类似于下面的信息的信息： ![ 被动](media/ad-fs-tshoot-endpoints/meta2.png)

## <a name="ws-mex-test-active-test"></a>WS MEX 测试 (活动测试) 
Ws-metadataexchange 是一种 web 服务协议，属于 WS 联合身份验证路线图。  它使用 SOAP 消息来请求元数据。  通过测试终结点，我们可以确定 AD FS 服务器是否响应 Ws-metadataexchange 的 web 请求。  使用以下过程来测试终结点。
1.  使用 web 浏览器导航到 AD FS 联合元数据终结点。  例如：https://sts.contoso.com/adfs/services/trust/mex
2. 该 xml 文件应在浏览器中自动显示。  它应该如下图所示：

![活动](media/ad-fs-tshoot-endpoints/meta3.png)


## <a name="next-steps"></a>后续步骤

- [AD FS 疑难解答](ad-fs-tshoot-overview.md)