---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: 域控制器位置
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: ada91f7205ba12e4d37a02e3503647c9560ccdd8
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939267"
---
# <a name="domain-controller-location"></a>域控制器位置

>适用于：Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

客户端使用域名系统 (DNS) 查找域控制器以完成操作，如处理登录请求或搜索已发布资源的目录。 域控制器在 DNS 中注册各种记录，以帮助客户端和其他计算机查找它们。 这些记录统称为定位符记录。

域控制器还使用 DNS 查找其他域控制器并执行复制等任务。 域控制器查找其他域控制器的过程与客户端查找域控制器的过程相同。



