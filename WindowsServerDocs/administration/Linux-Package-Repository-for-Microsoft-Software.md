---
title: 适用于 Microsoft 产品的 Linux 软件存储库
description: 本文档介绍了如何使用和安装适用于 Microsoft 产品的 Linux 软件包。
ms.topic: article
ms.assetid: b5387444-595f-4f38-abb7-163a70ea1895
author: victorcheng7
ms.author: vichen
ms.date: 08/14/2020
ms.openlocfilehash: dffd07d74e11253457f893d563c0b05272138f41
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078415"
---
# <a name="linux-software-repository-for-microsoft-products"></a>适用于 Microsoft 产品的 Linux 软件存储库

## <a name="overview"></a>概述

Microsoft 构建并支持适用于 Linux 系统的各种软件产品，并使它们可通过标准 APT 和 YUM 程序包存储库提供。 本文档介绍如何在 Linux 系统上配置存储库，以便可以使用分发的标准包管理工具来安装/升级 Microsoft 的 Linux 软件。

Microsoft 的 Linux 软件存储库由多个子存储库组成：

 - 生产–为要在生产中使用的包指定生产子存储库。 根据 Microsoft 的适用支持协议或计划，Microsoft 对这些包进行商业支持。

 - mssql server-这些存储库包含 Linux 上的 Microsoft SQL Server 的包-另请参阅： [Linux 上的 SQL Server](https://www.microsoft.com/sql-server/sql-server-vnext-including-Linux)。

> [!NOTE]
> Linux 软件存储库中的包受包中的许可条款的约束。 使用程序包之前请阅读这些许可条款。 安装和使用程序包即表示接受这些条款。 如果不同意许可条款，则不要使用程序包。

## <a name="configuring-the-repositories"></a>配置存储库

可以通过安装适用于 Linux 分发版和版本的 Linux 包自动配置存储库。 此包将安装存储库配置以及工具（如 apt/yum/zypper）使用的 GPG 公钥来验证已签名的包和/或存储库元数据。

### <a name="enterprise-linux-rhel-and-variants"></a>企业 Linux (RHEL 和变型) 

 - Enterprise Linux 6 (64.RPM) <p>`sudo rpm -Uvh https://packages.microsoft.com/config/rhel/6/packages-microsoft-prod.rpm`

 - 企业 Linux 7 (EL7) <p>`sudo rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm`

 - Enterprise Linux 8 (EL8) <p>`sudo rpm -Uvh https://packages.microsoft.com/config/rhel/8/packages-microsoft-prod.rpm`

### <a name="suse"></a>SUSE

 - SUSE Linux Enterprise Server 12<p>`sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm`

 - SUSE Linux Enterprise Server 15<p>`sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm`

### <a name="ubuntu"></a>Ubuntu

 - Ubuntu 16.04 (Xenial) <p>`curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -`<p>`sudo apt-add-repository https://packages.microsoft.com/ubuntu/16.04/prod`<p>`sudo apt-get update`

 - Ubuntu 18.04 (Bionic) <p>`curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -`<p>`sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.04/prod`<p>`sudo apt-get update`

 - Ubuntu 20.04 (Disco) <p>`curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -`<p>`sudo apt-add-repository https://packages.microsoft.com/ubuntu/20.04/prod`<p>`sudo apt-get update`

## <a name="manual-configuration"></a>手动配置

存储库配置文件可从 [packages.microsoft.com/config](https://packages.microsoft.com/config/)获取。可以使用以下 URI 命名约定来查找这些文件的名称和位置：

`https://packages.microsoft.com/config/<Distribution>/<Version>/prod.(repo|list)`

### <a name="package-and-repository-signing-key"></a>包和存储库签名密钥

- 可在此处下载 Microsoft 的 GPG 公钥： [https://packages.microsoft.com/keys/microsoft.asc](https://packages.microsoft.com/keys/microsoft.asc)
- 公钥 ID： Microsoft (版本签名) <gpgsecurity@microsoft.com>
- 公钥指纹： `BC52 8686 B50D 79E3 39D3 721C EB3E 94AD BE12 29CF`

### <a name="examples"></a>示例

 - RHEL/CentOS 7

```
# Install repository configuration
curl -sSL https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft-prod.repo

# Install Microsoft's GPG public key
curl -sSL https://packages.microsoft.com/keys/microsoft.asc > ./microsoft.asc
sudo rpm --import ./microsoft.asc
```

 - Ubuntu 20.04

```
# Install repository configuration
curl -sSL https://packages.microsoft.com/config/ubuntu/20.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft-prod.list

# Install Microsoft GPG public key
curl -sSL https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Update package index files
sudo apt-get update
```
