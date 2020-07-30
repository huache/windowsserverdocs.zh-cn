---
title: 向快速启动板中添加顶级类别（Macintosh 操作系统）
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: ee2173c3-e464-4001-9f43-6d926a575092
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 5ac16ca5c1b4e01364dc0fa0bfcb5e8dd0c5e54e
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181553"
---
# <a name="add-top-level-categories-to-the-launchpad-macintosh-operating-system"></a>向快速启动板中添加顶级类别（Macintosh 操作系统）

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

你可以在运行 Macintosh 操作系统的计算机上向快速启动板中添加顶级类别。 若要创建添加顶级类别的快速启动板加载项，可以结合使用此页面的信息和标题为 "如何：向快速启动板添加任务和类别" 的主题中的信息。[Windows Server 解决方案 SDK](https://go.microsoft.com/fwlink/?LinkID=248648)中的。

 以下示例显示了如何将快速启动板条目指定为 .launchpad 文件中的顶级类别：

```

<?xml version="1.0" encoding="utf-8" ?>
<LaunchPad resFile="Localizable">
   <Category id="Microsoft.Launchpad.HomeCategory" name="SampleAddin"  image="SampleImage01.png">
      <Task id="Microsoft.Launchpad.SampleAddin.Pictures"
          name="Pictures"
           src="smb://%ServerAddress%/Pictures"
         image="SampleImage02.png"/>
   </Category>
</LaunchPad>
```

 为使该条目成为顶级类别，Category 元素的 Id 属性必须为“Microsoft.Launchpad.HomeCategory”。

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)