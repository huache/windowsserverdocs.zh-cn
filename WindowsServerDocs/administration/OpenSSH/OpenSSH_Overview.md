---
ms.date: 01/07/2019
contributor: damaerteMSFT
author: maertendmsft
title: Windows 中的 OpenSSH
ms.product: windows-server
ms.openlocfilehash: 57126f38245f4547a04ea3a51f58aee865b5eb97
ms.sourcegitcommit: 3a3d62f938322849f81ee9ec01186b3e7ab90fe0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2020
ms.locfileid: "80852030"
---
# <a name="openssh-in-windows"></a>Windows 中的 OpenSSH

OpenSSH 是安全 Shell (SSH) 工具的开放源代码版本，Linux 及其他非 Windows 系统的管理员使用此类工具跨平台管理远程系统。 OpenSSH 在 2018 年秋季已添加至 Windows，并包含在 Windows 10 和 Windows Server 2019 中。 

SSH 基于客户端-服务器体系结构，用户在其中工作的系统是客户端，所管理的远程系统是服务器。 OpenSSH 包含一系列组件和工具，用于提供一种安全且简单的远程系统管理方法，其中包括：

* sshd.exe，它是远程所管理的系统上必须运行的 SSH 服务器组件 
* ssh.exe，它是在用户的本地系统上运行的 SSH 客户端组件
* ssh-keygen.exe，为 SSH 生成、管理和转换身份验证密钥 
* ssh-agent.exe，存储用于公钥身份验证的私钥
* ssh-add.exe，将私钥添加到服务器允许的列表中
* ssh-keyscan.exe，帮助从许多主机收集公用 SSH 主机密钥
* sftp.exe，这是提供安全文件传输协议的服务，通过 SSH 运行
* scp.exe 是在 SSH 上运行的文件复制实用工具

本部分中的文档重点介绍了如何在 Windows 上使用 OpenSSH，包括安装以及特定于 Windows 的配置和用例。 主题如下：
* 为 Windows Server 2019 和 Windows 10 安装和卸载 OpenSSH

有关常见 OpenSSH 功能的其他详细文档，请参阅 [OpenSSH.com](https://www.openssh.com/manual.html)。 

主 [OpenSSH 开源项目](https://www.openssh.com)是由 OpenBSD 项目的开发人员管理的。 此项目的 Microsoft 分支在 [GitHub](https://github.com/PowerShell/openssh-portable)中。
欢迎提供有关 Windows OpenSSH 的反馈，可以通过在我们的 [OpenSSH GitHub 存储库](https://github.com/PowerShell/openssh-portable)中创建 GitHub 问题来提供反馈。 
