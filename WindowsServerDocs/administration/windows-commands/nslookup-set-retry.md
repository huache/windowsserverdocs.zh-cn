---
title: nslookup set retry
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1baeeaefedc211434f46bd0cfad713f093a873bf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723587"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

设置重试次数。
## <a name="syntax"></a>语法
```
set retry=<Number>
```
### <a name="parameters"></a>参数

|    参数    |                                      描述                                       |
|-----------------|----------------------------------------------------------------------------------------|
|    <Number>     | 指定重试次数的新值。 默认重试次数为4。 |
| {help &#124;？} |                 显示**nslookup**子命令的简短摘要。                  |

## <a name="remarks"></a>备注
- 如果在特定时间段内未收到请求的答复，则超时期限将加倍，并重新发送请求。 重试值控制在放弃请求之前重新发送请求的次数。 您可以通过**设置超时**子命令更改超时期限。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法 Key](command-line-syntax-key.md)
  [nslookup 设置超时](nslookup-set-timeout.md)
