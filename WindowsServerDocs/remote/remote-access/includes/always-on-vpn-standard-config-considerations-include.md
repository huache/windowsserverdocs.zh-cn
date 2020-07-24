## <a name="standard-configuration-considerations"></a>标准配置注意事项

Always On VPN 有许多配置选项。 不过，请选择 VPN 配置，包括以下信息：

-   **连接类型。** 连接协议选择非常重要，最终将使用您要使用的身份验证类型。 有关可用隧道协议的详细信息，请参阅[VPN 连接类型](/windows/security/identity-protection/vpn/vpn-connection-type/)。

-   **传递.** 在此上下文中，路由规则确定用户是否可以在连接到 VPN 时使用其他网络路由。

    -   _拆分隧道_允许同时访问其他网络，如 Internet。

    -   _强制隧道_要求所有流量以独占方式通过 VPN，并且不允许同时访问其他网络。

-   **触发器.** _触发_确定如何以及何时启动 VPN 连接（例如，当应用程序打开时，用户手动打开时）。 有关触发选项，请参阅[VPN 自动触发的配置文件选项](/windows/security/identity-protection/vpn/vpn-auto-trigger-profile/)。

-   **设备或用户身份验证。** Always On VPN 通过称为[设备隧道](../vpn/vpn-device-tunnel-config.md)的功能使用设备证书和设备启动的连接。 该连接可以自动启动并且是持久的，类似于 DirectAccess 基础结构隧道连接。

>[!TIP]
>从 DirectAccess 迁移到 Always On VPN 时，请考虑从与你具有的内容类似的配置选项开始，然后从此处进行扩展。

通过使用用户证书，Always On VPN 客户端会自动连接，但在用户级别（用户登录后）而不是在设备级别（在用户登录之前）执行此操作。 用户仍无缝体验，但它支持更高级的身份验证机制，例如 Windows Hello 企业版。
