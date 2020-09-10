---
title: nslookup ls
description: 用于列出 DNS 域信息的 nslookup ls 命令的参考文章。
ms.topic: reference
ms.assetid: f15f06fe-67e7-41a9-93b5-192ab14ab380
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6910fa753ff394416f1cbf201db690647cebe9a0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635680"
---
# <a name="nslookup-ls"></a>nslookup ls

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

列出 DNS 域信息。

## <a name="syntax"></a>语法

```
ls [<option>] <DNSdomain> [{[>] <filename>|[>>] <filename>}]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<option>` | 有效选项包括：<ul><li>**-t：** 列出指定类型的所有记录。 有关详细信息，请参阅 [nslookup set querytype](nslookup-set-querytype.md)。</li><li>**-a：** 列出 DNS 域中计算机的别名。 此参数与 **-t CNAME**相同</li><li>**-d：** 列出 DNS 域的所有记录。 此参数与 **-t ANY**相同</li><li>**-h：** 列出 DNS 域的 CPU 和操作系统信息。 此参数与 **-t HINFO**相同</li><li>**-s：** 列出 DNS 域中计算机的已知服务。 此参数与 **-t WKS**相同。 |
| `<DNSdomain>` | 指定要获取其信息的 DNS 域。 |
| `<filename>` | 指定用于保存的输出的文件名。 您可以使用大于 (`>`) 和双大于 (`>>`) 字符，以常规方式重定向输出。 |
| /? | 在命令提示符下显示帮助。 |
| /help | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- 此命令的默认输出包括计算机名称及其关联的 IP 地址。

- 如果将输出定向到文件，则会为从服务器接收的每个50记录添加哈希标记。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [nslookup set querytype](nslookup-set-querytype.md)
