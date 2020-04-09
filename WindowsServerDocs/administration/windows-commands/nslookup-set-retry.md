---
title: nslookup set retry
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b95c4c8af2d7960270fd43f7a766b313ddbc07a
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838340"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

设置重试次数。
## <a name="syntax"></a>语法
```
set retry=<Number>
```
### <a name="parameters"></a>参数

|    参数    |                                      说明                                       |
|-----------------|----------------------------------------------------------------------------------------|
|    <Number>     | 指定重试次数的新值。 默认重试次数为4。 |
| {help &#124; ？} |                 显示**nslookup**子命令的简短摘要。                  |

## <a name="remarks"></a>备注
- 如果在特定时间段内未收到请求的答复，则超时期限将加倍，并重新发送请求。 重试值控制在放弃请求之前重新发送请求的次数。 您可以通过**设置超时**子命令更改超时期限。
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [nslookup 设置超时](nslookup-set-timeout.md)
