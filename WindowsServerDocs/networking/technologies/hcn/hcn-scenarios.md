---
title: 主机计算网络 (HCN) 方案
description: 示例演示如何使用主机计算网络服务 API 在主机上创建可用于将虚拟 NIC 连接到虚拟机或容器的主机计算网络。
ms.author: daschott
author: daschott
ms.date: 11/05/2018
ms.openlocfilehash: e865326b77fbdec19af3e7db347734715458b18a
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083677"
---
# <a name="common-scenarios"></a>常见方案

> 适用于： Windows Server (半年频道) 、Windows Server 2019

## <a name="scenario-hcn"></a>方案： HCN

### <a name="create-an-hcn"></a>创建 HCN

此示例演示如何使用主机计算网络服务 API 在主机上创建可用于将虚拟 NIC 连接到虚拟机或容器的主机计算网络。

```C++
using unique_hcn_network = wil::unique_any<
    HCN_NETWORK,
    decltype(&HcnCloseNetwork),
    HcnCloseNetwork>;
/// Creates a simple HCN Network, waiting synchronously to finish the task
void CreateHcnNetwork()
{
    unique_hcn_network hcnnetwork;
    wil::unique_cotaskmem_string result;
    std::wstring settings = LR"(
    {
        "SchemaVersion": {
            "Major": 2,
            "Minor": 0
        },
        "Owner" : "WDAGNetwork",
        "Flags" : 0,
        "Type"  : 0,
        "Ipams" : [
            {
                "Type" : 0,
                "Subnets" : [
                    {
                        "IpAddressPrefix" : "192.168.1.0/24",
                        "Policies" : [
                            {
                                "Type" : "VLAN",
                                "IsolationId" : 100,
                            }
                        ],
                        "Routes" : [
                            {
                                "NextHop" : "192.168.1.1",
                                "DestinationPrefix" : "0.0.0.0/0",
                            }
                        ]
                    }
                ],
            },
        ],
        "MacPool":  {
            "Ranges" : [
                {
                    "EndMacAddress":  "00-15-5D-52-CF-FF",
                    "StartMacAddress":  "00-15-5D-52-C0-00"
                }
            ],
        },
        "Dns" : {
            "Suffix" : "net.home",
            "ServerList" : ["10.0.0.10"],
        }
    }
    })";
    GUID networkGuid;
    HRESULT result = CoCreateGuid(&networkGuid);
    result = HcnCreateNetwork(
        networkGuid,              // Unique ID
        settings.c_str(),      // Compute system settings document
        &hcnnetwork,
        &result
        );
    if (FAILED(result))
    {
                    // UnMarshal  the result Json
     // ErrorSchema
        //   {
        //    "ErrorCode" : <uint32>,
        //    "Error" : <string>,
        //    "Success" : <bool>,
       //   }
        // Failed to create network
        THROW_HR(result);
    }
    // Close the Handle
    result = HcnCloseNetwork(hcnnetwork.get());
    if (FAILED(result))
    {
        // UnMarshal  the result Json
        THROW_HR(result);
    }
}
```
### <a name="delete-an-hcn"></a>删除 HCN
此示例演示如何使用主机计算网络服务 API 打开 & 删除主机计算网络
```C++
    wil::unique_cotaskmem_string errorRecord;
    GUID networkGuid; // Initialize it to appropriate network guid value
    HRESULT hr = HcnDeleteNetwork(networkGuid, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal the result Json
        THROW_HR(hr);
    }
```
### <a name="enumerate-all-networks"></a>枚举所有网络
此示例演示如何使用主机计算网络服务 API 枚举所有主机计算网络。
```C++
     wil::unique_cotaskmem_string resultNetworks;
     wil::unique_cotaskmem_string errorRecord;
     // Filter to select Networks based on properties
     std::wstring filter [] = LR"(
     {
         "Name"  : "WDAG",
     })";
     HRESULT result = HcnEnumerateNetworks(filter.c_str(), &resultNetworks, &errorRecord);
     if (FAILED(result))
     {
         // UnMarshal  the result Json
         THROW_HR(result);
     }
```
### <a name="query-network-properties"></a>查询网络属性
此示例演示如何使用主机计算网络服务 API 来查询网络属性。
```C++
    unique_hcn_network hcnnetwork;
    wil::unique_cotaskmem_string errorRecord;
    wil::unique_cotaskmem_string properties;
    std:wstring query = LR"(
    {
        // Future
    })";
    GUID networkGuid; // Initialize it to appropriate network guid value
    HRESULT hr = HcnOpenNetwork(networkGuid, &hcnnetwork, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    hr = HcnQueryNetworkProperties(hcnnetwork.get(), query.c_str(), &properties, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
## <a name="scenario-hcn-endpoint"></a>方案： HCN 终结点
### <a name="create-an-hcn-endpoint"></a>创建 HCN 终结点
此示例演示如何使用主机计算网络服务 API 创建主机计算网络终结点，并将其热添加到虚拟机或容器。
```C++
using unique_hcn_endpoint = wil::unique_any<
    HCN_ENDPOINT,
    decltype(&HcnCloseEndpoint),
    HcnCloseEndpoint>;
