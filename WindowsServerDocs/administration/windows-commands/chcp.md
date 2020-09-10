---
title: chcp
description: 用于更改活动控制台代码页的 chcp 命令的参考文章。
ms.topic: reference
ms.assetid: dc7b1c71-7b80-443d-9cf1-9bcf305aa1fd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ef70d73253782528bcd54f7cfd6f98de9d941702
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629835"
---
# <a name="chcp"></a>chcp

更改活动控制台代码页。 如果使用不带参数， **chcp** 显示活动控制台代码页的数目。

## <a name="syntax"></a>语法

```
chcp [<nnn>]
```

### <a name="parameters"></a>参数

| 参数 | 说明 |
| --------- | ----------- |
| `<nnn>` | 指定代码页。 |
| /? | 在命令提示符下显示帮助。 |

下表列出了每个受支持的代码页及其国家/地区或语言︰

| 代码页 | 国家/地区或语言 |
| --------- | -------------------------- |
| 437 | 美国 |
| 850 | 多语言 (拉丁文我) |
| 852 | 西里尔语 （俄语） |
| 855 | 西里尔语 （俄语） |
| 857 | 土耳其语 |
| 860 | 葡萄牙语 |
| 861 | 冰岛语 |
| 863 | 加拿大法语 |
| 865 | 北欧 |
| 866 | 俄语 |
| 869 | 现代希腊语 |
| 936 | 中文 |

#### <a name="remarks"></a>备注

- 仅与 Windows 一起安装的原始设备制造商 (OEM) 代码页正常显示在命令提示符窗口使用光栅字体。 在全屏幕模式下或使用 TrueType 字体的命令提示符窗口中，其他代码页正确显示。

- 不需要像在 MS-DOS) 中 (准备代码页。

- 之后启动的程序，将分配新的代码页使用新的代码页。 但是，程序 (在分配新代码页之前启动 Cmd.exe) ，将继续使用原始代码页。

## <a name="examples"></a>示例

若要查看活动的代码页设置，请键入︰

```
chcp
```

将显示一条类似于以下内容的消息： `Active code page: 437`

若要将活动代码页更改为 850 (多语言) ，请键入：

```
chcp 850
```

如果指定的代码页无效，则会显示以下错误消息： `Invalid code page`

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)
