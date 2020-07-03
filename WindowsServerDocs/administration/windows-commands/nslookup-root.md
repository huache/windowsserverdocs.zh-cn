---
title: nslookup root
description: Nslookup 根命令的参考文章，它将默认服务器更改为域名系统（DNS）域名空间的根的服务器。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 07dbfcf401314145cb0e7553d71480072da4b574
ms.sourcegitcommit: 2afed2461574a3f53f84fc9ec28d86df3b335685
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85936281"
---
# <a name="nslookup-root"></a>nslookup root

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

将服务器的默认服务器更改为域名系统（DNS）域名空间的根。 目前，使用了 ns.nic.ddn.mil 名称服务器。 可以使用[nslookup set root](nslookup-set-root.md)命令更改根服务器的名称。

> [!NOTE]
> 此命令与相同 `lserver ns.nic.ddn.mil` 。

## <a name="syntax"></a>语法

```
root
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set root](nslookup-set-root.md)
