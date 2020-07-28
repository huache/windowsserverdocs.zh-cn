---
title: 故障转移群集系统日志事件
description: Windows Server 系统日志中的故障转移群集事件的列表。 这些事件可用于对群集进行故障排除。
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
manager: lizross
ms.technology: storage-failover-clustering
ms.date: 01/14/2020
ms.openlocfilehash: 5988842ef2a88687bca95781b996babb4e4f3faa
ms.sourcegitcommit: d99bc78524f1ca287b3e8fc06dba3c915a6e7a24
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87181703"
---
# <a name="failover-clustering-system-log-events"></a>故障转移群集系统日志事件

> 适用于：Windows Server 2019、Windows Server 2016

本主题列出了 Windows Server 系统日志中的故障转移群集事件（可在事件查看器中查看）。 这些事件都共享**FailoverClustering**的事件源，并在排查群集问题时非常有用。

## <a name="critical-events"></a>关键事件

### <a name="event-1000-unexpected_fatal_error"></a>事件1000： UNEXPECTED_FATAL_ERROR

群集服务在源模块 %2 的第 %1 行遇到了意外的严重错误。 错误代码为 %3。

### <a name="event-1001-assertion_failure"></a>事件1001： ASSERTION_FAILURE

群集服务在源模块 %2 的第 %1 行中的有效性检查失败。 "%3"

### <a name="event-1006-nm_event_membership_halt"></a>事件1006： NM_EVENT_MEMBERSHIP_HALT

由于与其他群集节点的连接不完整，群集服务已停止。

### <a name="event-1057-dm_database_corrupt_or_missing"></a>事件1057： DM_DATABASE_CORRUPT_OR_MISSING

无法加载群集数据库。 此文件可能已丢失或损坏。
可能会尝试自动修复。

### <a name="event-1070-nm_event_begin_join_failed"></a>事件1070： NM_EVENT_BEGIN_JOIN_FAILED

由于错误代码 "%2"，节点无法联接故障转移群集 "%1"。

### <a name="event-1073-cs_event_inconsistency_halt"></a>事件1073： CS_EVENT_INCONSISTENCY_HALT

群集服务已停止，以防止故障转移群集中出现不一致的情况。 错误代码为 "%1"。

### <a name="event-1080-cs_diskwrite_failure"></a>事件1080： CS_DISKWRITE_FAILURE

群集服务无法更新群集数据库（错误代码 "%1"）。
可能的原因是磁盘空间不足或文件系统损坏。

### <a name="event-1090-cs_event_reg_operation_failed"></a>事件1090： CS_EVENT_REG_OPERATION_FAILED

无法启动群集服务。 尝试从 Windows 注册表读取配置数据失败，错误为 "%1"。 请使用 "故障转移群集管理" 管理单元来确保此计算机是群集的成员。
如果要将此计算机添加到现有群集，请使用 "添加节点" 向导。 或者，如果已将此计算机配置为群集的成员，则有必要还原群集服务标识为群集成员所需的缺少的配置数据。
执行此计算机的系统状态还原，以便还原配置数据。

### <a name="event-1092-nm_event_mm_form_failed"></a>事件1092： NM_EVENT_MM_FORM_FAILED

未能形成群集 "%1"，错误代码为 "%2"。 故障转移群集将不可用。

### <a name="event-1093-nm_event_node_not_member"></a>事件1093： NM_EVENT_NODE_NOT_MEMBER

群集服务无法将节点 "%1" 标识为故障转移群集 "%2" 的成员。 如果此节点的计算机名最近发生了更改，请考虑将其还原为以前的名称。 或者，将节点添加到故障转移群集，并在必要时重新安装群集应用程序。

### <a name="event-1105-cs_event_rpc_init_failed"></a>事件1105： CS_EVENT_RPC_INIT_FAILED

群集服务无法启动，因为它无法向 RPC 服务注册接口。 错误代码为 "%1"。

### <a name="event-1135-event_node_down"></a>事件1135： EVENT_NODE_DOWN

群集节点 "%1" 已从活动的故障转移群集成员身份中删除。 此节点上的群集服务可能已停止。 这也可能是由于节点与故障转移群集中的其他活动节点失去了通信。
运行验证配置向导检查您的网络配置。 如果此情况仍然存在，请检查与此节点上的网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1146-rcm_event_resmon_died"></a>事件1146： RCM_EVENT_RESMON_DIED

群集资源宿主子系统（RHS）进程已终止，将重新启动。 这通常与群集运行状况检测和资源恢复关联。 请参阅系统事件日志，确定导致此问题的资源和资源 DLL。

### <a name="event-1177-mm_event_arbitration_failed"></a>事件1177： MM_EVENT_ARBITRATION_FAILED

由于仲裁丢失，群集服务正在关闭。 这可能是由于群集中的部分或所有节点之间的网络连接断开，或是见证磁盘的故障转移。

运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1181-netres_resource_start_error"></a>事件1181： NETRES_RESOURCE_START_ERROR

无法使群集资源 "%1" 联机，因为关联的服务无法启动。 服务返回代码是 "%2"。 请检查与该服务关联的其他事件，并确保该服务正常启动。

### <a name="event-1247-cluster_event_invalid_service_sid_type"></a>事件1247： CLUSTER_EVENT_INVALID_SERVICE_SID_TYPE

群集服务的安全标识符（SID）类型配置为 "%1"，但预期 SID 类型为 "不受限制"。 群集服务使用服务控制管理器（SCM）自动修改其 SID 类型配置，并将重新启动以使此更改生效。

### <a name="event-1248-cluster_event_service_sid_missing"></a>事件1248： CLUSTER_EVENT_SERVICE_SID_MISSING

与群集服务关联的安全标识符（SID） "%1" 在进程令牌中不存在。 群集服务将自动更正此问题并重新启动。

### <a name="event-1282-sm_event_handshake_timeout"></a>事件1282： SM_EVENT_HANDSHAKE_TIMEOUT

本地和远程终结点 "%2" 之间的安全握手未在 "%1" 秒内完成，节点正在终止连接

### <a name="event-1542-service_prerestore_failed"></a>事件1542： SERVICE_PRERESTORE_FAILED

群集配置数据的还原请求失败。 此还原在 "预先还原" 阶段失败，通常表示构成群集的某些节点当前未运行。 请确保群集服务已成功地在构成此群集的所有节点上运行。

### <a name="event-1543-service_postrestore_failed"></a>事件1543： SERVICE_POSTRESTORE_FAILED

群集配置数据的还原操作失败。 此还原在 "还原后" 阶段失败，通常表示构成群集的某些节点当前未运行。 建议将当前群集配置数据文件（ClusDB）替换为 "%1"。

### <a name="event-1546-service_form_version_incompatible"></a>事件1546： SERVICE_FORM_VERSION_INCOMPATIBLE

节点 "%1" 无法形成故障转移群集。 这是因为一个或多个节点执行了不兼容的群集服务软件版本。 如果节点 "%1" 或群集中的其他节点最近已升级，请重新验证所有节点是否正在执行与群集服务软件兼容的版本。

### <a name="event-1547-service_connect_version_incompatible"></a>事件1547： SERVICE_CONNECT_VERSION_INCOMPATIBLE

节点 "%1" 尝试加入故障转移群集，但由于群集服务软件的版本不兼容而失败。 如果节点 "%1" 或群集中的其他节点最近已升级，请验证是否支持具有不同版本的群集服务软件的更改的群集部署。

### <a name="event-1553-service_no_network_connectivity"></a>事件1553： SERVICE_NO_NETWORK_CONNECTIVITY

此群集节点没有网络连接。 在连接恢复之前，它无法参与群集。 运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1554-service_network_connectivity_lost"></a>事件1554： SERVICE_NETWORK_CONNECTIVITY_LOST

此群集节点丢失了所有网络连接。 在连接恢复之前，它无法参与群集。 此节点上的群集服务将终止。

### <a name="event-1556-service_unhandled_exception_in_worker_thread"></a>事件1556： SERVICE_UNHANDLED_EXCEPTION_IN_WORKER_THREAD

群集服务遇到意外问题，将关闭。 错误代码为 "%2"。

### <a name="event-1561-service_nonstorage_witness_better_tag"></a>事件1561： SERVICE_NONSTORAGE_WITNESS_BETTER_TAG

群集服务无法启动，因为此节点检测到它没有群集配置数据的最新副本。 如果此节点不在成员身份中，则对群集的更改发生，因此无法接收配置数据更新。

#### <a name="guidance"></a>指南

尝试在群集中的所有节点上启动群集服务，使具有群集配置数据的最新副本的节点能够首先形成群集。 然后，此节点将能够加入群集，并将自动获取更新后的群集配置数据。 如果群集配置数据的最新副本没有可用节点，请运行 "Start-clusternode-FQ" Windows PowerShell cmdlet。 使用 ForceQuorum （FQ）参数将启动群集服务，并将此节点的群集配置数据副本标记为权威。 如果在具有过时群集数据库副本的节点上强制仲裁，可能会导致在节点未加入群集时所发生的群集配置更改。

### <a name="event-1564-res_fsw_arbitratefailure"></a>事件1564： RES_FSW_ARBITRATEFAILURE

文件共享见证资源 "%1" 无法仲裁文件共享 "%2"。
请确保文件共享 "%2" 存在并且可以由群集访问。

### <a name="event-1570-service_connect_authentication_failure"></a>事件1570： SERVICE_CONNECT_AUTHENTICATION_FAILURE

节点 "%1" 在加入群集时无法建立通信会话。
这是由于身份验证失败引起的。 请验证节点是否正在运行兼容版本的群集服务软件。

### <a name="event-1571-service_connect_authorizaion_failure"></a>事件1571： SERVICE_CONNECT_AUTHORIZAION_FAILURE

节点 "%1" 在加入群集时无法建立通信会话。
这是由于授权失败引起的。 请验证节点是否正在运行兼容版本的群集服务软件。

### <a name="event-1572-service_netft_route_initial_failure"></a>事件1572： SERVICE_NETFT_ROUTE_INITIAL_FAILURE

节点 "%1" 无法加入群集，因为它无法发送和接收与其他群集节点的故障检测网络消息。 请运行验证配置向导以确保网络设置。 同时，验证 Windows 防火墙的 "故障转移群集" 规则。

### <a name="event-1574-dm_database_unload_failed"></a>事件1574： DM_DATABASE_UNLOAD_FAILED

无法卸载故障转移群集数据库。 如果重新启动群集服务不能解决问题，请重新启动计算机。

### <a name="event-1575-dm_database_corrupt_or_missing_fixquorum"></a>事件1575： DM_DATABASE_CORRUPT_OR_MISSING_FIXQUORUM

尝试强制启动群集服务失败，因为此节点上的群集配置数据已丢失或损坏。 请先在具有完整且有效的群集配置数据副本的另一个节点上启动群集服务。 然后，重新尝试此节点上的启动操作（这将尝试自动获取更新的有效配置信息）。 如果没有其他节点可用，请使用 WBAdmin 执行此节点的系统状态还原，以便还原配置数据。

### <a name="event-1593-dm_could_not_discard_changes"></a>事件1593： DM_COULD_NOT_DISCARD_CHANGES

无法卸载故障转移群集数据库，无法放弃内存中可能不正确的更改。 群集服务将尝试通过从另一个群集节点检索数据库来修复数据库。 如果群集服务未联机，则重新启动此节点上的群集服务。 如果重新启动群集服务不能解决问题，请重新启动计算机。 如果群集服务在重新启动后未能联机，请从上次备份还原群集数据库。 当前数据库已复制到 "%1"。 如果没有可用的备份，请将 "%1" 复制到 "%2"，然后尝试启动群集服务。 如果群集服务在此节点上联机，则某些群集配置的更改可能会丢失，并且群集可能无法正常运行。 运行验证配置向导以检查群集配置，并验证托管服务和应用程序是否处于联机状态且正常工作。

### <a name="event-1672-event_node_quarantined"></a>事件1672： EVENT_NODE_QUARANTINED

已隔离群集节点 "%1"。 节点在一小段时间内连续失败并已从群集中删除，以避免进一步中断。 节点将被隔离到 "%3"，然后节点将自动尝试重新加入群集。

请参阅系统和应用程序事件日志来确定此节点上的问题。 解决问题后，可以手动清除隔离，以允许节点与 "Start-clusternode – ClearQuarantine" Windows PowerShell cmdlet 重新加入。

节点名： %1

连续群集成员身份丢失次数： %2

将自动清除时间隔离： %3

## <a name="error-events"></a>错误事件

### <a name="event-1024-cp_reg_ckpt_restore_failed"></a>事件1024： CP_REG_CKPT_RESTORE_FAILED

无法将群集资源 "%1" 的注册表检查点还原到注册表项 HKEY_LOCAL_MACHINE \\ %2。 资源可能无法正常工作。
请确保没有其他进程对此注册表子树中的注册表项具有打开的句柄。

### <a name="event-1034-res_disk_missing"></a>事件1034： RES_DISK_MISSING

群集物理磁盘资源 "%1" 无法联机，因为找不到关联的磁盘。 磁盘的预期签名为 "%2"。
如果磁盘已被替换或还原，则在故障转移群集管理器管理单元中，可以使用 Repair 函数（在磁盘的属性表中）来修复新磁盘或已还原的磁盘。 如果磁盘不会被替换，请删除关联的磁盘资源。

