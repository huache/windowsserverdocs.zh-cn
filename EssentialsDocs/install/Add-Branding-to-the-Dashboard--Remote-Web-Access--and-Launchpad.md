---
title: 向仪表板、远程 Web 访问和快速启动板添加品牌
description: 如何向仪表板、远程 Web 访问和快速启动板屏幕添加商标材料。
ms.date: 04/10/2014
ms.topic: article
ms.assetid: 166262f8-b2a5-4b1c-a4a7-a141e1c54f10
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 4d1b3ada8888de9885bfe88af56e5b0656fc92b7
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181603"
---
# <a name="add-branding-to-the-dashboard-remote-web-access-and-launchpad"></a>向仪表板、远程 Web 访问和快速启动板添加品牌

> 适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

可以通过在注册表中添加项来添加多个品牌。 操作系统的注册表中的所有品牌条目都位于下 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\OEM` 。

对于共同品牌用途，Windows Server Essentials 徽标的最小宽度为**170 像素**，保持正确的纵横比， **96 DPI**。

## <a name="to-add-branding-by-changing-the-registry"></a>通过更改注册表来添加品牌

1. 在服务器上，将鼠标移动到屏幕右上角，然后单击 **“搜索”**。

2. 在搜索框中，键入 **“regedit”**，然后单击 **“Regedit”** 应用程序。

3. 在导航窗格中，依次展开 **“HKEY_LOCAL_MACHINE”**、**“SOFTWARE”**、**“Microsoft”** 和 **“Windows Server”**。 如果**OEM**密钥不存在，你可以创建它：

    1. 右键单击 **“Windows Server”**，单击 **“新建”**，然后单击 **“项”**。

    2. 键入 **OEM** 作为该项的名称。

4. 可有可无如果要为徽标创建条目，可以创建不同的密钥来区分徽标的语言版本。 例如，如果你已拥有英语版和德语版的徽标，则可以为它们分别创建 en-us 项和 de-de 项。 由于所有徽标文件存储在同一文件夹中，因此提供徽标图像文件的实例时必须加上每种语言的唯一名称。 例如，可以创建名为 DashboardLogo_en.png 和 DashboardLogo_de.png 的文件。

5. 右键单击 " **OEM** " 或右键单击相应的语言项，单击 "**新建**"，然后单击 "**字符串值**"。

6. 输入字符串的名称，然后按 Enter 键。 有关字符串名称和数据值的详细信息，请参阅本文的 "**注册表字符串和值**" 一节。

7. 输入字符串的名称，然后按 Enter 键。 有关字符串名称和数据值的详细信息，请参阅本文的 "**注册表字符串和值**" 一节。

8. 右键单击新字符串，然后单击 **“修改”**。

9. 输入表中与此字符串名称相关联的值，然后单击 **“确定”**。

10. 如果要为徽标图像或附加链接创建条目，请将文件复制到 `%programFiles%\Windows Server\Bin\OEM` 。 如果 OEM 目录不存在，请创建该目录。

11. 如果在客户接管服务器后对远程 Web 访问进行更改，则必须通过以下方式打开远程 Web 访问：

    1. 在仪表板上，单击 **“设置”**，然后单击 **“随处访问”** 选项卡。

    2. 如果 "**随处访问**" 处于打开状态，请单击 "**配置**"，然后在 "**设置**随处访问权限" 向导的 "**选择要启用的随处访问功能**" 页上，清除 "远程 Web 访问" 复选框。

    3. 单击 **“配置”** 。

### <a name="registry-strings-and-values"></a>注册表字符串和值

下表提供了有关可用字符串名称和数据值的信息。

| 品牌位置 | 说明 | 字符串名称 | 数据值 |
|--|--|--|--|
| 仪表板徽标 | 向仪表板添加徽标图像。 仪表板徽标必须采用 .png 格式，且不能大于 350 像素宽 x 38 像素高。<p>**重要提示：** 若要将仪表板与徽标共同构成，必须编辑 OPK DVD 上提供的 "图稿" 磁贴，并按照相应的空白要求在图像上追加公司徽标。 | DashboardLogo | 输入徽标图像文件的名称。 |
| DashboardClientLogo | 向仪表板客户端登录屏幕添加徽标图像。 | DashboardClientLogo | 输入徽标图像文件的名称。 |
| 网站背景图片 | 更改在远程 Web 访问登录页上显示的背景图像。 典型的分辨率如下所示：<ul><li>**1024x768 像素**-此分辨率会精确填充 "登录" 页。</li><li>**800x600 像素**-此分辨率将图像置于页面上并显示黑色边框。</li><li>**1280x720 像素**-此分辨率用于使图像居中。 不会显示超出1024x720 的任何像素。 | LogonBackground | 输入背景图像文件的名称。 |
| 网站标题 | 将远程 Web 访问站点的标题从 Windows Server Essentials 替换为指定的标题。 | WebsiteName | 输入新的远程 Web 访问站点标题。 |
| 网站徽标 | 更改远程 Web 访问网站上的默认徽标。 徽标的预期大小是 32 x 32 像素。 如果你的徽标小于或等于此，则它将被拉伸或缩小以匹配这些尺寸。 | WebsiteLogo | 输入徽标图像文件的名称 |
| 附加的网站徽标 | 你的合作伙伴徽标将显示在 "远程 Web 访问" 网站上显示的 Microsoft 徽标下方。 徽标的预期大小是 200 像素高 x 50 像素宽。 如果你的徽标大于此尺寸，则将在保持原始纵横比的情况下根据该尺寸缩小徽标。 如果你的徽标小于此尺寸，它将在 200 x 50 像素的空间中居中放置，且大小和纵横比保持不变。 | OEMLogo | 输入徽标图像文件的名称。 |
| 网站主页和登录页上的链接 | 将链接添加到远程 Web 访问站点的登录页面和主页。 包含链接信息的 XML 文件必须位于 `%programFiles%\Windows Server\Bin\OEM` 文件夹中。 | LinksXML | 有关元素和说明的列表，请参考 LinksXML 元素表。 |
| 快速启动板徽标 | 向快速启动板添加徽标图像。 Launchpad 徽标必须为 .png 格式，并且不能高于 64 像素。 | LaunchpadLogo | 输入徽标图像文件的名称。 |

#### <a name="xml-linking-format"></a>XML 链接格式

你必须在网站**主页**和登录页上设置链接的格式，如下所示：

```xml
<OemLinks>
    <LogonLinks>
        <Link Name=LogonLinkName>
        <Text>LogonLinkDescription</Text>
        <Url>LogonLinkURL</Url>
        <Icon>LinkIcon</Icon>
        </Link>
    </LogonLinks>

    <HomepageLinks>
        <Link Name=HomepageLinkName>
        <Text>HomepageLinkDescription</Text>
        <Url>HomepageLinkURL</Url>
        <Icon>HomepageLinkIcon</Icon>
        </Link>
    </HomepageLinks>
