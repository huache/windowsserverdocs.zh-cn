---
title: bitsadmin
description: 适用于**bitsadmin**的 Windows 命令主题，它是一个用于创建、下载或上传作业并监视其进度的命令行工具。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: 4853036e-1df8-45ad-8be6-cfb097b8dd27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7a9cbf715474621b7102d0baf0c448e0ee578bf9
ms.sourcegitcommit: 1d83ca198c50eef83d105151551c6be6f308ab94
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605557"
---
# <a name="bitsadmin"></a>bitsadmin

> **适用于**： windows Server （半年频道），windows server 2016，windows Server 2012 R2，windows server 2012，windows 10

Bitsadmin 是一个命令行工具，用于创建、下载或上载作业，以及监视其进度。 Bitsadmin 工具使用开关来确定要执行的工作。 可以调用`bitsadmin /?`或`bitsadmin /help`以获取开关列表。

大多数交换机都需要`<job>`一个参数，该参数将设置为作业的显示名称或 GUID。 作业的显示名称不必是唯一的。 **/Create**和 **/list**开关返回作业的 GUID。

默认情况下，你可以访问你自己的作业的信息。 若要访问其他用户的作业信息，你必须拥有管理员权限。 如果作业是在提升的状态下创建的，则必须从提升的窗口中运行**bitsadmin** ;否则，你将拥有该作业的只读访问权限。