### <a name="event-1035-res_disk_mount_failed"></a>事件1035： RES_DISK_MOUNT_FAILED

当磁盘资源 "%1" 处于联机状态时，对一个或多个卷的访问失败，出现错误 "%2"。 运行验证配置向导以检查你的存储配置。 或者，您可能希望运行 Chkdsk 来验证此磁盘上的所有卷的完整性。

### <a name="event-1037-res_disk_filesystem_failed"></a>事件1037： RES_DISK_FILESYSTEM_FAILED

资源 "%1" 的磁盘上的一个或多个分区的文件系统可能已损坏。 运行验证配置向导以检查你的存储配置。 或者，您可能希望运行 Chkdsk 来验证此磁盘上的所有卷的完整性。

### <a name="event-1038-res_disk_reservation_lost"></a>事件1038： RES_DISK_RESERVATION_LOST

此节点意外丢失了群集磁盘 "%1" 的所有权。 运行验证配置向导以检查你的存储配置。

### <a name="event-1039-res_genapp_create_failed"></a>事件1039： RES_GENAPP_CREATE_FAILED

在尝试创建进程期间，一般应用程序 "%1" 无法联机（错误为 "%2"）。 可能的原因包括：此节点上可能不存在应用程序，路径名称可能指定不正确，二进制名称可能指定不正确。

### <a name="event-1040-res_gensvc_open_failed"></a>事件1040： RES_GENSVC_OPEN_FAILED

尝试打开服务期间，一般服务 "%1" 无法联机（错误为 "%2"）。 可能的原因包括：未安装服务或指定的服务名称无效。

### <a name="event-1041-res_gensvc_start_failed"></a>事件1041： RES_GENSVC_START_FAILED

在尝试启动服务期间，一般服务 "%1" 无法联机（错误为 "%2"）。 可能的原因：指定的服务参数可能无效。

### <a name="event-1042-res_gensvc_failed_after_start"></a>事件1042： RES_GENSVC_FAILED_AFTER_START

通用服务 "%1" 失败，错误为 "%2"。 请检查应用程序事件日志。

### <a name="event-1044-res_ipaddr_nbt_interface_create_failed"></a>事件1044： RES_IPADDR_NBT_INTERFACE_CREATE_FAILED

尝试在将资源 "%1" 联机时创建新的 NetBIOS 接口时遇到错误（错误代码为 "%2"）。 最多可以超过 NetBIOS 名称。

### <a name="event-1046-res_ipaddr_invalid_subnet"></a>事件1046： RES_IPADDR_INVALID_SUBNET

群集 IP 地址资源 "%1" 由于子网掩码值无效而无法联机。 请检查你的 IP 地址资源属性。

### <a name="event-1047-res_ipaddr_invalid_address"></a>事件1047： RES_IPADDR_INVALID_ADDRESS

群集 IP 地址资源 "%1" 不能联机，因为地址值无效。 请检查你的 IP 地址资源属性。

### <a name="event-1048-res_ipaddr_invalid_adapter"></a>事件1048： RES_IPADDR_INVALID_ADAPTER

群集 IP 地址资源 "%1" 联机失败。 无法确定与群集网络接口 "%2" 对应的网络适配器的配置数据（错误代码为 "%3"）。 请检查 IP 地址资源是否配置了正确的地址和网络属性。

### <a name="event-1049-res_ipaddr_in_use"></a>事件1049： RES_IPADDR_IN_USE

群集 IP 地址资源 "%1" 无法联机，因为在网络上检测到重复的 IP 地址 "%2"。 请确保所有 IP 地址都是唯一的。

### <a name="event-1050-res_netname_duplicate"></a>事件1050： RES_NETNAME_DUPLICATE

群集网络名称资源 "%1" 不能联机，因为名称 "%2" 与此群集节点名称匹配。 请确保网络名称是唯一的。

### <a name="event-1051-res_netname_no_ip_address"></a>事件1051： RES_NETNAME_NO_IP_ADDRESS

群集网络名称资源 "%1" 不能联机。 确保从属 IP 地址资源的网络适配器有权访问至少一个 DNS 服务器。 或者，为从属 IP 地址启用 NetBIOS。

### <a name="event-1052-res_netname_cant_add_name_status"></a>事件1052： RES_NETNAME_CANT_ADD_NAME_STATUS

群集网络名称资源 "%1" 不能联机，因为无法将该名称添加到系统中。 关联的错误代码存储在 data 节中。

### <a name="event-1053-res_smb_cant_create_share"></a>事件1053： RES_SMB_CANT_CREATE_SHARE

群集文件共享 "%1" 不能联机，因为无法创建此共享。

### <a name="event-1054-res_smb_share_not_found"></a>事件1054： RES_SMB_SHARE_NOT_FOUND

文件共享资源 "%1" 的运行状况检查失败。 检索共享 "%2" 的信息（作用域为网络名称 %3）返回了错误代码 "%4"。 请确保共享存在并且可访问。

### <a name="event-1055-res_smb_share_failed"></a>事件1055： RES_SMB_SHARE_FAILED

文件共享资源 "%1" 的运行状况检查失败。 正在检索共享 "%2" （作用域为网络名称 %3）的信息，指示该共享不存在（错误代码 "%4"）。 请确保共享存在并且可访问。

### <a name="event-1069-rcm_resource_failure"></a>事件1069： RCM_RESOURCE_FAILURE

群集角色 "%2" 中的群集资源 "%1" 失败。

### <a name="event-1069-rcm_resource_failure_with_typename"></a>事件1069： RCM_RESOURCE_FAILURE_WITH_TYPENAME

群集角色 "%2" 中类型为 "%3" 的群集资源 "%1" 失败。<br><br>根据资源和角色的故障策略，群集服务可能会尝试在此节点上使资源联机，或者将该组移至群集的其他节点，然后重新启动它。 使用故障转移群集管理器或 Get-clusterresource Windows PowerShell cmdlet 检查资源和组状态。

### <a name="event-1069-rcm_resource_failure_with_cause"></a>事件1069： RCM_RESOURCE_FAILURE_WITH_CAUSE

群集角色 "%2" 中类型为 "%3" 的群集资源 "%1" 失败。 错误代码为 "%5" （"%4"）。<br><br>根据资源和角色的故障策略，群集服务可能会尝试在此节点上使资源联机，或者将该组移至群集的其他节点，然后重新启动它。 使用故障转移群集管理器或 Get-clusterresource Windows PowerShell cmdlet 检查资源和组状态。

### <a name="event-1069-rcm_resource_failure_with_error_code"></a>事件1069： RCM_RESOURCE_FAILURE_WITH_ERROR_CODE

群集角色 "%2" 中类型为 "%3" 的群集资源 "%1" 失败。 错误代码为 "%4"。<br><br>根据资源和角色的故障策略，群集服务可能会尝试在此节点上使资源联机，或者将该组移至群集的其他节点，然后重新启动它。 使用故障转移群集管理器或 Get-clusterresource Windows PowerShell cmdlet 检查资源和组状态。

### <a name="event-1069-rcm_resource_failure_due_to_veto"></a>事件1069： RCM_RESOURCE_FAILURE_DUE_TO_VETO

群集角色 "%2" 中类型 "%3" 的群集资源 "%1" 失败，因为试图阻止该群集资源中所需的状态更改。

### <a name="event-1077-res_ipaddr_ipv4_address_interface_failed"></a>事件1077： RES_IPADDR_IPV4_ADDRESS_INTERFACE_FAILED

IP 接口 "%1" （地址 "%2"）的运行状况检查失败（状态为 "%3"）。 运行验证配置向导以确保网络适配器正常运行。

### <a name="event-1078-res_ipaddr_wins_address_failed"></a>事件1078： RES_IPADDR_WINS_ADDRESS_FAILED

群集 IP 地址资源 "%1" 不能联机，因为 WINS 在接口 "%2" 上注册失败，出现错误 "%3"。 确保指定了有效的可访问 WINS 服务器。

### <a name="event-1121-cp_crypto_ckpt_restore_failed"></a>事件1121： CP_CRYPTO_CKPT_RESTORE_FAILED

无法将群集资源 "%1" 的加密设置成功地应用到此节点上的容器名称 "%2"。

### <a name="event-1127-tm_event_cluster_netinterface_failed"></a>事件1127： TM_EVENT_CLUSTER_NETINTERFACE_FAILED

网络 "%3" 上群集节点 "%2" 的群集网络接口 "%1" 失败。 运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1129-tm_event_cluster_network_partitioned"></a>事件1129： TM_EVENT_CLUSTER_NETWORK_PARTITIONED

群集网络 "%1" 已分区。 某些附加的故障转移群集节点无法通过网络相互通信。 故障转移群集无法确定故障的位置。 运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1130-tm_event_cluster_network_down"></a>事件1130： TM_EVENT_CLUSTER_NETWORK_DOWN

群集网络 "%1" 已关闭。 可用节点均无法使用此网络进行通信。 运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1137-rcm_drain_move_failed"></a>事件1137： RCM_DRAIN_MOVE_FAILED

无法完成移动群集角色 "%1" 进行排出。 操作失败，错误代码为 %2。

### <a name="event-1138-res_smb_cant_create_dfs_root"></a>事件1138： RES_SMB_CANT_CREATE_DFS_ROOT

群集文件共享资源 "%1" 不能联机。 创建 DFS 命名空间根目录失败，出现错误 "%3"。 这可能是由于无法启动 "DFS 命名空间" 服务或无法为共享 "%2" 创建 DFS N。

### <a name="event-1141-res_smb_cant_init_dfs_svc"></a>事件1141： RES_SMB_CANT_INIT_DFS_SVC

群集文件共享资源 "%1" 不能联机。 重新同步 DFS 根目标 "%2" 失败，出现错误 "%3"。

### <a name="event-1142-res_smb_cant_online_dfs_root"></a>事件1142： RES_SMB_CANT_ONLINE_DFS_ROOT

由于出现错误 "%2"，DFS 命名空间的群集文件共享资源 "%1" 不能联机。

### <a name="event-1182-netres_resource_stop_error"></a>事件1182： NETRES_RESOURCE_STOP_ERROR

群集资源 "%1" 不能联机，因为关联的服务尝试重新启动失败。 错误代码为 "%2"。 服务需要重新启动才能更新参数。 但是，在停止并重新启动之前，服务失败。 请检查与该服务关联的其他事件，并确保该服务正常工作。

### <a name="event-1183-res_disk_invalid_mp_source_not_clustered"></a>事件1183： RES_DISK_INVALID_MP_SOURCE_NOT_CLUSTERED

群集磁盘资源 "%1" 包含无效的装入点。 与装入点相关联的源磁盘和目标磁盘都必须是群集磁盘，并且必须是同一组的成员。 <br>卷 "%3" 的装入点 "%2" 引用了无效的源磁盘。 请确保源磁盘也是群集磁盘，并且在与目标磁盘相同的组（承载装入点）中。

### <a name="event-1191-res_netname_delete_computer_account_failed_status"></a>事件1191： RES_NETNAME_DELETE_COMPUTER_ACCOUNT_FAILED_STATUS

群集网络名称资源 "%1" 无法删除其在域 "%2" 中的关联计算机对象。 错误代码为 "%3"。 <br>请让域管理员手动删除 Active Directory 域中的计算机对象。

### <a name="event-1192-res_netname_delete_computer_account_failed"></a>事件1192： RES_NETNAME_DELETE_COMPUTER_ACCOUNT_FAILED

群集网络名称资源 "%1" 无法删除其在域 "%2" 中的关联计算机对象，原因如下：<br>%3。 <br><br>请让域管理员手动删除 Active Directory 域中的计算机对象。

### <a name="event-1193-res_netname_add_computer_account_failed_status"></a>事件1193： RES_NETNAME_ADD_COMPUTER_ACCOUNT_FAILED_STATUS

群集网络名称资源 "%1" 无法在域 "%2" 中创建其关联的计算机对象，原因如下： %3。<br><br>关联的错误代码为： %5<br><br>
请与域管理员联系，以确保：

- 群集标识 "%4" 可以创建计算机对象。 默认情况下，在 "计算机" 容器中创建所有计算机对象;如果此位置已更改，请咨询域管理员。
- 尚未达到计算机对象的配额。
- 如果存在现有计算机对象，请使用 "Active Directory 用户和计算机" 工具验证群集标识 "%4" 是否对该计算机对象具有 "完全控制" 权限。

### <a name="event-1194-res_netname_add_computer_account_failed"></a>事件1194： RES_NETNAME_ADD_COMPUTER_ACCOUNT_FAILED

群集网络名称资源 "%1" 在以下时间内无法在域 "%2" 中创建其关联的计算机对象： %3。<br><br>相关错误代码的文本为： %4

请与域管理员联系，以确保：

- 群集标识 "%5" 具有 "创建计算机对象" 权限。 默认情况下，将在与群集标识 "%5" 相同的容器中创建所有计算机对象。
- 尚未达到计算机对象的配额。
- 如果存在现有计算机对象，请使用 "Active Directory 用户和计算机" 工具验证群集标识 "%5" 是否对该计算机对象具有 "完全控制" 权限。

