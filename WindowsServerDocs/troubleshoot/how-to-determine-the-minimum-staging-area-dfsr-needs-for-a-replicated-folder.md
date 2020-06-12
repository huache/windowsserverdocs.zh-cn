---
title: 如何确定复制文件夹的最小临时区域 DFSR 需求
description: 本文提供了有关如何计算 DFSR 正常运行所需的最小临时区域的快速参考指南。
ms.prod: windows-server
ms.technology: server-general
ms.date: 06/10/2020
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: 5e5bfdbb90d2b3e631aaa020a173eca779f0d6b3
ms.sourcegitcommit: fa9a8badf4eb366aeeca7d2905e2cad711ee8dae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2020
ms.locfileid: "84715001"
---
# <a name="how-to-determine-the-minimum-staging-area-dfsr-needs-for-a-replicated-folder"></a>如何确定复制文件夹的最小临时区域 DFSR 需求

本文提供了有关如何计算 DFSR 正常运行所需的最小临时区域的快速参考指南。 低于这些值的值可能会导致复制缓慢或停止。 

请记住，这些*只*是最小。 考虑暂存区域大小时，临时区域越大越好，直到复制文件夹的大小就越好。 请参阅本文末尾的 "如何确定是否有临时区域问题" 一节，了解有关为什么要使用适当调整大小的暂存区域很重要的详细信息。

