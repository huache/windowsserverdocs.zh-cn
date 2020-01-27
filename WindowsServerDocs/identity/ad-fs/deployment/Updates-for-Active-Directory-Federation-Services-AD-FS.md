---
ms.assetid: ed3206b4-bbfc-4bc7-a43c-981b0544a50d
title: Active Directory 联合身份验证服务（AD FS）所需的更新
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 3/29/2019
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 0850145c9281c769c5a2b6532ccb56615abd11b3
ms.sourcegitcommit: ff0db5ca093a31034ccc5e9156f5e9b45b69bae5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725782"
---
# <a name="required-updates-for-active-directory-federation-services-ad-fs-and-web-application-proxy-wap"></a>Active Directory 联合身份验证服务（AD FS）和 Web 应用程序代理（WAP）的必需更新

从2016年10月起，Windows Server 的所有组件的所有更新仅通过 Windows 更新（WU）发布。  没有更多的修补程序或单独的下载。
这适用于 Windows Server 2016、Windows Server 2012 R2、Windows Server 2012 和 Windows Server 2008 R2 SP1。

此页列出了 AD FS 和 WAP 的特定兴趣汇总包，以及建议用于 AD FS 和 WAP 的修补程序更新的历史列表。

## <a name="updates-for-ad-fs-and-wap-in-windows-server-2016"></a>AD FS 및 Windows Server 2016에서에서 WAP에 대 한 업데이트
Windows Server 2016 的更新通过 Windows 更新每月传递，并具有累积性。 建议所有 AD FS 和 WAP 2016 服务器使用下面列出的更新包，并包括以前所需的所有更新以及最新的修补程序。