### <a name="event-1195-res_netname_dns_registration_failed_status"></a>事件1195： RES_NETNAME_DNS_REGISTRATION_FAILED_STATUS

群集网络名称资源 "%1" 未能注册一个或多个关联的 DNS 名称。 错误代码为 "%2"。 确保将与从属 IP 地址资源关联的网络适配器配置为具有对至少一个 DNS 服务器的访问权限。

### <a name="event-1196-res_netname_dns_registration_failed"></a>事件1196： RES_NETNAME_DNS_REGISTRATION_FAILED

群集网络名称资源 "%1" 无法注册一个或多个关联的 DNS 名称，原因如下：<br>%2。<br><br>确保为与从属 IP 地址资源关联的网络适配器配置至少一个可访问的 DNS 服务器。

### <a name="event-1205-rcm_event_group_failed_online_offline"></a>事件1205： RCM_EVENT_GROUP_FAILED_ONLINE_OFFLINE

群集服务未能使群集角色 "%1" 完全联机或脱机。 一个或多个资源可能处于 "失败" 状态。 这可能会影响群集角色的可用性。

### <a name="event-1206-res_netname_update_computer_account_failed_status"></a>事件1206： RES_NETNAME_UPDATE_COMPUTER_ACCOUNT_FAILED_STATUS

无法在域 "%2" 中更新与群集网络名称资源 "%1" 关联的计算机对象。 错误代码为 "%3"。 群集标识 "%4" 可能缺少更新该对象所需的权限。 请与域管理员联系，以确保群集标识可以更新域中的计算机对象。

### <a name="event-1207-res_netname_update_computer_account_failed"></a>事件1207： RES_NETNAME_UPDATE_COMPUTER_ACCOUNT_FAILED

无法在域 "%2" 中更新与群集网络名称资源 "%1" 相关联的计算机对象。 <br>%3 操作。<br><br>相关错误代码的文本为： %4<br> <br>群集标识 "%5" 可能缺少更新该对象所需的权限。 请与域管理员联系，以确保群集标识可以更新域中的计算机对象。

### <a name="event-1208-res_disk_invalid_mp_target_not_clustered"></a>事件1208： RES_DISK_INVALID_MP_TARGET_NOT_CLUSTERED

群集磁盘资源 "%1" 包含无效的装入点。 与装入点相关联的源磁盘和目标磁盘都必须是群集磁盘，并且必须是同一组的成员。 <br>卷 "%3" 的装入点 "%2" 引用了无效的目标磁盘。 请确保目标磁盘也是群集磁盘，并且在与源磁盘相同的组（承载装入点）中。

### <a name="event-1211-res_netname_no_writeable_dc_status"></a>事件1211： RES_NETNAME_NO_WRITEABLE_DC_STATUS

群集网络名称资源 "%1" 不能联机。 尝试在域 %2 中查找可写域控制器以创建或更新与资源关联的计算机对象失败。 错误代码为 "%3"。
确保配置的域中的此节点可以访问可写域控制器。 还要确保 DNS 服务器正在运行，以便解析域控制器的名称。

### <a name="event-1212-res_netname_no_writeable_dc"></a>事件1212： RES_NETNAME_NO_WRITEABLE_DC

群集网络名称资源 "%1" 不能联机。 尝试在域 %2 中查找可写域控制器以创建或更新与资源关联的计算机对象失败，原因如下：<br>%3。<br><br> 错误代码为 "%4"。 确保配置的域中的此节点可以访问可写域控制器。 还要确保 DNS 服务器正在运行，以便解析域控制器的名称。

### <a name="event-1213-res_netname_rename_restore_failed"></a>事件1213： RES_NETNAME_RENAME_RESTORE_FAILED

群集网络名称资源 "%1" 无法在域控制器 "%2" 上完全重命名关联的计算机对象。 尝试将计算机对象从新名称 "%3" 重命名回其原始名称 "%4" 也失败。 错误代码为 "%5"。 这可能会影响客户端连接，直到网络名称及其关联的计算机对象名称保持一致。 请与域管理员联系以手动重命名计算机对象。

### <a name="event-1214-res_netname_cant_add_name2"></a>事件1214： RES_NETNAME_CANT_ADD_NAME2

无法向 Netbios 注册群集网络名称资源。 <br><br>网络名称： "%3" <br>失败原因： %2 <br>资源名称： "%1" <br><br> 为网络名称运行 nbtstat，以确保名称尚未注册到 Netbios。

### <a name="event-1215-res_netname_not_registered_with_rdr"></a>事件1215： RES_NETNAME_NOT_REGISTERED_WITH_RDR

群集网络名称资源 "%1" 的运行状况检查失败。 网络名称 "%2" 不再在此节点上注册。 错误代码为 "%3"。 检查与网络适配器相关的硬件或软件错误。 此外，还可以运行验证配置向导来检查网络配置。

### <a name="event-1218-res_netname_online_rename_recovery_missing_account"></a>事件1218： RES_NETNAME_ONLINE_RENAME_RECOVERY_MISSING_ACCOUNT

群集网络名称资源 "%1" 未能执行名称更改操作（尝试将原始名称 "%3" 更改为名称 "%4"）。 在域控制器 "%2" （创建它的位置）上找不到计算机对象。 下次资源进入联机状态时，将尝试重新创建计算机对象。 此外，请与域管理员联系，以确保域中存在该计算机对象。

### <a name="event-1219-res_netname_online_rename_dc_not_found"></a>事件1219： RES_NETNAME_ONLINE_RENAME_DC_NOT_FOUND

群集网络名称资源 "%1" 执行名称更改操作失败。
无法联系正在重命名计算机对象 "%3" 的域控制器 "%2"。 错误代码为 "%4"。 确保可以访问可写域控制器，并检查是否存在任何连接问题。

### <a name="event-1220-res_netname_online_rename_recovery_failed"></a>事件1220： RES_NETNAME_ONLINE_RENAME_RECOVERY_FAILED

无法使用域控制器 %4 将资源 "%1" 的计算机帐户从 %2 重命名为 %3。 关联的错误代码存储在 data 节中。<br>
<br>此资源的计算机帐户正处于重命名的过程中，未完成。 此资源在联机过程中检测到此情况。
若要恢复，计算机帐户必须重命名为 "名称" 属性的当前值，即网络上显示的名称。<br> <br>尝试重命名的域控制器可能不可用;如果是这种情况，请等待域控制器再次可用。 域控制器可能拒绝访问帐户;解析访问后，请尝试再次使名称联机。<br> <br>如果无法做到这一点，请禁用并重新启用 Kerberos 身份验证，并尝试在其他 DC 上查找计算机帐户。 需要将 "名称" 属性更改为 %2 才能使用现有计算机帐户。

### <a name="event-1223-res_ipaddr_invalid_network_role"></a>事件1223： RES_IPADDR_INVALID_NETWORK_ROLE

群集 IP 地址资源 "%1" 不能联机，因为群集网络 "%2" 未配置为允许客户端访问。 请使用故障转移群集管理器管理单元来检查群集网络的配置属性。

### <a name="event-1226-res_netname_tcb_not_held"></a>事件1226： RES_NETNAME_TCB_NOT_HELD

网络名称资源 "%1" （关联网络名称为 "%2"）已启用 Kerberos 身份验证支持。 未能将所需的凭据添加到 LSA-关联的错误代码 "%3" 指示此操作通常需要的权限不足。 所需的权限是 "受信任的计算基础"，必须在组成群集的每个节点上本地启用。

### <a name="event-1227-res_netname_lsa_error"></a>事件1227： RES_NETNAME_LSA_ERROR

网络名称资源 "%1" （关联网络名称为 "%2"）已启用 Kerberos 身份验证支持。 未能将所需的凭据添加到 LSA-关联的错误代码为 "%3"。

### <a name="event-1228-res_netname_clone_failure"></a>事件1228： RES_NETNAME_CLONE_FAILURE

群集网络名称资源 "%1" 在启用此节点上的网络名称时遇到错误。 失败的原因是： <br> "%2"。<br><br> 错误代码为 "%3"。 <br><br> 你可能会将网络名称资源脱机并再次联机以重试。

### <a name="event-1229-res_netname_no_ips_for_dns"></a>事件1229： RES_NETNAME_NO_IPS_FOR_DNS

群集网络名称资源 "%1" 无法确定要在 DNS 服务器上注册的任何 IP 地址。 确保为群集使用启用了一个或多个网络并使用 "允许客户端通过此网络连接" 设置，并且每个节点都具有为网络配置的有效 IP 地址。

### <a name="event-1230-rcm_deadlock_or_crash_detected"></a>事件1230： RCM_DEADLOCK_OR_CRASH_DETECTED

服务器上的组件未及时响应。 这导致群集资源 "%1" （资源类型 "%2"，DLL "%3"）超过其超时阈值。 作为群集运行状况检测的一部分，将执行恢复操作。
群集将通过终止并重新启动运行此资源的资源宿主子系统（RHS）进程来尝试自动恢复。 验证与资源关联的底层基础结构（例如存储、网络或服务）是否正常运行。

### <a name="event-1230-rcm_resource_control_deadlock_detected"></a>事件1230： RCM_RESOURCE_CONTROL_DEADLOCK_DETECTED

服务器上的组件未及时响应。 这导致群集资源 "%1" （资源类型 "%2"，DLL "%3"）在处理控制代码 "%4;" 时超过其超时阈值。 作为群集运行状况检测的一部分，将执行恢复操作。 群集将通过终止并重新启动运行此资源的资源宿主子系统（RHS）进程来尝试自动恢复。 验证与资源关联的底层基础结构（例如存储、网络或服务）是否正常运行。

### <a name="event-1231-res_netname_logon_failure"></a>事件1231： RES_NETNAME_LOGON_FAILURE

群集网络名称资源 "%1" 在登录域时遇到错误。 失败的原因是： <br> "%2"。<br><br> 错误代码为 "%3"。
<br><br> 请确保在配置的域中，此节点可以访问域控制器。

### <a name="event-1232-res_genscript_timeout"></a>事件1232： RES_GENSCRIPT_TIMEOUT

群集通用脚本资源 "%1" 中的入口点 "%2" 未及时完成执行。 这可能是由于无限循环或其他问题导致无限期等待。 或者，为此资源指定的挂起超时值可能太短。 请查看 "%2" 脚本入口点以确保脚本代码中所有可能的无限等待均已更正。 如果需要，请考虑增加挂起超时值。

### <a name="event-1233-res_genscript_hangmode"></a>事件1233： RES_GENSCRIPT_HANGMODE

群集泛型脚本资源 "%1"：将不处理执行 "%2" 操作的请求。 这是由于之前未能及时执行 "%3" 入口点。 请查看此入口点的脚本代码，以确保不存在任何无限循环或其他问题，这可能会导致无限期等待。 如果需要，请考虑增加资源挂起超时值。

### <a name="event-1234-cluster_event_account_missing_privs"></a>事件1234： CLUSTER_EVENT_ACCOUNT_MISSING_PRIVS

群集服务检测到其服务帐户缺少一个或多个所需的权限。 缺少权限列表是： "%1"，当前未被授予服务帐户。 使用 "sc.exe qprivs clussvc" 验证群集服务（ClusSvc）的权限。 此外，请在 Active Directory 域服务中检查任何可能已更改默认权限的安全策略或组策略。 键入以下命令，授予群集服务正确运行所需的权限：

```
sc.exe privs
clussvc
SeBackupPrivilege/SeRestorePrivilege/SeIncreaseQuotaPrivilege/SeIncreaseBasePriorityPrivilege/SeTcbPrivilege/SeDebugPrivilege/SeSecurityPrivilege/SeAuditPrivilege/SeImpersonatePrivilege/SeChangeNotifyPrivilege/SeIncreaseWorkingSetPrivilege/SeManageVolumePrivilege/SeCreateSymbolicLinkPrivilege/SeLoadDriverPrivilege
```

### <a name="event-1242-res_ipaddr_lease_expired"></a>事件1242： RES_IPADDR_LEASE_EXPIRED

与群集 IP 地址资源 "%1" 关联的 IP 地址 "%2" 的租用已过期或即将过期，当前无法续订。 请确保关联的 DHCP 服务器可访问且正确配置为续订此 IP 地址上的租约。

### <a name="event-1245-res_ipaddr_lease_renewal_failed"></a>事件1245： RES_IPADDR_LEASE_RENEWAL_FAILED

群集 IP 地址资源 "%1" 无法续订 IP 地址 "%2" 的租约。
确保 DHCP 服务器可访问且已正确配置为续订此 IP 地址上的租约。

### <a name="event-1250-rcm_resource_embedded_failure"></a>事件1250： RCM_RESOURCE_EMBEDDED_FAILURE

群集角色 "%2" 中的群集资源 "%1" 收到了严重状态通知。 对于虚拟机，这表示虚拟机内的应用程序或服务处于不正常状态。 验证在虚拟机中受监视的服务或应用程序的功能。

### <a name="event-1254-rcm_group_terminal_failure"></a>事件1254： RCM_GROUP_TERMINAL_FAILURE

群集角色 "%1" 已超过其故障转移阈值。 它已在分配给它的故障转移期间内耗尽了配置的故障转移尝试次数，并将处于失败状态。 不会再尝试执行该角色使其联机或将其故障转移到群集中的其他节点。
请检查与失败关联的事件。 解决导致失败的问题后，可以手动使角色联机，或者群集可能会在重新启动延迟期限后再次联机。

