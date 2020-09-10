---
title: tapicfg
description: 了解如何管理 TAPI 应用程序目录分区。
ms.topic: reference
ms.assetid: c0e642ce-5d98-4edb-9a65-1dff09aef4e1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: fc44ebc15c130dab34a1aff60aba7926b4cbbcb4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635467"
---
# <a name="tapicfg"></a>tapicfg

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

创建、删除或显示 TAPI 应用程序目录分区，或设置默认的 TAPI 应用程序目录分区。 TAPI 3.1 客户端可以将此应用程序目录分区中的信息与目录服务定位器服务一起使用来查找和通信 TAPI 目录。你还可以使用 **tapicfg** 来创建或删除服务连接点，使 tapi 客户端能够在域中有效地查找 tapi 应用程序目录分区。 有关详细信息，请参阅 "备注"。 若要查看命令语法，请单击命令。
-   [tapicfg 安装](#BKMK_install)
-   [tapicfg 删除](#BKMK_remove)
-   [tapicfg publishscp](#BKMK_publishscp)
-   [tapicfg removescp](#BKMK_removescp)
-   [tapicfg show](#BKMK_show)
-   [tapicfg makedefault](#BKMK_makedefault)

## <a name="tapicfg-install"></a><a name="BKMK_install"></a>tapicfg 安装
创建 TAPI 应用程序目录分区。

### <a name="syntax"></a>语法
```
tapicfg install /directory:<PartitionName> [/server:<DCName>] [/forcedefault]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|安装/目录：\<PartitionName>|必需。 指定要创建的 TAPI 应用程序目录分区的 DNS 名称。 此名称必须是完全限定的域名。|
|/server \<DCName>|指定在其上创建 TAPI 应用程序目录分区的域控制器的 DNS 名称。 如果未指定域控制器名称，则使用本地计算机的名称。|
|/forcedefault|指定此目录是域的默认 TAPI 应用程序目录分区。 一个域中可以有多个 TAPI 应用程序目录分区。<p>如果此目录是在域中创建的第一个 TAPI 应用程序目录分区，则无论是否使用 **/forcedefault** 选项，它都将自动设置为默认值。|
|/?|在命令提示符下显示帮助。|

## <a name="tapicfg-remove"></a><a name="BKMK_remove"></a>tapicfg 删除
删除 TAPI 应用程序目录分区。

### <a name="syntax"></a>语法
```
tapicfg remove /directory:<PartitionName>
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|删除/目录：\<PartitionName>|必需。 指定要删除的 TAPI 应用程序目录分区的 DNS 名称。 请注意，此名称必须是完全限定的域名。|
|/?|在命令提示符下显示帮助。|

## <a name="tapicfg-publishscp"></a><a name="BKMK_publishscp"></a>tapicfg publishscp
创建服务连接点以发布 TAPI 应用程序目录分区。

### <a name="syntax"></a>语法
```
tapicfg publishscp /directory:<PartitionName> [/domain:<DomainName>] [/forcedefault]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|publishscp/目录：\<PartitionName>|必需。 指定服务连接点将发布的 TAPI 应用程序目录分区的 DNS 名称。|
|/domain\<DomainName>|指定在其中创建服务连接点的域的 DNS 名称。 如果未指定域名，则使用本地域的名称。|
|/forcedefault|指定此目录是域的默认 TAPI 应用程序目录分区。 一个域中可以有多个 TAPI 应用程序目录分区。|
|/?|在命令提示符下显示帮助。|

## <a name="tapicfg-removescp"></a><a name="BKMK_removescp"></a>tapicfg removescp
删除 TAPI 应用程序目录分区的服务连接点。

### <a name="syntax"></a>语法
```
tapicfg removescp /directory:<PartitionName> [/domain:<DomainName>]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|removescp/目录：\<PartitionName>|必需。 指定为其删除服务连接点的 TAPI 应用程序目录分区的 DNS 名称。|
|/domain \<DomainName>|指定从中删除服务连接点的域的 DNS 名称。 如果未指定域名，则使用本地域的名称。|
|/?|在命令提示符下显示帮助。|

## <a name="tapicfg-show"></a><a name="BKMK_show"></a>tapicfg show
显示域中 TAPI 应用程序目录分区的名称和位置。

### <a name="syntax"></a>语法
```
tapicfg show [/defaultonly][ /domain:<DomainName>]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|/defaultonly|显示域中默认 TAPI 应用程序目录分区的名称和位置。|
|/domain \<DomainName>|指定显示 TAPI 应用程序目录分区的域的 DNS 名称。 如果未指定域名，则使用本地域的名称。|
|/?|在命令提示符下显示帮助。|

## <a name="tapicfg-makedefault"></a><a name="BKMK_makedefault"></a>tapicfg makedefault
设置域的默认 TAPI 应用程序目录分区。

### <a name="syntax"></a>语法
```
tapicfg makedefault /directory:<PartitionName> [/domain:<DomainName>]
```
#### <a name="parameters"></a>参数
|参数|说明|
|-------|--------|
|makedefault/目录：\<PartitionName>|必需。 将 TAPI 应用程序目录分区的 DNS 名称指定为域的默认分区。 请注意，此名称必须是完全限定的域名。 指定为其设置了 TAPI 应用程序目录分区的域的 DNS 名称。 如果未指定域名，则使用本地域的名称。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
你必须是 active directory 中 Enterprise Admins 组的成员，才能运行 **tapicfg install** (来创建 tapi 应用程序目录分区) 或 **tapicfg 删除** (删除 tapi 应用程序目录分区) 。

此命令行工具可在作为域成员的任何计算机上运行。

如果安装了适当的字体和语言支持，用户提供的文本 (例如 TAPI 应用程序目录分区、服务器和域) 具有国际或 Unicode 字符的名称将会正确显示。

你仍可以在组织中使用 Internet 定位符服务 (ILS) 服务器，如果需要使用 ILS 来支持某些应用程序，因为运行 Windows XP 或 Windows Server 2003 操作系统的 TAPI 客户端可以查询 ILS 服务器或 TAPI 应用程序目录分区。

你可以使用 **tapicfg** 来创建或删除服务连接点。 如果出于任何原因重命名了 TAPI 应用程序目录分区 (例如，如果你重命名它所在的域) ，则必须删除现有的服务连接点，并创建新的服务连接点，其中包含要发布的 TAPI 应用程序目录分区的新 DNS 名称。 否则，TAPI 客户端将无法找到和访问 TAPI 应用程序目录分区。 你还可以删除服务连接点，以便进行维护或安全目的 (例如，如果你不希望在特定的 TAPI 应用程序目录分区上公开 TAPI 数据) 。

## <a name="examples"></a>示例
若要在名为 testdc.testdom.microsoft.com 的服务器上创建名为 tapifiction.testdom.microsoft.com 的 TAPI 应用程序目录分区，然后将其设置为新域的默认 TAPI 应用程序目录分区，请键入：
```
tapicfg install /directory:tapifiction.testdom.microsoft.com /server:testdc.testdom.microsoft.com /forcedefault
```
若要显示新域的默认 TAPI 应用程序目录分区的名称，请键入：
```
tapicfg show /defaultonly
```
## <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)
