---
title: bitsadmin setcredentials
description: 适用于 bitsadmin setcredentials 的 Windows 命令主题，用于将凭据添加到作业。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 3cd099a4-9e85-46d8-8527-edb6dfab7f97
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 918bda93407e029cedaaf5eab937d1bb23dc3c4c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80849640"
---
# <a name="bitsadmin-setcredentials"></a>bitsadmin setcredentials

向作业添加凭据。

**BITS 1.2 及更早版本**：不支持。

## <a name="syntax"></a>语法

```
bitsadmin /SetCredentials <Job> <Target> <Scheme> <Username> <Password>
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|作业|该作业的显示名称或 GUID|
|目标|服务器或代理|
|机制|下列情况之一：</br>-基本-身份验证方案，在此方案中，用户名和密码以明文形式发送到服务器或代理。</br>-摘要-一种质询-响应身份验证方案，该方案将服务器指定的数据字符串用于质询。</br>-NTLM-一种质询-响应身份验证方案，该方案使用用户的凭据在 Windows 网络环境中进行身份验证。</br>-NEGOTIATE，也称为简单和受保护的协商协议（Snego）是一种质询响应身份验证方案，该方案与服务器或代理协商以确定要用于身份验证的方案。 例如，Kerberos 协议和 NTLM。</br>-PASSPORT — Microsoft 提供的一种集中式身份验证服务，可为成员站点提供单一登录。|
|Username|提供的凭据的名称|
|密码|与提供的*用户名*关联的密码|

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例将凭据添加到名为*myDownloadJob*的作业。
```
C:\>bitsadmin /RemoveCredentials myDownloadJob SERVER BASIC Edward Password20
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)