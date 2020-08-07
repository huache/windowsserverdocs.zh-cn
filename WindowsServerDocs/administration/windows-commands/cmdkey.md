---
title: cmdkey
description: 用于创建、列出和删除存储的用户名和密码或凭据的 cmdkey 命令的参考文章。
ms.topic: article
ms.assetid: 5fcd68ee-a14a-4b71-9300-c3f5c5d31e8e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d7194b19231209150197fbc4c20175b319da77cd
ms.sourcegitcommit: 53d526bfeddb89d28af44210a23ba417f6ce0ecf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87880067"
---
# <a name="cmdkey"></a>cmdkey

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建、列出并删除存储的用户名和密码或凭据。

## <a name="syntax"></a>语法

```
cmdkey [{/add:<targetname>|/generic:<targetname>}] {/smartcard | /user:<username> [/pass:<password>]} [/delete{:<targetname> | /ras}] /list:<targetname>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| ---------- | ----------- |
| /add`<targetname>` | 向列表添加用户名和密码。<p>需要的参数 `<targetname>` 标识此项将与之关联的计算机或域名。 |
| /常规`<targetname>` | 向列表中添加一般凭据。<p>需要的参数 `<targetname>` 标识此项将与之关联的计算机或域名。 |
| /smartcard | 从智能卡中检索凭据。 如果在使用此选项时系统上找到了多个智能卡，则**cmdkey**将显示所有可用智能卡的相关信息，然后提示用户指定要使用的智能卡。 |
| /user:`<username>` | 指定要与此条目一起存储的用户或帐户名称。 如果 `<username>` 未提供，则会请求它。 |
|/pass`<password>` | 指定要与此项一起存储的密码。 如果 `<password>` 未提供，则会请求它。 密码在存储后不会显示。 |
| /delete{:`<targetname>` | ra | 从列表中删除用户名和密码。 如果 `<targetname>` 指定了，则会删除该条目。 如果 `/ras` 指定，则删除存储的远程访问条目。 |
| /list`<targetname>` | 显示存储的用户名和凭据的列表。 如果 `<targetname>` 未指定，则会列出所有存储的用户名和凭据。 |
| /? | 在命令提示符下显示帮助。 |

## <a name="examples"></a>示例

若要显示所有已存储用户名和凭据的列表，请键入：

```
cmdkey /list
```

若要为用户*Mikedan*添加用户名和密码，以便使用 password *Kleo*访问计算机*Server01* ，请键入：

```
cmdkey /add:server01 /user:mikedan /pass:Kleo
```

若要为用户*Mikedan*添加用户名和密码以访问计算机*Server01* ，并在访问 Server01 时提示输入密码，请键入：

```
cmdkey /add:server01 /user:mikedan
```

若要删除远程访问存储的凭据，请键入：

```
cmdkey /delete /ras
```

若要删除为*Server01*存储的凭据，请键入：

```
cmdkey /delete:server01
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
