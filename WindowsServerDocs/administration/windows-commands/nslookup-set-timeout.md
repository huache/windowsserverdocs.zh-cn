---
title: nslookup set timeout
description: '* * * * 的参考主题'
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 68e9630b9690c9b6c9d4c316f8b328897289362c
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82723545"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改等待查找请求回复的初始秒数。
## <a name="syntax"></a>语法
```
set timeout=<Number>
```
### <a name="parameters"></a>参数

|    参数    |                                           描述                                            |
|-----------------|--------------------------------------------------------------------------------------------------|
|    <Number>     | 指定等待答复的秒数。 默认等待的秒数为5。 |
| {help &#124;？} |                      显示**nslookup**子命令的简短摘要。                       |

## <a name="remarks"></a>备注
- 如果在指定的时间段内未收到对请求的答复，则超时将加倍，并再次发送请求。 你可以使用 "**设置重试**" 命令来控制重试的次数。
  ## <a name="examples"></a>示例
  若要设置将响应时间设置为2秒的超时值：
  ```
  set timeout=2
  ```
  ## <a name="additional-references"></a>其他参考
  - [命令行语法密钥](command-line-syntax-key.md)
  [nslookup 设置重试](nslookup-set-retry.md)
