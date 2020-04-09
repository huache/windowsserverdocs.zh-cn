---
title: bitsadmin getproxybypasslist
description: 适用于**bitsadmin getproxybypasslist**的 Windows 命令主题，它检索指定作业的代理跳过列表。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9cd81aaef22c4173f198b765246b78b3d3bae136
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80850530"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

检索指定作业的代理跳过列表。

## <a name="syntax"></a>语法

```
bitsadmin /getproxybypasslist <job>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| -------------- | -------------- |
| 作业 | 作业的显示名称或 GUID。 |

## <a name="remarks"></a>备注

旁路列表包含不是通过代理路由的主机名或 IP 地址。 此列表可以包含引用同一 LAN 上所有服务器的 `<local>`。 列表可以为分号（;)或以空格分隔。

## <a name="examples"></a><a name=BKMK_examples></a>示例

下面的示例检索名为*myDownloadJob*的作业的代理跳过列表。

```
C:\>bitsadmin /getproxybypasslist myDownloadJob
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)