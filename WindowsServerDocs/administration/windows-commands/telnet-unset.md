---
title: 未设置 telnet
description: Telnet unset 的参考主题，这会关闭先前设置的选项。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09 vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c121d6501f87ae1218381871bcbf536d9407ba31
ms.sourcegitcommit: 4f407b82435afe3111c215510b0ef797863f9cb4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2020
ms.locfileid: "83821037"
---
# <a name="telnet-unset"></a>telnet： unset

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

关闭先前设置的选项。

## <a name="syntax"></a>语法
```
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|bsasdel|以**backspace**形式发送**backspace** 。|
|crlf|以 CR 形式发送**Enter**键。 也称为 "换行符" 模式。|
|delasbs|将**删除**作为**删除**发送。|
|转义符|删除转义符设置。|
|localecho|关闭 localecho。|
|logging|关闭日志记录功能。|
|ntlm|关闭 NTLM 身份验证。|
|?|显示此命令的帮助。|
## <a name="examples"></a>示例
关闭日志记录。
```
u logging
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
