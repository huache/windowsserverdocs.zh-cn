---
title: MultiPoint 服务-迁移后任务
description: 了解如何验证和关闭到 MultiPoint 服务的迁移
ms.date: 07/29/2016
ms.topic: article
ms.assetid: 1497cae0-071e-467d-89b8-a7050815d7de
author: lizap
manager: dongill
ms.openlocfilehash: ed3937cd6830de642c21616071e86eca3ad6cd5b
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969244"
---
# <a name="multipoint-services---post-migration-tasks"></a>MultiPoint 服务-迁移后任务

>适用于：Windows Server 2016

迁移到 Windows Server 2016 中的 MultiPoint 服务后，请使用以下信息来验证迁移并执行清理步骤。

## <a name="validate-the-migration-by-running-a-pilot-program"></a>通过运行试验程序来验证迁移

可以通过在生产环境中创建试点项目来验证 MultiPoint 服务迁移。 将迁移的角色服务投入生产之前，在服务器上运行试点项目，以验证你的部署是否按预期工作。 请考虑先限制连接的数量，从而慢慢增加访问 MultiPoint 服务的用户的数量。

> [!NOTE]
> 始终使用测试帐户来测试迁移。 使用具有管理权限的帐户和有效用户的帐户。

## <a name="retire-the-source-server"></a>停用源服务器
验证迁移之后，可以关闭源服务器或将其从网络断开连接。 如果服务器已加入域，则将其从域中删除，然后再断开连接。