void CreateAndHotAddEndpoint()
{
    unique_hcn_endpoint hcnendpoint;
    unique_hcn_network hcnnetwork;
    wil::unique_cotaskmem_string errorRecord;
    std::wstring settings[] = LR"(
    {
        "SchemaVersion": {
            "Major": 2,
            "Minor": 0
        },
        "Owner" : "Sample",
                   "Flags" : 0,
        "HostComputeNetwork" : "87fdcf16-d210-426e-959d-2a1d4f41d6d3",
        "DNS" : {
            "Suffix" : "net.home",
            "ServerList" : "10.0.0.10",
        }
    })";
    GUID endpointGuid;
    HRESULT result = CoCreateGuid(&endpointGuid);
    result = HcnOpenNetwork(
        networkGuid,              // Unique ID
        &hcnnetwork,
        &errorRecord
        );
    if (FAILED(result))
    {
        // Failed to find network
        THROW_HR(result);
    }
    result = HcnCreateEndpoint(
        hcnnetwork.get(),
        endpointGuid,              // Unique ID
        settings.c_str(),      // Compute system settings document
        &hcnendpoint,
        &errorRecord
        );
    if (FAILED(result))
    {
        // Failed to create endpoint
        THROW_HR(result);
    }
    // Can use the sample from HCS API Spec on how to attach this endpoint
    // to the VM using AddNetworkAdapterToVm
    result = HcnCloseEndpoint(hcnendpoint.get());
    if (FAILED(result))
    {
        // UnMarshal  the result Json
        THROW_HR(result);
    }
}
```
### <a name="delete-an-endpoint"></a>删除终结点
此示例演示如何使用主机计算网络服务 API 删除主机计算网络终结点。
```C++
    wil::unique_cotaskmem_string errorRecord;
    GUID endpointGuid; // Initialize it to appropriate endpoint guid value
    HRESULT hr = HcnDeleteEndpoint(endpointGuid, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
### <a name="modify-and-endpoint"></a>修改和终结点
此示例演示如何使用主机计算网络服务 API 来修改主机计算网络终结点。
```C++
    unique_hcn_endpoint hcnendpoint;
    GUID endpointGuid; // Initialize it to appropriate endpoint guid value
    HRESULT hr = HcnOpenEndpoint(endpointGuid, &hcnendpoint, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    std::wstring  ModifySettingAddPortJson = LR"(
    {
        "ResourceType" : 0,
        "RequestType" : 0,
        "Settings" : {
            "PortName" : "acbd341a-ec08-44c0-9d5e-61af0ee86902"
            "VirtualNicName" : "641313e1-7ae8-4ddb-94e5-3215f3a0b218--87fdcf16-d210-426e-959d-2a1d4f41d6d1"
            "VirtualMachineId" : "641313e1-7ae8-4ddb-94e5-3215f3a0b218"
        }
    }
    )";
    hr = HcnModifyEndpoint(hcnendpoint.get(), ModifySettingAddPortJson.c_str(), &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
### <a name="enumerate-all-enpoints"></a>枚举所有 enpoints
此示例演示如何使用主机计算网络服务 API 枚举所有主机计算网络终结点。
```C++
    wil::unique_cotaskmem_string errorRecord;
    wil::unique_cotaskmem_string resultEndpoints;
    wil::unique_cotaskmem_string errorRecord;
    // Filter to select Endpoint based on properties
    std::wstring filter [] = LR"(
    {
        "Name"  : "sampleNetwork",
    })";
    result = HcnEnumerateEndpoints(filter.c_str(), &resultEndpoints, &errorRecord);
    if (FAILED(result))
    {
        THROW_HR(result);
    }