|知识库# |설명|출시 날짜
|----- | ----- |-----
|[CVE-2019-1126](https://portal.msrc.microsoft.com/security-guidance/advisory/CVE-2019-1126) | 此安全更新解决了 Active Directory 联合身份验证服务（AD FS）中的漏洞，攻击者可能会绕过 extranet 锁定策略。 |2019 年 7 月|
|[4489889（OS 版本14393.2879）](https://support.microsoft.com/help/4489889/windows-10-update-kb4489889) | 解决了 Active Directory 联合身份验证服务（AD FS）中的问题，该问题会导致重复的信赖方信任出现在 AD FS 管理控制台中。 当你使用 AD FS 管理控制台创建或查看信赖方信任时，会发生这种情况。</br></br> 解决在 AD FS 2016 上启用 Extranet 智能锁定（ESL）时发生的高 Active Directory 联合身份验证服务（ADFS） Web 应用程序代理（WAP）延迟问题（超过10个000ms）。 此安全更新解决了[CVE-2018-16794](https://nvd.nist.gov/vuln/detail/CVE-2018-16794)中描述的漏洞。 |2019 年 3 月|
|[4487006（OS 版本14393.2828）](https://support.microsoft.com/help/4487006/windows-10-update-kb4487006) | 解决了使用 PowerShell 或 Active Directory 联合身份验证服务（AD FS）管理控制台时导致信赖方信任更新失败的问题。 如果将信赖方信任配置为使用发布多个 PassiveRequestorEndpoint 的联机元数据 URL，则会出现此问题。 错误为 "MSIS7615：信赖方信任中指定的受信任终结点对于该信赖方信任必须是唯一的。"  </br></br>解决了显示因 Azure 密码保护策略而导致外部复杂性密码更改的特定错误消息的问题。 |2019년 2월|
|[4462928（OS 版本14393.2580）](https://support.microsoft.com/help/4462928/windows-10-update-kb4462928)|解决 Active Directory 联合身份验证服务（ADFS） Extranet 智能锁定（ESL）与备用登录 ID 之间的互操作问题。 启用备用登录 ID 后，调用 AD FS Powershell cmdlet AdfsAccountActivity 和 AdfsAccountLockout，返回 "找不到帐户" 错误。 调用 AdfsAccountActivity 时，将添加新条目，而不是编辑现有条目。|2018년 10월|
|[4343884（OS 版本14393.2457）](https://support.microsoft.com/help/4343884/windows-10-update-kb4343884)|解决了在使用自定义区域性定义的移动设备上，多重身份验证不能正常工作的 Active Directory 联合身份验证服务（AD FS）问题。 </br></br>解决 Windows Hello 企业版中的问题，该问题导致新用户注册出现明显的延迟（15秒）。 当使用硬件安全模块存储 ADFS 注册机构（RA）证书时，会出现此问题。|2018년 8월|
|[4338822（OS 版本14393.2395）](https://support.microsoft.com/help/4338822/windows-10-update-kb4338822)|解决了在从控制台创建或查看信赖方信任时，在 AD FS 管理控制台中显示重复信赖方信任的 AD FS 问题。</br></br>解决 ADFS 中导致 Windows Hello 企业版失败的问题。 当存在两个声明提供程序时，会出现此问题。 PIN 注册将失败，出现 "400 内部服务器错误：无法获取设备标识符"。</br></br> 解决与从不结束的非活动连接相关的 WAP 问题。 这会导致系统资源泄漏（例如，内存泄漏），并导致 WAP 服务不再响应。 解决了阻止用户选择不同登录选项的 AD FS 问题。 当用户选择使用基于证书的身份验证登录时，将发生这种情况，但尚未对其进行配置。 如果用户选择 "基于证书的身份验证"，然后尝试选择另一个登录选项，也会发生这种情况。 如果发生这种情况，则用户将被重定向到 "基于证书的身份验证" 页，直到它们关闭浏览器。|2018 年 7 月|
|[4103720（OS 版本14393.2273）](https://support.microsoft.com/help/4103720/windows-10-update-kb4103720)|解决了 ADFS 的问题，该问题会导致在启用 PreventTokenReplays 时，IdP 启动到 SAML 信赖方的登录失败。 </br></br>解决在从设备或浏览器应用程序进行 OAUTH 身份验证时发生的 ADFS 问题。 用户密码更改将生成失败，并要求用户退出应用或浏览器进行登录。 </br></br>解决了在 UTC + 1 和更高版本（欧洲和亚洲）中启用 Extranet 智能锁定的问题不起作用。 此外，它还会导致正常的 Extranet 锁定失败，并出现以下错误： AdfsAccountActivity：大于或等于 MinValue 的 datetime 值，转换为 UTC 时，不能序列化为 JSON。</br></br>解决了 ADFS Windows Hello for business 问题，新用户无法设置其 PIN。 如果未配置 MFA 提供程序，则会发生这种情况。|2018년 5월|
|[4093120（OS 版本14393.2214）](https://support.microsoft.com/help/4093120/windows-10-update-kb4093120)| 解决未处理的刷新令牌验证问题。 它生成以下错误： "IdentityServer： OAuthInvalidRefreshTokenException： MSIS9312：收到的 OAuth 刷新令牌无效。 接收的刷新令牌早于令牌中允许的时间。 " |2018년 4월|
|[4077525（OS 版本14393.2097）](https://support.microsoft.com/help/4077525/windows-10-update-kb4077525)|解决当 ADFS 场至少有两台使用 Windows 内部数据库（WID）的服务器时，出现 HTTP 500 错误的问题。 在此方案中，Web 应用程序代理（WAP）服务器上的 HTTP 基本预身份验证无法对某些用户进行身份验证。 发生此错误时，可能还会在 WAP 事件日志中看到 Microsoft Windows Web 应用程序代理警告事件 ID 13039。 说明读取，"Web 应用程序代理无法对用户进行身份验证。 预身份验证为 "适用于丰富客户端的 ADFS"。 给定的用户无权访问给定的信赖方。 需要修改目标信赖方或 WAP 信赖方的授权规则。</br></br>解决了在身份验证期间 AD FS 不再忽略 prompt = login 的问题。 添加了禁用的选项，以支持未使用密码身份验证的情况。 有关详细信息，请参阅在 Windows Server 2016 RTM 中进行身份验证期间，AD FS 忽略 "prompt = login" 参数。</br></br>解决在 AD FS 中，将证书选作身份验证选项的授权客户（和信赖方）将无法连接。 如果启用了 Windows 集成身份验证（WIA）并且请求可以执行 WIA，则在使用 prompt = login 时会发生此错误。</br></br>解决当标识提供者（IDP）与 OAuth 组中的信赖方（RP）关联时，AD FS 错误地显示主领域发现（HRD）页的问题。 除非 OAuth 组中的 RP 关联了多个 Idp，否则不会向用户显示 HRD 页。 相反，用户将直接转到关联的 IDP 进行身份验证。|2018년 2월|
|[4041688（OS 版本14393.1794）](https://support.microsoft.com/kb/4041688)|此修补程序解决了由于缓存行为不正确而导致 AD 颁发商请求错误的标识提供程序的问题。 这可能会影响身份验证功能，如多重身份验证。 </br></br>添加了 AAD Connect Health 的功能，以便在混合 SQL2014SP1-WS2012R2 和 WS2016 ADFS 场中使用正确的保真度（使用详细审核）来报告 ADFS 服务器运行状况。</br></br>解决了在将 2012 R2 ADFS 场升级到 ADFS 2016 的过程中，如果有许多信赖方信任，用于引发场行为级别的 powershell cmdlet 将失败并出现超时。</br></br>解决了在将请求与其他安全令牌服务器（STS）进行联合时，AD FS 通过修改 wct 参数值导致身份验证失败的问题。|2017년 10월|
|[4038801（OS 版本14393.1737）](https://support.microsoft.com/kb/4038801)|使用联合 LDPs 为 OIDC 注销添加了支持。 这将允许 "展台方案"，在这种情况下，多个用户可能会按顺序登录到与 LDP 联合的单一设备。</br></br>修复了基于 CEP/CES 证书的 WinHello 问题无法与 gMSA 帐户一起使用。</br></br>修复 Windows Server 2016 ADFS 服务器上的 Windows 内部数据库（WID）因外键而无法同步某些设置（如 IdentityServerPolicy 和 IdentityServerPolicy 表中的 ApplicationGroupId 列）的问题constraint. 此类同步失败会导致在主 ADFS 服务器和辅助 ADFS 服务器之间出现不同的声明、声明提供程序和应用程序体验。 此外，如果将 WID 主角色移至辅助节点，则在 ADFS 管理 UX 中将无法再管理应用程序组。</br></br>此更新修复了多重身份验证在使用自定义区域性定义的移动设备上无法正常工作的问题|2017년 9월|
|[4034661（OS 版本14393.1613）](https://support.microsoft.com/kb/4034661)|修复了以下问题：在启用 "成功审核" 和 "失败审核" 之后，ADFS 4.0 \ Windows Server 2016 RS1 ADFS 服务器的安全事件日志中的411事件 nog 记录了调用方 IP 地址。</br></br>此修补程序解决了将 ADFX 服务器配置为使用 HTTP 代理时 Azure 多重身份验证（MFA）的问题。</br></br>"解决了向 ADFS 代理服务器呈现过期或吊销的证书的问题，不会向用户返回错误。"|2017년 8월|
|[4034658（OS 版本14393.1593）](https://support.microsoft.com/kb/4034658)|解决 2016 AD FS 服务器的问题，以便在本地的部署上支持适用于 Windows Hello 企业版的 MFA 证书注册|2017년 8월|
|[4025334（OS 版本14393.1532）](https://support.microsoft.com/kb/4025334)|解决了在 PkeyAuth 请求包含错误数据的情况下，PkeyAuth 标记处理程序可能导致身份验证失败的问题。 身份验证仍应继续，而不执行设备身份验证|2017년 7월|
|[4022723（OS 版本14393.1378）](https://support.microsoft.com/kb/4022723)|[Web 应用程序代理]2012R2/2016 混合部署中的 WAP 2016 未选取 DisableHttpOnlyCookieProtection 配置属性的值 </br></br>[Web 应用程序代理]无法从 EAS 预身份验证方案 AD FS 获取用户访问令牌。</br></br>AD FS 2016： WSFED 注销导致了异常|2017년 6월
|[3213986](https://support.microsoft.com/kb/3213986)|适用于基于 x64 的系统的 Windows Server 2016 累积更新（KB3213986）| 2017년 1월

## <a name="updates-for-ad-fs-and-wap-in-windows-server-2012-r2"></a>AD FS 및 WAP Windows Server 2012 r 2에서에 대 한 업데이트
下面是为 Windows Server 2012 R2 中的 Active Directory 联合身份验证服务（AD FS）发布的修补程序和更新汇总列表。

|知识库# |설명|출시 날짜
|----- | ----- |-----
|[4507448](https://support.microsoft.com/help/4507448/windows-8-1-update-kb4507448)| 此安全更新解决了 Active Directory 联合身份验证服务（AD FS）中的漏洞，攻击者可能会绕过 extranet 锁定策略。 |2019 年 7 月
|[4041685](https://support.microsoft.com/kb/4041685)|解决了一个 AD FS 问题：请求标头中的 MSISConext cookie 最终会使标头大小限制溢出，导致无法使用 HTTP 状态代码 400 "错误的请求标头过长" 进行身份验证。</br></br>修复了在身份验证期间，ADFS 无法再忽略 "prompt = login" 的问题。 添加了 "禁用" 选项，用于还原使用非密码身份验证的情况。|10月2017预览版更新汇总
|[4019217](https://support.microsoft.com/kb/4019217)|使用服务器 2012 R2 AD FS 服务器时，使用令牌代理的工作文件夹客户端不起作用|5月2017预览版更新汇总
|[4015550](https://support.microsoft.com/kb/4015550)|修复了 AD FS 不对外部用户进行身份验证和 AD FS WAP 随机失败转发请求的问题|2017年4月更新汇总
|[4015547](https://support.microsoft.com/kb/4015547)|修复了 AD FS 不对外部用户进行身份验证和 AD FS WAP 随机失败转发请求的问题|2017年4月安全更新
|[4012216](https://support.microsoft.com/kb/4009970)|MS17-019 此安全更新解决了 Active Directory 联合身份验证服务（ADFS）中的漏洞。 如果攻击者将特制请求发送到 AD FS 服务器，则该漏洞可能导致信息泄露，这使得攻击者能够读取有关目标系统的敏感信息。|2017年3月更新汇总
|[3179574](https://support.microsoft.com/kb/3179574)|修复了 AD FS extranet 密码更新的问题。 |2016年8月更新汇总
|[3172614](https://support.microsoft.com/kb/3172614)|引入了 prompt = 登录[支持](https://technet.microsoft.com/windows-server-docs/identity/ad-fs/overview/ad-fs-faq#BKMK_7)，已解决 AD FS 管理控制台和 AlwaysRequireAuthentication 设置问题。 |2016年7月更新汇总
|[3163306](https://support.microsoft.com/kb/3163306)|Active Directory 联合身份验证服务（AD FS）3.0 无法连接到配置为使用连接字符串中安全套接字层（SSL）端口636或3269的轻型目录访问协议（LDAP）属性存储。 |2016年6月更新汇总
|[3148533](https://support.microsoft.com/kb/3148533)|Windows Server 2012 r 2에서 ADFS 프록시를 통해 MFA 대체 (fallback) 인증에 실패 |2016년 5월
|[3134787](https://support.microsoft.com/kb/3134787)|AD FS 로그는 Windows Server 2012 r 2에서의 계정 잠금 시나리오에 대 한 클라이언트 IP 주소를 포함 하지 않습니다. |2016년 2월
|[3134222](https://support.microsoft.com/kb/3134222)|서비스 주소 거부에 Active Directory Federation Services 용 보안 업데이트 MS16-020:: 2016 년 2 월 9 일|2016년 2월
|[3105881](https://support.microsoft.com/kb/3105881)|AD FS Windows Server 2012 R2 기반 서버에서 디바이스 인증을 사용 하는 경우 애플리케이션에 액세스할 수 없습니다.|2015 년 10 월
|[3092003](https://support.microsoft.com/kb/3092003)|페이지를 반복적으로 로드 하 고 사용자가 Windows Server 2012 R2 AD FS에서 MFA를 사용할 때 인증에 실패|2015년 8월
|[3080778](https://support.microsoft.com/kb/3080778)|MFA 어댑터는 Windows Server 2012 r 2에서 예외를 throw 하는 경우 AD FS OnError를 호출 하지 않습니다.|2015 년 7 월
|[3075610](https://support.microsoft.com/kb/3075610)|트러스트 관계를 추가 하거나 Windows Server 2012 r 2에서 클레임 공급자를 제거한 후 보조 AD FS 서버에서 손실 됩니다.|2015 년 7 월
|[3070080](https://support.microsoft.com/kb/3070080)|비 클레임 인식 신뢰 당사자 트러스트에 대 한 제대로 작동 하지 홈 영역 검색|2015 년 6 월
|[3052122](https://support.microsoft.com/kb/3052122)|Windows Server 2012 r 2에서 AD FS 토큰에 복합 ID 클레임에 대 한 지원을 추가 하는 업데이트|2015 년 5 월
|[3045711](https://support.microsoft.com/kb/3045711)|MS15-040: Active Directory 페더레이션 서비스의 취약점으로 정보 공개|2015 년 4 월
|[3042127](https://support.microsoft.com/kb/3042127)|"HTTP 400-잘못 된 요청" Windows Server 2012 r 2에서 WAP 통해 공유 사서함을 열면 하는 동안 오류가 발생 했습니다.|2015 년 3 월
|[3042121](https://support.microsoft.com/kb/3042121)|Windows Server 2012 r 2에서 웹 애플리케이션 프록시 인증 토큰에 대 한 AD FS 토큰 재생 보호|2015 년 3 월
|[3035025](https://support.microsoft.com/kb/3035025)|사용자는 Windows Server 2012 r 2에서 등록 된 디바이스를 사용 하 여 필요가 없도록 암호 업데이트에 대 한 핫픽스 기능|2015 년 1 월
|[3033917](https://support.microsoft.com/kb/3033917)|AD FS는 Windows Server 2012 r 2에서 SAML 응답을 처리할 수 없습니다.|2015 년 1 월
|[3025080](https://support.microsoft.com/kb/3025080)|Windows Server 2012 r 2에서 웹 애플리케이션 프록시를 통해 Office 파일을 저장 하려고 할 때 작업이 실패|2015 년 1 월
|[3025078](https://support.microsoft.com/kb/3025078)|묻는 메시지가 사용자에 대 한 다시는 잘못 된 사용자 이름을 사용 하 여 Windows Server 2012 r 2에 로그온 할 때|2015 년 1 월
|[3020813](https://support.microsoft.com/kb/3020813)|Windows Server 2012 R2 AD FS에서 웹 애플리케이션을 실행할 때 인증을 위해 묻는|2015 년 1 월
|[3020773](https://support.microsoft.com/kb/3020773)|Windows Server 2012 r 2에서 디바이스 등록 서비스의 초기 배포 후 시간 초과 오류|2015 년 1 월
|[3018886](https://support.microsoft.com/kb/3018886)|메시지가 표시 되는 사용자 이름 및 암호를 두 번 인트라넷에서 Windows Server 2012 R2 AD FS 서버에 액세스할 때|2015 년 1 월
|[3013769](https://support.microsoft.com/kb/3013769)|Windows Server 2012 R2 업데이트 롤업|2014 년 12 월
|[3000850](https://support.microsoft.com/kb/3000850)|Windows Server 2012 R2 업데이트 롤업|2014 年 11 月
|[2975719](https://support.microsoft.com/kb/2975719)|Windows Server 2012 R2 업데이트 롤업|2014 년 8 월
|[2967917](https://support.microsoft.com/kb/2967917)|Windows Server 2012 R2 업데이트 롤업|2014 년 7 월
|[2962409](https://support.microsoft.com/kb/2962409)|Windows Server 2012 R2 업데이트 롤업|2014 년 6 월
|[2955164](https://support.microsoft.com/kb/2955164)|Windows Server 2012 R2 업데이트 롤업|2014 년 5 월
|[2919355](https://support.microsoft.com/kb/2919355)|Windows Server 2012 R2 업데이트 롤업|2014년 4월

## <a name="updates-for-ad-fs-in-windows-server-2012-ad-fs-21-and-ad-fs-20"></a>Windows Server 2012 中的 AD FS 更新（AD FS 2.1）和 AD FS 2。0
下面是针对 AD FS 2.0 和2.1 发布的修补程序和更新汇总列表。

|知识库# |설명|출시 날짜|적용 대상:
|----- | ----- |-----|-----
|[3197878](https://support.microsoft.com/kb/3197878)|在 Windows Server 2012 中通过代理进行身份验证失败（这是修补程序3094446的一般版本）|11月2016质量汇总|AD FS 2.1
|[3197869](https://support.microsoft.com/kb/3197869)|在 Windows Server 2008 R2 SP1 中通过代理进行的身份验证失败（修补程序3094446的一般版本）|11月2016质量汇总|AD FS 2.0
|[3094446](https://support.microsoft.com/kb/3094446)|Windows Server 2012 또는 Windows Server 2008 R2 s p 1에서 프록시를 통해 인증 실패|2015 년 9 월|AD FS 2.0 和2。1
|[3070078](https://support.microsoft.com/kb/3070078)|当你对 Windows Server 2012 中的加密证书进行身份验证时，AD FS 2.1 会引发异常|2015 년 7 월|AD FS 2.1
|[3062577](https://support.microsoft.com/kb/3062577)|MS15-062: Active Directory 페더레이션 서비스의 취약점으로 권한 상승 문제점|2015 년 6 월|AD FS 2.0 / 2.1
|[3003381](https://support.microsoft.com/kb/3003381)|M s 14-077: Active Directory 페더레이션 서비스의 취약점으로 정보 공개: 2015 년 4 월 14 일|2014 年 11 月|AD FS 2.0 / 2.1
|[2987843](https://support.microsoft.com/kb/2987843)|많은 사용자가 Windows Server 2012에서 웹 애플리케이션에 로그온 하는 경우 AD FS 페더레이션 서버의 메모리 사용량은 계속 증가|2014 년 7 월|AD FS 2.1
|[2957619](https://support.microsoft.com/kb/2957619)|위임 된 토큰에 대 한 AD FS를 요청 하는 경우 중지 됩니다. AD FS에서 신뢰 당사자 트러스트|2014 년 5 월|AD FS 2.1
|[2926658](https://support.microsoft.com/kb/2926658)|SQL 권한이 없을 경우 ADFS SQL 팜 배포 실패|2014년 10월|AD FS 2.1
|[2896713](https://support.microsoft.com/kb/2896713) 또는 [2989956](https://support.microsoft.com/kb/2989956)|업데이트는 AD FS 서버에 2843638 보안 업데이트를 설치 하려면 몇 가지 문제를 해결 하려면|2013 년 11 월</br></br>2014 년 9 월|AD FS 2.0 / 2.1
|[2877424](https://support.microsoft.com/kb/2877424)|업데이트를 사용 하면 2.1 팜의 AD FS에서 여러 신뢰 당사자 트러스트에 대 한 인증서가 두 개를 사용 하 여|2013년 10월|AD FS 2.1
|[2873168](https://support.microsoft.com/kb/2873168)|FIX: 타사 CSP 및 HSM을 사용 하 고 다음 Windows Server 2008 R2 서비스 팩 1에서 AD FS 2.0에 대 한 업데이트 롤업 3에서 클레임 공급자 트러스트를 구성할 때 오류가 발생 한다|2013 년 9 월|AD FS 2.0
|[2861090](https://support.microsoft.com/kb/2861090)|Windows Server 2008 R2 s p 1에서 예외를 발생 하는 암호화 인증서의 주체 이름에 쉼표|2013년8월|AD FS 2.0
|[2843639](https://support.microsoft.com/kb/2843639)|[보안] Active Directory Federation Services의 취약점으로 인 한 정보 공개|2013 년 11 월|AD FS 2.1
|[2843638](https://support.microsoft.com/kb/2843638)|MS13-066: 2008 Active Directory Federation Services 2.0에 대 한 보안 업데이트: 2013 년 8 월 13 일|2013년8월|AD FS 2.0
|[2827748](https://support.microsoft.com/kb/2827748)|Federationmetadata.xml 파일에 Windows Server 2012에서 Ws-trust 및 Ws-federation 엔드포인트에 대 한 MEX 엔드포인트 정보가 없습니다.|2013년 5월|AD FS 2.1
|[2790338](https://support.microsoft.com/kb/2790338)|Active Directory Federation Services (AD FS)에 대 한 업데이트 롤업 3의 설명 2.0|2013년 3월|AD FS 2.0
