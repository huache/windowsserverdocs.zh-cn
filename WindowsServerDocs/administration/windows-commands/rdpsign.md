---
title: rdpsign
description: 了解如何对 RDP 文件进行数字签名。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4a6fa8ce-3d32-49a5-b056-bcc1a23391f5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: 4245ea533238d31457563f4d3521fdb09ff1f255
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82722630"
---
# <a name="rdpsign"></a>rdpsign

> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使您能够对远程桌面协议（.rdp）文件进行数字签名。


> [!NOTE]
> 在 Windows Server 2008 R2 中，终端服务被重命名为远程桌面服务。 若要了解最新版本中的新增功能，请参阅 Windows server TechNet 库中的[Windows server 2012 远程桌面服务中的新增功能](https://technet.microsoft.com/library/hh831527)。

## <a name="syntax"></a>语法
```
rdpsign /sha1 <hash> [/q | /v |] [/l] <file_name.rdp>
```

### <a name="parameters"></a>参数

|参数|描述|
|-------|--------|
|/sha1 \<哈希>|指定指纹，该指纹是证书存储中包含的签名证书的安全哈希算法1（SHA1）哈希。 在 Windows Server 2012 R2 及更早版本中使用。|
|/sha256 \<哈希>|指定指纹，该指纹是证书存储中包含的签名证书的安全哈希算法256（SHA256）哈希。 替换 Windows Server 2016 和更高版本中的/sha1。|
|/q|静默模式。 如果命令成功，则没有输出，如果该命令失败，则输出最小。|
|/v|详细模式。 显示所有警告、消息和状态。|
|/l|测试签名和输出结果，而不实际替换任何输入文件。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注
-   SHA1 或 SHA256 证书指纹应表示受信任的 .rdp 文件发布者。 若要获取证书指纹，请打开 "证书" 管理单元，双击要使用的证书（在本地计算机的证书存储中或在个人证书存储区中），单击 "**详细信息**" 选项卡，然后在 "**字段**" 列表中，单击 "**指纹**"。

    > [!NOTE]
    > 复制指纹以用于 rdpsign 工具时，必须删除任何空格。

-   必须使用完整的文件名指定要签名的 .rdp 文件。 不接受通配符。
-   已签名的输出文件将覆盖输入文件。
-   如果无法读取或写入任何 .rdp 文件，则该工具将继续到下一个文件（如果指定了多个文件）。

## <a name="examples"></a><a name="BKMK_examples"></a>示例
- 若要对名为 File1 的 .rdp 文件进行签名，请导航到保存 .rdp 文件的文件夹，然后键入以下内容：
  ```
  rdpsign /sha1 hash file1.rdp
  ```
  > [!NOTE]
  > *哈希*值表示 SHA1 证书指纹，不含任何空格。
- 若要测试 .rdp 文件的数字签名是否会成功，而无需实际对文件进行签名，请键入以下内容：
  ```
  rdpsign /sha1 hash /l file1.rdp
  ```
- 若要对多个 .rdp 文件进行签名，请使用空格分隔文件名。 例如，若要对名为 File1、File2 和 File3 的多个 .rdp 文件进行签名，请键入以下内容：
  ```
  rdpsign /sha1 hash file1.rdp file2.rdp file3.rdp
  ```
  ## <a name="see-also"></a>另请参阅
  - [命令行语法键](command-line-syntax-key.md)
  [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