### <a name="event-1255-rcm_resource_network_failure"></a>事件1255： RCM_RESOURCE_NETWORK_FAILURE

群集角色 "%2" 中的群集资源 "%1" 收到了严重状态通知。 对于虚拟机，这表示虚拟机的关键网络处于不正常状态。 验证虚拟机和虚拟机配置为使用的虚拟网络的网络连接。

### <a name="event-1256-res_netname_dns_registration_failed_dynamic_dns_zone"></a>事件1256： RES_NETNAME_DNS_REGISTRATION_FAILED_DYNAMIC_DNS_ZONE

群集网络名称资源无法注册一个或多个关联的 DNS 名称，因为相应的 DNS 区域不接受动态更新。<br><br>群集网络名称： "%1"<br>DNS 区域： "%2"

#### <a name="guidance"></a>指南

确保 DNS 配置为动态 DNS 区域。 如果 DNS 服务器不接受动态更新，请在网络适配器属性中取消选中 "在 DNS 中注册此连接的地址"。

### <a name="event-1257-res_netname_dns_registration_failed_secure_dns_zone"></a>事件1257： RES_NETNAME_DNS_REGISTRATION_FAILED_SECURE_DNS_ZONE

群集网络名称资源未能注册一个或多个关联的 DNS 名称，因为更新安全 DNS 区域的访问被拒绝。<br><br>群集网络名称： "%1"<br>DNS 区域： "%2"<br><br>确保已向群集名称对象（CNO）授予对安全 DNS 区域的权限。

### <a name="event-1258-res_netname_dns_registration_failed_timeout"></a>事件1258： RES_NETNAME_DNS_REGISTRATION_FAILED_TIMEOUT

群集网络名称资源无法注册一个或多个关联的 DNS 名称，因为无法访问 DNS 服务器。<br><br>群集网络名称： "%1"<br>DNS 区域： "%2"<br>DNS 服务器： "%3"<br><br>确保为与从属 IP 地址资源关联的网络适配器配置至少一个可访问的 DNS 服务器。

### <a name="event-1259-res_netname_dns_registration_failed_cleanup"></a>事件1259： RES_NETNAME_DNS_REGISTRATION_FAILED_CLEANUP

群集网络名称资源无法注册一个或多个关联的 DNS 名称，因为群集服务无法清理与网络名称对应的现有记录。<br><br>群集网络名称： "%1"<br>DNS 区域： "%2"<br><br>确保已向群集名称对象（CNO）授予对安全 DNS 区域的权限。

### <a name="event-1260-res_netname_dns_registration_modify_failed"></a>事件1260： RES_NETNAME_DNS_REGISTRATION_MODIFY_FAILED

群集网络名称资源修改 DNS 注册失败。<br><br>群集网络名称： "%1"<br>错误代码： "%2"

#### <a name="guidance"></a>指南

确保将与从属 IP 地址资源关联的网络适配器配置为具有对至少一个 DNS 服务器的访问权限。

### <a name="event-1261-res_netname_dns_registration_modify_failed_status"></a>事件1261： RES_NETNAME_DNS_REGISTRATION_MODIFY_FAILED_STATUS

群集网络名称资源修改 DNS 注册失败。<br><br>群集网络名称： "%1"<br>原因： "%2"

#### <a name="guidance"></a>指南

确保将与从属 IP 地址资源关联的网络适配器配置为具有对至少一个 DNS 服务器的访问权限。

### <a name="event-1262-res_netname_dns_registration_publish_ptr_failed"></a>事件1262： RES_NETNAME_DNS_REGISTRATION_PUBLISH_PTR_FAILED

群集网络名称资源无法发布 DNS 反向查找区域中的 PTR 记录。<br><br>群集网络名称： "%1"<br>错误代码： "%2"

#### <a name="guidance"></a>指南

确保将与从属 IP 地址资源关联的网络适配器配置为具有对至少一个 DNS 服务器的访问权限并且 DNS 反向查找区域存在。

### <a name="event-1264-res_netname_dns_registration_publish_ptr_failed_status"></a>事件1264： RES_NETNAME_DNS_REGISTRATION_PUBLISH_PTR_FAILED_STATUS

群集网络名称资源无法发布 DNS 反向查找区域中的 PTR 记录。<br><br>群集网络名称： "%1"<br>原因： "%2"

#### <a name="guidance"></a>指南

确保将与从属 IP 地址资源关联的网络适配器配置为具有对至少一个 DNS 服务器的访问权限并且 DNS 反向查找区域存在。

### <a name="event-1265-res_type_control_timed_out"></a>事件1265： RES_TYPE_CONTROL_TIMED_OUT

在处理控制代码 %2 的过程中，群集资源类型 "%1" 超时。 群集将通过终止并重新启动正在处理调用的资源宿主子系统（RHS）进程来尝试自动恢复。

### <a name="event-1289-netft_adapter_not_found"></a>事件1289： NETFT_ADAPTER_NOT_FOUND

群集服务无法访问网络适配器 "%1"。 请验证其他网络适配器是否正常工作，并检查设备管理器中与适配器 "%1" 相关联的错误。 如果适配器 "%1" 的配置已更改，则可能需要在此计算机上重新安装故障转移群集功能。

### <a name="event-1360-res_ipaddr_invalid_network"></a>事件1360： RES_IPADDR_INVALID_NETWORK

群集 IP 地址资源 "%1" 联机失败。 请确保网络属性 "%2" 与群集网络名称匹配，或者地址属性 "%3" 与群集网络中的一个子网匹配。 如果这是 IPv6 地址类型，请验证与此资源匹配的群集网络是否至少有一个不是链接本地或隧道的 IPv6 前缀。

### <a name="event-1361-res_ipaddr_missing_dependant"></a>事件1361： RES_IPADDR_MISSING_DEPENDANT

IPv6 隧道地址资源 "%1" 无法联机，因为它不依赖 IP 地址（IPv4）资源。 至少需要一个 IP 地址（IPv4）资源的依赖项。

### <a name="event-1362-res_ipaddr_missing_data"></a>事件1362： RES_IPADDR_MISSING_DATA

群集 IP 地址资源 "%1" 无法联机，因为无法读取 "%2" 属性。 请确保已正确配置资源。

### <a name="event-1363-res_ipaddr_no_isatap_support"></a>事件1363： RES_IPADDR_NO_ISATAP_SUPPORT

IPv6 隧道地址资源 "%1" 联机失败。 与依赖 IP 地址（IPv4）资源 "%3" 关联的群集网络 "%2" 不支持 ISATAP 隧道。 请确保群集网络支持 ISATAP 隧道。

### <a name="event-1540-service_backup_noquorum"></a>事件1540： SERVICE_BACKUP_NOQUORUM

群集配置数据的备份操作已中止，因为尚未实现群集的仲裁。 请在群集实现仲裁后重试此备份操作。

### <a name="event-1554-service_restore_invaliduser"></a>事件1554： SERVICE_RESTORE_INVALIDUSER

群集配置数据的还原操作失败。 这是因为与执行还原的用户帐户关联的权限不足。 请确保用户帐户具有本地管理员特权。

### <a name="event-1557-service_witness_attach_failed"></a>事件1557： SERVICE_WITNESS_ATTACH_FAILED

群集服务更新见证服务器资源上的群集配置数据失败。 请确保见证服务器资源处于联机状态并且可访问。

### <a name="event-1559-res_witness_new_node_conflict"></a>事件1559： RES_WITNESS_NEW_NODE_CONFLICT

与文件共享见证资源关联的文件共享 "%1" 当前由服务器 "%2" 承载。 此服务器 "%2" 刚添加为故障转移群集中的新节点。 不建议通过包含同一群集的任何节点托管文件共享见证。 请选择不由同一群集中的任何节点托管的文件共享见证，并相应地修改文件共享见证资源的设置。

### <a name="event-1560-res_smb_share_conflict"></a>事件1560： RES_SMB_SHARE_CONFLICT

群集文件共享资源 "%1" 检测到共享文件夹冲突。 因此，可能无法访问其中某些共享文件夹。 若要纠正这种情况，请确保多个共享文件夹没有相同的共享名。

### <a name="event-1563-res_fsw_onlinefailure"></a>事件1563： RES_FSW_ONLINEFAILURE

文件共享见证资源 "%1" 联机失败。 请确保文件共享 "%2" 存在并且可以由群集访问。

### <a name="event-1566-res_netname_timedout"></a>事件1566： RES_NETNAME_TIMEDOUT

群集网络名称资源 "%1" 不能联机。 资源主机子系统已终止网络名称资源，因为它未在可接受的时间内完成操作。 操作在执行时超时：<br> "%2"

### <a name="event-1567-service_failed_to_change_log_size"></a>事件1567： SERVICE_FAILED_TO_CHANGE_LOG_SIZE

群集服务更改跟踪日志大小失败。 请验证 ClusterLogSize 设置和 "获取群集 \| 格式列表 \* " PowerShell cmdlet。 同时，使用性能监视器管理单元来验证 FailoverClustering 的事件跟踪会话设置。

### <a name="event-1567-res_vipaddr_address_interface_failed"></a>事件1567： RES_VIPADDR_ADDRESS_INTERFACE_FAILED

IP 接口 "%1" （地址 "%2"）的运行状况检查失败（状态为 "%3"）。 检查与物理或虚拟网络适配器相关的硬件或软件错误。

### <a name="event-1568-res_cloud_witness_cant_communicate_to_azure"></a>事件1568： RES_CLOUD_WITNESS_CANT_COMMUNICATE_TO_AZURE

云见证资源无法访问 Microsoft Azure 存储服务。<br><br>群集资源： %1 <br>群集节点： %2

#### <a name="guidance"></a>指南

这可能是由于群集节点和 Microsoft Azure 服务之间的网络通信被阻止。 验证节点与 Microsoft Azure 的 internet 连接。 连接到 Microsoft Azure 门户并验证存储帐户是否存在。

### <a name="event-1569-service_using_restricted_network"></a>事件1569： SERVICE_USING_RESTRICTED_NETWORK

已为故障转移群集使用而禁用的网络 "%1" 找到当前可能的网络，节点 "%2" 可使用该网络与群集中的其他节点进行通信。 这可能会影响节点加入群集的能力。 请验证节点 "%2" 的网络连接，并至少为群集通信启用一个网络。 运行验证配置向导检查您的网络配置。

### <a name="event-1569-res_cloud_witness_token_expired"></a>事件1569： RES_CLOUD_WITNESS_TOKEN_EXPIRED

云见证资源无法通过 Microsoft Azure 存储服务进行身份验证。 尝试与 Microsoft Azure 存储帐户联系时返回了访问被拒绝错误。 <br><br>群集资源： %1

#### <a name="guidance"></a>指南

存储帐户的访问密钥可能不再有效。 使用故障转移群集管理器中的配置群集仲裁向导或 Set-clusterquorum Windows PowerShell cmdlet，使用更新的存储帐户访问密钥配置云见证资源。

### <a name="event-1573-service_form_witness_failed"></a>事件1573： SERVICE_FORM_WITNESS_FAILED

节点 "%1" 无法形成群集。 这是因为见证服务器不可访问。 请确保见证服务器资源处于联机状态且可用。

### <a name="event-1580-res_netname_dns_registration_secure_zone_failed"></a>事件1580： RES_NETNAME_DNS_REGISTRATION_SECURE_ZONE_FAILED

群集网络名称资源 "%1" 无法在安全 DNS 区域中的适配器 "%4" 上注册名称 "%2"。 这是因为具有此名称的现有记录，并且该群集标识没有足够的权限更新该记录。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，验证群集标识是否具有 DNS 记录 "%2" 的权限。

### <a name="event-1580-res_netname_dns_registration_secure_zone_failed"></a>事件1580： RES_NETNAME_DNS_REGISTRATION_SECURE_ZONE_FAILED

群集网络名称资源 "%1" 无法在安全 DNS 区域中的适配器 "%4" 上注册名称 "%2"。 这是因为具有此名称的现有记录，并且该群集标识没有足够的权限更新该记录。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，验证群集标识是否具有 DNS 记录 "%2" 的权限。

### <a name="event-1585-res_fileserver_fscheck_srvsvc_stopped"></a>事件1585： RES_FILESERVER_FSCHECK_SRVSVC_STOPPED

群集文件服务器资源 "%1" 的运行状况检查失败。 这是因为服务器服务未启动。 请使用服务器管理器来确认此群集节点上的服务器服务的状态。

### <a name="event-1586-res_fileserver_fscheck_scoped_name_not_registered"></a>事件1586： RES_FILESERVER_FSCHECK_SCOPED_NAME_NOT_REGISTERED

群集文件服务器资源 "%1" 的运行状况检查失败。 这是因为某些共享文件夹不可访问。 验证是否可以从客户端访问这些文件夹。 此外，请使用服务器管理器确认该群集节点上的服务器服务的状态，并查找与此群集节点上的服务器服务相关的其他事件。 可能需要在此群集角色中重新启动网络名称资源 "%2"。

### <a name="event-1587-res_fileserver_fscheck_failed"></a>事件1587： RES_FILESERVER_FSCHECK_FAILED

