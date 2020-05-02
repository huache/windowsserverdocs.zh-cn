---
title: bitsadmin transfer
description: 用于传输一个或多个文件的 bitsadmin 传输命令的参考主题。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: fe302141-b33a-4a05-835e-dc4fc4db7d5a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9c7011f3ef3e85d7453e63d9a9c2e4a89a52cddf
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707748"
---
# <a name="bitsadmin-transfer"></a>bitsadmin transfer

传输一个或多个文件。 默认情况下，BITSAdmin 服务创建一个按**正常**优先级运行的下载作业，并在传输完成之前或发生严重错误之前，用进度信息更新命令窗口。

如果作业成功传输所有文件并在发生严重错误时取消作业，则该服务将完成该作业。 如果该服务无法将文件添加到作业中，或者为*类型*或*job_priority*指定了无效的值，则该服务不会创建作业。 若要传输多个文件，请指定`<RemoteFileName>-<LocalFileName>`多个对。 对必须以空格分隔。

> [!NOTE]
> 如果发生暂时性错误，BITSAdmin 命令将继续运行。 若要结束命令，请按 CTRL + C。

## <a name="syntax"></a>语法

```
bitsadmin /transfer <name> [<type>] [/priority <job_priority>] [/ACLflags <flags>] [/DYNAMIC] <remotefilename> <localfilename>
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| name | 作业的名称。 此命令不能是 GUID。 |
| type | 可选。 设置作业的类型，包括：<ul><li>**下载.** 默认值。 为下载作业选择此类型。</li><li>**上.** 为上载作业选择此类型。</li></ul> |
| priority | 可选。 设置作业的优先级，包括：<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |
| ACLflags | 可选。 指示你希望在要下载的文件中维护所有者和 ACL 信息。 指定一个或多个值，包括：<ul><li>**o** -将所有者信息复制到文件。</li><li>**g** -复制组信息和文件。</li><li>**d** -使用文件复制随机访问控制列表（DACL）信息。</li><li>**s** -使用文件复制系统访问控制列表（SACL）信息。</li></ul> |
| /DYNAMIC | 使用[**BITS_JOB_PROPERTY_DYNAMIC_CONTENT**](https://docs.microsoft.com/windows/win32/api/bits5_0/ne-bits5_0-bits_job_property_id)配置作业，放宽服务器端要求。 |
| remotefilename | 文件传输到服务器后的名称。 |
| localfilename | 位于本地的文件的名称。 |

## <a name="examples"></a>示例

若要启动名为*myDownloadJob*的传输作业：

```
bitsadmin /transfer myDownloadJob http://prodserver/audio.wma c:\downloads\audio.wma
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
