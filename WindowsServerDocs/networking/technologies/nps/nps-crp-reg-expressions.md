---
title: 在 NPS 中使用正则表达式
description: 本主题说明如何将正则表达式用于 Windows Server 中 NPS 中的模式匹配。 可以使用此语法来指定网络策略属性和 RADIUS 领域的条件。
manager: brianlic
ms.topic: article
ms.assetid: bc22d29c-678c-462d-88b3-1c737dceca75
ms.author: jgerend
author: jasongerend
msdate: 08/16/2019
ms.openlocfilehash: b2df170153e2848239a8846e58a84981bc9ad12e
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969384"
---
# <a name="use-regular-expressions-in-nps"></a>在 NPS 中使用正则表达式

> 适用于： Windows Server 2019、Windows Server 2016、Windows Server (半年通道) 

本主题说明如何将正则表达式用于 Windows Server 中 NPS 中的模式匹配。 可以使用此语法来指定网络策略属性和 RADIUS 领域的条件。

## <a name="pattern-matching-reference"></a>模式匹配参考

使用模式匹配语法来创建正则表达式时，可以使用下表作为参考源。 请注意，正则表达式模式通常由正斜杠 (/) 括起来。

|  字符  |  描述  |   示例                                                                 |
| ----------- | ------------- | ------------------------------------------------------------------------  |
|     `\ `     | 指示后面的字符是特殊字符，或应按原义解释。  | `/n/ matches the character "n" while the sequence /\n/ matches a line feed or newline character.`  |
|     `^`     |                                                                 与输入或行的开头匹配。                                                                  |                                                                 &nbsp;                                                                  |
|     `$`     |                                                                    与输入或行的结尾匹配。                                                                     |                                                                 &nbsp;                                                                  |
|     `*`     |                                                             与前面的字符零次或多次匹配。                                                              |                                                  `/zo*/ matches either "z" or "zoo."`                                                   |
|     `+`     |                                                              与前面的字符一次或多次匹配。                                                              |                                                   `/zo+/ matches "zoo" but not "z."`                                                    |
|     `?`     |                                                              与前面的字符零次或一次匹配。                                                              |                                                 `/a?ve?/ matches the "ve" in "never."`                                                  |
|     `.`     |                                                           与新行符除外的任何单个字符匹配。                                                           |                                                                 &nbsp;                                                                  |
| `(pattern)` |                         匹配 "pattern" 并记住匹配。<br />若要匹配原义字符 `(` 和 `)` (括号) ，请使用 `\(` 或 `\)` 。                         |                                                                 &nbsp;                                                                  |
|   `x | y `  |                                                                               与 x 或 y 匹配。                                                          |
|   `{n} `    |                                                          完全匹配 n 次 \( n 是一个非 \- 负整数 \) 。                                                           |               `/o{2}/ does not match the "o" in "Bob," but matches the first two instances of the letter o in "foooood."`               |
|   `{n,}`    |                                                          至少匹配 n 次 \( n 是一个非 \- 负整数 \) 。                                                          | `/o{2,}/ does not match the "o" in "Bob" but matches all of the instances of the letter o in "foooood." /o{1,}/ is equivalent to /o+/.` |
|   `{n,m}`   |                                                至少匹配 n 个，最多 m 次 \( m 次，n 为非 \- 负整数 \) 。                                                |                               `/o{1,3}/ matches the first three instances of the letter o in "fooooood."`                               |
|   `[xyz]`   |                                                       将一个包含的字符与一个 \( 字符集匹配 \) 。                                                        |                                                  `/[abc]/ matches the "a" in "plain."`                                                  |
|  `[^xyz]`   |                                                  匹配不包含负字符集的任何字符 \( \) 。                                                  |                                                 `/[^abc]/ matches the "p" in "plain."`                                                  |
|    `\b`     |                                                              匹配字边界 \( （例如，空格） \) 。                                                               |                                              `/ea*r\b/ matches the "er" in "never early."`                                              |
|    `\B`     |                                                                         与非字边界匹配。                                                                          |                                             `/ea*r\B/ matches the "ear" in "never early."`                                              |
|    `\d`     |                                                       匹配与 \( 0 到9之间的数字等效的数字字符 \) 。                                                        |                                                                 &nbsp;                                                                  |
|    `\D`     |                                                           匹配与等效的 nondigit 字符 \( `[^0-9]` \) 。                                                           |                                                                 &nbsp;                                                                  |
|    `\f`     |                                                                        与换页符匹配。                                                                        |                                                                 &nbsp;                                                                  |
|    `\n`     |                                                                        与换行符匹配。                                                                        |                                                                 &nbsp;                                                                  |
|    `\r`     |                                                                     与回车符匹配。                                                                     |                                                                 &nbsp;                                                                  |
|    `\s`     |                                   匹配任何空白字符（包括空格、制表符和 \( 等效于的换页符） `[ \f\n\r\t\v]` \) 。                                   |                                                                 &nbsp;                                                                  |
|    `\S`     |                                                  匹配与等效的任何非空白字符 \( `[^ \f\n\r\t\v]` \) 。                                                   |                                                                 &nbsp;                                                                  |
|    `\t`     |                                                                           与制表符匹配。                                                                           |                                                                 &nbsp;                                                                  |
|    `\v`     |                                                                      与垂直制表符匹配。                                                                       |                                                                 &nbsp;                                                                  |
|    `\w`     |                                              匹配任意单词字符，包括与 \( 等效的下划线 `[A-Za-z0-9_]` \) 。                                              |                                                                 &nbsp;                                                                  |
|    `\W`     |                                           匹配任何非 \- 单词字符，不包括与等效的下划线 \( `[^A-Za-z0-9_]` \) 。                                           |                                                                 &nbsp;                                                                  |
|   `\num`    | 引用记住的匹配项 \( `?num` ，其中 num 是一个正整数 \) 。  此选项只能在配置属性操作时在 "**替换**" 文本框中使用。 |                                       `\1`替换第一个记住的匹配项中存储的内容。                                       |
|   `/n/ `    |                      允许将 ASCII 代码插入正则表达式 \( `?n` ，其中 n 是八进制、十六进制或小数转义值 \) 。                       |                                                                 &nbsp;                                                                  |

