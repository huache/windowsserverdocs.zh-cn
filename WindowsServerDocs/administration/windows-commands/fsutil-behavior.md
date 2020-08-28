---
title: fsutil behavior
description: 用于查询或设置 NTFS 卷行为的 "fsutil 行为" 命令参考文章。
manager: dmoss
ms.author: toklima
author: toklima
ms.topic: reference
ms.date: 10/16/2017
ms.assetid: 84eaba2c-c0af-49e1-bbbd-2ed2928e5e4b
ms.openlocfilehash: 223a326a5ac60dfdb88c20ca3541b0128cf0943e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030165"
---
# <a name="fsutil-behavior"></a>fsutil behavior

> 适用于： Windows Server (半年通道) ，Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8

查询或设置 NTFS 卷行为，其中包括：

- 创建8.3 字符长度的文件名。

- 扩展 NTFS 卷上8.3 字符长度短文件名中使用的字符。

- 在 NTFS 卷上列出目录时更新 **上次访问时间** 戳。

- 配额事件写入系统日志以及 NTFS 页面缓冲池和 NTFS 非分页池内存缓存级别所用的频率。

- 主文件表区域 (MFT 区域) 的大小。

- 当系统在 NTFS 卷上遇到损坏时，无提示删除数据。

- 文件删除通知 (也称为剪裁或取消映射) 。

## <a name="syntax"></a>语法