许多开关对应于[BITS 接口](https://docs.microsoft.com/windows/win32/bits/bits-interfaces)中的方法。 有关可能与使用开关相关的其他详细信息，请参阅相应的方法。

使用以下开关创建作业、设置和检索作业的属性，以及监视作业的状态。 有关演示如何使用其中一些开关执行任务的示例，请参阅[bitsadmin 示例](bitsadmin-examples.md)。

## <a name="available-switches"></a>可用开关

- [bitsadmin/addfile](bitsadmin-addfile.md)
- [bitsadmin/addfileset](bitsadmin-addfileset.md)
- [bitsadmin/addfilewithranges](bitsadmin-addfilewithranges.md)
- [bitsadmin/cache](bitsadmin-cache.md)
- [bitsadmin/cache/delete](bitsadmin-cache-and-delete.md)
- [bitsadmin/cache/deleteurl](bitsadmin-cache-and-deleteurl.md)
- [bitsadmin/cache/getexpirationtime](bitsadmin-cache-and-getexpirationtime.md)
- [bitsadmin/cache/getlimit](bitsadmin-cache-and-getlimit.md)
- [bitsadmin/cache/help](bitsadmin-cache-and-help.md)
- [bitsadmin/cache/info](bitsadmin-cache-and-info.md)
- [bitsadmin/cache/list](bitsadmin-cache-and-list.md)
- [bitsadmin/cache/setexpirationtime](bitsadmin-cache-and-setexpirationtime.md)
- [bitsadmin/cache/setlimit](bitsadmin-cache-and-setlimit.md)
- [bitsadmin/cache/clear](bitsadmin-cache-clear.md)
- [bitsadmin/cancel](bitsadmin-cancel.md)
- [bitsadmin/complete](bitsadmin-complete.md)
- [bitsadmin/create](bitsadmin-create.md)
- [bitsadmin/examples](bitsadmin-examples.md)
- [bitsadmin/getaclflags](bitsadmin-getaclflags.md)
- [bitsadmin/getbytestotal](bitsadmin-getbytestotal.md)
- [bitsadmin/getbytestransferred](bitsadmin-getbytestransferred.md)
- [bitsadmin/getclientcertificate](bitsadmin-getclientcertificate.md)
- [bitsadmin/getcompletiontime](bitsadmin-getcompletiontime.md)
- [bitsadmin/getcreationtime](bitsadmin-getcreationtime.md)
- [bitsadmin/getcustomheaders](bitsadmin-getcustomheaders.md)
- [bitsadmin/getdescription](bitsadmin-getdescription.md)
- [bitsadmin/getdisplayname](bitsadmin-getdisplayname.md)
- [bitsadmin/geterror](bitsadmin-geterror.md)
- [bitsadmin/geterrorcount](bitsadmin-geterrorcount.md)
- [bitsadmin/getfilestotal](bitsadmin-getfilestotal.md)
- [bitsadmin/getfilestransferred](bitsadmin-getfilestransferred.md)
- [bitsadmin/gethelpertokenflags](bitsadmin-gethelpertokenflags.md)
- [bitsadmin/gethelpertokensid](bitsadmin-gethelpertokensid.md)
- [bitsadmin/gethttpmethod](bitsadmin-gethttpmethod.md)
- [bitsadmin/getmaxdownloadtime](bitsadmin-getmaxdownloadtime.md)
- [bitsadmin/getminretrydelay](bitsadmin-getminretrydelay.md)
- [bitsadmin/getmodificationtime](bitsadmin-getmodificationtime.md)
- [bitsadmin/getnoprogresstimeout](bitsadmin-getnoprogresstimeout.md)
- [bitsadmin/getnotifycmdline](bitsadmin-getnotifycmdline.md)
- [bitsadmin/getnotifyflags](bitsadmin-getnotifyflags.md)
- [bitsadmin/getnotifyinterface](bitsadmin-getnotifyinterface.md)
- [bitsadmin/getowner](bitsadmin-getowner.md)
- [bitsadmin/getpeercachingflags](bitsadmin-getpeercachingflags.md)
- [bitsadmin/getpriority](bitsadmin-getpriority.md)
- [bitsadmin/getproxybypasslist](bitsadmin-getproxybypasslist.md)
- [bitsadmin/getproxylist](bitsadmin-getproxylist.md)
- [bitsadmin/getproxyusage](bitsadmin-getproxyusage.md)
- [bitsadmin/getreplydata](bitsadmin-getreplydata.md)
- [bitsadmin/getreplyfilename](bitsadmin-getreplyfilename.md)
- [bitsadmin/getreplyprogress](bitsadmin-getreplyprogress.md)
- [bitsadmin/getsecurityflags](bitsadmin-getsecurityflags.md)
- [bitsadmin/getstate](bitsadmin-getstate.md)
- [bitsadmin/gettemporaryname](bitsadmin-gettemporaryname.md)
- [bitsadmin/gettype](bitsadmin-gettype.md)
- [bitsadmin/getvalidationstate](bitsadmin-getvalidationstate.md)
- [bitsadmin/help](bitsadmin-help.md)
- [bitsadmin/info](bitsadmin-info.md)
- [bitsadmin/list](bitsadmin-list.md)
- [bitsadmin/listfiles](bitsadmin-listfiles.md)
- [bitsadmin/makecustomheaderswriteonly](bitsadmin-makecustomheaderswriteonly.md)
- [bitsadmin/monitor](bitsadmin-monitor.md)
- [bitsadmin/nowrap](bitsadmin-nowrap.md)
- [bitsadmin/peercaching](bitsadmin-peercaching.md)
- [bitsadmin/peercaching/getconfigurationflags](bitsadmin-peercaching-and-getconfigurationflags.md)
- [bitsadmin/peercaching/help](bitsadmin-peercaching-and-help.md)
- [bitsadmin/peercaching/setconfigurationflags](bitsadmin-peercaching-and-setconfigurationflags.md)
- [bitsadmin/peers](bitsadmin-peers.md)
- [bitsadmin/peers/clear](bitsadmin-peers-and-clear.md)
- [bitsadmin/peers/discover](bitsadmin-peers-and-discover.md)
- [bitsadmin/peers/help](bitsadmin-peers-and-help.md)
- [bitsadmin/peers/list](bitsadmin-peers-and-list.md)
- [bitsadmin/rawreturn](bitsadmin-rawreturn.md)
- [bitsadmin/removeclientcertificate](bitsadmin-removeclientcertificate.md)
- [bitsadmin/removecredentials](bitsadmin-removecredentials.md)
- [bitsadmin/replaceremoteprefix](bitsadmin-replaceremoteprefix.md)
- [bitsadmin/reset](bitsadmin-reset.md)
- [bitsadmin/resume](bitsadmin-resume.md)
- [bitsadmin/setaclflag](bitsadmin-setaclflag.md)
- [bitsadmin/setclientcertificatebyid](bitsadmin-setclientcertificatebyid.md)
- [bitsadmin/setclientcertificatebyname](bitsadmin-setclientcertificatebyname.md)
- [bitsadmin/setcredentials](bitsadmin-setcredentials.md)
- [bitsadmin/setcustomheaders](bitsadmin-setcustomheaders.md)
- [bitsadmin/setdescription](bitsadmin-setdescription.md)
- [bitsadmin/setdisplayname](bitsadmin-setdisplayname.md)
- [bitsadmin/sethelpertoken](bitsadmin-sethelpertoken.md)
- [bitsadmin/sethelpertokenflags](bitsadmin-sethelpertokenflags.md)
- [bitsadmin/sethttpmethod](bitsadmin-sethttpmethod.md)
- [bitsadmin/setmaxdownloadtime](bitsadmin-setmaxdownloadtime.md)
- [bitsadmin/setminretrydelay](bitsadmin-setminretrydelay.md)
- [bitsadmin/setnoprogresstimeout](bitsadmin-setnoprogresstimeout.md)
- [bitsadmin/setnotifycmdline](bitsadmin-setnotifycmdline.md)
- [bitsadmin/setnotifyflags](bitsadmin-setnotifyflags.md)
- [bitsadmin/setpeercachingflags](bitsadmin-setpeercachingflags.md)
- [bitsadmin/setpriority](bitsadmin-setpriority.md)
- [bitsadmin/setproxysettings](bitsadmin-setproxysettings.md)
- [bitsadmin/setreplyfilename](bitsadmin-setreplyfilename.md)
- [bitsadmin/setsecurityflags](bitsadmin-setsecurityflags.md)
- [bitsadmin/setvalidationstate](bitsadmin-setvalidationstate.md)
- [bitsadmin/suspend](bitsadmin-suspend.md)
- [bitsadmin/takeownership](bitsadmin-takeownership.md)
- [bitsadmin/transfer](bitsadmin-transfer.md)
- [bitsadmin/util](bitsadmin-util.md)
- [bitsadmin/util/enableanalyticchannel](bitsadmin-util-and-enableanalyticchannel.md)
- [bitsadmin/util/getieproxy](bitsadmin-util-and-getieproxy.md)
- [bitsadmin/util/help](bitsadmin-util-and-help.md)
- [bitsadmin/util/repairservice](bitsadmin-util-and-repairservice.md)
- [bitsadmin/util/setieproxy](bitsadmin-util-and-setieproxy.md)
- [bitsadmin/util/version](bitsadmin-util-and-version.md)
- [bitsadmin/wrap](bitsadmin-wrap.md)