## <a name="examples-for-network-policy-attributes"></a>网络策略属性的示例

以下示例描述了如何使用模式匹配语法来指定网络策略属性：

- 若要指定 899 区号中的所有电话号码，语法为：

     `899.*`

- 若要指定以192.168.1 开头的 IP 地址范围，语法为：

    `192\.168\.1\..+`

## <a name="examples-for-manipulation-of-the-realm-name-in-the-user-name-attribute"></a>用户名属性中的领域名称处理的示例

下面的示例说明如何使用模式匹配语法来操作用户名属性的领域名称，该属性位于连接请求策略属性中的 "**属性**" 选项卡上。

**删除用户名属性的领域部分**

在 Internet 服务提供商 \( ISP 将 \) 连接请求路由到组织 NPS 的外包拨号方案中，isp RADIUS 代理可能需要使用领域名来路由身份验证请求。 但是，NPS 可能无法识别用户名的领域名称部分。 因此，在将领域名称转发到组织 NPS 之前，必须由 ISP RADIUS 代理将其删除。

- 查找： @microsoft \. com

- 将：

**替换为 <em>user@example.microsoft.com</em> _com\user_**

- 查找`(.*)@(.*)`

- 全部`$2\$1`



**用_specific_domain \_ _用户名替换 domain\user_**

- 查找`(.*)\\(.*)`

- 替换： *specific_domain*`\$2`



<strong>将*用户*替换为*user@specific_domain</strong>*

- 查找`$`

- Replace： @*specific_domain*

## <a name="example-for-radius-message-forwarding-by-a-proxy-server"></a>通过代理服务器转发 RADIUS 消息的示例

将 NPS 用作 RADIUS 代理时，可以创建用于将带有指定领域名称的 RADIUS 消息转发给一组 RADIUS 服务器的路由规则。 以下是根据领域名称路由请求的建议语法。

- **NetBIOS 名称**：`WCOAST`
- **模式**：`^wcoast\\`

在以下示例中，wcoast.microsoft.com 是 DNS 或 Active Directory 域 wcoast.microsoft.com (UPN) 后缀的唯一用户主体名称。 NPS 代理使用提供的模式基于域 NetBIOS 名称或 UPN 后缀来路由消息。

- **NetBIOS 名称**：`WCOAST`
- **UPN 后缀**：`wcoast.microsoft.com`
- **模式**：`^wcoast\\|@wcoast\.microsoft\.com$`


有关管理 NPS 的详细信息，请参阅[管理网络策略服务器](nps-manage-top.md)。

有关 NPS 的详细信息，请参阅[网络策略服务器 (nps) ](nps-top.md)。
