---
title: 为顶级 IPAM & 子网对象生成的 "开始代码" 示例
description: 为顶级 IPAM & 子网对象生成的 "开始代码" 示例。
ms.author: daschott
author: daschott
ms.date: 11/05/2018
ms.openlocfilehash: 75874edaae006bf75d734f2b5adf3cd95784564a
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083698"
---
# <a name="example-of-go-generated-code"></a>Go 生成的代码示例

> 适用于： Windows Server (半年频道) 、Windows Server 2019

```Go
/*
 * HCN API
 *
 * No description provided (generated by Swagger Codegen https://github.com/swagger-api/swagger-codegen)
 *
 * API version: 2.1
 * Generated by: Swagger Codegen (https://github.com/swagger-api/swagger-codegen.git)
 */
package swagger
type Ipam struct {
    //  Type : dhcp
    Type_ string `json:"Type,omitempty"`
    Subnets []Subnet `json:"Subnets,omitempty"`
}
/*
 * HCN API
 *
 * No description provided (generated by Swagger Codegen https://github.com/swagger-api/swagger-codegen)
 *
 * API version: 2.1
 * Generated by: Swagger Codegen (https://github.com/swagger-api/swagger-codegen.git)
 */
package swagger
type Subnet struct {
    ID string `json:"ID,omitempty"`
    IpAddressPrefix string `json:"IpAddressPrefix,omitempty"`
    Policies []SubnetPolicy `json:"Policies,omitempty"`
    Routes []Route `json:"Routes,omitempty"`
}
```