---
title: Diskraid
description: Diskraid 命令行工具的参考主题，使你能够配置和管理独立（或廉价）磁盘（RAID）存储子系统冗余阵列。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 20aef1e5-7641-47cf-b4eb-cda117f65b6e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ffceb9347921536a1bee59f46a4d5ab4800c1e70
ms.sourcegitcommit: aed942d11f1a361fc1d17553a4cf190a864d1268
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/12/2020
ms.locfileid: "83235207"
---
# <a name="diskraid"></a>Diskraid

**Diskraid**是一种命令行工具，可用于配置和管理独立（或廉价）磁盘（RAID）的冗余阵列（RAID）存储子系统。

RAID 通常在服务器上用于对容错磁盘系统进行标准化和分类。 RAID 等级提供了性能、可靠性和费用方面的不同组合。 某些服务器提供了三个 RAID 级别：级别0（条带化）、级别1（镜像）和级别5（带奇偶校验的带区）。

硬件 RAID 子系统使用逻辑单元号（LUN）将物理上可寻址的存储单元彼此区分开来。 LUN 对象必须至少具有一个 plex，并且可以有任意数量的附加丛。 每个 plex 都包含 LUN 对象上的数据副本。 可以将丛添加到 LUN 对象并从中删除。

大多数 Diskraid 命令对特定的主机总线适配器（HBA）端口、发起程序适配器、发起程序门户、提供程序、子系统、控制器、端口、驱动器、LUN、目标门户、目标或目标门户组进行操作。 使用 "**选择**" 命令可选择对象。 所选对象有焦点。 焦点简化了常见的配置任务，例如在同一子系统中创建多个 Lun。

> [!NOTE]
> Diskraid 命令行工具仅适用于支持虚拟磁盘服务（VDS）的存储子系统。

## <a name="diskraid-commands"></a>Diskraid 命令

以下命令可从 Diskraid 工具中获取。

### <a name="add"></a>add

向当前选定的 LUN 添加现有 LUN，或将 iSCSI 目标门户添加到当前选定的 iSCSI 目标门户组。

#### <a name="syntax"></a>语法

```
add plex lun=n [noerr]
add tpgroup tportal=n [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| plex lun =`<n>` | 指定要作为 plex 添加到当前所选 LUN 的 LUN 编号。 警告：将删除 LUN 上作为 plex 添加的所有数据。 |
| tpgroup 门户 =`<n>` | 指定要添加到当前选定的 iSCSI 目标门户组的 iSCSI 目标门户编号。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="associate"></a>将

为当前所选的 LUN （其他控制器端口处于非活动状态）设置指定的控制器端口列表，或将指定的控制器端口添加到当前所选 lun 的现有活动控制器端口列表，或将指定的 iSCSI 目标与当前选定的 LUN 关联。

#### <a name="syntax"></a>语法

```
associate controllers [add] <n>[,<n> [,…]]
associate ports [add] <n-m>[,<n-m>[,…]]
associate targets [add] <n>[,<n> [,…]]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| controller | 添加或替换与当前所选 LUN 关联的控制器的列表。 仅与 VDS 1.0 提供程序一起使用。 |
| ports | 添加或替换与当前所选 LUN 关联的控制器端口的列表。 仅与 VDS 1.1 提供程序一起使用。 |
| 目标 | 添加或替换与当前所选 LUN 关联的 iSCSI 目标的列表。 仅与 VDS 1.1 提供程序一起使用。 |
| add | **如果使用 VDS 1.0 提供程序：** 将指定的控制器添加到与 LUN 关联的现有控制器列表中。 如果未指定此参数，则控制器列表将替换与此 LUN 关联的现有控制器列表。<p>**如果使用 VDS 1.1 提供程序：** 将指定的控制器端口添加到 LUN 关联的现有控制器端口列表。 如果未指定此参数，则控制器端口的列表将替换与该 LUN 关联的现有控制器端口列表。 |
| `<n>[,<n> [, ...]]` | 与**控制器**或**目标**参数一起使用。 指定要设置为活动或关联的控制器或 iSCSI 目标的编号。 |
| `<n-m>[,<n-m>[,…]]` | 与**端口**参数一起使用。 使用控制器号（*n*）和端口号（*m*）对指定要设置为活动状态的控制器端口。 |

#### <a name="example"></a>示例

关联端口并将其添加到使用 VDS 1.1 提供程序的 LUN：

```
DISKRAID> SEL LUN 5
LUN 5 is now the selected LUN.

DISKRAID> ASSOCIATE PORTS 0-0,0-1
Controller port associations changed.
(Controller ports active after this command: Ctlr 0 Port 0, Ctlr 0 Port 1)

DISKRAID> ASSOCIATE PORTS ADD 1-1
Controller port associations changed.
(Controller ports active after this command: Ctlr 0 Port 0, Ctlr 0 Port 1, Ctlr 1 Port 1)
```