</OemLinks>
```

### <a name="linksxml-elements"></a>LinksXML 元素

| LinksXML 元素 | 说明 |
|--|--|
| LogonLinks | 用于登录链接的父项。 |
| 链接名称 | 登录链接名称。 |
| 文本 | 显示为 "登录页" 链接的文本。 |
| URL | 解析为登录页链接的 URL。 |
| 图标 | "登录" 链接的图标文件的名称。 此文件应与 .xml 文件位于同一文件夹位置。 图标图像应为16x16 像素且采用 .png 格式。 如果未提供图标，则使用默认的链接图标图像。 |
| HomepageLinks | **主页**的父项。 |
| 链接名称 | **主页**链接名称。 |
| 文本 | 显示为**主页**链接的文本。 |
| URL | 解析为**主页**链接的 URL。 |
| 图标 | **主页**链接的图标文件的名称。 此文件应与 .xml 文件位于同一文件夹位置。 图标图像应为16x16 像素且采用 .png 格式。 如果未提供图标，则使用默认**主页**链接图标图像。 |

## <a name="additional-references"></a>其他参考

- [创建和自定义映像](Creating-and-Customizing-the-Image.md)

- [其他自定义](Additional-Customizations.md)

- [准备要部署的映像](Preparing-the-Image-for-Deployment.md)

- [测试客户体验](Testing-the-Customer-Experience.md)