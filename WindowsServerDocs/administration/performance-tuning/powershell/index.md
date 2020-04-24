---
title: PowerShell 的性能优化
description: PowerShell 的性能优化
ms.prod: windows-server
ms.technology: performance-tuning-guide
ms.topic: landing-page
ms.author: jasonsh
author: lzybkr
ms.date: 10/16/2017
ms.openlocfilehash: 382305e2bd15ef6fcb038c3fa064bc2841eabae1
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80851950"
---
# <a name="performance-tuning-for-powershell"></a>PowerShell 的性能优化

本文档讨论了用于实现 PowerShell 5.1 的最佳可能性能的一般指南。 本文档中所述的一些问题在将来的版本中可能会解决。

本文档未介绍最佳做法。

应用本文档中的指南时应当考虑周密。
* 性能通常不是问题，节省 10 毫秒或 100 毫秒可能完全不会被注意到。
* 本文档中的一些指导介绍了某些 PowerShell 用户可能会混淆且不熟悉的非典型 PowerShell 用法。

以下主题提供了具体指南。

-   [脚本创作注意事项](script-authoring-considerations.md)

-   [模块创作注意事项](module-authoring-considerations.md)