---
title: nslookup set srchlist
description: Nslookup set srchlist 命令的参考文章，可更改默认域名系统（DNS）域名和搜索列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5d43107ed2c777349a8cac1a0411c035371bc0f7
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85930412"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

更改默认的域名系统（DNS）域名和搜索列表。 此命令替代[nslookup set 域](nslookup-set-domain.md)命令的默认 DNS 域名和搜索列表。

## <a name="syntax"></a>语法

```
set srchlist=<domainname>[/...]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<domainname>` | 为默认 DNS 域和搜索列表指定新名称。 默认域名值基于主机名。 最多可以指定六个用斜杠（/）分隔的名称。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 使用[nslookup "全部设置](nslookup-set-all.md)" 命令来显示列表。

### <a name="examples"></a>示例

若要将 DNS 域设置为*mfg.widgets.com* ，并将搜索列表设置为三个名称：

```
set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set domain](nslookup-set-domain.md)

- [nslookup set all](nslookup-set-all.md)