### <a name="automagic"></a>automagic

设置或清除一些标志，这些标志向提供程序提供有关如何配置 LUN 的提示。 使用不带参数的**automagic**操作将显示标志列表。

#### <a name="syntax"></a>语法

```
automagic {set | clear | apply} all <flag=value> [<flag=value> [...]]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| set | 将指定的标志设置为指定值。 |
| clear | 清除指定标志。 **All**关键字清除所有 automagic 标志。 |
| apply | 将当前标志应用于所选的 LUN。 |
| `<flag>` | 标志由三个字母组成的缩写词标识，其中包括：<ul><li>**FCR** -需要快速崩溃恢复</li><li>**FTL** -容错</li><li>**MSR** -大多数读取</li><li>**MXD** -最大驱动器</li><li>**MXS** -预期的最大大小</li><li>**Tnsnames.ora** -最佳读取对齐方式</li><li>**Or** -最佳读取大小</li><li>**OSR** -针对顺序读取进行优化</li><li>**OSW** -针对顺序写入进行优化</li><li> **OWA**最佳写入对齐方式</li><li>**OWS** -最佳写入大小</li><li>**RBP** -重新生成优先级</li><li>**RBV** -已启用读回验证</li><li>**RMP** -重新映射已启用</li><li>**STS**块大小</li><li>**WTC** -已启用写入缓存</li><li>**Ynk-f8-clz** -可移动</li></ul> |

### <a name="break"></a>break

从当前所选的 LUN 中删除 plex。 不保留 plex 及其包含的数据，并且可以回收驱动器范围。

> [!CAUTION]
> 使用此命令之前，必须先选择镜像的 LUN。 Plex 上的所有数据都将被删除。 原始 LUN 上包含的所有数据都不一定是一致的。

#### <a name="syntax"></a>语法

```
break plex=<plex_number> [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 丛 | 指定要删除的 plex 的编号。 不会保留该 plex 及其包含的数据，并且将回收此 plex 使用的资源。 LUN 中包含的数据不一定是一致的。 如果要保留此 plex，请使用卷影复制服务（VSS）。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="chap"></a>chap

设置质询握手身份验证协议（CHAP）共享机密，以便 iSCSI 发起程序和 iSCSI 目标可以相互通信。

#### <a name="syntax"></a>语法

```
chap initiator set secret=[<secret>] [target=<target>]
chap initiator remember secret=[<secret>] target=<target>
chap target set secret=[<secret>] [initiator=<initiatorname>]
chap target remember secret=[<secret>] initiator=<initiatorname>
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 发起方集 | 设置本地 iSCSI 发起程序服务中的共享机密，以便在发起方对目标进行身份验证时使用。 |
| 发起方记得 | 将 iSCSI 目标的 CHAP 机密传达给本地 iSCSI 发起程序服务，以便发起方服务可以使用该机密在 CHAP 身份验证期间向目标进行身份验证。 |
| 目标集 | 设置在目标对发起程序进行身份验证时，用于 CHAP 身份验证的当前选定 iSCSI 目标中的共享机密。 |
| 目标记住 | 将 iSCSI 发起程序的 CHAP 机密传达给当前的焦点 iSCSI 目标，以便目标可以使用机密，以便在双方 CHAP 身份验证期间对发起方进行身份验证。 |
| secret | 指定要使用的机密。 如果为空，则将清除密钥。 |
| 目标 | 指定当前所选子系统中要与机密关联的目标。 当在发起方上设置机密并将其退出时，这是可选的，指示该机密将用于还没有关联密钥的所有目标。 |
| initiatorname | 指定要与机密关联的发起方 iSCSI 名称。 如果在目标上设置机密，并将其留出，则这是可选的，它指示该机密将用于还没有关联密钥的所有发起程序。 |

### <a name="create"></a>create

在当前选定的子系统上创建新的 LUN 或 iSCSI 目标，或在当前选定的目标上创建目标门户组。 您可以使用**Diskraid list**命令查看实际绑定。

#### <a name="syntax"></a>语法

```
create lun simple [size=<n>] [drives=<n>] [noerr]
create lun stripe [size=<n>] [drives=<n, n> [,...]]  [stripesize=<n>] [noerr]
create lun raid [size=<n>] [drives=<n, n> [,...]] [stripesize=<n>] [noerr]
create lun mirror [size=<n>] [drives=<n, n> [,...]] [stripesize=<n>] [noerr]
create lun automagic size=<n> [noerr]
create target name=<name> [iscsiname=<iscsiname>] [noerr]
create tpgroup [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 简单 | 创建一个简单的 LUN。 |
| 带状线 (stripe) | 创建条带化 LUN。 |
| raid | 创建具有奇偶校验的带区 LUN。 |
| mirror | 创建镜像 LUN。 |
| automagic | 使用当前有效的*automagic*提示创建 LUN。 有关详细信息，请参阅本文中的**automagic**子命令。 |
| size= | 指定 LUN 总大小（mb）。 必须指定**size**= 或**驱动器**= 参数。 它们也可以一起使用。 如果未指定**size =** 参数，则创建的 LUN 将是所有指定驱动器允许的最大大小。<p>通常，提供程序创建一个 LUN，其大小至少与请求的大小相同，但是，在某些情况下，访问接口可能需要向上舍入到下一个最大大小。 例如，如果将 size 指定为. 99 GB，并且提供程序只能分配 GB 磁盘区，则生成的 LUN 将为 1 GB。 若要使用其他单位指定大小，请在大小后立即使用以下可识别的后缀之一：<ul><li>**B**字节</li><li>**Kb** -kb</li><li>**MB** -mb</li><li>**Gb** -gb</li><li>**Tb** -tb</li><li>**Pb** -pb。</li></ul> |
| 驱动器 = | 指定用于创建 LUN 的驱动器的*drive_number* 。 必须指定**size**= 或**驱动器**= 参数。 它们也可以一起使用。 如果未指定**size =** 参数，则创建的 LUN 是所有指定驱动器允许的最大大小。 如果指定**size =** 参数，则提供程序将从指定的驱动器列表中选择驱动器以创建 LUN。 如果可能，提供程序将尝试按指定顺序使用驱动器。 |
| stripesize = | 指定*条带*或*raid* LUN 的大小（以 mb 为单位）。 创建 LUN 后，不能更改 stripesize。 若要使用其他单位指定大小，请在大小后立即使用以下可识别的后缀之一：<ul><li>**B**字节</li><li>**Kb** -kb</li><li>**MB** -mb</li><li>**Gb** -gb</li><li>**Tb** -tb</li><li>**Pb** -pb。</li></ul> |
| 目标 | 在当前选定的子系统上创建新的 iSCSI 目标。 |
| name | 提供目标的友好名称。 |
| iscsiname | 为目标提供 iSCSI 名称，可将其省略，使提供程序生成名称。 |
| tpgroup | 在当前选定的目标上创建新的 iSCSI 目标门户组。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="delete"></a>删除

删除当前所选的 LUN、iSCSI 目标（只要没有与 iSCSI 目标关联的 Lun）或 iSCSI 目标门户组。

#### <a name="syntax"></a>语法

```
delete lun [uninstall] [noerr]
delete target [noerr]
delete tpgroup [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| lun | 删除当前所选的 LUN 和其中的所有数据。 |
| 卸载 | 指定在删除 LUN 之前，将清理与 LUN 关联的本地系统上的磁盘。 |
| 目标 | 如果没有与目标关联的 Lun，则删除当前选定的 iSCSI 目标。 |
| tpgroup | 删除当前选定的 iSCSI 目标门户组。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="detail"></a>详细信息

显示有关指定类型的当前所选对象的详细信息。

#### <a name="syntax"></a>语法

```
detail {hbaport | iadapter | iportal | provider | subsystem | controller | port | drive | lun | tportal | target | tpgroup} [verbose]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| hbaport | 列出有关当前所选主机总线适配器（HBA）端口的详细信息。 |
| iadapter | 列出有关当前所选 iSCSI 发起程序适配器的详细信息。 |
| iportal | 列出有关当前所选 iSCSI 发起程序门户的详细信息。 |
| provider | 列出有关当前所选提供程序的详细信息。 |
| 子系统 | 列出有关当前所选子系统的详细信息。 |
| controller | 列出有关当前所选控制器的详细信息。 |
| port | 列出有关当前所选控制器端口的详细信息。 |
| 驱动器 | 列出有关当前所选驱动器的详细信息，包括占用的 Lun。 |
| lun | 列出有关当前所选 LUN 的详细信息，包括相关驱动器。 输出略有不同，具体取决于 LUN 是光纤通道还是 iSCSI 子系统的一部分。 如果未屏蔽的主机列表仅包含星号，这意味着该 LUN 不会被所有主机屏蔽。 |
| 门户 | 列出有关当前所选 iSCSI 目标门户的详细信息。 |
| 目标 | 列出有关当前所选 iSCSI 目标的详细信息。 |
| tpgroup | 列出有关当前所选 iSCSI 目标门户组的详细信息。 |
| verbose | 仅与 LUN 参数一起使用。 列出附加信息，包括其 plex。 |

### <a name="dissociate"></a>取消

为当前所选 LUN （其他控制器端口不受影响）将指定的控制器端口列表设置为非活动状态，或将当前所选 LUN 的 iSCSI 目标的指定列表取消。

#### <a name="syntax"></a>语法

```
dissociate controllers <n> [,<n> [,...]]
dissociate ports <n-m>[,<n-m>[,…]]
dissociate targets <n> [,<n> [,…]]
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 控制器 | 从与当前所选 LUN 关联的控制器列表中删除控制器。 仅与 VDS 1.0 提供程序一起使用。 |
| ports | 从与当前所选 LUN 关联的控制器端口列表中删除控制器端口。 仅与 VDS 1.1 提供程序一起使用。 |
| 目标 | 从与当前所选 LUN 关联的 iSCSI 目标列表中删除目标。 仅与 VDS 1.1 提供程序一起使用。 |
| `<n> [,<n> [,…]]` | 用于**控制器**或**目标**参数。 指定要设置为非活动或取消关联的控制器或 iSCSI 目标的编号。 |
| `<n-m>[,<n-m>[,…]]` | 与**端口**参数一起使用。 使用控制器号（*n*）和端口号（*m*）对指定要设置为非活动状态的控制器端口。 |

#### <a name="example"></a>示例

```
DISKRAID> SEL LUN 5
LUN 5 is now the selected LUN.

DISKRAID> ASSOCIATE PORTS 0-0,0-1
Controller port associations changed.
(Controller ports active after this command: Ctlr 0 Port 0, Ctlr 0 Port 1)

DISKRAID> ASSOCIATE PORTS ADD 1-1
Controller port associations changed.
(Controller ports active after this command: Ctlr 0 Port 0, Ctlr 0 Port 1, Ctlr 1 Port 1)

DISKRAID> DISSOCIATE PORTS 0-0,1-1
Controller port associations changed.
(Controller ports active after this command: Ctlr 0 Port 1)
```

### <a name="exit"></a>exit

退出 Diskraid。

#### <a name="syntax"></a>语法

```
exit
```

### <a name="extend"></a>extend

通过将扇区添加到 LUN 的末尾来扩展当前选定的 LUN。 并非所有提供程序都支持扩展 Lun。 不扩展 LUN 上包含的任何卷或文件系统。 扩展 LUN 后，应使用**DiskPart 扩展**命令扩展关联的磁盘上结构。

#### <a name="syntax"></a>语法

```
extend lun [size=<LUN_size>] [drives=<drive_number>, [<drive_number>, ...]] [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 | 指定扩展 LUN 的大小（以 mb 为单位）。 必须指定*大小*或 `<drive>` 参数。 它们也可以一起使用。 如果未指定**size =** 参数，则 LUN 将按所有指定驱动器允许的最大大小进行扩展。 如果指定了**size =** 参数，则提供程序会从**驱动器 =** 参数指定的列表中选择驱动器，以创建 LUN。 若要使用其他单位指定大小，请在大小后立即使用以下可识别的后缀之一：<ul><li>**B**字节</li><li>**Kb** -kb</li><li>**MB** -mb</li><li>**Gb** -gb</li><li>**Tb** -tb</li><li>**Pb** -pb。</li></ul> |
| 驱动器 = | 指定 `<drive_number>` 创建 LUN 时要使用的驱动器的。 必须指定*大小*或 `<drive>` 参数。 它们也可以一起使用。 如果未指定**size =** 参数，则创建的 LUN 是所有指定驱动器允许的最大大小。 提供程序按尽可能指定的顺序使用驱动器。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="flushcache"></a>flushcache

清除当前所选控制器上的缓存。

#### <a name="syntax"></a>语法

```
flushcache controller
```

### <a name="help"></a>帮助

显示所有 Diskraid 命令的列表。

#### <a name="syntax"></a>语法

```
help
```

### <a name="importtarget"></a>importtarget

检索或设置当前所选子系统的当前卷影复制服务（VSS）导入目标。

#### <a name="syntax"></a>语法

```
importtarget subsystem [set target]
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 设置目标 | 如果已指定，则将当前选定的目标设置为当前所选子系统的 VSS 导入目标。 如果未指定，则该命令将检索为当前所选子系统设置的当前 VSS 导入目标。 |

### <a name="initiator"></a>initiator

检索有关本地 iSCSI 发起程序的信息。

#### <a name="syntax"></a>语法

```
initiator
```

### <a name="invalidatecache"></a>invalidatecache

使当前选定的控制器上的缓存失效。

#### <a name="syntax"></a>语法

```
invalidatecache controller
```

### <a name="lbpolicy"></a>lbpolicy

设置当前所选 LUN 上的负载平衡策略。

#### <a name="syntax"></a>语法

```
lbpolicy set lun type=<type> [paths=<path>-{primary | <weight>}[,<path>-{primary | <weight>}[,…]]]
lbpolicy set lun paths=<path>-{primary | <weight>}[,<path>-{primary | <weight>}[,…]]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| type | 指定负载平衡策略。 如果未指定类型，则必须指定**path**参数。 Type 可以是下列类型之一：<ul><li>**故障转移**-使用具有其他路径的主路径作为备份路径。</li><li>**ROUNDROBIN** -以循环方式使用所有路径，这将按顺序尝试每个路径。</li><li>**SUBSETROUNDROBIN** -以循环方式使用所有主路径;仅当所有主路径都出现故障时，才使用备份路径。</li><li>**DYNLQD** -使用包含最少活动请求数的路径。<li><li>**加权**-使用最小权重的路径（必须为每个路径分配一个权重）。</li><li>**LEASTBLOCKS** -使用包含最少块的路径。</li><li>**VENDORSPECIFIC** -使用特定于供应商的策略。</li></ul> |
| path | 指定路径是**主要**路径还是具有特定路径 `<weight>` 。 未指定的任何路径将隐式设置为备份。 列出的任何路径都必须是当前选定的 LUN 路径之一。 |

### <a name="list"></a>list

显示指定类型的对象的列表。

#### <a name="syntax"></a>语法

```
list {hbaports | iadapters | iportals | providers | subsystems | controllers | ports | drives | LUNs | tportals | targets | tpgroups}
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| hbaports | 列出有关 VDS 已知的所有 HBA 端口的摘要信息。 当前选定的 HBA 端口标有星号（*）。 |
| iadapters | 列出有关 VDS 已知的所有 iSCSI 发起程序适配器的摘要信息。 当前选定的发起程序适配器由星号（*）标记。 |
| iportals | 列出有关当前所选发起程序适配器中的所有 iSCSI 发起程序门户的摘要信息。 当前选定的发起程序门户标有星号（*）。 |
| providers | 列出有关 VDS 已知的每个提供程序的摘要信息。 当前选定的提供程序以星号（*）标记。 |
| 子系统 | 列出系统中每个子系统的摘要信息。 当前选定的子系统标有星号（*）。 |
| 控制器 | 列出有关当前所选子系统中每个控制器的摘要信息。 当前选定的控制器标有星号（*）。 |
| ports | 列出有关当前所选控制器中的每个控制器端口的摘要信息。 当前选择的端口标有星号（*）。 |
| 驱动器 | 列出有关当前所选子系统中每个驱动器的摘要信息。 当前选定的驱动器标有星号（*）。 |
| lun | 列出有关当前所选子系统中的每个 LUN 的摘要信息。 当前选定的 LUN 标有星号（*）。 |
| tportals | 列出当前所选子系统中所有 iSCSI 目标门户的摘要信息。 当前选定的目标门户标有星号（*）。 |
| 目标 | 列出当前所选子系统中的所有 iSCSI 目标的摘要信息。 当前选定的目标由星号（*）标记。 |
| tpgroups | 列出有关当前所选目标中所有 iSCSI 目标门户组的摘要信息。 当前选定的门户组标有星号（*）。 |

### <a name="login"></a>login

将指定的 iSCSI 发起程序适配器记录到当前选定的 iSCSI 目标。

#### <a name="syntax"></a>语法

```
login target iadapter=<iadapter> [type={manual | persistent | boot}] [chap={none | oneway | mutual}] [iportal=<iportal>] [tportal=<tportal>] [<flag> [<flag> […]]]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| type | 指定要执行的登录类型：**手动**或**持久**。 如果未指定，将执行手动登录。 |
| manual | 手动登录。 还有一个用于将来开发且当前未使用的**启动**选项。 |
| 式 | 重新启动计算机时自动使用相同的登录名。 |
| chap | 指定要使用的 CHAP 身份验证类型： **none**、**单向**chap 或**相互**chap;如果未指定，将不使用任何身份验证。 |
| 门户 | 指定当前所选子系统中用于登录的可选目标门户。 |
| iportal | 指定指定发起程序适配器中用于登录的可选发起程序门户。 |
| `<flag>` | 由三个字母的首字母缩写标识：<ul><li>**Ip** -需要 IPsec</li><li>**EMP** -启用多路径</li><li>**EHD** -启用标头摘要</li><li>**EDD** -启用数据摘要</li></ul> |

### <a name="logout"></a>logout

将指定的 iSCSI 发起程序适配器记录在当前选定的 iSCSI 目标外。

#### <a name="syntax"></a>语法

```
logout target iadapter= <iadapter>
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| iadapter | 指定发起程序适配器以及要从中注销的登录会话。 |

### <a name="maintenance"></a>维护

对指定类型的当前选定对象执行维护操作。

#### <a name="syntax"></a>语法

```
maintenance <object operation> [count=<iteration>]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<object>` | 指定要对其执行操作的对象的类型。 *对象*类型可以是**子系统**、**控制器**、**端口、驱动器**或**LUN**。 |
| `<operation>` | 指定要执行的维护操作。 *操作*类型可以是**spinup**、 **spindown**、**闪烁**、**嘟嘟声**或**ping**。 必须指定一个*操作*。 |
| 计数 = | 指定*操作*的重复次数。 通常使用**闪烁**、**嘟嘟声**或**ping**来使用。 |

### <a name="name"></a>name

将当前所选子系统、LUN 或 iSCSI 目标的友好名称设置为指定名称。

#### <a name="syntax"></a>语法

```
name {subsystem | lun | target} [<name>]
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<name>` | 指定子系统、LUN 或目标的名称。 名称的长度必须小于64个字符。 如果未提供任何名称，则会删除现有名称（如果有）。 |

### <a name="offline"></a>offline

将指定类型的当前选定对象的状态设置为**脱机**。

#### <a name="syntax"></a>语法

```
offline <object>
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<object>` | 指定要对其执行此操作的对象的类型。 类型可以是：**子系统**、**控制器**、**驱动器**、 **LUN**或**门户**。 |

### <a name="online"></a>联机

将指定类型的选定对象的状态设置为 "**联机**"。 如果对象为**hbaport**，则将当前所选 HBA 端口的路径状态更改为 "**联机**"。

#### <a name="syntax"></a>语法

```
online <object>
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<object>` | 指定要对其执行此操作的对象的类型。 类型可以是： **hbaport**、**子系统**、**控制器**、**驱动器**、 **LUN**或**门户**。 |

### <a name="recover"></a>recover

执行必要的操作，如重新同步或热备用，以修复当前选定的容错 LUN。 例如，RECOVER 可能导致热备用绑定到磁盘或其他磁盘区重新分配的 RAID 集。

#### <a name="syntax"></a>语法

```
recover <lun>
```

### <a name="reenumerate"></a>reenumerate

指定类型的 Reenumerates 对象。 如果使用 "扩展 LUN" 命令，则在使用 reenumerate 命令之前，必须使用 refresh 命令更新磁盘大小。

#### <a name="syntax"></a>语法

```
reenumerate {subsystems | drives}
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 子系统 | 查询提供程序以发现在当前选定的提供程序中添加的任何新子系统。 |
| 驱动器 | 查询内部 i/o 总线，以发现当前所选子系统中添加的任何新驱动器。 |

### <a name="refresh"></a>refresh

刷新当前所选提供程序的内部数据。

#### <a name="syntax"></a>语法

```
refresh provider
```

### <a name="rem"></a>rem

用于注释脚本。

#### <a name="syntax"></a>语法

```
Rem <comment>
```

### <a name="remove"></a>remove

从当前所选的目标门户组中删除指定的 iSCSI 目标门户。

#### <a name="syntax"></a>语法

```
remove tpgroup tportal=<tportal> [noerr]
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| tpgroup 门户 =`<tportal>` | 指定要删除的 iSCSI 目标门户。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="replace"></a>replace

将指定的驱动器替换为当前选定的驱动器。 指定的驱动器可能不是当前所选驱动器。

#### <a name="syntax"></a>语法

```
replace drive=<drive_number>
```

##### <a name="parameter"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 驱动器 = | 指定 `<drive_number>` 要替换的驱动器的。 |

### <a name="reset"></a>reset

重置当前选定的控制器或端口。

#### <a name="syntax"></a>语法

```
reset {controller | port}
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| controller | 重置控制器。 |
| port | 重置端口。 |

### <a name="select"></a>select

显示或更改当前选定的对象。

#### <a name="syntax"></a>语法

```
select {hbaport | iadapter | iportal | provider | subsystem | controller | port | drive | lun | tportal | target | tpgroup } [<n>]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 对象 | 指定要选择的对象类型，包括：**提供程序**、**子系统**、**控制器**、**驱动器**或**LUN**。 |
| hbaport`[<n>]` | 将焦点设置到指定的本地 HBA 端口。 如果未指定 HBA 端口，则该命令将显示当前所选 HBA 端口（如果有）。 指定无效的 HBA 端口索引将导致未处于焦点的 HBA 端口。 选择 HBA 端口会取消选择任何所选的发起程序适配器和发起程序门户。 |
| iadapter`[<n>]` | 将焦点设置到指定的本地 iSCSI 发起程序适配器。 如果未指定发起程序适配器，则该命令将显示当前所选的发起程序适配器（如果有）。 指定无效的发起程序适配器索引会导致不存在焦点发起程序适配器。 选择发起程序适配器会取消选择任何所选 HBA 端口和发起程序门户。 |
| iportal`[<n>]` | 将焦点设置到所选 iSCSI 发起程序适配器中指定的本地 iSCSI 发起程序门户。 如果未指定发起程序门户，则该命令将显示当前所选的发起程序门户（如果有）。 指定无效的发起方门户索引会导致所选的发起方门户。 |
| 程序`[<n>]` | 将焦点设置到指定的提供程序。 如果未指定提供程序，则该命令将显示当前所选的提供程序（如果有）。 指定无效的提供程序索引将导致没有关注的提供程序。 |
| 适用`[<n>]` | 将焦点设置到指定的子系统。 如果未指定子系统，则该命令将显示具有焦点的子系统（如果有）。 指定无效的子系统索引将导致没有关注的子系统。 选择子系统将隐式选择其关联的提供程序。 |
| 控制器`[<n>]` | 将焦点设置到当前所选子系统中的指定控制器。 如果未指定控制器，则该命令将显示当前所选的控制器（如果有）。 指定无效的控制器索引将导致焦点控制器不存在。 选择控制器会取消选择任何所选控制器端口、驱动器、Lun、目标门户、目标和目标门户组。 |
| 口`[<n>]` | 将焦点设置到当前所选控制器中的指定控制器端口上。 如果未指定端口，则该命令将显示当前所选端口（如果有）。 指定无效的端口索引将导致所选端口无效。 |
| 光驱`[<n>]` | 将焦点设置到当前所选子系统中的指定驱动器或物理主轴。 如果未指定驱动器，则该命令将显示当前所选驱动器（如果有）。 指定无效的驱动器索引将导致没有聚焦的驱动器。 选择驱动器将取消选择任何选定的控制器、控制器端口、Lun、目标门户、目标和目标门户组。 |
| lun`[<n>]` | 将焦点设置到当前所选子系统中的指定 LUN。 如果未指定 LUN，则该命令将显示当前所选的 LUN （如果有）。 指定无效的 LUN 索引将导致选定的 LUN。 选择 LUN 会取消选择任何所选的控制器、控制器端口、驱动器、目标门户、目标和目标门户组。 |
| 门户`[<n>]` | 将焦点设置到当前所选子系统中的指定 iSCSI 目标门户。 如果未指定目标门户，则该命令将显示当前所选的目标门户（如果有）。 指定无效的目标门户索引将导致选定的目标门户。 选择目标门户会取消选择任何控制器、控制器端口、驱动器、Lun、目标和目标门户组。 |
| 靶`[<n>]` | 将焦点设置到当前所选子系统中的指定 iSCSI 目标。 如果未指定目标，则该命令将显示当前选择的目标（如果有）。 指定无效的目标索引将导致选定的目标无效。 选择目标会取消选择任何控制器、控制器端口、驱动器、Lun、目标门户和目标门户组。 |
| tpgroup`[<n>]` | 在当前选定的 iSCSI 目标内将焦点设置到指定的 iSCSI 目标门户组。 如果未指定目标门户组，则该命令将显示当前所选的目标门户组（如果有）。 指定无效的目标门户组索引将导致未处于焦点的目标门户组。 |
|`[<n>]` | 指定 `<object number>` 要选择的。 如果指定的无效 `<object number>` ，则会清除指定类型的对象的任何现有选择。 如果未 `<object number>` 指定，则显示当前的对象。

### <a name="setflag"></a>setflag

将当前所选驱动器设置为热备用。 不能将热备用用于普通 LUN 绑定操作。 它们只保留用于故障处理。 驱动器当前不得绑定到任何现有的 LUN。

#### <a name="syntax"></a>语法

```
setflag drive hotspare={true | false}
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 是 | 选择当前所选驱动器作为热备用。 |
| false | 取消选择当前选定的驱动器作为热备用。 |

### <a name="shrink"></a>缩减

减小所选 LUN 的大小。

#### <a name="syntax"></a>语法

```
shrink lun size=<n> [noerr]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| 大小 | 指定所需的空间量（以兆字节（MB）为单位）以减小 LUN 的大小。 若要使用其他单位指定大小，请在大小后立即使用以下可识别的后缀之一：<ul><li>**B**字节</li><li>**Kb** -kb</li><li>**MB** -mb</li><li>**Gb** -gb</li><li>**Tb** -tb</li><li>**Pb** -pb。 |
| noerr | 仅用于脚本。 遇到错误时，Diskraid 将继续处理命令，就像未发生错误一样。 |

### <a name="standby"></a>转入

将当前所选主机总线适配器（HBA）端口的路径状态更改为 "备用"。

#### <a name="syntax"></a>语法

```
standby hbaport
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| hbaport | 将当前所选主机总线适配器（HBA）端口的路径状态更改为 "备用"。 |

### <a name="unmask"></a>取消屏蔽

使当前选定的 Lun 可从指定的主机访问。

#### <a name="syntax"></a>语法

```
unmask lun {all | none | [add] wwn=<hexadecimal_number> [;<hexadecimal_number> [;…]] | [add] initiator=<initiator>[;<initiator>[;…]]} [uninstall]
```

##### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| all | 指定应对 LUN 的所有主机进行访问。 但是，不能取消对 iSCSI 子系统中的所有目标的 LUN 的屏蔽。<P>在运行该命令之前，必须先注销目标 `unmask lun all` 。 |
| 无 | 指定 LUN 不应可供任何主机访问。<P>在运行该命令之前，必须先注销目标 `unmask lun none` 。 |
| add | 指定必须将指定的主机添加到可从其访问此 LUN 的现有主机列表。 如果未指定此参数，则提供的主机列表将替换此 LUN 可访问的主机的现有列表。 |
| wwn = | 指定一个十六进制数字的列表，该数字表示要从其访问 LUN 或主机的全球名称。 若要屏蔽/屏蔽到光纤通道子系统中的一组特定主机，可以在相关主机计算机上键入以分号分隔的 WWN 列表。 |
| 发起程序 = | 指定要使当前选定的 LUN 可访问的 iSCSI 发起程序的列表。 要屏蔽/取消屏蔽到 iSCSI 子系统中的一组特定主机，可以在相关主机计算机上键入以分号分隔的 iSCSI 发起程序名称列表。 |
| 卸载 | 如果已指定，则在屏蔽 LUN 之前，卸载与本地系统上的 LUN 关联的磁盘。 |

## <a name="scripting-diskraid"></a>脚本 Diskraid

在运行受支持的 Windows Server 版本的任何计算机上，可以使用关联的 VDS 硬件提供程序为 Diskraid 编写脚本。 若要调用 Diskraid 脚本，请在命令提示符下键入：

```
diskraid /s <script.txt>
```

默认情况下，如果脚本中出现问题，Diskraid 将停止处理命令并返回错误代码。 若要继续运行脚本并忽略错误，请在命令中包含**noerr**参数。 这就允许使用单个脚本删除子系统中的所有 Lun，而不考虑 Lun 的总数量。 并非所有命令都支持**noerr**参数。 不管是否包含**noerr**参数，都将始终在命令语法错误上返回错误。

## <a name="diskraid-error-codes"></a>Diskraid 错误代码

| 错误代码 | 错误说明 |
| ---------- | ----------------- |
| 0 | 未发生错误。 成功运行整个脚本。 |
| 1 | 出现异常情况。 |
| 2 | 在 Diskraid 命令行上指定的参数不正确。 |
| 3 | Diskraid 无法打开指定的脚本或输出文件。 |
| 4 | 某个 Diskraid 使用的服务返回了故障。 |
| 5 | 出现一个命令语法错误。 脚本失败，因为不正确地选择了对象或对象不能与此命令一起使用。 |

## <a name="example"></a>示例

若要查看计算机上子系统0的状态，请键入：

```
diskraid
```

按 ENTER 键并显示类似如下的输出：

```
Microsoft Diskraid version 5.2.xxxx
Copyright (©) 2003 Microsoft Corporation
On computer: COMPUTER_NAME
```

若要选择子系统0，请在 Diskraid 提示符下键入以下内容：

```
select subsystem 0
```

按 ENTER 键并显示类似如下的输出：

```
Subsystem 0 is now the selected subsystem.

DISKRAID> list drives

  Drive ###  Status      Health          Size      Free    Bus  Slot  Flags
  ---------  ----------  ------------  --------  --------  ---  ----  -----
  Drive 0    Online      Healthy         107 GB    107 GB    0     1
  Drive 1    Offline     Healthy          29 GB     29 GB    1     0
  Drive 2    Online      Healthy         107 GB    107 GB    0     2
  Drive 3    Not Ready   Healthy          19 GB     19 GB    1     1
```

若要退出 Diskraid，请在 Diskraid 提示符下键入以下内容：

```
exit
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)