```
### <a name="query-endpoint-properties"></a>查询终结点属性
此示例演示如何使用主机计算网络服务 API 来查询主机计算网络终结点的所有属性。
```C++
    unique_hcn_endpoint hcnendpoint;
    wil::unique_cotaskmem_string errorRecord;
    GUID endpointGuid; // Initialize it to appropriate endpoint guid value
    HRESULT hr = HcnOpenEndpoint(endpointGuid, &hcnendpoint, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    wil::unique_cotaskmem_string properties;
    std:wstring query = LR"(
    {
        // Future
    })";
    hr = HcnQueryEndpointProperties(hcnendpoint.get(), query.c_str(), &properties, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the errorRecord Json
        THROW_HR(hr);
    }
```
## <a name="scenario-hcn-namespace"></a>方案： HCN 命名空间
### <a name="create-an-hcn-namespace"></a>创建 HCN 命名空间
此示例演示如何使用主机计算网络服务 API 在主机上创建主机计算网络命名空间，该命名空间可用于连接终结点和容器。
```C++
using unique_hcn_namespace = wil::unique_any<
    HCN_NAMESPACE,
    decltype(&HcnCloseNamespace),
    HcnCloseNamespace>;
/// Creates a simple HCN Network, waiting synchronously to finish the task
void CreateHcnNamespace()
{
    unique_hcn_namespace handle;
    wil::unique_cotaskmem_string errorRecord;
    std::wstring settings = LR"(
    {
        "SchemaVersion": {
            "Major": 2,
            "Minor": 0
        },
        "Owner" : "Sample",
        "Flags" : 0,
        "Type" : 0,
    })";
    GUID namespaceGuid;
    HRESULT result = CoCreateGuid(&namespaceGuid);
    result = HcnCreateNamespace(
        namespaceGuid,              // Unique ID
        settings.c_str(),      // Compute system settings document
        &handle,
        &errorRecord
        );
    if (FAILED(result))
    {
                    // UnMarshal  the result Json
     // ErrorSchema
        //   {
        //    "ErrorCode" : <uint32>,
        //    "Error" : <string>,
        //    "Success" : <bool>,
       //   }
        // Failed to create network
        THROW_HR(result);
    }
    result = HcnCloseNamespace(handle.get());
    if (FAILED(result))
    {
        // UnMarshal  the result Json
        THROW_HR(result);
    }
}
```
### <a name="delete-an-hcn-namespace"></a>删除 HCN 命名空间
此示例演示如何使用主机计算网络服务 API 删除主机计算网络命名空间。
```C++
    wil::unique_cotaskmem_string errorRecord;
    GUID namespaceGuid; // Initialize it to appropriate namespace guid value
    HRESULT hr = HcnDeleteNamespace(namespaceGuid, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal the result Json
        THROW_HR(hr);
    }