群集文件服务器资源 "%1" 的运行状况检查失败。 这是因为某些共享文件夹不可访问。 验证是否可以从客户端访问这些文件夹。 此外，请使用服务器管理器确认该群集节点上的服务器服务的状态，并查找与此群集节点上的服务器服务相关的其他事件。

### <a name="event-1588-res_fileserver_share_cant_add"></a>事件1588： RES_FILESERVER_SHARE_CANT_ADD

群集文件服务器资源 "%1" 不能联机。 资源未能创建与网络名称 "%3" 关联的文件共享 "%2"。 错误代码为 "%4"。 验证文件夹是否存在并可访问。 此外，请使用服务器管理器确认此群集节点上的服务器服务的状态，并在此群集节点上查找其他相关事件。 可能需要重新启动此群集角色中的网络名称资源 "%3"。

### <a name="event-1600-clusapi_create_cannot_set_ad_dacl"></a>事件1600： CLUSAPI_CREATE_CANNOT_SET_AD_DACL

群集服务无法设置群集计算机对象 "%1" 的权限。 请与网络管理员联系，以检查 Active Directory 中计算机对象的群集安全描述符，验证 DACL 是否不太大，并删除对象上的任何不必要的额外 ACE （如有必要）。

### <a name="event-1603-res_fileserver_clone_failed"></a>事件1603： RES_FILESERVER_CLONE_FAILED

由于找不到 "网络名称" 资源上的预期依赖关系或配置不正确，文件服务器无法启动。 错误 = 0x %2。

### <a name="event-1606-res_disk_cno_check_failed"></a>事件1606： RES_DISK_CNO_CHECK_FAILED

群集磁盘资源 "%1" 包含受 BitLocker 保护的卷 "%2"，但对于此卷，Active Directory 群集名称帐户（也称为群集名称对象或 CNO）不是卷的 BitLocker 保护程序。 这是受 BitLocker 保护的卷所必需的。 若要更正此错误，请先从群集中删除该磁盘。 接下来，使用 Manage-bde.exe 命令行工具将群集名称添加为 ADAccountOrGroup 保护程序，并将 ClusterName 的格式设置 \\ \$ 为群集名称。 然后将该磁盘添加回群集。 有关详细信息，请参阅文档 Manage-bde.exe

### <a name="event-1607-res_disk_cno_unlock_failed"></a>事件1607： RES_DISK_CNO_UNLOCK_FAILED

群集磁盘资源 "%1" 无法解锁受 BitLocker 保护的卷 "%2"。 群集名称对象（CNO）未设置为此卷的有效 BitLocker 保护程序。 若要更正此错误，请从群集中删除该磁盘。 然后，使用 Manage-bde.exe 命令行工具将群集名称添加为 ADAccountOrGroup 保护程序，使用 format domain \\ ClusterName \$ ，并将磁盘添加回群集。 有关详细信息，请参阅 Manage-bde.exe 的文档。

### <a name="event-1608-res_fileserver_leader_failed"></a>事件1608： RES_FILESERVER_LEADER_FAILED

由于找不到 "网络名称" 资源上的预期依赖关系或配置不正确，文件服务器无法启动。 错误 = 0x %2。

### <a name="event-1609-res_soda_fileserver_leader_failed"></a>事件1609： RES_SODA_FILESERVER_LEADER_FAILED

Scale Out 文件服务器无法启动，因为找不到 "分布式网络名称" 资源上的预期依赖项或配置不正确。 错误 = 0x %2。

### <a name="event-1632-clusapi_create_mismatched_ou"></a>事件1632： CLUSAPI_CREATE_MISMATCHED_OU

群集的创建失败。 无法在 active directory 组织单位 "%2" 中创建群集名称对象 "%1"。 组织单位 "%3" 中已存在该对象。 验证指定的可分辨名称路径和群集名称对象是否正确。 如果未指定可分辨名称路径，将使用现有计算机对象 "%1"。

### <a name="event-1652-service_tcp_connection_failure"></a>事件1652： SERVICE_TCP_CONNECTION_FAILURE

群集节点 "%1" 无法加入群集。 无法与节点 "%2" 建立 TCP 连接。 验证网络连接和任何网络防火墙的配置。

### <a name="event-1652-service_udp_connection_failure"></a>事件1652： SERVICE_UDP_CONNECTION_FAILURE

群集节点 "%1" 无法加入群集。 无法建立到节点 "%2" 的 UDP 连接。 验证网络连接和任何网络防火墙的配置。

### <a name="event-1652-service_virtual_tcp_connection_failure"></a>事件1652： SERVICE_VIRTUAL_TCP_CONNECTION_FAILURE

群集节点 "%1" 无法加入群集。 无法为节点 "%2" 建立使用 Microsoft 故障转移群集虚拟适配器的 TCP 连接。 验证网络连接和任何网络防火墙的配置。

### <a name="event-1653-service_no_connectivity"></a>事件1653： SERVICE_NO_CONNECTIVITY

群集节点 "%1" 无法加入群集，因为它无法通过网络与群集中的任何其他节点通信。 验证网络连接和任何网络防火墙的配置。

### <a name="event-1654-res_vipaddr_invalid_adaptername"></a>事件1654： RES_VIPADDR_INVALID_ADAPTERNAME

群集非连续 IP 地址资源 "%1" 联机失败。 无法确定与网络适配器 "%2" 对应的网络适配器的配置数据（错误代码为 "%3"）。 检查 IP 地址资源是否配置了正确的地址和网络属性。

### <a name="event-1655-res_vipaddr_invalid_vsid"></a>事件1655： RES_VIPADDR_INVALID_VSID

群集非连续 IP 地址资源 "%1" 联机失败。 无法确定与虚拟子网 Id "%2" 和路由域 Id "%3" 对应的网络适配器的配置数据（错误代码为 "%4"）。 检查 IP 地址资源是否配置了正确的地址和网络属性。

### <a name="event-1656-res_vipaddr_address_create_failed"></a>事件1656： RES_VIPADDR_ADDRESS_CREATE_FAILED

无法为非连续 IP 地址资源 "%1" 添加 IP 地址 "%2" （错误代码为 "%3"）。 检查与物理或虚拟网络适配器相关的硬件或软件错误。

### <a name="event-1664-cluster_upgrade_incomplete"></a>事件1664： CLUSTER_UPGRADE_INCOMPLETE

升级群集的功能级别失败。 检查群集的所有节点当前是否正在运行并且是否为同一版本的 Windows Server，然后再次运行 Update-clusterfunctionallevel Windows PowerShell cmdlet。

### <a name="event-1676-event_local_node_quarantined"></a>事件1676： EVENT_LOCAL_NODE_QUARANTINED

"%1" 已隔离本地群集节点。 节点将被隔离到 "%2"，然后节点将自动尝试重新加入群集。
<br><br>请参阅系统和应用程序事件日志来确定此节点上的问题。 解决问题后，可以手动清除隔离，以允许节点与 "Start-clusternode – ClearQuarantine" Windows PowerShell cmdlet 重新加入。<br><br>QuarantineType：由 %1 隔离<br>将自动清除时间隔离： %2

### <a name="event-1677-event_node_drain_failed"></a>事件1677： EVENT_NODE_DRAIN_FAILED

群集节点 %1 上的节点排出失败。 <br><br>引用节点的系统和应用程序事件日志以及群集日志，调查排出失败的原因。 解决问题后，可以重试排出操作。

### <a name="event-1683-res_netname_computer_account_no_dc"></a>事件1683： RES_NETNAME_COMPUTER_ACCOUNT_NO_DC

群集服务无法连接到域中的任何可用域控制器。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>DC 服务器： %1

#### <a name="guidance"></a>指南

验证域控制器是否可在网络上访问群集节点。

### <a name="event-1684-res_netname_computer_object_vco_not_found"></a>事件1684： RES_NETNAME_COMPUTER_OBJECT_VCO_NOT_FOUND

群集网络名称资源在 Active Directory 中找不到关联的计算机对象。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>网络名称： %1<br>组织单位： %2

#### <a name="guidance"></a>指南

从 Active Directory 回收站中还原网络名称的计算机对象。 或者，使群集网络名称资源脱机，并运行修复操作以在 Active Directory 中重新创建计算机对象。

### <a name="event-1685-res_netname_computer_object_cno_not_found"></a>事件1685： RES_NETNAME_COMPUTER_OBJECT_CNO_NOT_FOUND

群集网络名称资源在 Active Directory 中找不到关联的计算机对象。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>网络名称： %1<br>组织单位： %2
#### <a name="guidance"></a>指南

从 Active Directory 回收站中还原网络名称的计算机对象。

### <a name="event-1686-res_netname_computer_object_vco_disabled"></a>事件1686： RES_NETNAME_COMPUTER_OBJECT_VCO_DISABLED

群集网络名称资源在 Active Directory 中找到要禁用的关联计算机对象。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>网络名称： %1<br>组织单位： %2

#### <a name="guidance"></a>指南

在 Active Directory 中启用网络名称的计算机对象。

### <a name="event-1687-res_netname_computer_object_cno_disabled"></a>事件1687： RES_NETNAME_COMPUTER_OBJECT_CNO_DISABLED

群集网络名称资源在 Active Directory 中找到要禁用的关联计算机对象。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>网络名称： %1<br>组织单位： %2

#### <a name="guidance"></a>指南

在 Active Directory 中启用网络名称的计算机对象。 或者，使群集网络名称资源脱机，并运行修复操作以在 Active Directory 中启用计算机对象。

### <a name="event-1688-res_netname_computer_object_failed"></a>事件1688： RES_NETNAME_COMPUTER_OBJECT_FAILED

群集网络名称资源检测到 Active Directory 中的关联计算机对象已禁用，但在尝试启用该对象时失败。 这可能会影响依赖于群集网络名称身份验证的功能。<br><br>网络名称： %1<br>组织单位： %2

#### <a name="guidance"></a>指南

在 Active Directory 中启用网络名称的计算机对象。

### <a name="event-4608-nodecleanup_get_clustered_disks_failed"></a>事件4608： NODECLEANUP_GET_CLUSTERED_DISKS_FAILED

群集服务在销毁群集时无法检索群集磁盘的列表。 错误代码为 "%1"。 如果这些磁盘不可访问，请执行 "ClusterDiskReservation" PowerShell cmdlet。

### <a name="event-4611-nodecleanup_release_clustered_disks_from_partmgr_failed"></a>事件4611： NODECLEANUP_RELEASE_CLUSTERED_DISKS_FROM_PARTMGR_FAILED

销毁群集时，分区管理器未释放 ID 为 "%2" 的群集磁盘。 错误代码为 "%1"。 重新启动计算机将确保磁盘由分区管理器释放。

### <a name="event-4613-nodecleanup_clear_clusdisk_database_failed"></a>事件4613： NODECLEANUP_CLEAR_CLUSDISK_DATABASE_FAILED

群集服务在销毁群集时无法正确清理 ID 为 "%2" 的群集磁盘。 错误代码为 "%1"。 在成功完成清理之前，你可能无法访问该磁盘。 对于手动清理，请 \\ \\ 在 Windows 注册表中删除 "HKEY_LOCAL_MACHINE SYSTEM CurrentControlSet \\ Services \\ ClusDisk \\ Parameters" 项的 "AttachedDisks" 值。

### <a name="event-4615-nodecleanup_disable_cluster_service_failed"></a>事件4615： NODECLEANUP_DISABLE_CLUSTER_SERVICE_FAILED

群集服务已停止，并在群集节点清理过程中被设置为 "已禁用"。

### <a name="event-4616-nodecleanup_disable_cluster_service_timeout"></a>事件4616： NODECLEANUP_DISABLE_CLUSTER_SERVICE_TIMEOUT

群集节点清理期间终止群集服务未在预期的时间段内完成。 请重新启动此计算机以确保群集服务不再运行。

### <a name="event-4618-nodecleanup_reset_cluster_registry_entries_failed"></a>事件4618： NODECLEANUP_RESET_CLUSTER_REGISTRY_ENTRIES_FAILED

群集节点清理期间重置群集服务注册表项失败。
错误代码为 "%1"。 在成功完成清理之前，你可能无法使用此计算机创建或加入群集。 对于手动清理，请在此计算机上执行 "Start-clusternode" PowerShell cmdlet。

### <a name="event-4620-nodecleanup_unload_cluster_hive_failed"></a>事件4620： NODECLEANUP_UNLOAD_CLUSTER_HIVE_FAILED

在群集节点清理期间卸载群集服务注册表配置单元失败。
错误代码为 "%1"。 在成功完成清理之前，你可能无法使用此计算机创建或加入群集。 对于手动清理，请在此计算机上执行 "Start-clusternode" PowerShell cmdlet。

### <a name="event-4622-nodecleanup_errors"></a>事件4622： NODECLEANUP_ERRORS

群集服务在节点清除过程中遇到错误。 在成功完成清理之前，你可能无法使用此计算机创建或加入群集。 在此节点上使用 "Start-clusternode" PowerShell cmdlet。

### <a name="event-4624-nodecleanup_reset_nlbsflags_failed"></a>事件4624： NODECLEANUP_RESET_NLBSFLAGS_FAILED

