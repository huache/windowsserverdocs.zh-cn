---
title: mode
description: 适用于 * * * * 的 Windows 命令主题
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: b59b04f2-b41d-42df-b5be-19c3721445b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 528277075f7448c86ca2d660c5e65c59098afbc0
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80839430"
---
# <a name="mode"></a>mode



显示系统状态、更改系统设置或重新配置端口或设备。 如果在没有参数的情况下使用，则**mode**显示控制台和可用 COM 设备的所有可控制属性。

您可以使用**模式**执行以下任务-每个任务都使用不同的语法：
-   [配置串行通信端口](#BKMK_1)
-   [显示所有设备或单个设备的状态](#BKMK_2)
-   [将输出从并行端口重定向到串行通信端口](#BKMK_3)
-   [选择、刷新或显示控制台代码页的数目](#BKMK_4)
-   [更改命令提示符屏幕缓冲区的大小](#BKMK_5)
-   [设置键盘按键速度](#BKMK_6)

## <a name="to-configure-a-serial-communications-port"></a><a name=BKMK_1></a>配置串行通信端口

### <a name="syntax"></a>语法

```
mode com<M>[:] [baud=<B>] [parity=<P>] [data=<D>] [stop=<S>] [to={on|off}] [xon={on|off}] [odsr={on|off}] [octs={on|off}] [dtr={on|off|hs}] [rts={on|off|hs|tg}] [idsr={on|off}]
```

#### <a name="parameters"></a>参数

|  参数  |                                                                                                                                                                                     说明                                                                                                                                                                                     |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Com\<M > [：]  |                                                                                                                                                      指定 async Prncnfg vbshronous 通信端口的编号。                                                                                                                                                      |
|  波特 =\<B >  | 指定传输速率（以每秒位数为单位）。 下表列出了*B*的有效缩写以及其相关费率。</br>-   **11** = 110 波特</br>-   **15** = 150 波特</br>-   **30** = 300 波特</br>-   **60** = 600 波特</br>-   **12** = 1200 波特</br>-   **24** = 2400 波特</br>-   **48** = 4800 波特</br>-   **96** = 9600 波特</br>-   **19** = 19200 波特 |
| 奇偶校验 =\<P > |                              指定系统如何使用奇偶校验位检查传输错误。 下表列出了*P*的有效值。默认值为**e**。 并非所有计算机都支持值**m**和**s**。</br>-   **n** = 无</br>-   **e** = 偶数</br>-   **o** = 奇数</br>-   **m** = mark</br>-   **s** = space                              |
|  data =\<D >  |                                                                                                    指定字符中的数据位数。 **D**的有效值介于5到8的范围内。 默认值为 7。 并非所有计算机都支持值5和6。                                                                                                     |
|  stop =\<S >  |                                                                                  指定定义字符结尾的停止位的数目：1、1.5 或2。 如果波特率为110，则默认值为2。 否则，默认值为1。 并非所有计算机都支持值1.5。                                                                                   |
|   to = {on    |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|   xon = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|  odsr = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|  octs = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|   dtr = {on   |                                                                                                                                                                                         off                                                                                                                                                                                         |
|   rts = {on   |                                                                                                                                                                                         off                                                                                                                                                                                         |
|  idsr = {on   |                                                                                                                                                                                        off}                                                                                                                                                                                         |
|     /?      |                                                                                                                                                                        在命令提示符下显示帮助。                                                                                                                                                                         |

## <a name="to-display-the-status-of-all-devices-or-of-a-single-device"></a><a name=BKMK_2></a>显示所有设备或单个设备的状态

### <a name="syntax"></a>语法

```
mode [<Device>] [/status]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<设备 >|指定要显示其状态的设备的名称。|
|/status|请求任何重定向的并行打印机的状态。 可以将 **/status**命令行选项缩写为 **/sta**。|
|/?|在命令提示符下显示帮助。|

### <a name="remarks"></a>备注

如果在没有参数的情况下使用，则**mode**显示系统上安装的所有设备的状态。

## <a name="to-redirect-output-from-a-parallel-port-to-a-serial-communications-port"></a><a name=BKMK_3></a>将输出从并行端口重定向到串行通信端口

### <a name="syntax"></a>语法

```
mode lpt<N>[:]=com<M>[:]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|lpt\<N > [：]|必需。 指定并行端口。 *N*的有效值为1到3之间的值。|
|com\<M > [：]|必需。 指定串行端口。 *M*的有效值介于1到4之间。|
|/?|在命令提示符下显示帮助。|

### <a name="remarks"></a>备注

您必须是 Administrators 组的成员才能重定向打印。

### <a name="examples"></a>示例

若要设置系统以便将并行打印机输出发送到串行打印机，必须使用**模式**命令两次。 第一次使用**模式**来配置串行端口。 第二次使用**模式**将并行打印机输出重定向到在第一**模式**命令中指定的串行端口。

例如，如果串行打印机的运行速度为4800波特，甚至具有奇偶校验，并且它连接到 COM1 端口（计算机上的第一个串行连接），请键入：
```
mode com1 48,e,,,b
mode lpt1=com1
```
如果将并行打印机输出从 LPT1 重定向到 COM1，但随后决定要使用 LPT1 打印文件，请在打印文件之前键入以下命令：
```
mode lpt1
```
此命令可防止将文件从 LPT1 重定向到 COM1。

## <a name="to-select-refresh-or-display-the-numbers-of-the-code-pages-for-the-console"></a><a name=BKMK_4></a>选择、刷新或显示控制台代码页的数目

### <a name="syntax"></a>语法

```
mode <Device> codepage select=<YYY>
mode <Device> codepage [/status]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|\<设备 >|必需。 指定要为其选择代码页的设备。 CON 是设备的唯一有效名称。|
|代码页 select =|必需。 指定要与指定设备一起使用的代码页。 您可以将**代码页** **选择**缩写为**cp** **sel**。|
|\<YYY >|必需。 指定要选择的代码页的编号。 下面的列表显示了受支持的每个代码页及其国家/地区或语言。</br>437：美国</br>850：多语言（拉丁语 I）</br>852：斯拉夫语（拉丁语 II）</br>855：西里尔语（俄语）</br>857：土耳其语</br>860：葡萄牙语</br>861：冰岛语</br>863：加拿大-法语</br>865：北欧</br>866：俄语</br>869：新式希腊语|
|ansi|必需。 显示为指定设备选择的代码页（如果有）的编号。|
|/status|显示为指定设备选择的当前代码页的编号。 可以缩写 **/status**到 **/sta**。 无论是否指定 **/status**，**模式代码**页都显示为指定设备选择的代码页的编号。|
|/?|在命令提示符下显示帮助。|

## <a name="to-change-the-size-of-the-command-prompt-screen-buffer"></a><a name=BKMK_5></a>更改命令提示符屏幕缓冲区的大小

### <a name="syntax"></a>语法

```
mode con[:] [cols=<C>] [lines=<N>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|con [：]|必需。 指示更改将应用到命令提示符窗口。|
|cols =\<C >|指定命令提示符屏幕缓冲区中的列数。|
|lines =\<N >|指定命令提示符屏幕缓冲区中的行数。|
|/?|在命令提示符下显示帮助。|

## <a name="to-set-the-keyboard-typematic-rate"></a><a name=BKMK_6></a>设置键盘按键速度

### <a name="syntax"></a>语法

```
mode con[:] [rate=<R> delay=<D>]
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|con [：]|必需。 指键盘。|
|rate =\<R >|指定按住某个键时，在屏幕上重复该字符的速率。|
|delay =\<D >|指定在字符输出重复之前按下并按下某个键所需的时间。|
|/?|在命令提示符下显示帮助。|

### <a name="remarks"></a>备注

- 输入速率是指在按住该字符的键时，字符重复的速率。 按键率具有两个组件：速度和延迟。 某些键盘不能识别此命令。
- 使用**速率 =** <em>R</em>

  有效值介于1到32之间。 这些值的每秒约为2到30个字符。 对于 IBM 的兼容键盘，默认值为20，对于 IBM PS/2 兼容键盘，默认值为21。 如果设置速率，则还必须设置延迟。
- 使用**延迟**=*D*

  *D*的有效值为1、2、3和4（表示0.25、0.50、0.75 和1秒）。 默认值为2。 如果设置延迟，还必须设置速率。

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)