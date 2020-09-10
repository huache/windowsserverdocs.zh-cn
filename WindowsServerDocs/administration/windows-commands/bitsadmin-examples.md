---
title: bitsadmin 示例
description: 演示如何使用 bitsadmin 工具执行最常见任务的示例。
ms.topic: reference
ms.assetid: cb8f8374-ba6e-4a68-85a1-9a95b8215354
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 05/31/2018
ms.openlocfilehash: a40091e71739cb2604a86301e9de24a27a7ecd84
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632337"
---
# <a name="bitsadmin-examples"></a>bitsadmin 示例

下面的示例演示如何使用 `bitsadmin` 工具执行最常见的任务。

## <a name="transfer-a-file"></a>传输文件

若要创建作业，请添加文件，激活传输队列中的作业并完成该作业：

`bitsadmin /transfer myDownloadJob /download /priority normal https://downloadsrv/10mb.zip c:\\10mb.zip`

在传输完成或发生错误之前，BITSAdmin 会继续在 MS-DOS 窗口中显示进度信息。

## <a name="create-a-download-job"></a>创建下载作业

若要创建名为 *myDownloadJob*的下载作业：

```
bitsadmin /create myDownloadJob
```

BITSAdmin 返回一个用于唯一标识该作业的 GUID。 在后续调用中使用 GUID 或作业名称。 以下文本是示例输出。

### <a name="sample-output"></a>示例输出

`created job {C775D194-090F-431F-B5FB-8334D00D1CB6}`

## <a name="add-files-to-the-download-job"></a>将文件添加到下载作业

若要将文件添加到作业：

```
bitsadmin /addfile myDownloadJob https://downloadsrv/10mb.zip c:\\10mb.zip
```

对要添加的每个文件重复此调用。 如果有多个作业使用 *myDownloadJob* 作为其名称，则必须使用作业的 GUID 来唯一地标识该作业才能完成。

## <a name="activate-the-download-job"></a>激活下载作业

创建新作业后，BITS 会自动挂起该作业。 激活传输队列中的作业：

```
bitsadmin /resume myDownloadJob
```

如果有多个作业使用 *myDownloadJob* 作为其名称，则必须使用作业的 GUID 来唯一地标识该作业才能完成。

## <a name="determine-the-progress-of-the-download-job"></a>确定下载作业的进度

**/Info**开关返回作业的状态以及传输的文件和字节数。 当状态显示为时 `TRANSFERRED` ，表示 BITS 已成功传输作业中的所有文件。 还可以添加 **/verbose** 参数以获取作业的完整详细信息，并添加 **/list** 或 **/monitor** 以获取传输队列中的所有作业。

返回作业的状态：

```
bitsadmin /info myDownloadJob /verbose
```

如果有多个作业使用 *myDownloadJob* 作为其名称，则必须使用作业的 GUID 来唯一地标识该作业才能完成。

## <a name="complete-the-download-job"></a>完成下载作业

若要在状态更改为后完成作业 `TRANSFERRED` ：

```
bitsadmin /complete myDownloadJob
```

必须先运行该 `/complete` 开关，然后才能使用该作业中的文件。 如果有多个作业使用 *myDownloadJob* 作为其名称，则必须使用作业的 GUID 来唯一地标识该作业才能完成。

## <a name="monitor-jobs-in-the-transfer-queue-using-the-list-switch"></a>使用/list 开关监视传输队列中的作业

返回作业状态以及传输队列中所有作业传输的文件数和字节数：

```
bitsadmin /list
```

### <a name="sample-output"></a>示例输出

```
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN

Listed 2 job(s).
```

## <a name="monitor-jobs-in-the-transfer-queue-using-the-monitor-switch"></a>使用/monitor 开关监视传输队列中的作业

若要返回作业的状态以及传输队列中所有作业传输的文件数和字节数，请每隔5秒刷新一次数据：

```
bitsadmin /monitor
```

> [!NOTE]
> 若要停止刷新，请按 CTRL + C。

### <a name="sample-output"></a>示例输出

```
MONITORING BACKGROUND COPY MANAGER(5 second refresh)
{6AF46E48-41D3-453F-B7AF-A694BBC823F7} job1 SUSPENDED 0 / 0 0 / 0
{482FCAF0-74BF-469B-8929-5CCD028C9499} job2 TRANSIENT_ERROR 0 / 1 0 / UNKNOWN
{0B138008-304B-4264-B021-FD04455588FF} job3 TRANSFERRED 1 / 1 100379370 / 100379370
```

## <a name="monitor-jobs-in-the-transfer-queue-using-the-info-switch"></a>使用/info 开关监视传输队列中的作业

返回作业状态以及传输的文件数和字节数：

```
bitsadmin /info
```

### <a name="sample-output"></a>示例输出

```
GUID: {482FCAF0-74BF-469B-8929-5CCD028C9499} DISPLAY: myDownloadJob
TYPE: DOWNLOAD STATE: TRANSIENT_ERROR OWNER: domain\user
PRIORITY: NORMAL FILES: 0 / 1 BYTES: 0 / UNKNOWN
CREATION TIME: 12/17/2002 1:21:17 PM MODIFICATION TIME: 12/17/2002 1:21:30 PM
COMPLETION TIME: UNKNOWN
NOTIFY INTERFACE: UNREGISTERED NOTIFICATION FLAGS: 3
RETRY DELAY: 600 NO PROGRESS TIMEOUT: 1209600 ERROR COUNT: 0
PROXY USAGE: PRECONFIG PROXY LIST: NULL PROXY BYPASS LIST: NULL
ERROR FILE:    https://downloadsrv/10mb.zip -> c:\10mb.zip
ERROR CODE:    0x80072ee7 - The server name or address could not be resolved
ERROR CONTEXT: 0x00000005 - The error occurred while the remote file was being
processed.
DESCRIPTION:
JOB FILES:
0 / UNKNOWN WORKING https://downloadsrv/10mb.zip -> c:\10mb.zip
NOTIFICATION COMMAND LINE: none
```

## <a name="delete-jobs-from-the-transfer-queue"></a>从传输队列中删除作业

若要从传输队列中删除所有作业，请使用/reset 开关：

```
bitsadmin /reset
```

### <a name="sample-output"></a>示例输出

```
{DC61A20C-44AB-4768-B175-8000D02545B9} canceled.
{BB6E91F3-6EDA-4BB4-9E01-5C5CBB5411F8} canceled.
2 out of 2 jobs canceled.
```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

- [bitsadmin 命令](bitsadmin.md)
