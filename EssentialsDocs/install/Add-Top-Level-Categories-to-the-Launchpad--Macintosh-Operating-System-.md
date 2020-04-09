---
title: 向快速启动板中添加顶级类别（Macintosh 操作系统）
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.prod: windows-server
ms.topic: article
ms.assetid: ee2173c3-e464-4001-9f43-6d926a575092
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c8a15a831a89afc55d20db4e1c1195173d466b3c
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80817510"
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
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)   
 [其他自定义](Additional-Customizations.md)   
 [准备映像以进行部署](Preparing-the-Image-for-Deployment.md)   
 [测试客户体验](Testing-the-Customer-Experience.md)