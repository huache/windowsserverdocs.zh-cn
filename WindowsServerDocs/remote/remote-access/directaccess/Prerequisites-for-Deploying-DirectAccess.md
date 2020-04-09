---
title: 部署 DirectAccess 的先决条件
description: 本主题提供了在 Windows Server 2016 中部署 DirectAccess 的先决条件。
manager: brianlic
ms.prod: windows-server
ms.technology: networking-da
ms.topic: article
ms.assetid: 57c7e039-42ef-4909-867a-b5f669c9e74e
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 5916c5bb87d7bdb10bcc32e24647923d434de2e7
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80857441"
---
# <a name="prerequisites-for-deploying-directaccess"></a>部署 DirectAccess 的先决条件

>适用于：Windows Server（半年频道）、Windows Server 2016

下表列出了使用配置向导部署 DirectAccess 所需的先决条件。  
  
|||  
|-|-|  
|方案|先决条件|  
|[使用入门向导部署单个 DirectAccess 服务器](../../remote-access/directaccess/single-server-wizard/Deploy-a-Single-DirectAccess-Server-Using-the-Getting-Started-Wizard.md)|-必须在所有配置文件上启用 Windows 防火墙<p>-仅支持运行 Windows 10&reg;的客户端。 <br />              Windows&reg; 8 和 Windows&reg; 8.1 企业版。<p>-不需要公钥基础结构。<p>-不支持部署双因素身份验证。 身份验证需要域凭据。<p>-自动将 DirectAccess 部署到当前域中的所有移动计算机。<p>-流向 Internet 的流量不通过 DirectAccess。 不支持强制隧道配置。<p>-DirectAccess 服务器是网络位置服务器。<p>-不支持网络访问保护（NAP）。<p>-不支持通过使用 DirectAccess 管理控制台或 Windows PowerShell cmdlet 以外的功能来更改策略。<p>-对于多站点配置，现在或将来，首先按照[使用高级设置部署单个 DirectAccess 服务器](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)中的指南进行操作。|  
|[使用高级设置部署单台 DirectAccess 服务器](../../remote-access/directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md)|-必须部署公钥基础结构。<br />    有关详细信息，请参阅[测试实验室指南微型模块： Windows Server 2012 的基本 PKI](https://social.technet.microsoft.com/wiki/contents/articles/7862.test-lab-guide-mini-module-basic-pki-for-windows-server-2012.aspx)。<p>-必须在所有配置文件上启用 Windows 防火墙。<p>以下服务器操作系统支持 DirectAccess。<p>-可以将所有版本的 Windows Server 2016 作为 DirectAccess 客户端或 DirectAccess 服务器进行部署。<br />-可以将所有版本的 Windows Server 2012 R2 作为 DirectAccess 客户端或 DirectAccess 服务器进行部署。<br />-可以将所有版本的 Windows Server 2012 作为 DirectAccess 客户端或 DirectAccess 服务器进行部署。<br />-可以将所有版本的 Windows Server 2008 R2 作为 DirectAccess 客户端或 DirectAccess 服务器进行部署。<p>以下客户端操作系统支持 DirectAccess。<p>-Windows 10&reg; Enterprise<br />-Windows 10&reg; Enterprise 2015 Long Term Servicing Branch （LTSB）<br />-Windows&reg; 8 和8.1 企业版<br />-Windows&reg; 7 旗舰版<br />-Windows&reg; 7 企业版<p>-KerbProxy authentication 不支持强制隧道配置。<p>-不支持通过使用 DirectAccess 管理控制台或 Windows PowerShell cmdlet 以外的功能来更改策略。<p>-不支持在另一台服务器上分隔 NAT64/DNS64 和 IPHTTPS 服务器角色。|  
  