```
fsutil behavior query {allowextchar | bugcheckoncorrupt | disable8dot3 [<volumepath>] | disablecompression | disablecompressionlimit | disableencryption | disablefilemetadataoptimization | disablelastaccess | disablespotcorruptionhandling | disabletxf | disablewriteautotiering | encryptpagingfile | mftzone | memoryusage | quotanotify | symlinkevaluation | disabledeletenotify}

fsutil behavior set {allowextchar {1|0} | bugcheckoncorrupt {1|0} | disable8dot3 [ <value> | [<volumepath> {1|0}] ] | disablecompression {1|0} | disablecompressionlimit {1|0} | disableencryption {1|0} | disablefilemetadataoptimization {1|0} | disablelastaccess {1|0} | disablespotcorruptionhandling {1|0} | disabletxf {1|0} | disablewriteautotiering {1|0} | encryptpagingfile {1|0} | mftzone <Value> | memoryusage <Value> | quotanotify <frequency> | symlinkevaluation <symboliclinktype> | disabledeletenotify {1|0}}
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- |------------ |
| query | 查询文件系统行为参数。 |
| set | 更改文件系统行为参数。 |
| allowextchar `{1|0}` | 允许 (**1**) 或不允许扩展字符集中 (**0**) 字符 (包括音调符号字符) 在 NTFS 卷上的8.3 字符长度短文件名中使用。<p>您必须重新启动计算机才能使此参数生效。 |
| Bugcheckoncorrupt `{1|0}` | 当 NTFS 卷损坏时，允许 (**1**) 或不允许 (**0**) 生成 bug 检查。 此功能可用于在与自愈 NTFS 功能一起使用时防止 NTFS 无提示删除数据。<p>您必须重新启动计算机才能使此参数生效。 |
| disable8dot3 [ <volumepath> ] `{1|0}` | 禁用 (**1**) 或启用 (**0**) 在 FAT 和 NTFS 格式的卷上创建8.3 字符长度的文件名称。 （可选）使用指定为驱动器名称后跟冒号或 GUID 的 *volumepath* 前缀。 |
| disablecompression `{1|0}` | 禁用 ** (1) ** 或启用 ** (0) ** NTFS 压缩。<p>您必须重新启动计算机才能使此参数生效。 |
| disablecompressionlimit `{1|0}` | 禁用 ** (1) ** 或 ** (0) ** ntfs 卷上的 ntfs 压缩限制。 压缩文件达到特定的碎片级别时，而不是扩展文件时，NTFS 将停止压缩文件的其他区。 这样做是为了允许压缩文件比平时更大。 如果将此值设置为 **TRUE，则** 将禁用限制系统上压缩文件大小的此功能。 不建议禁用此功能。<p>您必须重新启动计算机才能使此参数生效。 |
| disableencryption `{1|0}` | 禁用 ** (1) ** 或启用 ** (0) ** NTFS 卷上的文件夹和文件的加密。<p>您必须重新启动计算机才能使此参数生效。 |
| disablefilemetadataoptimization `{1|0}` | 禁用 ** (1) ** 或启用 ** (0) ** 文件元数据优化。 NTFS 对给定文件可以具有的区数有限制。 压缩文件和稀疏文件可能会产生很大的碎片。 默认情况下，NTFS 会定期压缩其内部元数据结构，以允许更多的碎片文件。 如果将此值设置为 **TRUE，则** 将禁用此内部优化。 不建议禁用此功能。<p>您必须重新启动计算机才能使此参数生效。 |
| disablelastaccess `{1|0}` | 禁用 (**1**) 或者在 NTFS 卷上列出目录时，使 (**0**) 更新到每个目录上的最后一个访问时间戳。<p>您必须重新启动计算机才能使此参数生效。 |
| disablespotcorruptionhandling `{1|0}` | 禁用 ** (1) ** 或启用 ** (0) ** 点损坏处理。 还允许系统管理员运行 CHKDSK 来分析卷的状态，而无需使其脱机。 不建议禁用此功能。<p>您必须重新启动计算机才能使此参数生效。 |
| disabletxf `{1|0}` | 禁用 ** (1) ** 或启用指定 NTFS 卷上 ** (0) ** txf。 TxF 是一项 NTFS 功能，可将语义（如语义）提供给文件系统操作。 现在已弃用了 TxF，但该功能仍然可用。 不建议在 C：卷上禁用此功能。<p>您必须重新启动计算机才能使此参数生效。 |
| disablewriteautotiering `{1|0}` | 为分层卷禁用 ReFS v2 自动分层逻辑。<p>您必须重新启动计算机才能使此参数生效。 |
| encryptpagingfile `{1|0}` | 加密 (**1**) 或不对 Windows 操作系统中的内存分页文件 (**0** 进行加密) 。<p>您必须重新启动计算机才能使此参数生效。 |
| mftzone `<value>` | 设置 MFT 区的大小，并将其表示为200MB 单元的倍数。 将 *值* 设置为介于 **1** (默认值为 200 mb) 到 **4** (最大值为 800 mb) 。<p>您必须重新启动计算机才能使此参数生效。 |
| memoryusage `<value>` | 配置 NTFS 分页池内存和 NTFS 非分页缓冲池内存的内部缓存级别。 设置为 **1** 或 **2**。 如果设置为 **1** (默认) ，NTFS 将使用默认的分页池内存量。 设置为 **2**时，NTFS 将增加其后备链表列表和内存阈值的大小。  (后备链表列表是固定大小内存缓冲区的池，内核和设备驱动程序将其创建为文件系统操作的专用内存缓存，如读取文件。 ) <p>您必须重新启动计算机才能使此参数生效。 |
| quotanotify `<frequency>` | 配置在系统日志中报告 NTFS 配额冲突的频率。 的有效值范围是 **0 – 4294967295**。 默认频率为 **3600** 秒 (一小时) 。<p>您必须重新启动计算机才能使此参数生效。 |
| symlinkevaluation `<symboliclinktype>` | 控制可以在计算机上创建的符号链接的种类。 有效选项包括：<ul><li>**1** -本地到本地符号链接， `L2L:{0|1}`</li><li>**2** -本地到远程符号链接， `L2R:{1|0}`</li><li>**3** -远程到本地符号链接， `R2R:{1|0}`</li><li>**4** -远程到远程符号链接， `R2L:{1|0}`</li></ul> |
| disabledeletenotify | 禁用 (**1**) 或启用 (**0**) 删除通知。 删除通知 (也称为剪裁或取消映射) 是一项功能，它将已释放的群集的基础存储设备通知为文件删除操作。 此外：<ul><li>对于使用 ReFS v2 的系统，默认情况下，修整处于禁用状态。</li><li>对于使用 ReFS v1 的系统，默认情况下会启用 trim。</li><li>对于使用 NTFS 的系统，默认情况下会启用剪裁，除非管理员禁用了它。</li><li>如果硬盘驱动器或 SAN 报告其不支持剪裁，则硬盘驱动器和 San 不会获取剪裁通知。</li><li>启用或禁用不需要重新启动。</li><li>当发出下一个取消映射命令时，Trim 将有效。</li><li>现有的即时 IO 不受注册表更改的影响。</li><li>启用或禁用 trim 后，不需要重新启动任何服务。</li></ul> |

#### <a name="remarks"></a>注解

- MFT 区是一个保留区域，它使主文件表 (MFT) 根据需要进行扩展，以防止 MFT 碎片。 如果卷上的平均文件大小为 2 KB 或更小，则将 **mftzone** 值设置为 **2**可能会很有用。 如果卷上的平均文件大小为 1 KB 或更小，则将 **mftzone** 值设置为 **4**会很有用。

- 如果将 **disable8dot3** 设置为 **0**，则每次创建具有较长文件名的文件时，NTFS 都会创建一个具有8.3 个字符长度的第二个文件项。 NTFS 在目录中创建文件时，必须查找与长文件名关联的8.3 字符长度的文件名。 此参数更新 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation** 注册表项。

- **Allowextchar**参数将更新**HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsAllowExtendedCharacterIn8dot3Name**注册表项。

- **Disablelastaccess**参数可降低日志记录更新对文件和目录上**最后访问时间**戳的影响。 禁用 " **上次访问时间** " 功能可提高文件和目录访问的速度。 此参数更新 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsDisableLastAccessUpdate** 注册表项。

    **注意：**

    - 即使所有磁盘上的值不是最新的，基于文件的 **上次访问时间** 查询也是准确的。 NTFS 为查询返回正确的值，因为准确的值存储在内存中。

    - 一小时是 NTFS 可以延迟更新磁盘上的 **上次访问时间** 的最长时间。 如果 NTFS 更新其他文件属性（如 " **上次修改时间**"），并且 " **上次访问时间** " 更新处于挂起状态，则 NTFS 将 **上次访问时间** 与其他更新进行更新，而不会对性能产生额外的影响。

    - **Disablelastaccess**参数可能会影响依赖于此功能的程序，例如备份和远程存储。

- 增加物理内存不会始终增加 NTFS 可用的分页池内存量。 将 **memoryusage** 设置为 **2** 将引发分页池内存的限制。 如果系统打开并关闭了同一文件集中的多个文件，并且尚未对其他应用或缓存内存使用大量系统内存，这可能会提高性能。 如果计算机已将大量系统内存用于其他应用或缓存内存，则增加 NTFS 分页和非分页池内存的限制将减少其他进程的可用池内存。 这可能会降低整体系统性能。 此参数更新 **HKLM\SYSTEM\CurrentControlSet\Control\FileSystem\NtfsMemoryUsage** 注册表项。

- 在 **mftzone** 参数中指定的值是在新卷上，mft 的初始大小加上 mft 区的近似值，并为每个文件系统在装入时设置。 由于使用的是卷上的空间，因此 NTFS 会调整保留的空间，以备今后 MFT 增长。 如果 MFT 区域已经很大，则不会再次保留完整的 MFT 区域大小。 因为 MFT 区域基于 MFT 末尾之后的连续范围，所以在使用空间时，将会收缩。

    在完全使用当前 MFT 区域之前，文件系统不会确定新的 MFT 区域位置。 请注意，此操作永远不会出现在典型的系统上。

- 当 "删除通知" 功能打开时，某些设备可能会遇到性能下降。 在这种情况下，请使用 **disabledeletenotify** 选项关闭通知功能。

### <a name="examples"></a>示例

若要查询使用 GUID "{928842df-5a01-11de-a85c-806e6f6e6963}" 指定的磁盘卷的 "禁用8dot3 名称" 行为，请键入：

```
fsutil behavior query disable8dot3 volume{928842df-5a01-11de-a85c-806e6f6e6963}
```

还可以使用 **8dot3name** 子命令查询8dot3 名称行为。

若要查询系统以查看是否已启用剪裁，请键入：

```
fsutil behavior query DisableDeleteNotify
```

这会生成类似于下面的输出：

```
NTFS DisableDeleteNotify = 1
ReFS DisableDeleteNotify is not currently set
```

若要覆盖 ReFS v2 (disabledeletenotify) 的默认行为，请键入：

```
fsutil behavior set disabledeletenotify ReFS 0
```

若要为 NTFS 和 ReFS v1 替代 TRIM (disabledeletenotify) 的默认行为，请键入：

```
fsutil behavior set disabledeletenotify 1
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [fsutil](fsutil.md)

- [fsutil 8dot3name](fsutil-8dot3name.md)
