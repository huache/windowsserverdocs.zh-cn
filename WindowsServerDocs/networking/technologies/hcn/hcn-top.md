---
title: 为 Vm 和容器 (HCN) 服务 API 的主机计算网络
description: 主机计算网络 (HCN) 服务 API 是一种面向公众的 Win32 API，它提供平台级别的访问权限来管理虚拟网络、虚拟网络终结点和关联的策略。 这两者提供了虚拟机 (Vm) 和 Windows 主机上运行的容器的连接和安全性。
ms.author: jmesser
author: jmesser81
ms.date: 11/05/2018
ms.openlocfilehash: 8e83af4ea54d2fcc75ff8ff054f4ad253a5422ea
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87955654"
---
# <a name="host-compute-network-hcn-service-api-for-vms-and-containers"></a>为 Vm 和容器 (HCN) 服务 API 的主机计算网络

>适用于： Windows Server (半年频道) 、Windows Server 2019

主机计算网络 (HCN) 服务 API 是一种面向公众的 Win32 API，它提供平台级别的访问权限来管理虚拟网络、虚拟网络终结点和关联的策略。 这两者提供了虚拟机 (Vm) 和 Windows 主机上运行的容器的连接和安全性。

开发人员使用 HCN service API 在其应用程序工作流中管理 Vm 和容器的网络。 HCN API 旨在为开发人员提供最佳体验。 最终用户不会直接与这些 Api 进行交互。

## <a name="features-of-the-hcn-service-api"></a>HCN 服务 API 的功能
-    作为由主机网络服务托管的 C API 实现 () OnCore/VM 上的 HNS。

-    提供创建、修改、删除和枚举 HCN 对象（如网络、终结点、命名空间和策略）的功能。 操作执行对象的句柄 (例如，网络句柄) ，在内部使用 RPC 上下文句柄实现这些句柄。

-    基于架构。 API 的大多数函数将输入和输出参数定义为字符串，其中包含作为 JSON 文档的函数调用的参数。 JSON 文档基于强类型和版本化的架构，这些架构是公共文档的一部分。

-    提供了订阅/回调 API，使客户端能够注册服务范围事件的通知，例如网络创建和删除。

-    HCN API 适用于 Desktop Bridge (也称为 Centennial) 在系统服务中运行的应用。 API 通过从调用方检索用户令牌来检查 ACL。

>[!TIP]
>HCN service API 在后台任务和非前台窗口中受支持。

## <a name="terminology-host-vs-compute"></a>术语：主机与计算
主机计算服务允许调用方在一台物理计算机上创建和管理虚拟机和容器。 其命名为遵循行业术语。

- **主机**广泛用于虚拟化行业，可引用提供虚拟化资源的操作系统。

- **计算**用于指比虚拟机更广泛的虚拟化方法。 主机计算网络服务允许调用方在一台物理计算机上为虚拟机和容器创建和管理网络。

