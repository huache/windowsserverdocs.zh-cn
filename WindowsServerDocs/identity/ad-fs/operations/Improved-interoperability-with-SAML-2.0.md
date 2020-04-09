---
ms.assetid: 80b5335b-fa02-4944-900c-5fe4f5c6111d
title: SAML 2.0 改进的互操作性
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 3abc3f09e5ae572800e5580d14a76ada6d62e320
ms.sourcegitcommit: b00d7c8968c4adc8f699dbee694afe6ed36bc9de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "80816360"
---
# <a name="improved-interoperability-with-saml-20"></a>SAML 2.0 改进的互操作性



  
Windows Server 2016 中的 AD FS 包含附加 SAML 协议支持，包括支持基于包含多个实体的元数据导入信任。  这使你可以将 AD FS 配置为参与联合身份验证，例如 InCommon 联合身份验证和其他符合 eGov 2.0 标准的实现。   
  
新功能基于信赖方或声明提供方信任组。 每个组都是在 eGov 2.0 配置文件中指定的 EntitiesDescriptor （< md： EntitiesDescriptor >）元素，其中包含一个或多个 EntityDescriptor 元素。  组具有常见的授权规则，可以像修改单个信任对象一样修改所有其他属性。  
  
将信任组导入 AD FS 后，AD FS 会根据元数据文档自动将信任更新为组。  
  
启用这些方案非常简单，只是使用添加和删除 AdfsClaimsProviderTrustsGroup 和 AdfsRelyingPartyTrustsGroup 对象的新 PowerShell commandlet。 这可以使用元数据 URL 或文件完成，如以下示例中所示。  
  
此外，AD FS 2016 支持范围参数，如 SAML Core 规范3.4.1.2 部分中所述。 此元素允许信赖方为身份验证请求指定一个或多个标识提供者。  
  
## <a name="examples"></a>示例  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataUrl "https://www.contosoconsortium.com/metadata/metadata.xml"   
```  
  
  
  
```  
Add-AdfsClaimsProviderTrustsGroup -MetadataFile "C:\metadata.xml"   
```  
  
## <a name="references"></a>参考  
  
可在此处找到 eGov 2.0 配置文件[。](https://kantarainitiative.org/confluence/download/attachments/60817482/kantara-report-egov-saml2-profile-2.0.pdf?version=1&modificationDate=1345580916000&api=v2)  
  
可在此处找到 SAML 核心规范[。](https://docs.oasis-open.org/security/saml/v2.0/saml-core-2.0-os.pdf)   


