---
title: 排查事件 ID 50 错误消息
description: 描述如何排查事件 ID 50 错误消息
author: Deland-Han
manager: dcscontentpm
ms.topic: article
ms.author: delhan
ms.date: 12/25/2019
ms.openlocfilehash: 7ce3551b60450a3720c9350b5c55f396368490c1
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80815230"
---
# <a name="troubleshoot-the-event-id-50-error-message"></a>排查事件 ID 50 错误消息

##  <a name="symptoms"></a>症状

将信息写入物理磁盘时，系统事件日志中可能会记录以下两个事件消息： 

```
Event ID: 50 
Event Type: Warning 
Event Source: Ftdisk 
Description: {Lost Delayed-Write Data} The system was attempting to transfer file data from buffers to \Device\HarddiskVolume4. The write operation failed, and only some of the data may have been written to the file.
Data: 
0000: 00 00 04 00 02 00 56 00 
0008: 00 00 00 00 32 00 04 80 
0010: 00 00 00 00 00 00 00 00 
0018: 00 00 00 00 00 00 00 00 
0020: 00 00 00 00 00 00 00 00 
0028: 11 00 00 80 
```

```
Event ID: 26 
Event Type: Information
Event Source: Application Popup
Description: Windows - Delayed Write Failed : Windows was unable to save all the data for the file \Device\HarddiskVolume4\Program Files\Microsoft SQL Server\MSSQL$INSTANCETWO\LOG\ERRORLOG. The data has been lost. This error may be caused by a failure of your computer hardware or network connection.

Please try to save this file elsewhere.
```

这些事件 ID 消息意味着完全相同，并且出于相同的原因而生成。 对于本文，只描述了事件 ID 50 消息。

> [!NOTE] 
> 说明中的设备和路径以及特定的十六进制数据将有所不同。 

##  <a name="more-information"></a>详细信息

如果在 Windows 尝试将信息写入磁盘时出现一般错误，则会记录事件 ID 50 消息。 当 Windows 尝试将数据从文件系统缓存管理器（而不是硬件级别缓存）提交到物理磁盘时，会发生此错误。 此行为是 Windows 内存管理的一部分。 例如，如果程序发送写入请求，则缓存管理器会缓存写入请求，并通知程序写入已成功完成。 在以后的某个时间点，缓存管理器尝试将数据延迟写入物理磁盘。 当缓存管理器尝试将数据提交到磁盘时，写入数据时将发生错误，并且数据将从缓存中刷新并被丢弃。 写回缓存可提高系统性能，但丢失延迟写入失败可能会导致数据丢失和卷完整性损失。

务必要记住的是，并非所有 i/o 都由缓存管理器进行缓冲处理。 程序可以设置一个绕过缓存管理器的 FILE_FLAG_NO_BUFFERING 标志。 当 SQL 执行到数据库的关键写入时，此标志被设置为保证事务直接完成到磁盘中。 例如，对日志文件的非关键写入将执行缓冲 i/o 以提高总体性能。 事件 ID 50 消息从不由非缓冲 i/o 导致。

事件 ID 50 消息有几个不同的源。 例如，如果重定向程序存在网络连接问题，则会出现从 MRxSmb 源记录的事件 ID 50 消息。 若要避免执行不正确的故障排除步骤，请确保查看事件 ID 50 消息，确认它是指磁盘 i/o 问题，并且此文章适用。

事件 ID 50 消息类似于事件 ID 9 和事件 ID 11 消息。 尽管错误不像事件 ID 9 和事件 ID 11 消息指示的错误那样严重，但对于事件 id 9 和事件 ID 11 消息，可以使用与事件 id 50 消息相同的故障排除方法。 但请记住，堆栈中的任何内容都会导致丢失延迟写入，如筛选器驱动程序和微型端口驱动程序。 

您可以使用与任何伴随的 "磁盘" 错误相关的二进制数据（由事件 ID 9、11、51错误消息或其他消息指示）来帮助您确定问题。

###  <a name="how-to-decode-the-data-section-of-an-event-id-50-event-message"></a>如何解码事件 ID 50 事件消息的数据部分 

当你对 "摘要" 部分中包含的事件 ID 50 消息的示例中的数据进行解码时，你会发现尝试执行写操作失败，因为设备繁忙并且数据丢失。 本部分介绍如何对此事件 ID 50 消息进行解码。 

下表描述了此消息的每个偏移量表示的内容： 

|OffsetLengthValues|长度|值|
|-----------|------------|---------|
|0x00|2|不使用|
|0x02|2|转储数据大小 = 0x0004|
|0x04|2|字符串数 = 0x0002|
|0x06|2|字符串偏移量|
|0x08|2|事件类别|
|0x0c|4|NTSTATUS 错误代码 = 0x80040032 = IO_LOST_DELAYED_WRITE|
|0x10|8|不使用|
|0x18|8|不使用|
|0x20|8|不使用|
|0x28|4|NT 状态错误代码|

#### <a name="key-sections-to-decode"></a>要解码的关键部分

**错误代码**

在 "摘要" 部分的示例中，错误代码在第二行中列出。 此行以 "0008：" 开头，其中包含以下行中的最后四个字节：0008： 00 00 00 00 32 00 04 80 在这种情况下，错误代码为0x80040032。 下面的代码是用于错误50的代码，它对于所有事件 ID 50 消息都是相同的： IO_LOST_DELAYED_WRITEWARNINGNote 在将事件 ID 消息中的十六进制数据转换为状态代码时，请记住这些值采用小字节序格式表示。

**目标磁盘**

您可以使用事件 ID 消息的 "描述" 部分中的驱动器上列出的符号链接来识别要尝试写入的磁盘，例如： \Device\HarddiskVolume4。 有关如何识别驱动器的其他信息，请单击以下文章编号以查看 Microsoft 知识库中的文章： [159865](/EN-US/help/159865)如何将物理磁盘设备与事件消息区分开来

**最终状态代码**

最终状态代码是事件 ID 50 消息中最重要的信息片段。 这是发出 i/o 请求时返回的错误代码，它是信息的关键来源。 在 "摘要" 部分的示例中，最终状态代码在0x28 （以 "0028：" 开头的第六行）中列出，并且此行中仅包含四个八位字节： 

```
0028: 11 00 00 80 
```

在这种情况下，最终状态等于0x80000011。此状态代码映射到 STATUS_DEVICE_BUSY 并表示设备当前正忙。

>[!NOTE] 
> 将事件 ID 50 消息中的十六进制数据转换为状态代码时，请记住，值以小字节序格式表示。 因为状态代码是您感兴趣的唯一信息片段，所以以词语格式（而非字节）查看数据可能会更容易。 如果这样做，这些字节将采用正确的格式，并且数据可能更易于快速解释。

为此，请在 "**事件属性**" 窗口中单击 "**字词**"。 在 "数据字" 视图中，"症状" 部分中的示例如下所示：数据： 

```
() Bytes (.) 
Words 0000: 00040000 00560002 00000000 80040032 0010: 00000000 00000000 00000000 00000000 0020: 00000000 00000000 80000011
```

若要获取 Windows NT 状态代码的列表，请参阅 NTSTATUS。H 在 Windows 软件开发工具包（SDK）中。