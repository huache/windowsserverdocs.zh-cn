---
title: tcmsetup
description: 了解如何设置和禁用 TAPI 客户端。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 15e0c10f-996f-4301-92e5-943f7ee8212d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: bbfc9a0238d258f11233b0e48a30048c1d62cef4
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80833410"
---
# <a name="tcmsetup"></a>tcmsetup



设置或禁用 TAPI 客户端。

## <a name="syntax"></a>语法

```
tcmsetup [/q] [/x] /c <Server1> [<Server2> …] 
tcmsetup  [/q] /c /d
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/q|阻止显示消息框。|
|/x|指定针对流量过大的网络中频繁丢失数据包的情况，将使用面向连接的回拨。 如果忽略该参数，将使用无连接回拨。|
|/c|必需。 指定客户端设置。|
|\<Server1 >|必需。 指定包含客户端将使用的 TAPI 服务提供程序的远程服务器的名称。 客户端将使用服务提供商的线路和电话。 该客户端必须与服务器位于同一域中，或位于与包含该服务器的域具有双向信任关系的域中。|
|\<Server2 > 。|指定任何其他服务器，或可用于该客户端的服务器。 如果指定的是服务器列表，则使用空格分隔服务器名称。|
|/d|清除远程服务器列表。 通过阻止 TAPI 客户端使用远程服务器上的 TAPI 服务提供程序，可以禁用该 TAPI 客户端。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   若要执行此过程，您必须是本地计算机上“Administrators”组的成员或者必须被委派了适当的授权。 如果计算机已加入某个域，则“Domain Admins”组的成员也许能够执行此过程。 作为安全方面的最佳做法，请考虑使用“运行方式”来执行该过程。
-   为了使 TAPI 正常运行，必须运行**tcmsetup**来指定 tapi 客户端将使用的远程服务器。
-   在客户端用户可以使用 TAPI 服务器上的电话或线路之前，电话服务器管理员必须将该用户分配到电话号码或线路。
-   该命令创建的电话服务器列表会替换客户端可使用的所有现有的电话服务器列表。 无法使用该命令将电话服务器添加到现有列表。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

[命令外壳概述](https://technet.microsoft.com/library/cc737438(v=ws.10).aspx)

[指定客户端计算机上的电话服务器](https://technet.microsoft.com/library/cc759226(v=ws.10).aspx)

[将电话服务用户分配给线路或电话](https://technet.microsoft.com/library/cc736875(v=ws.10).aspx)

