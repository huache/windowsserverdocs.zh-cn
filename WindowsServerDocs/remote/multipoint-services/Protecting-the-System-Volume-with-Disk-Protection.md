---
title: 通过磁盘保护保护系统卷
description: 提供有关 MultiPoint 服务的磁盘保护的信息
ms.date: 07/22/2016
ms.topic: article
ms.assetid: 18694665-ed65-4d84-8505-f460cf3df907
author: evaseydl
manager: scotman
ms.author: evas
ms.openlocfilehash: aae561dc506ea75d25229a66b1e2a25ed41ccc17
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87953793"
---
# <a name="protecting-the-system-volume-with-disk-protection"></a>通过磁盘保护保护系统卷
MultiPoint 服务提供了一个选项，用于在每次启动计算机时立即清除对系统卷所做的任何更改。 如果启用磁盘保护功能，则在下次重新启动计算机时，将撤消对驱动器的任何修改，例如配置损坏或恶意软件引入。 对于希望确保每次加载已知的 "良好" 或 "黄金" 软件映像的管理员来说，这是一项便利的功能。 可以安排自动更新或软件修补，例如，在晚上中期。 规划注意事项是您是否希望最终用户能够从 Internet 进行更改，如安装软件。 启用此功能后，如果你希望用户能够存储文件，则文件共享需要位于系统卷之外。