> [!Note]
> 我们还提供了一个修补程序，可帮助你计算暂存大小。 [DFS 复制（DFSR）管理接口的更新可用](https://support.microsoft.com/kb/2607047)

## <a name="rules-of-thumb"></a>经验法则

**Windows Server 2003 R2** –过渡区域配额必须与已复制文件夹中的9个最大文件大小相同

**Windows Server 2008 和 2008 R2** –过渡区域配额必须与已复制文件夹中32最大的文件一样大

初始复制将比日常复制更多地使用临时区域。 如果你有可用的驱动器空间，则强烈建议在初始复制期间将暂存区域设置得高于最小值

## <a name="where-do-i-get-powershell"></a>在哪里可以获取 PowerShell？

PowerShell 包含在 Windows 2008 和更高版本中。 必须在 Windows Server 2003 上安装 PowerShell。 可在[此处](https://support.microsoft.com/kb/968930)下载适用于 Windows 2003 的 PowerShell。

## <a name="how-do-you-find-these-x-largest-files"></a>如何查找这些 X 最大的文件？

使用 PowerShell 脚本查找32或9个最大的文件，并确定它们最多可添加多少千兆字节数（这归功于 PowerShell 命令的需要 Pyle）。 接下来，我将向您展示三个 PowerShell 脚本。 每个都可用于自己的;但是，数字3是最有用的。

1. 运行下面的命令：  
   ```Powershell
   Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | ft name,length -wrap –auto
   ```
   
   此命令将返回文件的名称和文件大小（以字节为单位）。 如果要了解哪些32文件在已复制文件夹中最大，以便可以 "访问" 其所有者，这一点很有用。

2. 运行下面的命令：  
   ```Poswershell
   Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | measure-object -property length –sum
   ```
   此命令将返回文件夹中最大32文件的总字节数，而不列出文件名。

3. 运行下面的命令：  
   ```Poswershell
   $big32 = Get-ChildItem c:\\temp -recurse | Sort-Object length -descending | select-object -first 32 | measure-object -property length –sum
   
   $big32.sum /1gb
   ```
   此命令将获取文件夹中最大的32文件的总字节数，并执行 math 将字节转换为千兆字节。 此命令为两个单独的行。 可以同时将这两个文件粘贴到 PowerShell 命令行界面中，或将其重新运行。

## <a name="manual-walkthrough"></a>手动演练

为了说明该过程并希望提高对我们所做工作的了解，我将手动单步执行每个部分。

运行命令1将返回类似于以下输出的结果。 对于简洁起见，此示例只使用16个文件。 对于 Windows 2008 和更高版本的操作系统，始终使用32，Windows 2003 R2 始终使用9

### <a name="example-data-returned-by-powershell"></a>PowerShell 返回的示例数据

<table>
<tbody>
<tr class="odd">
<td>“属性”</td>
<td>长度</td>
</tr>
<tr class="even">
<td><strong>File5.zip</strong></td>
<td>10286089216</td>
</tr>
<tr class="odd">
<td><strong>archive.zip</strong></td>
<td>6029853696</td>
</tr>
<tr class="even">
<td><strong>BACKUP.zip</strong></td>
<td>5751522304</td>
</tr>
<tr class="odd">
<td> <strong>file9.zip</strong></td>
<td>5472683008</td>
</tr>
<tr class="even">
<td><strong>MENTOS.zip</strong></td>
<td>5241586688</td>
</tr>
<tr class="odd">
<td><strong>File7.zip</strong></td>
<td>4321264640</td>
</tr>
<tr class="even">
<td><strong>file2.zip</strong></td>
<td>4176765952</td>
</tr>
<tr class="odd">
<td><strong>frd2.zip</strong></td>
<td>4176765952</td>
</tr>
<tr class="even">
<td><strong>BACKUP.zip</strong></td>
<td>4078994432</td>
</tr>
<tr class="odd">
<td><strong>File44.zip</strong></td>
<td>4058424320</td>
</tr>
<tr class="even">
<td><strong>file11.zip</strong></td>
<td>3858056192</td>
</tr>
<tr class="odd">
<td><strong>Backup2.zip</strong></td>
<td>3815138304</td>
</tr>
<tr class="even">
<td><strong>BACKUP3.zip</strong></td>
<td>3815138304</td>
</tr>
<tr class="odd">
<td><strong>Current.zip</strong></td>
<td>3576931328</td>
</tr>
<tr class="even">
<td><strong>Backup8.zip</strong></td>
<td>3307488256</td>
</tr>
<tr class="odd">
<td><strong>File999.zip</strong></td>
<td>3274982400</td>
</tr>
</tbody>
</table>

### <a name="how-to-use-this-data-to-determine-the-minimum-staging-area-size"></a>如何使用此数据来确定最小临时区域大小：

  - Name = 文件的名称。
  - 长度 = 字节
  - 1 Gb = 1073741824 字节

首先，您需要总计字节数。 接下来，将总数除以1073741824。 我建议使用 Excel 或您选择的电子表格来完成数学计算。

### <a name="example"></a>示例

在上面的示例中，总字节数 = 75241684992。 若要获取所需的最小临时区域配额，需要将75241684992除以1073741824。

> 75241684992/1073741824 = 70.07 GB

根据此数据，如果向上舍入到最接近的整数，我会将过渡区域设置为 71 GB。

### <a name="real-world-scenario"></a>实际方案：

尽管手动演练很有趣，但可能不是您自己的时间来自己完成数学计算。 若要自动执行此过程，请使用上述示例中的命令3。 结果将如下所示

> [![影像](https://msdnshared.blob.core.windows.net/media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/58/02/metablogapi/8204.image_thumb_02CB3914.png "image")](https://msdnshared.blob.core.windows.net/media/TNBlogsFS/prod.evol.blogs.technet.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/58/02/metablogapi/0876.image_03A39EFE.png)

除了舍入为最接近的整数以外，使用示例命令3不进行任何额外的工作，我可以确定我需要用于 d：文档的 6 GB 暂存区域配额 \\ 。

## <a name="do-i-need-to-reboot-or-restart-the-service-for-the-changes-to-be-picked-up"></a>是否需要重新启动或重新启动服务才能获取所做的更改？

对临时区域配额的更改不需要重新启动或重新启动服务即可生效。 需要等待 AD 复制和 DFSR 的 AD 轮询周期，以应用所做的更改。

## <a name="how-to-determine-if-you-have-a-staging-area-problem"></a>如何确定是否有临时区域问题

可以通过监视 DFSR 服务器上的特定事件 Id 来检测临时区域问题。 事件列表为4202、4204、4206、4208和4212。 下面列出了这些事件的文本。 必须区分4202与4204以及其他事件。 在正常操作情况下，可以记录大量的4202和4204事件。 将4202和4204事件视为类似于采取脉冲，而4206、4208和4212就像披肩的难题。 下面介绍如何解释下面的4202和4204事件。

### <a name="staging-area-events"></a>临时区域事件

> 事件 ID： **4202**  
> 严重性：**警告**
> 
> DFS 复制服务检测到用于本地路径（路径）上已复制文件夹的暂存空间高于高水位线。 服务将尝试删除最旧的暂存文件。 性能可能会受到影响。
> 
> 事件 ID： **4204**  
> 严重性：**信息**
> 
> DFS 复制服务已成功地删除了本地路径（路径）上已复制文件夹的旧暂存文件。 暂存空间现在低于高水位线。
> 
> 事件 ID： **4206**  
> 严重性：**警告**
> 
> DFS 复制服务未能清除本地路径（路径）上已复制文件夹的旧暂存文件。 此服务可能无法复制某些大型文件，并且已复制文件夹可能不同步。服务将在（x）分钟内自动重试临时空间清除。 如果该服务检测到一些暂存文件已经解除锁定，则该服务可能会提前进行清理。
> 
> 事件 ID： **4208**  
> 严重性：**警告**
> 
> DFS 复制服务检测到临时空间使用量高于本地路径（路径）的已复制文件夹的暂存配额。 此服务可能无法复制某些大型文件，并且已复制文件夹可能不同步。服务将尝试自动清理暂存空间。
> 
> 事件 ID： **4212**  
> 严重性：**错误**
> 
> 由于临时路径无效或无法访问，因此 DFS 复制服务无法复制本地路径（路径）上的已复制文件夹。

## <a name="what-is-the-difference-between-4202-and-4208"></a>4202和4208之间的区别是什么？

事件4202和4208具有相似的文本;例如，DFSR 检测到临时区域使用量超过高水位线。 不同之处在于，在运行临时区域清理并仍超出暂存配额后，将记录4208。 4202是正常和预期事件，而4208是异常情况，需要介入。

## <a name="how-many-4202-4204-events-are-too-many"></a>多少4202，4204事件太多？

此问题没有单个答案。 不同于4206、4208或4212事件，它们始终都是错误的，表示需要执行操作，4202和4204事件发生在正常的操作条件下。 看到许多4202和4204事件*可能*表示存在问题。 注意事项：

1.  已复制文件夹（RF）日志记录4202正在执行初始复制？ 如果是这样，则记录4202和4204事件是正常的。 在初始复制期间，你可能希望尽可能少地将这些内容保留在初始复制中，方法是提供尽可能多的临时区域
2.  只需检查4202事件的总数就够了。 必须知道每个 RF 记录了多少。 如果在24小时内为一个 RF 记录了 20 4202 事件，此时间较高。 但是，如果您有20个已复制文件夹，并且每个文件夹有一个事件，那么您就会很好。
3.  你应检查几天的数据，以确定趋势。

我通常会在正常操作情况下，让客户每天每个已复制文件夹不超过 1 4202 事件。 "正常" 表示不发生初始复制。 为此，我们的原因如下：

1.  清理临时区域所用的时间是指不复制文件所花费的时间。 清理临时区域时复制已暂停。
2.  DFSR 从使用它进行 RDC 和跨文件 RDC，或将相同文件复制到其他成员的完整临时区域受益
3.  记录的4202和4204事件越多，就会遇到这样的情况： DFSR 无法清理临时区域，或者需要提前从临时区域清除文件。
4.  4206、4208和4212事件在我的体验中，始终前后都有大量的4202和4204事件。

尽管每天每个 RF 仅允许 1 4202 事件是保守的，但它极大地降低了运行到临时区域问题的几率，并可更好地利用 DFSR 服务器的资源来复制文件。


