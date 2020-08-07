---
title: Managing Remote Storage Resources
description: 本文介绍了如何管理远程计算机上的存储资源
ms.date: 7/7/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 8498d55cbdeab609bb3526c9ef884e330148d714
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87950631"
---
# <a name="managing-remote-storage-resources"></a>Managing Remote Storage Resources

> 适用于： Windows Server 2019，Windows Server 2016，Windows Server (半年通道) ，Windows Server 2012 R2，Windows Server 2012，Windows Server 2008 R2

以下两个选项可用于管理远程计算机上的存储资源：

-   可从文件服务器资源管理器 Microsoft<sup>®</sup> 管理控制台 (MMC) 管理单元（随后可用于管理远程资源）连接到远程计算机。
-   使用通过文件服务器资源管理器安装的命令行工具。

无论选择哪个选项，均可借助这些远程资源处理配额、屏蔽文件、管理分类、安排文件管理任务及生成报告。

> [!Note]
> 文件服务器资源管理器可以管理本地计算机或远程计算机上的资源，但不能同时进行管理。

例如，你可以：

-   使用文件服务器资源管理器 MMC 管理单元连接到该域中的另一台计算机，并检查远程计算机上的卷或文件夹的存储使用率。
-   在本地服务器上创建配额和文件屏蔽模板，然后使用命令行工具将这些模板导入位于分支机构的文件服务器中。

本节包括下列主题：

-   [连接到远程计算机](connect-to-remote-computer.md)
-   [命令行工具](command-line-tools.md)
