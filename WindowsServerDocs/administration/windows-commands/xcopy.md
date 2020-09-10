---
title: xcopy
description: Xcopy 的参考文章，用于复制文件和目录，包括子目录。
ms.topic: reference
ms.assetid: 76a310d7-9925-4571-a252-0e28960d5f89
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 01/05/2019
ms.openlocfilehash: a3925843b80c60c689050c9a28236903e1912b3a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640679"
---
# <a name="xcopy"></a>xcopy

复制文件和目录，包括子目录。

有关如何使用此命令的示例，请参阅[示例](#examples)。

## <a name="syntax"></a>语法

```
Xcopy <Source> [<Destination>] [/w] [/p] [/c] [/v] [/q] [/f] [/l] [/g] [/d [:MM-DD-YYYY]] [/u] [/i] [/s [/e]] [/t] [/k] [/r] [/h] [{/a | /m}] [/n] [/o] [/x] [/exclude:FileName1[+[FileName2]][+[FileName3]] [{/y | /-y}] [/z] [/b] [/j]
```

### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<Source>|必需。 指定要复制的文件的位置和名称。 此参数必须包含驱动器或路径。|
|[\<Destination>]|指定要复制的文件的目标。 此参数可以包含驱动器号和冒号、目录名称、文件名或它们的组合。|
|/W|显示以下消息，并在开始复制文件之前等待你的响应：</br>**按任意键开始复制文件 () **|
|/p|提示您确认是否要创建每个目标文件。|
|/c|忽略错误。|
|/v|在将每个文件写入目标文件时对其进行验证，以确保目标文件与源文件完全相同。|
|/q|禁止显示 **xcopy** 消息。|
|/f|复制时显示源和目标文件名。|
|/l|显示要复制的文件的列表。|
|/g|如果目标不支持加密，则创建已解密的 *目标* 文件。|
|/d [： MM-DD]|仅复制在指定日期或指定日期之后更改的源文件。 如果不包括*MM DD*值，则**xcopy**会复制比现有*目标*文件新的所有*源文件*。 使用此命令行选项，可以更新已更改的文件。|
|/U|*仅**从源*副本复制文件。|
|/i|如果 *源* 是一个目录或包含通配符并且 *目标* 不存在，则 **xcopy** 假设 *destination* 指定目录名称并创建一个新目录。 然后， **xcopy** 将所有指定的文件复制到新目录中。 默认情况下， **xcopy** 会提示您指定 *目标* 是文件还是目录。|
|/s|复制目录和子目录，除非它们为空。 如果省略 **/s**，则 **xcopy** 在单个目录中工作。|
|/e|复制所有子目录（即使它们为空）。 使用 **/e** 和 **/s** 和 **/t** 命令行选项。|
|/t |复制 (的子目录结构，即树) ，而不是文件。 若要复制空目录，必须包含 **/e** 命令行选项。|
|遇到|复制文件并在 *目标* 文件上保留只读属性（如果存在于 *源文件* 上）。 默认情况下， **xcopy** 会删除只读属性。|
|/r|复制只读文件。|
|/h|复制具有隐藏文件和系统文件属性的文件。 默认情况下， **xcopy** 不复制隐藏文件或系统文件|
|/a|仅复制设置了存档文件属性的 *源文件* 。 **/a** 不修改源文件的 "存档文件" 属性。 有关如何使用 **attrib**设置存档文件属性的信息，请参阅 " [其他参考](#additional-references)"。|
|/m|复制设置了其存档文件属性的 *源文件* 。 与 **/a**不同， **/m** 关闭源中指定的文件中的存档文件属性。 有关如何使用 **attrib**设置存档文件属性的信息，请参阅 " [其他参考](#additional-references)"。|
|/n|使用 NTFS 短文件名或目录名称创建副本。 从 NTFS 卷向 FAT 卷复制文件或目录时，或者当 FAT 文件系统命名约定 (即，在*目标*文件系统上) 需要8.3 个字符时，需要 **/n** 。 *目标*文件系统可以是 FAT 或 NTFS。|
|/o| (DACL) 信息复制文件所有权和随机访问控制列表。|
|/x| (SACL) 信息复制文件审核设置和系统访问控制列表， (隐含 **/o**) 。|
|/exclude： FileName1 [+ [FileName2] [+ [FileName3] ( \) ]|指定文件的列表。 至少必须指定一个文件。 每个文件都包含搜索字符串，每个字符串在文件中的单独一行上。</br>如果任意字符串与要复制的文件的绝对路径的任何部分匹配，则将不复制该文件。 例如，如果指定字符串 **obj** ，将排除目录 **obj** 下的所有文件或扩展名为 **.obj** 的所有文件。|
|/y|禁止提示您确认是否要覆盖现有目标文件。|
|/-y|提示确认是否要覆盖现有目标文件。|
|/z|在可重启模式下通过网络复制。|
|/b|复制符号链接而不是文件。 此参数是在 Windows Vista®中引入的。|
|/j|无缓冲复制文件。 建议用于非常大的文件。 此参数是在 Windows Server 2008 R2 中添加的。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

- 使用 **/z**

  如果在复制阶段丢失连接 (例如，如果服务器脱机时断开连接) ，则在重新建立连接后会恢复。 **/z** 还显示每个文件完成的复制操作的百分比。

- 在 COPYCMD 环境变量中使用 **/y** 。

  可以在 COPYCMD 环境变量中使用 **/y** 。 可以通过在命令行上使用 **/-y** 来覆盖此命令。 默认情况下，系统将提示您进行覆盖。

- 复制加密的文件

  将加密文件复制到不支持 EFS 的卷会导致错误。 首先对文件进行解密，或将文件复制到支持 EFS 的卷。

- 追加文件

  若要附加文件，请为目标指定单个文件，但对于源 (使用多个文件，使用通配符或 file1 + file2 + file3 格式) 。

- *目标*的默认值

  如果省略 *Destination*， **xcopy** 命令会将文件复制到当前目录中。

- 指定 *目标* 是否为文件或目录

  如果 *目标* 不包含现有目录且不以反斜杠 (结尾 \) ，将显示以下消息：

  ```
  Does <Destination> specify a file name or directory name on the target(F = file, D = directory)?
  ```

如果要将文件复制到文件中，请按 F。 如果要将文件复制到目录，请按 D。

  您可以通过使用 **/i** 命令行选项来禁止显示此消息，这会导致 **xcopy** 假设目标是一个目录（如果源是多个文件或目录）。
- 使用 **xcopy** 命令为 *目标* 文件设置存档属性

  如果在源文件中设置了此属性， **xcopy** 命令将创建具有 archive 属性集的文件。 有关文件 **属性和属性**的详细信息，请参阅 " [其他参考](#additional-references)"。

- 比较 **xcopy** 和 **diskcopy**

  如果有包含子目录中的文件的磁盘，并且想要将文件复制到具有不同格式的磁盘，请使用 **xcopy** 命令而不是 **diskcopy**。 由于 **diskcopy** 命令按曲目复制磁盘曲目，因此源和目标磁盘的格式必须相同。 **Xcopy**命令没有这一要求。 使用 **xcopy** ，除非你需要完整的磁盘映像副本。

- **Xcopy**的退出代码

  若要处理**xcopy**返回的退出代码，请在批处理程序的**if**命令行中使用**ErrorLevel**参数。 有关使用 **if**处理退出代码的批处理程序的示例，请参阅 " [其他参考](#additional-references)"。 下表列出了每个退出代码和说明。

  |退出代码|说明|
  |---------|-----------|
  |0|复制文件时没有错误。|
  |1|找不到要复制的文件。|
  |2|用户按下 CTRL + C 终止了 **xcopy**。|
  |4|出现初始化错误。 内存或磁盘空间不足，或者您在命令行中输入了无效的驱动器名称或无效语法。|
  |5|出现磁盘写入错误。|

## <a name="examples"></a>示例

**1.** 若要复制所有文件和子目录 (包括从驱动器 a 到驱动器 B) 的任何空子目录，请键入：

```
xcopy a: b: /s /e
```

**2.** 若要包括上一示例中的任何系统文件或隐藏文件，请添加<strong>/h</strong> 命令行选项，如下所示：

```
xcopy a: b: /s /e /h
```

**3.** 若要使用自1993年12月29日以来发生更改的 \Rawdata 目录中的文件更新 \Reports 目录中的文件，请键入：

```
xcopy \rawdata \reports /d:12-29-1993
```

**4.** 若要更新上一个示例中的 \Reports 中存在的所有文件，而不考虑日期，请键入：

```
xcopy \rawdata \reports /u
```

**5.** 若要获取前一个命令要复制的文件的列表 (也就是说，不) 实际复制文件，请键入：

```
xcopy \rawdata \reports /d:12-29-1993 /l > xcopy.out
```

文件 xcopy 列出每个要复制的文件。

**6.** 若要将 \Customer 目录和所有子目录复制到 \\ \\ 网络驱动器 H：上的目录 Public\Address，请保留只读属性，并且在 H：上创建新文件时，请键入：

```
xcopy \customer h:\public\address /s /e /k /p
```

**7.** 若要发出前面的命令，请确保 **xcopy** 创建 \Address 目录（如果不存在），并取消创建新目录时显示的消息，并按如下所示添加 **/i** 命令行选项：

```
xcopy \customer h:\public\address /s /e /k /p /i
```

**8.** 您可以创建一个批处理程序来执行 **xcopy** 操作，并使用 batch **if** 命令处理退出代码（如果出现错误）。 例如，以下批处理程序对 **xcopy** 源和目标参数使用可替换参数：

```
@echo off
rem COPYIT.BAT transfers all files in all subdirectories of
rem the source drive or directory (%1) to the destination
rem drive or directory (%2)
xcopy %1 %2 /s /e
if errorlevel 4 goto lowmemory
if errorlevel 2 goto abort
if errorlevel 0 goto exit
:lowmemory
echo Insufficient memory to copy files or
echo invalid drive or command-line syntax.
goto exit
:abort
echo You pressed CTRL+C to end the copy operation.
goto exit
:exit
```

若要使用上述批处理程序将 C:\Prgmcode 目录及其子目录中的所有文件复制到驱动器 B，请键入：

```
copyit c:\prgmcode b:
```

命令解释器会将 *%1*和**B：** 替换为 *%2*的**C:\Prgmcode** ，**并使用** **/e**和 **/s**命令行选项。 如果 **xcopy** 遇到错误，批处理程序将读取退出代码，并转到相应 **IF ERRORLEVEL** 语句中指示的标签，然后显示相应的消息并退出批处理程序。

**9.** 此示例复制所有非空目录，并复制其名称与星号符号给定的模式匹配的文件。

```
xcopy .\toc*.yml ..\..\Copy-To\ /S /Y

rem Output example.
rem  .\d1\toc.yml
rem  .\d1\d12\toc.yml
rem  .\d2\toc.yml
rem  3 File(s) copied
```

在前面的示例中，此特定的源参数值 **。 \\即使 \* **删除了两个**路径 \\ 字符，** docker-compose.override.yml 也会复制相同的3个文件。 但是，如果从 source 参数中删除星号通配符，则不会复制任何文件 **。 \\docker-compose.override.yml**。

## <a name="additional-references"></a>其他参考

- [复制](copy.md)
- [移动](move.md)
- [目录](dir.md)
- [恶性](attrib.md)
- [Diskcopy](diskcopy.md)
- [If](if.md)
- [命令行语法项](command-line-syntax-key.md)