```
### <a name="modify-an-hcn-namespace"></a>修改 HCN 命名空间
此示例演示如何使用主机计算网络服务 API 来修改主机计算网络命名空间。
```C++
    unique_hcn_namespace handle;
    GUID namespaceGuid; // Initialize it to appropriate namespace guid value
    HRESULT hr = HcnOpenNamespace(namespaceGuid, &handle, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    wil::unique_cotaskmem_string errorRecord;
    static std::wstring  ModifySettingAddEndpointJson = LR"(
    {
        "ResourceType" : 1,
        "ResourceType" : 0,
        "Settings" : {
            "EndpointId" : "87fdcf16-d210-426e-959d-2a1d4f41d6d1"
        }
    }
    )";
    hr = HcnModifyNamespace(handle.get(), ModifySettingAddEndpointJson.c_str(), &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal the result Json
        THROW_HR(hr);
    }
    hr = HcnCloseNamespace(handle.get());
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
### <a name="enumerate-all-namespaces"></a>枚举所有命名空间
此示例演示如何使用主机计算网络服务 API 枚举所有主机计算网络命名空间。
```C++
    wil::unique_cotaskmem_string resultNamespaces;
    wil::unique_cotaskmem_string errorRecord;
    std::wstring filter [] = LR"(
    {
            // Future
    })";
    HRESULT hr = HcnEnumerateNamespace(filter.c_str(), &resultNamespaces, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
### <a name="query-namespace-properties"></a>查询命名空间属性
此示例演示如何使用主机计算网络服务 API 查询主机计算网络命名空间属性
```C++
    unique_hcn_namespace handle;
    GUID namespaceGuid; // Initialize it to appropriate namespace guid value
    HRESULT hr = HcnOpenNamespace(namespaceGuid, &handle, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    wil::unique_cotaskmem_string errorRecord;
    wil::unique_cotaskmem_string properties;
    std:wstring query = LR"(
    {
        // Future
    })";
    HRESULT hr = HcnQueryNamespaceProperties(handle.get(), query.c_str(), &properties, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
## <a name="scenario-hcn-load-balancer"></a>方案： HCN 负载均衡器
### <a name="create-an-hcn-load-balancer"></a>创建 HCN 负载均衡器
此示例演示如何使用主机计算网络服务 API 在主机上创建主机计算网络负载均衡器，该负载均衡器可用于在计算之间负载平衡终结点。
```C++
using unique_hcn_loadbalancer = wil::unique_any<
    HCN_LOADBALANCER,
    decltype(&HcnCloseLoadBalancer),
    HcnCloseLoadBalancer>;
/// Creates a simple HCN LoadBalancer, waiting synchronously to finish the task
void CreateHcnLoadBalancer()
{
    unique_hcn_loadbalancer handle;
    wil::unique_cotaskmem_string errorRecord;
    std::wstring settings = LR"(
     {
        "SchemaVersion": {
            "Major": 2,
            "Minor": 0
        },
        "Owner" : "Sample",
        "HostComputeEndpoints" : [
            "87fdcf16-d210-426e-959d-2a1d4f41d6d1"
        ],
        "VirtualIPs" : [ "10.0.0.10" ],
        "PortMappings" : [
            {
                "Protocol" : 0,
                "InternalPort" : 8080,
                "ExternalPort" : 80,
            }
        ],
        "EnableDirectServerReturn" : true,
        "InternalLoadBalancer" : false,
    }
     )";
    GUID lbGuid;
    HRESULT result = CoCreateGuid(&lbGuid);
    HRESULT hr = HcnCreateLoadBalancer(
        lbGuid,              // Unique ID
        settings.c_str(),      // LoadBalancer settings document
        &handle,
        &errorRecord
        );
    if (FAILED(hr))
    {
                    // UnMarshal  the result Json
     // ErrorSchema
        //   {
        //    "ErrorCode" : <uint32>,
        //    "Error" : <string>,
        //    "Success" : <bool>,
       //   }
        // Failed to create network
        THROW_HR(hr);
    }
    hr = HcnCloseLoadBalancer(handle.get());
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
}
```
### <a name="delete-an-hcn-load-balancer"></a>删除 HCN 负载均衡器
此示例演示如何使用主机计算网络服务 API 删除主机计算网络 LoadBalancer。
```C++
    wil::unique_cotaskmem_string errorRecord;
    GUID lbGuid; // Initialize it to appropriate loadbalancer guid value
    HRESULT hr = HcnDeleteLoadBalancer(lbGuid , &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal the result Json
        THROW_HR(hr);
    }
```
### <a name="modify-an-hcn-load-balancer"></a>修改 HCN 负载均衡器
此示例演示如何使用主机计算网络服务 API 来修改主机计算网络命名空间。
```C++
    unique_hcn_loadbalancer handle;
    GUID lbGuid; // Initialize it to appropriate loadbalancer guid value
    HRESULT hr = HcnOpenLoadBalancer(lbGuid, &handle, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    wil::unique_cotaskmem_string errorRecord;
    static std::wstring  ModifySettingAddEndpointJson = LR"(
    {
        "ResourceType" : 1,
        "ResourceType" : 0,
        "Settings" : {
            "EndpointId" : "87fdcf16-d210-426e-959d-2a1d4f41d6d1"
        }
    }
    )";
    hr = HcnModifyLoadBalancer(handle.get(), ModifySettingAddEndpointJson.c_str(), &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal the result Json
        THROW_HR(hr);
    }
    hr = HcnCloseLoadBalancer(handle.get());
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
### <a name="enumerate-all-load-balancers"></a>枚举所有负载均衡器
此示例演示如何使用主机计算网络服务 API 枚举所有主机计算网络负载均衡器。
```C++
    wil::unique_cotaskmem_string resultLoadBalancers;
    wil::unique_cotaskmem_string errorRecord;
    std::wstring filter [] = LR"(
    {
         // Future
    })";
    HRESULT result = HcnEnumerateLoadBalancers(filter.c_str(), & resultLoadbalancers, &errorRecord);
    if (FAILED(result))
    {
            // UnMarshal  the result Json
            THROW_HR(result);
    }
