---
title: rdpsign
description: Rdpsign 命令的参考文章，可用于对远程桌面协议 ( .rdp) 文件进行数字签名。
ms.topic: reference
ms.assetid: 4a6fa8ce-3d32-49a5-b056-bcc1a23391f5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: a98619c468ce26e7af3406512be54937c8aa799d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637342"
---
# <a name="rdpsign"></a>rdpsign

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows Server 2012 R2，Windows Server 2012

使你能够对远程桌面协议 ( .rdp) 文件进行数字签名。

> [!NOTE]
> 若要了解最新版本中的新增功能，请参阅 [Windows Server 中远程桌面服务的新增功能](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))。

## <a name="syntax"></a>语法

```
rdpsign /sha1 <hash> [/q | /v |] [/l] <file_name.rdp>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
|--|--|
| /sha1 `<hash>` | 指定指纹，该指纹是证书存储中包含的签名证书的安全哈希算法 1 (SHA1) 哈希。 在 Windows Server 2012 R2 及更早版本中使用。 |
| /sha256 `<hash>` | 指定指纹，该指纹是安全哈希算法 256 (SHA256) 包含在证书存储中的签名证书哈希。 替换 Windows Server 2016 和更高版本中的/sha1。 |
| /q | 静默模式。 如果命令成功，则没有输出，如果该命令失败，则输出最小。 |
| /v | 详细模式。 显示所有警告、消息和状态。 |
| /l | 测试签名和输出结果，而不实际替换任何输入文件。 |
| `<file_name.rdp>` | .Rdp 文件的名称。 您必须指定 .rdp 文件 (或文件) 使用完整文件名进行签名。 不接受通配符。 |
| /? | 在命令提示符下显示帮助。 |

#### <a name="remarks"></a>备注

- SHA1 或 SHA256 证书指纹应表示受信任的 .rdp 文件发布者。 若要获取证书指纹，请打开 " **证书** " 管理单元，在 "本地计算机的证书存储" 或 "个人证书存储" 中双击要使用 (证书) 中，单击 " **详细信息** " 选项卡，然后在 " **字段** " 列表中，单击 " **指纹**"。

    > [!NOTE]
    > 复制指纹以用于 rdpsign.exe 工具时，必须删除任何空格。

- 已签名的输出文件将覆盖输入文件。

- 如果指定了多个文件，并且无法读取或写入任何 .rdp 文件，则该工具将继续到下一个文件中。

### <a name="examples"></a>示例

若要对名为 *file1*的 .rdp 文件进行签名，请导航到保存 .rdp 文件的文件夹，然后键入：

```
rdpsign /sha1 hash file1.rdp
```

> [!NOTE]
> *哈希*值表示 SHA1 证书指纹，不含任何空格。

若要测试 .rdp 文件的数字签名是否会成功，而无需实际对文件进行签名，请键入：

```
rdpsign /sha1 hash /l file1.rdp
```

若要对名为的多个 .rdp 文件、 *file2*和*file3*进行*签名，请*键入 (包含文件名之间的空格) ：

```
rdpsign /sha1 hash file1.rdp file2.rdp file3.rdp
```

## <a name="see-also"></a>另请参阅

- [命令行语法项](command-line-syntax-key.md)

- [远程桌面服务（终端服务）命令参考](remote-desktop-services-terminal-services-command-reference.md)