在群集节点清理过程中，重置 IPSec 安全关联超时注册表值失败。 错误代码为 "%1"。 对于手动清理，请在此计算机上执行 "Start-clusternode" PowerShell cmdlet。 或者，你可以通过从 Windows 注册表中的 HKEY_LOCAL_MACHINE 删除 "%2" 值和 "%3" 值来重置 IPSec 安全关联超时值。

### <a name="event-4627-nodecleanup_delete_cluster_tasks_failed"></a>事件4627： NODECLEANUP_DELETE_CLUSTER_TASKS_FAILED

节点清理期间删除群集任务失败。 错误代码为 "%1"。
使用 Windows 任务计划程序删除所有剩余的群集任务。

### <a name="event-4629-nodecleanup_delete_local_account_failed"></a>事件4629： NODECLEANUP_DELETE_LOCAL_ACCOUNT_FAILED

在节点清理期间，不会删除由群集管理的本地用户帐户。 错误代码为 "%1"。 打开 "本地用户和组" （lusrmgr.msc）以删除帐户。

### <a name="event-4864-res_vsstask_open_failed"></a>事件4864： RES_VSSTASK_OPEN_FAILED

卷影复制服务任务资源 "%1" 创建失败。 错误代码为 "%2"。

### <a name="event-4865-res_vsstask_terminate_task_failed"></a>事件4865： RES_VSSTASK_TERMINATE_TASK_FAILED

卷影复制服务任务资源 "%1" 失败。 错误代码为 "%2"。
这是因为在脱机操作过程中无法停止关联的任务。 你可能需要使用任务计划程序管理单元手动停止它。

### <a name="event-4866-res_vsstask_delete_task_failed"></a>事件4866： RES_VSSTASK_DELETE_TASK_FAILED

卷影复制服务任务资源 "%1" 失败。 错误代码为 "%2"。
这是因为关联的任务未能作为脱机操作的一部分删除。 可能需要使用任务计划程序管理单元手动删除该管理单元。

### <a name="event-4867-res_vsstask_online_failed"></a>事件4867： RES_VSSTASK_ONLINE_FAILED

卷影复制服务任务资源 "%1" 失败。 错误代码为 "%2"。
这是因为关联的任务未能作为联机操作的一部分添加。 请使用任务计划程序管理单元确保任务配置正确。

### <a name="event-4868-unable_to_start_autologger"></a>事件4868： UNABLE_TO_START_AUTOLOGGER

群集服务启动群集日志跟踪会话失败。 错误代码为 "%2"。 群集将正常工作，但补充日志记录信息将丢失。 使用性能监视器管理单元验证 "%1" 的事件通道设置。

### <a name="event-4869-netft_watchdog_process_hung"></a>事件4869： NETFT_WATCHDOG_PROCESS_HUNG

用户模式运行状况监视已检测到系统未响应。 故障转移群集虚拟适配器已与进程 ID 为 "%2" 的进程 "%1" 失去联系，时间为 "%3" 秒。 请使用性能监视器来评估系统的运行状况，并确定哪个进程可能会对系统产生负面影响。

### <a name="event-4870-netft_watchdog_process_terminated"></a>事件4870： NETFT_WATCHDOG_PROCESS_TERMINATED

用户模式运行状况监视已检测到系统未响应。 故障转移群集虚拟适配器已与进程 ID 为 "%2" 的进程 "%1" 失去联系，时间为 "%3" 秒。 将执行恢复操作。

### <a name="event-4871-netft_miniport_initialization_failure"></a>事件4871： NETFT_MINIPORT_INITIALIZATION_FAILURE

群集服务无法启动。 这是因为故障转移群集虚拟适配器无法初始化微型端口适配器。 错误代码为 "%1"。 验证其他网络适配器是否正常工作，并检查设备管理器中是否存在错误。 如果配置已更改，则可能需要在此计算机上重新安装故障转移群集功能。

### <a name="event-4872-netft_missing_datalink_address"></a>事件4872： NETFT_MISSING_DATALINK_ADDRESS

故障转移群集虚拟适配器无法生成唯一的 MAC 地址。
找不到要从中生成唯一地址的物理以太网适配器，或生成的地址与此计算机上的另一个适配器冲突。 请运行验证配置向导检查您的网络配置。

### <a name="event-5122-dcm_event_root_creation_failed"></a>事件5122： DCM_EVENT_ROOT_CREATION_FAILED

群集服务无法创建群集共享卷根目录 "%2"。
错误消息为 "%1"。

### <a name="event-5142-dcm_volume_no_access"></a>事件5142： DCM_VOLUME_NO_ACCESS

由于出现错误 "%3"，无法再从此群集节点访问群集共享卷 "%1" （"%2"）。 请对此节点与存储设备和网络连接的连接进行故障排除。

### <a name="event-5143-dcm_veto_resource_move_due_to_cc"></a>事件5143： DCM_VETO_RESOURCE_MOVE_DUE_TO_CC

基于节点 "%1" 上的缓存管理器的当前状态，不允许移动磁盘（"%2"），以防止潜在的死锁。 "缓存管理器脏页阈值" 为 %3，"缓存管理器脏页" 为 %4。 如果 "缓存管理器脏页" 小于 "缓存管理器脏页阈值" 的70%，或者如果 "缓存管理器脏页阈值" 减 "缓存管理器脏页" 大于128000页（如果页大小为4096字节，则为 "关于 500MB"）。
群集拒绝资源移动，以防止在此磁盘上的群集共享卷暂停时缓存管理器阻止缓冲写入导致的潜在死锁。

### <a name="event-5144-dcm_snapshot_diff_area_failure"></a>事件5144： DCM_SNAPSHOT_DIFF_AREA_FAILURE

将磁盘（"%1"）添加到群集共享卷时，为卷（"%2"）设置显式快照差异区域关联失败，出现错误 "%3"。 支持群集共享卷的唯一受支持的软件快照差异区域关联。

### <a name="event-5145-dcm_snapshot_diff_area_delete_failure"></a>事件5145： DCM_SNAPSHOT_DIFF_AREA_DELETE_FAILURE

群集磁盘资源 "%1" 删除软件快照失败。 卷 "%3" 上的差异区域无法与卷 "%2" 分离。 这可能是由活动快照引起的。 群集共享卷要求软件快照位于同一磁盘上。

### <a name="event-5146-dcm_veto_resource_move_due_to_dismount"></a>事件5146： DCM_VETO_RESOURCE_MOVE_DUE_TO_DISMOUNT

移动群集共享卷资源 "%1" 被拒绝，因为属于该资源的某个卷处于已卸载状态。 请在卸载操作完成后重试该操作。

### <a name="event-5147-dcm_veto_resource_move_due_to_snapshot"></a>事件5147： DCM_VETO_RESOURCE_MOVE_DUE_TO_SNAPSHOT

移动群集共享卷资源 "%1" 被拒绝，因为属于该资源的某个卷处于已卸载状态。 请在卸载操作完成后重试该操作。

### <a name="event-5148-dcm_veto_resource_move_due_to_io_mode_change"></a>事件5148： DCM_VETO_RESOURCE_MOVE_DUE_TO_IO_MODE_CHANGE

不能移动群集共享卷资源 "%1"，因为在属于该资源的某个卷上正在执行 IO 模式更改操作（直接 IO 到重定向 IO，反之亦然）。 请在操作完成后重试该操作。

### <a name="event-5150-dcm_set_resource_in_failed_state"></a>事件5150： DCM_SET_RESOURCE_IN_FAILED_STATE

群集物理磁盘资源 "%1" 失败。 群集共享卷置于失败状态，出现以下错误： "%2"

### <a name="event-5200-cam_cannot_create_cno_token"></a>事件5200： CAM_CANNOT_CREATE_CNO_TOKEN

群集服务无法创建群集共享卷的群集标识令牌。 错误代码为 "%1"。 确保域控制器是可访问的，并检查连接问题。 在恢复到域控制器的连接之前，对群集共享卷的此节点上的某些操作可能会失败。

### <a name="event-5216-csv_sw_snapshot_failed"></a>事件5216： CSV_SW_SNAPSHOT_FAILED

在群集共享卷 "%1" （"%2"）上创建软件快照失败，出现错误 %3。 资源必须联机才能支持快照创建。 请检查资源的状态。

### <a name="event-5217-csv_sw_snapshot_set_failed"></a>事件5217： CSV_SW_SNAPSHOT_SET_FAILED

在快照集 id 为 "%2" 的群集共享卷（"%1"）上创建软件快照失败，出现错误 "%3"。 请检查 CSV 资源的状态和资源所有者节点的系统事件。

### <a name="event-5219-csv_register_snapshot_prov_with_vss_failed"></a>事件5219： CSV_REGISTER_SNAPSHOT_PROV_WITH_VSS_FAILED

群集服务无法向卷影服务（VSS）注册群集共享卷快照提供程序。 这可能是由于 VSS 服务关闭导致的，或者可能是 VSS 服务出现问题，导致它无法接受传入的请求。 <br>错误: %1

### <a name="event-5377-operation_exceeded_timeout"></a>事件5377： OPERATION_EXCEEDED_TIMEOUT

内部群集服务操作超过了定义的阈值 "%2" 秒。 已终止群集服务来恢复。 服务控制管理器将重新启动群集服务，节点将重新加入群集。

### <a name="event-5396-two_partitions_have_quorum"></a>事件5396： TWO_PARTITIONS_HAVE_QUORUM

此节点上的群集服务正在关闭，因为它检测到有其他群集节点具有仲裁。 当群集服务检测到通过强制仲裁交换机（/fq）启动的另一个节点时，会发生这种情况。 通过强制仲裁交换机启动的节点将继续运行。 使用故障转移群集管理器验证群集服务重新启动时此节点是否自动加入群集。

### <a name="event-5397-rlua_account_failed"></a>事件5397： RLUA_ACCOUNT_FAILED

群集资源 "%1" 无法在此节点上创建或修改复制的本地用户帐户 "%2"。 有关详细信息，请查看群集日志。

### <a name="event-5398-nm_event_cluster_failed_to_form"></a>事件5398： NM_EVENT_CLUSTER_FAILED_TO_FORM

群集无法启动。 群集配置数据的最新副本在尝试启动群集的节点集中不可用。 当节点集不在成员身份中时，对群集的更改发生，因此无法接收配置数据更新。 .<br><br>需要投票才能启动群集： %1<br>可用的投票： %2<br>具有投票的节点： %3

#### <a name="guidance"></a>指南

尝试在群集中的所有节点上启动群集服务，使具有群集配置数据的最新副本的节点能够首先形成群集。 群集将能够启动，节点将自动获取更新后的群集配置数据。 如果群集配置数据的最新副本没有可用节点，请运行 "Start-clusternode-FQ" Windows PowerShell cmdlet。 使用 ForceQuorum （FQ）参数将启动群集服务，并将此节点的群集配置数据副本标记为权威。 如果在具有过时群集数据库副本的节点上强制仲裁，可能会导致在节点未加入群集时所发生的群集配置更改。

## <a name="warning-events"></a>警告事件

### <a name="event-1011-nm_node_evicted"></a>事件1011： NM_NODE_EVICTED

群集节点 %1 已从故障转移群集中逐出。

### <a name="event-1045-res_ipaddr_ipv4_address_create_failed"></a>事件1045： RES_IPADDR_IPV4_ADDRESS_CREATE_FAILED

找不到资源 "%1" IP 地址 "%2" 的匹配网络接口（返回代码是 "%3"）。 如果群集节点跨不同子网，则这可能是正常的。

### <a name="event-1066-res_disk_corrupt_disk"></a>事件1066： RES_DISK_CORRUPT_DISK

群集磁盘资源 "%1" 指示卷 "%2" 损坏。 运行 Chkdsk 以修复问题。 在 Chkdsk 完成之前，磁盘不可用。
Chkdsk 输出将记录到文件 "%3"。<br> Chkdsk 还可以将信息写入应用程序事件日志。

### <a name="event-1068-res_smb_share_cant_add"></a>事件1068： RES_SMB_SHARE_CANT_ADD

群集文件共享资源 "%1" 不能联机。 由于出现错误 "%4"，创建文件共享 "%2" （作用域为网络名称 %3）失败。 将自动重试此操作。

### <a name="event-1071-rcm_resource_online_blocked_by_locked_mode"></a>事件1071： RCM_RESOURCE_ONLINE_BLOCKED_BY_LOCKED_MODE

尝试在群集角色 "%2" 中的 "%3" 类型的群集资源 "%1" 上尝试的操作无法完成，因为该资源或其提供程序之一已锁定状态。

### <a name="event-1071-rcm_resource_offline_blocked_by_locked_mode"></a>事件1071： RCM_RESOURCE_OFFLINE_BLOCKED_BY_LOCKED_MODE

对于群集角色 "%2" 中类型 "%3" 的群集资源 "%1"，尝试的操作无法完成，因为该资源或其某个依赖项的状态为 "已锁定"。

### <a name="event-1094-sm_invalid_security_level"></a>事件1094： SM_INVALID_SECURITY_LEVEL

群集公用属性 SecurityLevel 无法在此群集上更改。 群集安全级别无法更改，因为当前已将群集配置为无身份验证模式。

### <a name="event-1119-res_netname_dns_registration_missing"></a>事件1119： RES_NETNAME_DNS_REGISTRATION_MISSING