```
### <a name="query-load-balancer-properties"></a>查询负载平衡器属性
此示例演示如何使用主机计算网络服务 API 来查询主机计算网络 LoadBalancer 属性。
```C++
    unique_hcn_loadbalancer handle;
    GUID lbGuid; // Initialize it to appropriate loadbalancer guid value
    HRESULT hr = HcnOpenLoadBalancer(lbGuid, &handle, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
    wil::unique_cotaskmem_string errorRecord;
    wil::unique_cotaskmem_string properties;
    std:wstring query = LR"(
    {
        "ID"  : "",
        "Type" : 0,
    })";
    hr = HcnQueryNProperties(handle.get(), query.c_str(), &properties, &errorRecord);
    if (FAILED(hr))
    {
        // UnMarshal  the result Json
        THROW_HR(hr);
    }
```
## <a name="scenario-hcn-notifications"></a>方案： HCN 通知
### <a name="register-and-unregister-service-wide-notifications"></a>注册和注销服务范围通知
此示例演示如何使用主机计算网络服务 API 来注册和注销服务范围通知。 这使得调用方可以通过在注册) 过程中指定的回调函数接收通知 (，只要发生了服务范围的操作（如新的网络创建事件时）。
```C++
using unique_hcn_callback = wil::unique_any<
    HCN_CALLBACK,
    decltype(&HcnUnregisterServiceCallback),
    HcnUnregisterServiceCallback>;
// Callback handle returned by registration api. Kept at
// global or module scope as it will automatically be
// unregistered when it goes out of scope.
unique_hcn_callback g_Callback;
// Event notification callback function.
void
CALLBACK
ServiceCallback(
    DWORD   NotificationType,
    void*   Context,
    HRESULT NotificationStatus,
    PCWSTR  NotificationData)
{
    // Optional client context
    UNREFERENCED_PARAMETER(context);
    // Reserved for future use
    UNREFERENCED_PARAMETER(NotificationStatus);
    switch (NotificationType)
    {
        case HcnNotificationNetworkCreate:
            // TODO: UnMarshal the NotificationData
            //
            // // Notification
            // {
            //     "ID" : Guid,
            //     "Flags" : <uint32>,
            // };
            break;
        case HcnNotificationNetworkDelete:
            // TODO: UnMarshal the NotificationData
            break;
        Default:
            // TODO: handle other events.
            break;
    }
}
/// Register for service-wide notifications
void RegisterForServiceNotifications()
{
    THROW_IF_FAILED(HcnRegisterServiceCallback(
        ServiceCallback,
        nullptr,
        &g_Callback));
}
/// Unregister from service-wide notifications
void UnregisterForServiceNotifications()
{
    // As this is a unique_hcn_callback, this will cause HcnUnregisterServiceCallback to be invoked
    g_Callback.reset();
}
```
## <a name="next-steps"></a>后续步骤
- 详细了解 HCN 的 [RPC 上下文句柄](hcn-declaration-handles.md)。
- 详细了解 [HCN JSON 文档架构](hcn-json-document-schemas.md)。