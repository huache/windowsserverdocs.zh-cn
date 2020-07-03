---
title: 使用 web 浏览器和 GitHub 编辑现有 Windows Server 文章
description: 如何使用 web 浏览器和 GitHub （Microsoft 员工）快速编辑现有 Windows Server 文档。
author: eross-msft
ms.author: lizross
ms.date: 07/02/2020
ms.openlocfilehash: 61ceb05b6cb9602faaa4d17b4dc2d978cb571ddb
ms.sourcegitcommit: d754f9e39fc28e4c8768b77bcc9d02ffe2fa6535
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85911230"
---
# <a name="update-existing-windows-server-and-azure-stack-hci-articles-using-a-web-browser-and-github"></a>使用 web 浏览器和 GitHub 更新现有的 Windows Server 和 Azure Stack HCI 文章

这里有两个不同的位置，即保留 Windows Server 技术内容。 其中一个位置是公共的（windowsserverdocs），而另一个是专用的（windowsserverdocs）。 你要确定你参与的位置：

- **我不是 Microsoft 的员工。** 作为非 Microsoft 员工，你必须参与到公共位置。 有关如何执行此操作的信息，请参阅[Contributing.md](https://github.com/MicrosoftDocs/windowsserverdocs/blob/master/CONTRIBUTING.md)文件。

- **我是 Microsoft 员工。** 作为一名 Microsoft 员工，你可以选择基于你要执行的操作：

    - **创建全新的文章。** 若要创建全新的项目，必须创建并设置 GitHub 帐户和工具、分支和克隆 windowsserverdocs 存储库，设置远程分支，创建文章，最后创建新的拉取请求以批准和发布。 有关这些说明，请参阅[使用 GitHub 创建新的 Windows Server 文章和 Visual Studio Code](create-new-using-github.md)一文。

    - **对现有文章进行大更改。** 若要对现有文章进行重大更改，你可以按照[使用 GitHub 和 Visual Studio Code 文章编辑现有 Windows Server 一文](edit-existing-using-github.md)中的说明进行操作。

    - **对现有项目进行少量更改。** 若要对现有文章进行较小的更改，请按照本文中的说明进行操作。

    > [!IMPORTANT]
    > 发布到 docs.microsoft.com 的所有存储库均遵循 [Microsoft 开放源代码行为准则](https://opensource.microsoft.com/codeofconduct/)或 [.NET 基础行为准则](https://dotnetfoundation.org/code-of-conduct)。 有关详细信息，请参阅[行为准则常见问题解答](https://opensource.microsoft.com/codeofconduct/faq/)。 或如有任何疑问或意见，请联系 [opencode@microsoft.com](mailto:opencode@microsoft.com) 或 [conduct@dotnetfoundation.org](mailto:conduct@dotnetfoundation.org)。
    >
    > [docs.microsoft.com 使用条款](https://docs.microsoft.com/legal/termsofuse)适用于对公共存储库中文档和代码示例所做的小修订和澄清。 如果你不是 Microsoft 的员工，那么新内容或重大更改会在拉取请求中生成一条评论，要求你在线提交一份贡献许可协议 (CLA)。 在我们评审或接受拉取请求之前，需要你填写这份在线表单。

## <a name="quick-edits-to-existing-articles-using-github-and-a-web-browser"></a>使用 GitHub 和 web 浏览器快速编辑现有项目

快速编辑可简化报告并修复文档中的小错误和遗漏的过程。 尽管我们做出了各种各样的努力，我们发布的文档中仍可能出现小的语法错误和拼写错误__。

1. 按照[GitHub 帐户设置](https://review.docs.microsoft.com/en-us/help/contribute/contribute-get-started-setup-github?branch=master)中的说明进行操作。

1. 请参阅[Windows Server](https://github.com/MicrosoftDocs/windowsserverdocs-pr/tree/master/WindowsServerDocs)或[Azure Stack HCI](https://github.com/MicrosoftDocs/azure-stack-docs-pr/tree/master/azure-stack/hci)专用存储库。 专用存储库受到更频繁地监视，因此我们的审批时间更快，它们受益于更高的质量检查，并提供在过渡中查看内容的功能，因为它将显示在实时站点中。

2. 导航到要编辑的项目，然后选择 "**编辑此文件**" 按钮。

   !["编辑此文件" 按钮](media/github-browser-updates/edit-this-file.png)

3. 编辑主题，然后向下滚动到底部，简要说明更改，然后选择 "**提交更改**"。

    ![提交带有标题信息的更改](media/github-browser-updates/commit-changes.png)

## <a name="submit-the-pull-request"></a>提交拉取请求

创建拉取请求后，必须提交该请求以供审批和发布。

### <a name="to-submit-your-pull-request"></a>提交拉取请求

1. 在 "**打开拉取请求**" 页上，更新提交消息，使其更适合 PR。 例如：更正第一段中的拼写错误。

2. 请确保只包含预期包含的提交和文件。 同时检查 PR 是否转到上游存储库中的正确分支（"master" （通常为）或 "发布" 分支（有时）。

3. 在右窗格的 "**审阅者**" 区域中，选择齿轮图标，然后输入 " _windowsservercontent_"。 别名的成员将在上，查看你的更改，并合并你的拉取请求，或在合并前添加有关要更改的项的注释。

4. 选择“创建拉取请求”。 新 PR 链接到分叉中的工作分支。 在合并 PR 之前，推送到分叉中同一工作分支的任何新提交都会自动包含在 PR 中。 新标签将添加到拉取请求，即 "**不合并**"。 这只是表示你的内容仍在进行，不应查看或推送到活动站点。

5. 当你已准备好审核你的内容时，你必须将文本添加 **#sign**到注释。 此注释：

    - 将拉取请求的标签从 "**不合并**" 更新为 "**准备合并**"。

    - 允许别名和编写人员知道您已准备好查看内容。

    - 让管理员知道在批准后，你的内容已准备就绪。
