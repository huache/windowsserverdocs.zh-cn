---
title: Scwcmd 配置
description: '* * * * 的参考文章'
ms.topic: reference
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54faae6fd24aac91a94ec9ab1f373737569dda78
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036185"
---
# <a name="scwcmd-configure"></a>Scwcmd: configure

> 适用于： Windows Server 2012 R2、Windows Server 2012

将 (SCW) 生成的安全策略的安全配置向导应用到计算机。 此命令行工具还接受计算机名称的列表作为输入。

## <a name="syntax"></a>语法

```
scwcmd configure [[[/m:<ComputerName> | /ou:<OuName>] /p:<Policy>] | /i:<ComputerList>] [/u:<UserName>] [/pw:<Password>] [/t:<Threads>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|一样\<ComputerName>|指定要配置的计算机的 NetBIOS 名称、DNS 名称或 IP 地址。 如果指定了 **/m** 参数，则还必须指定 **/p** 参数。|
|/ou\<OuName>|指定组织单位的完全限定的域名 (FQDN) 在 Active Directory 域服务中的组织单位 (OU) 。 如果指定 **/ou** 参数，则还必须指定 **/p** 参数。 OU 中的所有计算机都将根据给定的策略进行分析。|
|/p\<Policy>|指定要用于执行配置的 .xml 策略文件的路径和文件名。|
|/i\<ComputerList>|指定 .xml 文件的路径和文件名，该文件包含计算机的列表及其预期的策略文件。 .Xml 文件中的所有计算机都将根据其相应的策略文件进行配置。 示例 .xml 文件是% windir% \security\SampleMachineList.xml。|
|/u\<UserName>|指定在配置远程计算机时要使用的备用用户凭据。 默认值为已登录的用户。|
|pw\<Password>|指定在配置远程计算机时要使用的备用用户凭据。 默认值为登录用户的密码。|
|/t:\<Threads>|指定在配置过程中应保持的同时未完成的配置操作的数量 (DefaultValue = 40，MinValue = 1，= 1000) 。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>注解

Scwcmd.exe 仅适用于运行 Windows Server 2008 R2、Windows Server 2008 或 Windows Server 2003 的计算机。

## <a name="examples"></a>示例

若要根据文件 webpolicy.xml 配置安全策略，请键入：
```
scwcmd configure /p:webpolicy.xml
```
若要使用 webadmin 帐户凭据为 webpolicy.xml 172.16.0.0 上的计算机配置安全策略，请键入：
```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```
若要在列表中的所有计算机上配置安全策略，最多可包含100个线程 campusmachines.xml，请键入：
```
scwcmd configure /i:campusmachines.xml /t:100
```
若要使用 DomainAdmin 帐户的凭据 webpolicy.xml 在 WebServers OU 中的所有计算机上配置安全策略，请键入：
```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)