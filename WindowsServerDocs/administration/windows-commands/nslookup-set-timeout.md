---
title: nslookup set timeout
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8506511fc203f94d395851471f6a981ef0765928
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80838270"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

>适用于：Windows Server（半年频道）、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

更改等待查找请求回复的初始秒数。
## <a name="syntax"></a>语法
```
set timeout=<Number>
```
### <a name="parameters"></a>参数

|    参数    |                                           说明                                            |
|-----------------|--------------------------------------------------------------------------------------------------|
|    <Number>     | 指定等待答复的秒数。 默认等待的秒数为5。 |
| {help &#124; ？} |                      显示**nslookup**子命令的简短摘要。                       |

## <a name="remarks"></a>备注
- 如果在指定的时间段内未收到对请求的答复，则超时将加倍，并再次发送请求。 你可以使用 "**设置重试**" 命令来控制重试的次数。
  ## <a name="examples"></a><a name=BKMK_examples></a>示例
  下面的示例将获取响应的超时时间设置为2秒：
  ```
  set timeout=2
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法键](command-line-syntax-key.md)
  [nslookup 设置重试](nslookup-set-retry.md)