群集网络名称资源 "%1" 无法通过适配器 "%4" 注册 DNS 名称 "%2"，原因如下： <br><br>"%3"

### <a name="event-1125-tm_event_cluster_netinterface_unreachable"></a>事件1125： TM_EVENT_CLUSTER_NETINTERFACE_UNREACHABLE

网络 "%3" 上的群集节点 "%2" 的群集网络接口 "%1" 至少被连接到网络的一个其他群集节点无法访问。 故障转移群集无法确定故障的位置。 运行验证配置向导检查您的网络配置。 如果问题仍然存在，请检查与网络适配器相关的硬件或软件错误。 还要检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1149-res_netname_cant_delete_dns_records"></a>事件1149： RES_NETNAME_CANT_DELETE_DNS_RECORDS

与群集资源 "%1" 关联的 DNS 主机（A）和指针（PTR）记录未从资源的关联 DNS 服务器中删除。 如有必要，可以手动删除它们。 请与 DNS 管理员联系，以帮助完成此工作。

### <a name="event-1150-res_netname_dns_ptr_record_delete_failed"></a>事件1150： RES_NETNAME_DNS_PTR_RECORD_DELETE_FAILED

删除与群集网络名称资源 "%1" 关联的主机 "%3" 的 DNS 指针（PTR）记录 "%2" 失败，出现错误 "%4"。
如有必要，可以手动删除记录。 请与 DNS 管理员联系以获得帮助。

### <a name="event-1151-res_netname_dns_a_record_delete_failed"></a>事件1151： RES_NETNAME_DNS_A_RECORD_DELETE_FAILED

删除与群集网络名称资源 "%1" 关联的 DNS 主机（A）记录 "%2" 失败，出现错误 "%3"。 如有必要，可以手动删除记录。 请与 DNS 管理员联系以获得帮助。

### <a name="event-1155-rcm_event_exited_queuing"></a>事件1155： RCM_EVENT_EXITED_QUEUING

角色 "%1" 的挂起移动未完成。

### <a name="event-1197-res_netname_delete_disable_failed"></a>事件1197： RES_NETNAME_DELETE_DISABLE_FAILED

群集网络名称资源 "%1" 在删除资源期间无法删除或禁用其关联的计算机对象 "%2"。 错误代码为 "%3"。 <br>请检查站点是否为只读。 确保群集名称对象在 Active Directory 的 "%2" 对象上具有适当的权限。

### <a name="event-1198-res_netname_delete_vco_guid_failed"></a>事件1198： RES_NETNAME_DELETE_VCO_GUID_FAILED

群集网络名称资源 "%1" 未能删除 guid 为 "%2" 的计算机对象。 错误代码为 "%3"。 <br>请检查站点是否为只读。 确保群集名称对象在 Active Directory 的 "%2" 对象上具有适当的权限。

### <a name="event-1216-service_netname_change_warning"></a>事件1216： SERVICE_NETNAME_CHANGE_WARNING

群集核心网络名称资源上的名称更改操作失败。
尝试将名称更改操作还原回原始名称也失败。 错误代码为 "%1"。 在手动更正此情况之前，你可能无法使用群集名称远程管理群集。

### <a name="event-1221-res_netname_rename_out_of_synch_with_compobj"></a>事件1221： RES_NETNAME_RENAME_OUT_OF_SYNCH_WITH_COMPOBJ

群集网络名称资源 "%1" 的名称 "%2" 与相应的计算机对象名称 "%3" 不匹配。 计算机对象先前的名称更改可能未复制到域中的所有域控制器。 在名称变得一致之前，你将无法重命名网络名称资源。 如果未最近更改计算机对象，请与域管理员联系，以重命名计算机对象，从而使其保持一致。 另外，请确保跨域控制器的复制已成功完成。

### <a name="event-1222-res_netname_set_permissions_failed"></a>事件1222： RES_NETNAME_SET_PERMISSIONS_FAILED

无法更新与群集网络名称资源 "%1" 相关联的计算机对象。<br><br>相关错误代码的文本为： %2<br> <br>群集标识 "%3" 可能缺少更新该对象所需的权限。 请与域管理员联系，以确保群集标识可以更新域中的计算机对象。

### <a name="event-1240-res_ipaddr_obtain_lease_failed"></a>事件1240： RES_IPADDR_OBTAIN_LEASE_FAILED

群集 IP 地址资源 "%1" 无法获取租用的 IP 地址。

### <a name="event-1243-res_ipaddr_release_lease_failed"></a>事件1243： RES_IPADDR_RELEASE_LEASE_FAILED

群集 IP 地址资源 "%1" 无法释放 IP 地址 "%2" 的租约。

### <a name="event-1251-rcm_group_preempted"></a>事件1251： RCM_GROUP_PREEMPTED

群集角色 "%2" 已脱机。 此角色已被较高优先级群集角色 "%1" 抢占。 群集服务将在以后使用系统资源时，尝试使群集角色 "%2" 联机。

### <a name="event-1544-service_vss_onabort"></a>事件1544： SERVICE_VSS_ONABORT

群集配置数据的备份操作已被取消。 群集卷影复制服务（VSS）编写器收到了中止请求。

### <a name="event-1548-service_connect_version_compatible"></a>事件1548： SERVICE_CONNECT_VERSION_COMPATIBLE

节点 "%1" 与节点 "%2" 建立了通信，检测到它正在运行不同但兼容的操作系统版本。 建议所有节点都运行相同版本的操作系统。 升级所有节点后，运行 Update-clusterfunctionallevel Windows PowerShell cmdlet 来完成群集的升级。

### <a name="event-1550-service_connect_novercheck"></a>事件1550： SERVICE_CONNECT_NOVERCHECK

节点 "%1" 已建立与节点 "%2" 的通信会话，但未执行版本兼容性检查，因为禁用了版本兼容性检查。 不支持禁用版本兼容性检查。

### <a name="event-1551-service_form_novercheck"></a>事件1551： SERVICE_FORM_NOVERCHECK

节点 "%1" 形成了故障转移群集，但未执行版本兼容性检查，因为禁用了版本兼容性检查。 不支持禁用版本兼容性检查。

### <a name="event-1555-service_netft_disable_autoconfig_failed"></a>事件1555： SERVICE_NETFT_DISABLE_AUTOCONFIG_FAILED

尝试使用 "%1" 网络适配器的 IPv4 失败。 这是因为无法禁用 IPv4 自动配置和 DHCP。 如果已禁用 DHCP 客户端服务，则可能会出现这种情况。 如果启用，则将使用 IPv6，否则此节点可能无法参与故障转移群集。

### <a name="event-1558-service_witness_failover_attempt"></a>事件1558： SERVICE_WITNESS_FAILOVER_ATTEMPT

群集服务检测到见证服务器资源有问题。 见证服务器资源将故障转移到群集中的其他节点，尝试重新建立对群集配置数据的访问。

### <a name="event-1562-res_fsw_alivefailure"></a>事件1562： RES_FSW_ALIVEFAILURE

文件共享见证资源 "%1" 未能定期检查文件共享 "%2"。 请确保文件共享 "%2" 存在并且可以由群集访问。

### <a name="event-1576-res_netname_dns_registration_secure_zone_refused"></a>事件1576： RES_NETNAME_DNS_REGISTRATION_SECURE_ZONE_REFUSED

群集网络名称资源 "%1" 无法在安全 DNS 区域中的适配器 "%4" 上注册名称 "%2"。 这是因为具有此名称的现有记录，并且该群集标识没有足够的权限更新该记录。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，验证群集标识是否具有 DNS 记录 "%2" 的权限。

### <a name="event-1576-res_netname_dns_registration_secure_zone_refused"></a>事件1576： RES_NETNAME_DNS_REGISTRATION_SECURE_ZONE_REFUSED

群集网络名称资源 "%1" 无法在安全 DNS 区域中的适配器 "%4" 上注册名称 "%2"。 这是因为具有此名称的现有记录，并且该群集标识没有足够的权限更新该记录。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，验证群集标识是否具有 DNS 记录 "%2" 的权限。

### <a name="event-1577-res_netname_dns_server_could_not_be_contacted"></a>事件1577： RES_NETNAME_DNS_SERVER_COULD_NOT_BE_CONTACTED

群集网络名称资源 "%1" 无法在适配器 "%4" 上注册名称 "%2"。 无法联系 DNS 服务器。 错误代码为 "%3"。 确保可从该群集节点访问 DNS 服务器。 稍后将重试 DNS 注册。

### <a name="event-1577-res_netname_dns_server_could_not_be_contacted"></a>事件1577： RES_NETNAME_DNS_SERVER_COULD_NOT_BE_CONTACTED

群集网络名称资源 "%1" 无法在适配器 "%4" 上注册名称 "%2"。 无法联系 DNS 服务器。 错误代码为 "%3"。 确保可从该群集节点访问 DNS 服务器。 稍后将重试 DNS 注册。

### <a name="event-1578-res_netname_dns_test_for_dynamic_update_failed"></a>事件1578： RES_NETNAME_DNS_TEST_FOR_DYNAMIC_UPDATE_FAILED

群集网络名称资源 "%1" 无法在适配器 "%4" 上注册名称 "%2" 的动态更新。 DNS 服务器可能未配置为接受动态更新。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，以验证 DNS 服务器是否可用并已配置为进行动态更新。<br><br>或者，你可以通过在 "DNS" 选项卡下的 "适配器 ' %4" 的 "高级 TCP/IP 设置" 中取消选中 "在 DNS 中注册此连接的地址" 设置来禁用动态 DNS 更新。

### <a name="event-1578-res_netname_dns_test_for_dynamic_update_failed"></a>事件1578： RES_NETNAME_DNS_TEST_FOR_DYNAMIC_UPDATE_FAILED

群集网络名称资源 "%1" 无法在适配器 "%4" 上注册名称 "%2" 的动态更新。 DNS 服务器可能未配置为接受动态更新。 错误代码为 "%3"。 请与 DNS 服务器管理员联系，以验证 DNS 服务器是否可用并已配置为进行动态更新。<br><br>或者，你可以通过在 "DNS" 选项卡下的 "适配器 ' %4" 的 "高级 TCP/IP 设置" 中取消选中 "在 DNS 中注册此连接的地址" 设置来禁用动态 DNS 更新。

### <a name="event-1579-res_netname_dns_record_update_failed"></a>事件1579： RES_NETNAME_DNS_RECORD_UPDATE_FAILED

群集网络名称资源 "%1" 无法更新适配器 "%4" 上的名称 "%2" 的 DNS 记录。 错误代码为 "%3"。 请确保可从该群集节点访问 DNS 服务器，并与 DNS 服务器管理员联系，以验证群集标识是否可以更新 DNS 记录 "%2"。

### <a name="event-1579-res_netname_dns_record_update_failed"></a>事件1579： RES_NETNAME_DNS_RECORD_UPDATE_FAILED

群集网络名称资源 "%1" 无法更新适配器 "%4" 上的名称 "%2" 的 DNS 记录。 错误代码为 "%3"。 请确保可从该群集节点访问 DNS 服务器，并与 DNS 服务器管理员联系，以验证群集标识是否可以更新 DNS 记录 "%2"。

### <a name="event-1581-clussvc_unable_to_move_hive_to_safe_file"></a>事件1581： CLUSSVC_UNABLE_TO_MOVE_HIVE_TO_SAFE_FILE

群集配置数据的还原请求无法创建现有群集配置数据文件（ClusDB）的副本。 尝试保留现有配置时，还原操作无法在位置 "%1" 上创建副本。 如果现有配置数据文件已损坏，则可能会出现这种情况。 还原操作已继续，但可能无法恢复到现有群集配置。

### <a name="event-1582-clussvc_unable_to_move_restored_hive_to_current"></a>事件1582： CLUSSVC_UNABLE_TO_MOVE_RESTORED_HIVE_TO_CURRENT

群集服务无法将位于 "%1" 的还原的群集配置单元移至 "%2"。 这可能会导致还原操作无法成功完成。 如果未正确还原群集配置，请重试还原操作。

### <a name="event-1583-clussvc_netft_disable_connectionsecurity_failed"></a>事件1583： CLUSSVC_NETFT_DISABLE_CONNECTIONSECURITY_FAILED

群集服务无法禁用故障转移群集虚拟适配器 "%1" 上的 Internet 协议安全性（IPsec）。 这可能会对群集通信性能产生负面影响。 如果此问题仍然存在，请验证你的本地和域连接安全策略是否适用于 IPSec 和 Windows 防火墙。 此外，请检查与基本筛选引擎服务有关的事件。

### <a name="event-1584-shared_volume_not_ready_for_snapshot"></a>事件1584： SHARED_VOLUME_NOT_READY_FOR_SNAPSHOT

备份应用程序在群集共享卷 "%1" （"%3"）上启动了 VSS 快照，但未正确为快照准备卷。 此快照可能无效，并且备份可能无法用于还原操作。 请联系你的备份应用程序供应商以验证与群集共享卷的兼容性。

### <a name="event-1589-res_netname_dns_returning_ip_that_is_not_provider"></a>事件1589： RES_NETNAME_DNS_RETURNING_IP_THAT_IS_NOT_PROVIDER