## <a name="schema-based-configuration-documents"></a>基于架构的配置文档
基于定义完善的架构的配置文档是虚拟化空间中的一种既定行业标准。 大多数虚拟化解决方案（例如 Docker 和 Kubernetes）都提供基于配置文档的 Api。 多个行业计划，加入了 Microsoft，推动了用于定义和验证这些架构的生态系统，如[OpenAPI](https://www.openapis.org/)。  这些计划还推动了用于容器的架构的特定架构定义的标准化，如[ (OCI) 的开放容器计划](https://www.opencontainers.org/)。

用于创作配置文档的语言是[JSON](https://tools.ietf.org/html/rfc8259)，你可以将其与结合使用：
-    定义文档的对象模型的架构定义
-    验证 JSON 文档是否符合架构
-    在这些架构的调用方使用的编程语言中，从这些架构的本机表示形式自动转换为

常用架构定义是[OpenAPI](https://www.openapis.org/)和[JSON 架构](http://json-schema.org/)，可让你在文档中指定属性的详细定义，例如：
-    属性的有效值集，例如0-100，表示百分比。
-    枚举的定义，表示为属性的一组有效字符串。
-    字符串预期格式的正则表达式。

作为记录 HCN Api 的一部分，我们计划将 JSON 文档的架构发布为 OpenAPI 规范。 根据此规范，架构的特定于语言的表示形式可允许使用客户端使用的编程语言中的架构对象进行类型安全的使用。

### <a name="example"></a>示例

下面是在 VM 的配置文档中表示 SCSI 控制器的对象的此工作流的示例。

```
enum IpamType
{
    [NewIn("2.0")] Static,
    [NewIn("2.0")] Dhcp,
};

class Ipam
{
    // Type : dhcp
    [NewIn("2.0"),OmitEmpty] IpamType   Type;
    [NewIn("2.0"),OmitEmpty] Subnet     Subnets[];
};

class Subnet : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] string         IpAddressPrefix;
    [NewIn("2.0"),OmitEmpty] SubnetPolicy   Policies[];
    [NewIn("2.0"),OmitEmpty] Route          Routes[];
};


enum SubnetPolicyType
{
    [NewIn("2.0")] VLAN
};

class SubnetPolicy
{
    [NewIn("2.0"),OmitEmpty] SubnetPolicyType                 Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Common.PolicySettings Data;
};

class PolicySettings
{
    [NewIn("2.0"),OmitEmpty]  string      Name;
};

class VlanPolicy : HCN.Schema.Common.PolicySettings
{
    [NewIn("2.0")] uint32 IsolationId;
};

class Route
{
    [NewIn("2.0"),OmitEmpty] string NextHop;
    [NewIn("2.0"),OmitEmpty] string DestinationPrefix;
    [NewIn("2.0"),OmitEmpty] uint16 Metric;
};

```

>[!TIP]
>[NewIn ( "2.0" ) 批注是架构定义的版本控制支持的一部分。

在此内部定义中，将生成架构的 OpenAPI 规范：

```
{
    "swagger" : "2.0",
    "info" : {
       "version" : "2.1",
       "title" : "HCN API"
    },
    "definitions": {
        "Ipam": {
            "type": "object",
            "properties": {
                "Type": {
                    "type": "string",
                    "enum": [
                        "Static",
                        "Dhcp"
                    ],
                    "description": " Type : dhcp"
                },
                "Subnets": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/Subnet"
                    }
                }
            }
        },
        "Subnet": {
            "type": "object",
            "properties": {
                "ID": {
                    "type": "string",
                    "pattern": "^[0-9A-Fa-f]{8}-([0-9A-Fa-f]{4}-){3}[0-9A-Fa-f]{12}$"
                },
                "IpAddressPrefix": {
                    "type": "string"
                },
                "Policies": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/SubnetPolicy"
                    }
                },
                "Routes": {
                    "type": "array",
                    "items": {
                        "$ref": "#/definitions/Route"
                    }
                }
            }
        },
        "SubnetPolicy": {
            "type": "object",
            "properties": {
                "Type": {
                    "type": "string",
                    "enum": [
                        "VLAN",
                        "VSID"
                    ]
                },
                "Data": {
                    "$ref": "#/definitions/PolicySettings"
                }
            }
        },
        "PolicySettings": {
            "type": "object",
            "properties": {
                "Name": {
                    "type": "string"
                }
            }
        },
        "VlanPolicy": {
            "type": "object",
            "properties": {
                "Name": {
                    "type": "string"
                },
                "IsolationId": {
                    "type": "integer",
                    "format": "uint32"
                }
            }
        },
        "Route": {
            "type": "object",
            "properties": {
                "NextHop": {
                    "type": "string"
                },
                "DestinationPrefix": {
                    "type": "string"
                },
                "Metric": {
                    "type": "integer",
                    "format": "uint16"
                }
            }
        }
    }
}
```

您可以使用诸如[Swagger](https://swagger.io/)这样的工具来生成客户端使用的架构编程语言的特定于语言的表示形式。 Swagger 支持多种语言，如 c #、中转、Javascript 和 Python) 。

- 为顶级 IPAM & 子网对象[生成的 c # 代码示例](example-c-sharp.md)。

- 为顶级 IPAM & 子网对象生成的 "[开始代码" 示例](example-go.md)。 中转由 Docker 和 Kubernetes 使用，后者是主机计算网络服务 Api 的两个使用者。 "开始" 为封送与 JSON 文档之间的中转类型提供内置支持。

除了代码生成和验证外，还可以使用工具简化 JSON 文档的工作，即[Visual Studio Code](https://code.visualstudio.com/Docs/languages/json)。

### <a name="top-level-objects-defined-in-the-hcnschemasmars-file"></a>在 HCN 中定义的顶级对象。架构 mars 文件
如前文所述，你可以在以下文件中查找 HCN Api 使用的文档的文档架构： onecore/vm/dv/net/hns/schema/mars/Schema

顶层对象包括：
- [HostComputeNetwork](hcn-scenarios.md#scenario-hcn)
- [HostComputeEndpoint](hcn-scenarios.md#scenario-hcn-endpoint)
- [HostComputeNamespace](hcn-scenarios.md#scenario-hcn-namespace)
- [HostComputeLoadBalancer](hcn-scenarios.md#scenario-hcn-load-balancer)

```
class HostComputeNetwork : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.NetworkMode          Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.NetworkPolicy        Policies[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.MacPool              MacPool;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.DNS                  Dns;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Ipam                 Ipams[];
};

class HostComputeEndpoint : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] string                                     HostComputeNetwork;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Endpoint.EndpointPolicy Policies[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Endpoint.IpConfig       IpConfigurations[];
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.DNS                     Dns;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Network.Route                   Routes[];
    [NewIn("2.0"),OmitEmpty] string                                     MacAddress;
};

class HostComputeNamespace : HCN.Schema.Common.Base
{
    [NewIn("2.0"),OmitEmpty] uint32                                    NamespaceId;
    [NewIn("2.0"),OmitEmpty] Guid                                      NamespaceGuid;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Namespace.NamespaceType        Type;
    [NewIn("2.0"),OmitEmpty] HCN.Schema.Namespace.NamespaceResource    Resources[];
};

class HostComputeLoadBalancer : HCN.Schema.Common.Base
{
    [NewIn("2.0"), OmitEmpty] string                                               HostComputeEndpoints[];
    [NewIn("2.0"), OmitEmpty] string                                               VirtualIPs[];
    [NewIn("2.0"), OmitEmpty] HCN.Schema.Network.Endpoint.Policy.PortMappingPolicy PortMappings[];
    [NewIn("2.0"), OmitEmpty] HCN.Schema.LoadBalancer.LoadBalancerPolicy           Policies[];
};
```

## <a name="next-steps"></a>后续步骤

- 详细了解常见的[HCN 方案](hcn-scenarios.md)。

- 详细了解 HCN 的[RPC 上下文句柄](hcn-declaration-handles.md)。

- 详细了解[HCN JSON 文档架构](hcn-json-document-schemas.md)。
