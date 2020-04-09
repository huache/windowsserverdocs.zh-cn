---
title: typeperf
description: 适用于 typeperf 的 Windows 命令主题，它将性能数据写入到 "命令" 窗口或日志文件。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 0c7ca89a-03b3-4626-afcf-ef8565e90043
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ac5f7def37939a472eb8f47cf65edf184a2fe2fc
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80832360"
---
# <a name="typeperf"></a>typeperf

**Typeperf**命令将性能数据写入命令窗口或日志文件。 若要停止**typeperf**，请按 CTRL + C。

有关如何使用**typeperf**的示例，请参阅[示例](#BKMK_EXAMPLES)。

## <a name="syntax"></a>语法

```
typeperf <counter [counter ...]> [options]
typeperf -cf <filename> [options]
typeperf -q [object] [options]
typeperf -qx [object] [options]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<counter [counter [...]]>|指定要监视的性能计数器。|

> [!NOTE]
> **\<counter >** 是 *\\\\Computer\Object （实例） \Counter*格式的性能计数器的完整名称，例如\\的**用户时间 \\\% Server1\Processor （0）** 。

## <a name="options"></a>Options

|                   选项                   |                                                         说明                                                          |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
|                     -?                     |                                               显示区分上下文的帮助。                                               |
| -f \<CSV&verbar;TSV&verbar;BIN&verbar;SQL > |                                    指定输出文件格式。 默认值为 CSV。                                     |
|              -cf \<文件名 >               |              指定一个文件，其中包含要监视的性能计数器的列表，每行一个计数器。               |
|             -si < [[hh：] mm：] ss >             |                                  指定采样间隔。 默认值为1秒。                                   |
|               -o \<文件名 >               |     指定输出文件或 SQL 数据库的路径。 默认值为 STDOUT （写入到 "命令" 窗口）。      |
|                -q [对象]                 | 显示已安装的计数器（无实例）的列表。 若要列出一个对象的计数器，请包括对象名称。 \*\*\*示例 |
|                -qx [对象]                |        显示包含实例的已安装计数器列表。 若要列出一个对象的计数器，请包括对象名称。        |
|               -sc \<示例 >               |             指定要收集的样本数。 默认情况下，在按下 CTRL + C 之前，将收集数据。              |
|            -config \<文件名 >             |                                    指定包含命令选项的设置文件。                                     |
|            -s \<computer_name >             |                   指定要监视的远程计算机是否在计数器路径中指定了计算机。                    |
|                     -y                     |                                        在不提示的情况下回答 "是"。                                        |

## <a name="examples"></a><a name=BKMK_EXAMPLES></a>示例

- 下面的示例将本地计算机性能计数器的值 **\\\\processor （_Total）\% 处理器时间**，以默认采样间隔1秒，直到按下 CTRL + C。  
  ```
  typeperf \Processor(_Total)\% Processor Time
  ```  
- 下面的示例将文件**计数器**中的计数器列表的值写入到以5秒为单位的制表符分隔的**2** ，直到收集到50个样本。  
  ```
  typeperf -cf counters.txt -si 5 -sc 50 -f TSV -o domain2.tsv
  ```  
- 下面的示例查询计数器对象**PhysicalDisk**的已安装计数器，并将生成的列表写入文件**计数器 .txt**。  
  ```
  typeperf -qx PhysicalDisk -o counters.txt
  ```
