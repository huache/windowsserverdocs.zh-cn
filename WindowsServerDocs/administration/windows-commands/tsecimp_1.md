---
title: tsecimp
description: 用于 tsecimp 的参考文章，可将分配信息从可扩展标记语言（XML）文件导入到 TAPI 服务器安全文件（Tsec.ini）。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: d7488ec6-0eff-45ff-89ee-9cbe752416bf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c5c3362571df5a3b22dda1b663fcbba749ee6df6
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/23/2020
ms.locfileid: "86954889"
---
# <a name="tsecimp"></a>tsecimp

将可扩展标记语言（XML）文件中的分配信息导入到 TAPI 服务器安全文件（Tsec.ini）。 你还可以使用此命令来显示 TAPI 提供程序和与每个设备关联的线路设备的列表，验证 XML 文件的结构，而无需导入内容以及检查域成员身份。

## <a name="syntax"></a>语法

```
tsecimp /f <Filename> [{/v | /u}]
tsecimp /d
```

#### <a name="parameters"></a>参数

|参数|说明|
|---------|-----------|
|/f \<Filename>|必需。 指定 XML 文件的名称，该文件包含要导入的分配信息。|
|/v|验证 XML 文件的结构而无须将该信息导入 Tsec.ini 文件。|
|/U|检查每个用户是否为 XML 文件中指定的域成员。 使用该参数的计算机必须连接到网络。 如果您正在处理大量的用户分配信息，该参数可能会导致性能的显著下降。|
|/d|显示已安装电话服务提供程序的列表。 对于每个电话服务提供程序，均会列出关联的线路设备，以及与每个线路设备关联的地址和用户。|
|/?|在命令提示符下显示帮助。|

## <a name="remarks"></a>备注

-   要导入其分配信息的 XML 文件必须采用如下所述的结构。
    -   **UserList**元素

        **UserList**是 XML 文件的顶级元素。
    -   **User**元素

        每个**User**元素都包含有关作为域成员的用户的信息。 可能为每个用户分配了一个或多个线路设备。

        此外，每个**用户**元素可能有一个名为**NoMerge**的属性。 如果指定了该属性，则在为该用户分配新线路设备之前，将删除所有当前的线路设备分配。 可以使用该属性轻松删除不需要的用户分配。 默认情况下，不设置该属性。

        **User**元素必须包含单个**DomainUserName**元素，该元素指定用户的域和用户名。 **User**元素还可能包含一个**FriendlyName**元素，该元素指定用户的友好名称。

        **User**元素可能包含一个**LineList**元素。 如果**LineList**元素不存在，则将删除该用户的所有线路设备。
    -   **LineList**元素

        **LineList**元素包含有关可能分配给用户的每个线路或设备的信息。 每个**LineList**元素可以包含多个**Line**元素。
    -   **线条**元素

        每个**线条**元素都指定了线条设备。 必须通过在**line**元素下添加**Address**元素或**PermanentID**元素来标识每个行设备。

        对于每个**Line**元素，可以设置**Remove**特性。 如果设置了该属性，将不再向用户分配该线路设备。 如果未设置该属性，则用户可访问该线路设备。 如果用户无法使用线路设备，则不会提供错误。

## <a name="examples"></a>示例
- 下列 XML 代码段示例说明了上述定义元素的正确使用方法。
  - 以下代码删除分配给 User1 的所有线路设备。
    ```
    <UserList>
      <User NoMerge=1>
        <DomainUser>domain1\user1</DomainUser>
      </User>
    </UserList>
    ```
  - 以下代码将删除分配给 User1 的所有线路设备，然后再分配一个地址为99999的行。 无论先前是否已分配了任何线路设备，都不会再将任何其他线路设备分配给 User1。
    ```
    <UserList>
      <User NoMerge=1>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```
  - 下列代码在未删除任何以前分配的线路设备的情况下，为 User1 添加了一个线路设备。
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```
  - 下面的代码添加行地址99999并从 User1's 访问中删除线路地址88888。
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <Address>99999</Address>
          </Line>
          <Line Remove=1>
            <Address>88888</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```
  - 下面的代码添加永久设备1000并从 User1's 访问中删除行88888。
    ```
    <UserList>
      <User>
        <DomainUser>domain1\user1</DomainUser>
        <FriendlyName>User1</FriendlyName>
        <LineList>
          <Line>
            <PermanentID>1000</PermanentID>
          </Line>
          <Line Remove=1>
            <Address>88888</Address>
          </Line>
        </LineList>
      </User>
    </UserList>
    ```

-   指定了 **/d**命令行选项以显示当前 TAPI 配置后，会显示以下示例输出。 对于每个电话服务提供程序，均会列出关联的线路设备，以及与每个线路设备关联的地址和用户。
    ```
    NDIS Proxy TAPI Service Provider
            Line: WAN Miniport (L2TP)
                    Permanent ID: 12345678910

    NDIS Proxy TAPI Service Provider
            Line: LPT1DOMAIN1\User1
                    Permanent ID: 12345678910

    Microsoft H.323 Telephony Service Provider
            Line: H323 Line
                    Permanent ID: 123456
                    Addresses:
                            BLDG1-TAPI32

    ```

## <a name="additional-references"></a>其他参考

- [命令行语法项](command-line-syntax-key.md)

[命令外壳概述](/previous-versions/windows/it-pro/windows-server-2003/cc737438(v=ws.10))