群集网络名称资源 "%1" 找到与 DNS 名称 "%2" 关联的一个或多个 IP 地址，这些 IP 地址不是从属 IP 地址资源。 找到的其他地址为 "%3"。 这可能会影响客户端连接，直到网络名称及其关联的 DNS 记录一致。 请与 DNS 服务器管理员联系，以验证与名称 "%2" 关联的记录。

### <a name="event-1604-res_disk_chkdsk_spotfix_needed"></a>事件1604： RES_DISK_CHKDSK_SPOTFIX_NEEDED

群集磁盘资源 "%1" 检测到卷 "%2" 的损坏。 修复问题需要 Spotfix Chkdsk。

### <a name="event-1605-res_disk_spotfix_performed"></a>事件1605： RES_DISK_SPOTFIX_PERFORMED

群集磁盘资源 "%1" 已完成 ChkDsk.exe 卷 "%2" 上的/spotfix 运行。
返回代码为 "%4"。 已将 ChkDsk 的输出记录到文件 "%3"。<br>
在应用程序事件日志中检查 ChkDsk 的其他信息。

### <a name="event-1671-res_disk_online_set_attributes_completed_failure"></a>事件1671： RES_DISK_ONLINE_SET_ATTRIBUTES_COMPLETED_FAILURE

群集物理磁盘资源不能联机。<br><br>物理磁盘资源名称： %1<br>错误代码： %2<br>已用时间（秒）： %3

#### <a name="guidance"></a>指南

运行验证配置向导以检查你的存储配置。 如果错误代码为 ERROR_CLUSTER_SHUTDOWN，则管理员取消了联机挂起状态。 如果这是复制的卷，则可能是由于无法设置磁盘属性。 有关其他信息，请查看存储复制事件。

### <a name="event-1673-cluster_node_entered_isolated_state"></a>事件1673： CLUSTER_NODE_ENTERED_ISOLATED_STATE

群集节点 "%1" 已进入隔离状态。

### <a name="event-1675-event_joining_node_quarantined"></a>事件1675： EVENT_JOINING_NODE_QUARANTINED

群集节点 "%1" 已由 "%2" 隔离，无法加入群集。 节点将被隔离到 "%3"，然后节点将自动尝试重新加入群集。 <br><br>请参阅系统和应用程序事件日志来确定此节点上的问题。 解决问题后，可以手动清除隔离，以允许节点与 "Start-clusternode – ClearQuarantine" Windows PowerShell cmdlet 重新加入。<br><br>节点名： %1<br>QuarantineType：由 %2 隔离<br>将自动清除时间隔离： %3

### <a name="event-1681-cluster_groups_unmonitored_on_node"></a>事件1681： CLUSTER_GROUPS_UNMONITORED_ON_NODE

节点 "%1" 上的虚拟机已进入未监视状态。 节点从隔离状态返回后，将再次监视虚拟机的运行状况，如果节点未返回，将会进行故障转移。 不再监视的虚拟机是： %2。

### <a name="event-1689-event_disable_and_stop_other_service"></a>事件1689： EVENT_DISABLE_AND_STOP_OTHER_SERVICE

群集服务检测到与故障转移群集不兼容的服务。 已禁用该服务，以避免故障转移群集出现问题。<br><br>服务名称： "%1"

### <a name="event-4625-nodecleanup_reset_nlbsflags_preserved"></a>事件4625： NODECLEANUP_RESET_NLBSFLAGS_PRESERVED

在群集节点清理过程中，重置 IPSec 安全关联超时注册表值失败。 这是因为在将此计算机配置为群集的成员后，将修改 IPSec 安全关联超时。 对于手动清理，请在此计算机上执行 "Start-clusternode" PowerShell cmdlet。 或者，你可以通过从 Windows 注册表中的 HKEY_LOCAL_MACHINE 删除 "%1" 值和 "%2" 值，来重置 IPSec 安全关联超时值。

### <a name="event-4873-netft_clussvc_terminate_because_of_watchdog"></a>事件4873： NETFT_CLUSSVC_TERMINATE_BECAUSE_OF_WATCHDOG

群集服务检测到故障转移群集虚拟适配器已停止。 在此节点上执行热替换 CPU 时，会出现这种情况。
操作完成后，群集服务将停止，并将自动重新启动。 请检查与该服务关联的其他事件，并确保已在此节点上重新启动群集服务。

### <a name="event-5120-dcm_volume_auto_pause_after_failure"></a>事件5120： DCM_VOLUME_AUTO_PAUSE_AFTER_FAILURE

群集共享卷 "%1" （"%2"）已进入暂停状态，因为 "%3"。
所有 i/o 都将暂时排队，直到重新建立卷的路径。

### <a name="event-5123-dcm_event_root_rename_success"></a>事件5123： DCM_EVENT_ROOT_RENAME_SUCCESS

群集共享卷根目录 "%1" 已存在。 目录 "%1" 已重命名为 "%2"。 请验证访问此位置中的数据的应用程序是否在必要时更新。

### <a name="event-5124-dcm_unsafe_filters_found"></a>事件5124： DCM_UNSAFE_FILTERS_FOUND

群集共享卷 "%1" （"%3"）在此设备堆栈上标识了一个或多个活动的筛选器驱动程序，这可能会干扰 CSV 操作。 I/o 访问将通过网络通过其他群集节点重定向到存储设备。 这可能会导致性能下降。 请与筛选器驱动程序供应商联系，验证与群集共享卷的互操作性。 <br><br>找到的活动筛选器驱动程序：<br>%2

### <a name="event-5125-dcm_unsafe_volfilter_found"></a>事件5125： DCM_UNSAFE_VOLFILTER_FOUND

群集共享卷 "%1" （"%3"）在此设备堆栈上标识了一个或多个活动的卷驱动程序，这可能会干扰 CSV 操作。 I/o 访问将通过网络通过其他群集节点重定向到存储设备。 这可能会导致性能下降。 请与卷驱动程序供应商联系，验证与群集共享卷的互操作性。 <br><br>找到的活动卷驱动程序：<br>%2

### <a name="event-5126-dcm_event_cannot_disable_short_names"></a>事件5126： DCM_EVENT_CANNOT_DISABLE_SHORT_NAMES

物理磁盘资源 "%1" 不允许禁用短名称生成。 这可能会导致应用程序兼容性问题。 请使用 "fsutil 8dot3name set 2" 允许禁用短名称生成，然后脱机/联机资源。

### <a name="event-5128-dcm_event_cannot_disable_short_names"></a>事件5128： DCM_EVENT_CANNOT_DISABLE_SHORT_NAMES

物理磁盘资源 "%1" 不允许禁用短名称生成。 这可能会导致应用程序兼容性问题。 请使用 "fsutil 8dot3name set 2" 允许禁用短名称生成，然后脱机/联机资源。

### <a name="event-5133-dcm_cannot_restore_drive_letters"></a>事件5133： DCM_CANNOT_RESTORE_DRIVE_LETTERS

群集磁盘 "%1" 已被删除并放回 "可用存储" 群集组。 在此过程中，还原原始驱动器号的尝试时间比预期要长，这可能是因为这些驱动器号已在使用中。

### <a name="event-5134-dcm_cannot_set_acl_on_root"></a>事件5134： DCM_CANNOT_SET_ACL_ON_ROOT

群集服务无法设置群集共享卷根目录 "%1" 上的权限（ACL）。 错误为 "%2"。

### <a name="event-5135-dcm_cannot_set_acl_on_volume_folder"></a>事件5135： DCM_CANNOT_SET_ACL_ON_VOLUME_FOLDER

群集服务无法设置对群集共享卷目录 "%1" （"%2"）的权限。 错误为 "%3"。

### <a name="event-5136-dcm_csv_into_redirected_mode"></a>事件5136： DCM_CSV_INTO_REDIRECTED_MODE

群集共享卷 "%1" （"%2"）重定向访问已启用。 将从访问此卷的所有群集节点中的网络重定向对存储设备的访问。 这可能会导致性能下降。 关闭此卷的重定向访问以恢复正常操作。

### <a name="event-5149-dcm_csv_block_cache_resized"></a>事件5149： DCM_CSV_BLOCK_CACHE_RESIZED

缓存大小已根据填充的内存调整为 "%1"，用户 setsize 过高。

### <a name="event-5156-dcm_volume_auto_pause_after_snapshot_failure"></a>事件5156： DCM_VOLUME_AUTO_PAUSE_AFTER_SNAPSHOT_FAILURE

群集共享卷 "%1" （"%2"）已进入暂停状态，因为 "%3"。
如果在用户请求之外删除了 CSV 卷的所有 volsnap 快照，则会出现此错误。 删除快照的可能原因是卷上的空间不足以使快照增长，或者尝试更新快照数据时出现 IO 故障。 在快照状态与 volsnap 同步之前，所有 i/o 都将暂时排队。

### <a name="event-5157-dcm_volume_auto_pause_after_failure_expected"></a>事件5157： DCM_VOLUME_AUTO_PAUSE_AFTER_FAILURE_EXPECTED

群集共享卷 "%1" （"%2"）已进入暂停状态，因为 "%3"。
所有 i/o 都将暂时排队，直到重新建立卷的路径。
此错误通常是由基础结构故障引起的。 例如，失去了到存储或要从活动群集成员身份中删除群集共享卷的节点的连接。

### <a name="event-5394-pool_online_warnings"></a>事件5394： POOL_ONLINE_WARNINGS

群集服务尝试使存储池联机时遇到一些存储错误。 运行群集存储验证以解决此问题。

### <a name="event-5395-rcm_group_auto_move_storage_pool"></a>事件5395： RCM_GROUP_AUTO_MOVE_STORAGE_POOL

群集正在移动存储池 "%1" 的组，因为当前节点 "%3" 没有到存储池物理磁盘的最佳连接。

## <a name="informational-events"></a>信息事件

### <a name="event-1592-clussvc_tcp_reconnect_connection_reestablished"></a>事件1592： CLUSSVC_TCP_RECONNECT_CONNECTION_REESTABLISHED

群集节点 "%1" 丢失了与群集节点 "%2" 的通信。 已重新建立网络通信。 这可能是由于防火墙或连接安全策略更新暂时阻止了通信。 如果此问题仍然存在并且未重新建立网络通信，则一个或多个节点上的群集服务将停止。 如果发生这种情况，请运行验证配置向导检查您的网络配置。 此外，检查与此节点上的网络适配器相关的硬件或软件错误，并检查节点连接到的任何其他网络组件（如集线器、交换机或网桥）中是否存在故障。

### <a name="event-1594-cluster_functional_level_upgrade_complete"></a>事件1594： CLUSTER_FUNCTIONAL_LEVEL_UPGRADE_COMPLETE

群集服务成功升级群集功能级别。 <br><br>
功能级别： %1 <br> 升级版本： %2

### <a name="event-1635-rcm_resource_failure_info_with_typename"></a>事件1635： RCM_RESOURCE_FAILURE_INFO_WITH_TYPENAME

群集角色 "%2" 中类型为 "%3" 的群集资源 "%1" 失败。

### <a name="event-1636-clussvc_password_changed"></a>事件1636： CLUSSVC_PASSWORD_CHANGED

群集服务更改了节点 "%2" 上的帐户 "%1" 的密码。

### <a name="event-1680-cluster_node_exited_isolated_state"></a>事件1680： CLUSTER_NODE_EXITED_ISOLATED_STATE

群集节点 "%1" 已退出隔离状态。

### <a name="event-1682-cluster_group_moved_no_longer_unmonitored"></a>事件1682： CLUSTER_GROUP_MOVED_NO_LONGER_UNMONITORED

已将独立节点 "%1" 上未监视的虚拟机 "%2" 故障转移到另一个节点。 再次监视虚拟机的运行状况。

### <a name="event-1682-cluster_multiple_groups_no_longer_unmonitored"></a>事件1682： CLUSTER_MULTIPLE_GROUPS_NO_LONGER_UNMONITORED

节点 "%1" 已加入群集，并且在该节点上运行的以下虚拟机再次被监视其运行状况状态： %2。

### <a name="event-4621-nodecleanup_success"></a>事件4621： NODECLEANUP_SUCCESS

已成功从群集中删除此节点。

### <a name="event-5121-dcm_volume_no_direct_io_due_to_failure"></a>事件5121： DCM_VOLUME_NO_DIRECT_IO_DUE_TO_FAILURE

群集共享卷 "%1" （"%2"）无法再从此群集节点直接访问。 I/o 访问将通过网络重定向到拥有该卷的节点。 如果这导致性能下降，请在重新建立与存储设备的连接后，对此节点到存储设备的连接进行故障排除，并将恢复到正常状态。

### <a name="event-5218-csv_old_sw_snapshot_deleted"></a>事件5218： CSV_OLD_SW_SNAPSHOT_DELETED

群集物理磁盘资源 "%1" 删除了软件快照。 群集共享卷 "%2" 上的软件快照已被删除，因为它早于 "%3" 天。 快照 ID 是 "%4"，它是从节点 "%5" （位于 "%6"）创建的。
备份作业完成后，备份应用程序应删除快照。 此快照超过了快照所需的时间。 向备份应用程序验证备份作业是否成功完成。

## <a name="additional-references"></a>其他参考

-   [Windows Server 2008 中故障转移群集组件的详细事件信息](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753362(v%3dws.10))
