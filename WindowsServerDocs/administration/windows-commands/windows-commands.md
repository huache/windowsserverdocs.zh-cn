---
title: Windows 命令
description: 参考
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: c703d07c-8227-4e86-94a6-8ef390f94cdc
author: jasongerend
ms.author: jgerend
manager: dongill
ms.date: 06/09/2020
ms.prod: windows-server
ms.openlocfilehash: 66de80652f764840af70e88dfd39df2398ae495c
ms.sourcegitcommit: 99d548141428c964facf666c10b6709d80fbb215
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/12/2020
ms.locfileid: "84721110"
---
# <a name="windows-commands"></a>Windows 命令

所有受支持的 Windows 版本（服务器和客户端）都具有内置的一组 Win32 控制台命令。

此文档集介绍了可用于通过脚本或脚本工具自动执行任务的 Windows 命令。

若要查找有关特定命令的信息，请在下面的 A-z 菜单中，单击命令开头的字母，然后单击命令名称。

[一个](#a)  |
[B](#b)  |
[C](#c)  |
[D](#d)  |
[E](#e)  |
[F](#f)  |
[G](#g)  |
[H](#h)  |
[I](#i)  |
[J](#j)  |
[K](#k)  |
[L](#l)  |
[M](#m)  |
[N](#n)  |
[O](#o)  |
[P](#p)  |
[Q](#q)  |
[R](#r)  |
[S](#s)  |
[T](#t)  |
[U](#u)  |
[V](#v)  |
[W](#w)  |
[X](#x) |Y |Z

## <a name="prerequisites"></a>先决条件

本主题中包含的信息适用于：

- Windows Server 2019
- Windows Server（半年频道）
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2
- Windows 2008 Server
- Windows 10
- Windows 8.1

### <a name="command-shell-overview"></a>命令外壳概述

命令行界面是 Windows 中内置的第一个 shell，用批处理（.bat）文件自动完成日常任务，如用户帐户管理或夜间备份。 借助 Windows 脚本宿主，你可以在命令行界面中运行更复杂的脚本。 有关详细信息，请参阅[cscript](cscript.md)或[wscript.echo](wscript.md)。 使用脚本可以更有效地执行操作，而不是使用用户界面。 脚本接受命令行中可用的所有命令。

Windows 有两个命令 shell：命令 shell 和[PowerShell](https://docs.microsoft.com/powershell/scripting/powershell-scripting?view=powershell-6)。 每个 shell 是一种软件程序，它提供你与操作系统或应用程序之间的直接通信，同时提供用于自动执行 IT 操作的环境。

PowerShell 旨在扩展命令行界面的功能，以运行称为 cmdlet 的 PowerShell 命令。 Cmdlet 类似于 Windows 命令，但提供更可扩展的脚本语言。 可以在 Powershell 中运行 Windows 命令和 PowerShell cmdlet，但命令 shell 只能运行 Windows 命令，而不能运行 PowerShell cmdlet。

对于最新的 Windows automation 最新功能，建议使用 PowerShell，而不是 Windows 命令或 windows 脚本宿主来实现 Windows automation。

> [!NOTE]
>你还可以下载和安装 powershell [Core](https://docs.microsoft.com/powershell/scripting/whats-new/what-s-new-in-powershell-core-60?view=powershell-6)，即 powershell 的开源版本。

> [!CAUTION]
> 不正确地编辑注册表可能会对系统造成严重损坏。 在对注册表进行以下更改之前，应备份计算机上任何有价值的数据。

> [!NOTE]
> 若要在计算机或用户登录会话上的命令行界面中启用或禁用文件和目录名完成，请运行**regedit.exe** ，并设置以下**reg_DWOrd 值**：
>
> HKEY_LOCAL_MACHINE \Software\Microsoft\Command Processor\completionChar\ reg_DWOrd
>
> 若要设置**reg_DWOrd**值，请将控制字符的十六进制值用于特定函数（例如， **0 9**为 Tab， **0 08**为 Backspace）。 用户指定的设置优先于计算机设置，命令行选项优先于注册表设置。

## <a name="command-line-reference-a-z"></a>命令行参考 a-z

若要查找有关特定 Windows 命令的信息，请在以下 a-z 菜单中，单击该命令的开头字母，然后单击命令名称。

[一个](#a)  |
[B](#b)  |
[C](#c)  |
[D](#d)  |
[E](#e)  |
[F](#f)  |
[G](#g)  |
[H](#h)  |
[I](#i)  |
[J](#j)  |
[K](#k)  |
[L](#l)  |
[M](#m)  |
[N](#n)  |
[O](#o)  |
[P](#p)  |
[Q](#q)  |
[R](#r)  |
[S](#s)  |
[T](#t)  |
[U](#u)  |
[V](#v)  |
[W](#w)  |
[X](#x) |Y |Z

### <a name="a"></a>A

- [active](active.md)
- [add](add.md)
- [add alias](add-alias.md)
- [add volume](add-volume.md)
- [append](append.md)
- [arp](arp.md)
- [assign](assign.md)
- [assoc](assoc.md)
- [at](at.md)
- [atmadm](atmadm.md)
- [attach-vdisk](attach-vdisk.md)
- [attrib](attrib.md)
- [attributes](attributes.md)
  - [attributes disk](attributes-disk.md)
  - [attributes volume](attributes-volume.md)
- [auditpol](auditpol.md)
  - [auditpol backup](auditpol-backup.md)
  - [auditpol clear](auditpol-clear.md)
  - [auditpol get](auditpol-get.md)
  - [auditpol list](auditpol-list.md)
  - [auditpol remove](auditpol-remove.md)
  - [auditpol resourcesacl](auditpol-resourcesacl.md)
  - [auditpol restore](auditpol-restore.md)
  - [auditpol set](auditpol-set.md)
- [autochk](autochk.md)
- [autoconv](autoconv.md)
- [autofmt](autofmt.md)
- [automount](automount.md)

### <a name="b"></a>B

- [bcdboot](bcdboot.md)
- [bcdedit](bcdedit.md)
- [bdehdcfg](bdehdcfg.md)
  - [bdehdcfg driveinfo](bdehdcfg-driveinfo.md)
  - [bdehdcfg newdriveletter](bdehdcfg-newdriveletter.md)
  - [bdehdcfg quiet](bdehdcfg-quiet.md)
  - [bdehdcfg restart](bdehdcfg-restart.md)
  - [bdehdcfg size](bdehdcfg-size.md)
  - [bdehdcfg target](bdehdcfg-target.md)
- [begin backup](begin-backup.md)
- [begin restore](begin-restore.md)
- [bitsadmin](bitsadmin.md)
  - [bitsadmin addfile](bitsadmin-addfile.md)
  - [bitsadmin addfileset](bitsadmin-addfileset.md)
  - [bitsadmin addfilewithranges](bitsadmin-addfilewithranges.md)
  - [bitsadmin cache](bitsadmin-cache.md)
    - [bitsadmin cache 和 delete](bitsadmin-cache-and-delete.md)
    - [bitsadmin cache 和 deleteurl](bitsadmin-cache-and-deleteurl.md)
    - [bitsadmin cache 和 getexpirationtime](bitsadmin-cache-and-getexpirationtime.md)
    - [bitsadmin cache 和 getlimit](bitsadmin-cache-and-getlimit.md)
    - [bitsadmin cache 和 help](bitsadmin-cache-and-help.md)
    - [bitsadmin cache 和 info](bitsadmin-cache-and-info.md)
    - [bitsadmin cache 和 list](bitsadmin-cache-and-list.md)
    - [bitsadmin cache 和 setexpirationtime](bitsadmin-cache-and-setexpirationtime.md)
    - [bitsadmin cache 和 setlimit](bitsadmin-cache-and-setlimit.md)
    - [bitsadmin cache 和 clear](bitsadmin-cache-clear.md)
  - [bitsadmin cancel](bitsadmin-cancel.md)
  - [bitsadmin complete](bitsadmin-complete.md)
  - [bitsadmin create](bitsadmin-create.md)
  - [bitsadmin 示例](bitsadmin-examples.md)
  - [bitsadmin getaclflags](bitsadmin-getaclflags.md)
  - [bitsadmin getbytestotal](bitsadmin-getbytestotal.md)
  - [bitsadmin getbytestransferred](bitsadmin-getbytestransferred.md)
  - [bitsadmin getclientcertificate](bitsadmin-getclientcertificate.md)
  - [bitsadmin getcompletiontime](bitsadmin-getcompletiontime.md)
  - [bitsadmin getcreationtime](bitsadmin-getcreationtime.md)
  - [bitsadmin getcustomheaders](bitsadmin-getcustomheaders.md)
  - [bitsadmin getdescription](bitsadmin-getdescription.md)
  - [bitsadmin getdisplayname](bitsadmin-getdisplayname.md)
  - [bitsadmin geterror](bitsadmin-geterror.md)
  - [bitsadmin geterrorcount](bitsadmin-geterrorcount.md)
  - [bitsadmin getfilestotal](bitsadmin-getfilestotal.md)
  - [bitsadmin getfilestransferred](bitsadmin-getfilestransferred.md)
  - [bitsadmin gethelpertokenflags](bitsadmin-gethelpertokenflags.md)
  - [bitsadmin gethelpertokensid](bitsadmin-gethelpertokensid.md)
  - [bitsadmin gethttpmethod](bitsadmin-gethttpmethod.md)
  - [bitsadmin getmaxdownloadtime](bitsadmin-getmaxdownloadtime.md)
  - [bitsadmin getminretrydelay](bitsadmin-getminretrydelay.md)
  - [bitsadmin getmodificationtime](bitsadmin-getmodificationtime.md)
  - [bitsadmin getnoprogresstimeout](bitsadmin-getnoprogresstimeout.md)
  - [bitsadmin getnotifycmdline](bitsadmin-getnotifycmdline.md)
  - [bitsadmin getnotifyflags](bitsadmin-getnotifyflags.md)
  - [bitsadmin getnotifyinterface](bitsadmin-getnotifyinterface.md)
  - [bitsadmin getowner](bitsadmin-getowner.md)
  - [bitsadmin getpeercachingflags](bitsadmin-getpeercachingflags.md)
  - [bitsadmin getpriority](bitsadmin-getpriority.md)
  - [bitsadmin getproxybypasslist](bitsadmin-getproxybypasslist.md)
  - [bitsadmin getproxylist](bitsadmin-getproxylist.md)
  - [bitsadmin getproxyusage](bitsadmin-getproxyusage.md)
  - [bitsadmin getreplydata](bitsadmin-getreplydata.md)
  - [bitsadmin getreplyfilename](bitsadmin-getreplyfilename.md)
  - [bitsadmin getreplyprogress](bitsadmin-getreplyprogress.md)
  - [bitsadmin getsecurityflags](bitsadmin-getsecurityflags.md)
  - [bitsadmin getstate](bitsadmin-getstate.md)
  - [bitsadmin gettemporaryname](bitsadmin-gettemporaryname.md)
  - [bitsadmin gettype](bitsadmin-gettype.md)
  - [bitsadmin getvalidationstate](bitsadmin-getvalidationstate.md)
  - [bitsadmin help](bitsadmin-help.md)
  - [bitsadmin info](bitsadmin-info.md)
  - [bitsadmin list](bitsadmin-list.md)
  - [bitsadmin listfiles](bitsadmin-listfiles.md)
  - [bitsadmin makecustomheaderswriteonly](bitsadmin-makecustomheaderswriteonly.md)
  - [bitsadmin monitor](bitsadmin-monitor.md)
  - [bitsadmin nowrap](bitsadmin-nowrap.md)
  - [bitsadmin peercaching](bitsadmin-peercaching.md)
    - [bitsadmin peercaching 和 getconfigurationflags](bitsadmin-peercaching-and-getconfigurationflags.md)
    - [bitsadmin peercaching 和 help](bitsadmin-peercaching-and-help.md)
    - [bitsadmin peercaching 和 setconfigurationflags](bitsadmin-peercaching-and-setconfigurationflags.md)
  - [bitsadmin peers](bitsadmin-peers.md)
    - [bitsadmin peers 和 clear](bitsadmin-peers-and-clear.md)
    - [bitsadmin peers 和 discover](bitsadmin-peers-and-discover.md)
    - [bitsadmin peers 和 help](bitsadmin-peers-and-help.md)
    - [bitsadmin peers 和 list](bitsadmin-peers-and-list.md)
  - [bitsadmin rawreturn](bitsadmin-rawreturn.md)
  - [bitsadmin removeclientcertificate](bitsadmin-removeclientcertificate.md)
  - [bitsadmin removecredentials](bitsadmin-removecredentials.md)
  - [bitsadmin replaceremoteprefix](bitsadmin-replaceremoteprefix.md)
  - [bitsadmin reset](bitsadmin-reset.md)
  - [bitsadmin resume](bitsadmin-resume.md)
  - [bitsadmin setaclflag](bitsadmin-setaclflag.md)
  - [bitsadmin setclientcertificatebyid](bitsadmin-setclientcertificatebyid.md)
  - [bitsadmin setclientcertificatebyname](bitsadmin-setclientcertificatebyname.md)
  - [bitsadmin setcredentials](bitsadmin-setcredentials.md)
  - [bitsadmin setcustomheaders](bitsadmin-setcustomheaders.md)
  - [bitsadmin setdescription](bitsadmin-setdescription.md)
  - [bitsadmin setdisplayname](bitsadmin-setdisplayname.md)
  - [bitsadmin sethelpertoken](bitsadmin-sethelpertoken.md)
  - [bitsadmin sethelpertokenflags](bitsadmin-sethelpertokenflags.md)
  - [bitsadmin sethttpmethod](bitsadmin-sethttpmethod.md)
  - [bitsadmin setmaxdownloadtime](bitsadmin-setmaxdownloadtime.md)
  - [bitsadmin setminretrydelay](bitsadmin-setminretrydelay.md)
  - [bitsadmin setnoprogresstimeout](bitsadmin-setnoprogresstimeout.md)
  - [bitsadmin setnotifycmdline](bitsadmin-setnotifycmdline.md)
  - [bitsadmin setnotifyflags](bitsadmin-setnotifyflags.md)
  - [bitsadmin setpeercachingflags](bitsadmin-setpeercachingflags.md)
  - [bitsadmin setpriority](bitsadmin-setpriority.md)
  - [bitsadmin setproxysettings](bitsadmin-setproxysettings.md)
  - [bitsadmin setreplyfilename](bitsadmin-setreplyfilename.md)
  - [bitsadmin setsecurityflags](bitsadmin-setsecurityflags.md)
  - [bitsadmin setvalidationstate](bitsadmin-setvalidationstate.md)
  - [bitsadmin suspend](bitsadmin-suspend.md)
  - [bitsadmin takeownership](bitsadmin-takeownership.md)
  - [bitsadmin transfer](bitsadmin-transfer.md)
  - [bitsadmin util](bitsadmin-util.md)
    - [bitsadmin util 和 enableanalyticchannel](bitsadmin-util-and-enableanalyticchannel.md)
    - [bitsadmin util 和 getieproxy](bitsadmin-util-and-getieproxy.md)
    - [bitsadmin util 和 help](bitsadmin-util-and-help.md)
    - [bitsadmin util 和 repairservice](bitsadmin-util-and-repairservice.md)
    - [bitsadmin util 和 setieproxy](bitsadmin-util-and-setieproxy.md)
    - [bitsadmin util 和 version](bitsadmin-util-and-version.md)
  - [bitsadmin wrap](bitsadmin-wrap.md)
- [bootcfg](bootcfg.md)
  - [bootcfg addsw](bootcfg-addsw.md)
  - [bootcfg copy](bootcfg-copy.md)
  - [bootcfg dbg1394](bootcfg-dbg1394.md)
  - [bootcfg debug](bootcfg-debug.md)
  - [bootcfg default](bootcfg-default.md)
  - [bootcfg delete](bootcfg-delete.md)
  - [bootcfg ems](bootcfg-ems.md)
  - [bootcfg query](bootcfg-query.md)
  - [bootcfg raw](bootcfg-raw.md)
  - [bootcfg rmsw](bootcfg-rmsw.md)
  - [bootcfg timeout](bootcfg-timeout.md)
- [break](break_1.md)

### <a name="c"></a>C

- [cacls](cacls.md)
- [call](call.md)
- [cd](cd.md)
- [certreq](certreq_1.md)
- [certutil](certutil.md)
- [change](change.md)
  - [change logon](change-logon.md)
  - [change port](change-port.md)
  - [change user](change-user.md)
- [chcp](chcp.md)
- [chdir](chdir.md)
- [chglogon](chglogon.md)
- [chgport](chgport.md)
- [chgusr](chgusr.md)
- [chkdsk](chkdsk.md)
- [chkntfs](chkntfs.md)
- [choice](choice.md)
- [cipher](cipher.md)
- [clean](clean.md)
- [cleanmgr](cleanmgr.md)
- [clip](clip.md)
- [cls](cls.md)
- [cmd](Cmd.md)
- [cmdkey](cmdkey.md)
- [cmstp](cmstp.md)
- [color](color.md)
- [comp](comp.md)
- [compact](compact.md)
- [compact vdisk](compact-vdisk.md)
- [convert](convert.md)
  - convert basic 
  - [convert dynamic](convert-dynamic.md)
  - [convert gpt](convert-gpt.md)
  - [convert mbr](convert-mbr.md)
- [copy](copy.md)
- [cprofile](cprofile.md)
- [create](create.md)
  - [create partition efi](create-partition-efi.md)
  - [创建[分区扩展](create-partition-extended.md)
  - [create partition logical](create-partition-logical.md)
  - [create partition msr](create-partition-msr.md)
  - [创建分区主副本](create-partition-primary.md)
  - [创建卷镜像](create-volume-mirror.md)
  - [create volume raid](create-volume-raid.md)
  - [create volume simple](create-volume-simple.md)
  - [create volume stripe](create-volume-stripe.md)
- [cscript](cscript.md)

### <a name="d"></a>D

- [date](date.md)
- [dcgpofix](dcgpofix.md)
- [defrag](defrag.md)
- [del](del.md)
- [delete](delete.md)
  - [删除磁盘](delete-disk.md)
  - [delete partition](delete-partition.md)
  - [删除阴影](delete-shadows.md)
  - delete volume 
- [分离 vdisk](detach-vdisk.md)
- [仔细](detail.md)
  - [detail disk](detail-disk.md)
  - [detail partition](detail-partition.md)
  - [详细信息 vdisk](detail-vdisk.md)
  - [detail volume](detail-volume.md)
- [dfsdiag](dfsdiag.md)
  - [dfsdiag testdcs](dfsdiag-testdcs.md)
  - [dfsdiag testdfsconfig](dfsdiag-testdfsconfig.md)
  - [dfsdiag testdfsintegrity](dfsdiag-testdfsintegrity.md)
  - [dfsdiag testreferral](dfsdiag-testreferral.md)
  - [dfsdiag testsites](dfsdiag-testsites.md)
- [dfsrmig](dfsrmig.md)
- [diantz](diantz.md)
- [dir](dir.md)
- [diskcomp](diskcomp.md)
- [diskcopy](diskcopy.md)
- [diskpart](diskpart.md)
- [diskperf](diskperf.md)
- [diskraid](diskraid.md)
- [diskshadow](diskshadow.md)
- [dispdiag](dispdiag.md)
- [dnscmd](dnscmd.md)
- [doskey](doskey.md)
- [driverquery](driverquery.md)

### <a name="e"></a>E

- [echo](echo.md)
- [edit](edit.md)
- [endlocal](endlocal.md)
- [结束还原](end-restore.md)
- [erase](erase.md)
- [eventcreate](eventcreate.md)
- [eventquery](eventquery.md)
- [eventtriggers](eventtriggers.md)
- [Evntcmd](evntcmd.md)
- [exec](exec.md)
- [exit](exit_2.md)
- [expand](expand.md)
- [展开 vdisk](expand-vdisk.md)
- [让](expose.md)
- [extend](extend.md)
- [extract](extract.md)

### <a name="f"></a>F

- [fc](fc.md)
- [filesystems](filesystems.md)
- [find](find.md)
- [findstr](findstr.md)
- [finger](finger.md)
- [flattemp](flattemp.md)
- [fondue](fondue.md)
- [for](for.md)
- [forfiles](forfiles.md)
- [format](format.md)
- [freedisk](freedisk.md)
- [fsutil](fsutil.md)
  - [fsutil 8dot3name](fsutil-8dot3name.md)
  - [fsutil behavior](fsutil-behavior.md)
  - [fsutil dirty](fsutil-dirty.md)
  - [fsutil file](fsutil-file.md)
  - [fsutil fsinfo](fsutil-fsinfo.md)
  - [fsutil hardlink](fsutil-hardlink.md)
  - [fsutil objectid](fsutil-objectid.md)
  - [fsutil quota](fsutil-quota.md)
  - [fsutil repair](fsutil-repair.md)
  - [fsutil reparsepoint](fsutil-reparsepoint.md)
  - [fsutil resource](fsutil-resource.md)
  - [fsutil sparse](fsutil-sparse.md)
  - [fsutil tiering](fsutil-tiering.md)
  - [fsutil transaction](fsutil-transaction.md)
  - [fsutil usn](fsutil-usn.md)
  - [fsutil volume](fsutil-volume.md)
  - [fsutil wim](fsutil-wim.md)
- [ftp](ftp.md)
  - [ftp append](ftp-append.md)
  - [ftp ascii](ftp-ascii.md)
  - [ftp bell](ftp-bell_1.md)
  - [ftp binary](ftp-binary.md)
  - [ftp bye](ftp-bye.md)
  - [ftp cd](ftp-cd.md)
  - [ftp close](ftp-close_1.md)
  - [ftp debug](ftp-debug.md)
  - [ftp delete](ftp-delete.md)
  - [ftp dir](ftp-dir.md)
  - [ftp disconnect](ftp-disconnect_1.md)
  - [ftp get](ftp-get.md)
  - [ftp glob](ftp-glob_1.md)
  - [ftp hash](ftp-hash_1.md)
  - [ftp lcd](ftp-lcd.md)
  - [ftp literal](ftp-literal_1.md)
  - [ftp ls](ftp-ls_1.md)
  - [ftp mget](ftp-mget.md)
  - [ftp mkdir](ftp-mkdir.md)
  - [ftp mls](ftp-mls_1.md)
  - [ftp mput](ftp-mput_1.md)
  - [ftp open](ftp-open_1.md)
  - [ftp prompt](ftp-prompt_1.md)
  - [ftp put](ftp-put.md)
  - [ftp pwd](ftp-pwd_1.md)
  - [ftp quit](ftp-quit.md)
  - [ftp quote](ftp-quote.md)
  - [ftp recv](ftp-recv.md)
  - [ftp remotehelp](ftp-remotehelp_1.md)
  - [ftp rename](ftp-rename.md)
  - [ftp rmdir](ftp-rmdir.md)
  - [ftp send](ftp-send_1.md)
  - [ftp status](ftp-status.md)
  - [ftp trace](ftp-trace_1.md)
  - [ftp type](ftp-type.md)
  - [ftp user](ftp-user.md)
  - [ftp verbose](ftp-verbose_1.md)
  - [ftp mdelete](ftp-.mdelete_1.md)
  - [ftp mdir](ftp.mdir.md)
- [ftype](ftype.md)
- [fveupdate](fveupdate.md)

### <a name="g"></a>G

- [getmac](getmac.md)
- [gettype](gettype.md)
- [goto](goto.md)
- [gpfixup](gpfixup.md)
- [gpresult](gpresult.md)
- [gpt](gpt.md)
- [gpupdate](gpupdate.md)
- [graftabl](graftabl.md)

### <a name="h"></a>H

- [help](help.md)
- [helpctr](helpctr.md)
- [hostname](hostname.md)

### <a name="i"></a>I

- [icacls](icacls.md)
- [if](if.md)
- [导入（shadowdisk）](import.md)
- [导入（diskpart）](import_1.md)
- [inactive](inactive.md)
- [inuse](inuse.md)
- [ipconfig](ipconfig.md)
- [ipxroute](ipxroute.md)
- [irftp](irftp.md)

### <a name="j"></a>J

- [jetpack](jetpack.md)

### <a name="k"></a>K

- [klist](klist.md)
- [ksetup](ksetup.md)
  - [ksetup addenctypeattr](ksetup-addenctypeattr.md)
  - [ksetup addhosttorealmmap](ksetup-addhosttorealmmap.md)
  - [ksetup addkdc](ksetup-addkdc.md)
  - [ksetup addkpasswd](ksetup-addkpasswd.md)
  - [ksetup addrealmflags](ksetup-addrealmflags.md)
  - [ksetup changepassword](ksetup-changepassword.md)
  - [ksetup delenctypeattr](ksetup-delenctypeattr.md)
  - [ksetup delhosttorealmmap](ksetup-delhosttorealmmap.md)
  - [ksetup delkdc](ksetup-delkdc.md)
  - [ksetup delkpasswd](ksetup-delkpasswd.md)
  - [ksetup delrealmflags](ksetup-delrealmflags.md)
  - [ksetup domain](ksetup-domain.md)
  - [ksetup dumpstate](ksetup-dumpstate.md)
  - [ksetup getenctypeattr](ksetup-getenctypeattr.md)
  - [ksetup listrealmflags](ksetup-listrealmflags.md)
  - [ksetup mapuser](ksetup-mapuser.md)
  - [ksetup removerealm](ksetup-removerealm.md)
  - [ksetup server](ksetup-server.md)
  - [ksetup setcomputerpassword](ksetup-setcomputerpassword.md)
  - [ksetup setenctypeattr](ksetup-setenctypeattr.md)
  - [ksetup setrealm](ksetup-setrealm.md)
  - [ksetup setrealmflags](ksetup-setrealmflags.md)
- [ktmutil](ktmutil.md)
- [ktpass](ktpass.md)

### <a name="l"></a>L

- [label](label.md)
- [list](list.md)
  - [列出提供程序](list-providers.md)
  - [列表阴影](list-shadows.md)
  - [列出写入者](list-writers.md)
- [加载元数据](load-metadata.md)
- [lodctr](lodctr.md)
- [logman](logman.md)
  - [logman create](logman-create.md)
  - [logman 创建警报](logman-create-alert.md)
  - [logman 创建 api](logman-create-api.md)
  - [logman 创建 cfg](logman-create-cfg.md)
  - [logman create 计数器](logman-create-counter.md)
  - [logman 创建跟踪](logman-create-trace.md)
  - [logman delete](logman-delete.md)
  - [logman 导入和 logman 导出](logman-import-export.md)
  - [logman query](logman-query.md)
  - [logman 启动和 logman 停止](logman-start-stop.md)
  - [logman update](logman-update.md)
  - [logman 更新警报](logman-update-alert.md)
  - [logman 更新 api](logman-update-api.md)
  - [logman 更新 cfg](logman-update-cfg.md)
  - [logman 更新计数器](logman-update-counter.md)
  - [logman 更新跟踪](logman-update-trace.md)
- [logoff](logoff.md)
- [lpq](lpq.md)
- [lpr](lpr.md)

### <a name="m"></a>M

- [macfile](macfile.md)
- [makecab](makecab.md)
- [管理 manage-bde](manage-bde.md)
  - [管理 manage-bde 状态](manage-bde-status.md)
  - [管理](manage-bde-on.md)
  - [管理 manage-bde 关闭](manage-bde-off.md)
  - [管理 manage-bde 暂停](manage-bde-pause.md)
  - [管理 manage-bde 恢复](manage-bde-resume.md)
  - [管理 manage-bde 锁](manage-bde-lock.md)
  - [管理 manage-bde 解锁](manage-bde-unlock.md)
  - [管理 autounlock](manage-bde-autounlock.md)
  - [管理 manage-bde 保护程序](manage-bde-protectors.md)
  - [管理 manage-bde tpm](manage-bde-tpm.md)
  - [管理 setidentifier](manage-bde-setidentifier.md)
  - [管理 forcerecovery](manage-bde-forcerecovery.md)
  - [管理 manage-bde changepassword](manage-bde-changepassword.md)
  - [管理 changepin](manage-bde-changepin.md)
  - [管理 changekey](manage-bde-changekey.md)
  - [管理 ms-fve-keypackage](manage-bde-keypackage.md)
  - [管理 manage-bde 升级](manage-bde-upgrade.md)
  - [管理 wipefreespace](manage-bde-wipefreespace.md)
- [mapadmin](mapadmin.md)
- [md](md.md)
- [merge vdisk](merge-vdisk.md)
- [mkdir](mkdir.md)
- [mklink](mklink.md)
- [mmc](mmc.md)
- [mode](mode.md)
- [more](more.md)
- [mount](mount.md)
- [mountvol](mountvol.md)
- [move](move.md)
- [mqbkup](mqbkup.md)
- [mqsvc](mqsvc.md)
- [mqtgsvc](mqtgsvc.md)
- [msdt](msdt.md)
- [msg](msg.md)
- [msiexec](msiexec.md)
- [msinfo32](msinfo32.md)
- [mstsc](mstsc.md)

### <a name="n"></a>N

- [nbtstat](nbtstat.md)
- [netcfg](netcfg.md)
- [净打印](net-print.md)
- [netsh](netsh.md)
- [netstat](netstat.md)
- [nfsadmin](nfsadmin.md)
- [nfsshare](nfsshare.md)
- [nfsstat](nfsstat.md)
- [nlbmgr](nlbmgr.md)
- [nslookup](nslookup.md)
  - [nslookup exit 命令](nslookup-exit-command.md)
  - [nslookup finger 命令](nslookup-finger-command.md)
  - [nslookup help](nslookup-help.md)
  - [nslookup ls](nslookup-ls.md)
  - [nslookup lserver](nslookup-lserver.md)
  - [nslookup root](nslookup-root.md)
  - [nslookup server](nslookup-server.md)
  - [nslookup set](nslookup-set.md)
  - [nslookup set all](nslookup-set-all.md)
  - [nslookup set class](nslookup-set-class.md)
  - [nslookup set d2](nslookup-set-d2.md)
  - [nslookup set debug](nslookup-set-debug.md)
  - [nslookup set domain](nslookup-set-domain.md)
  - [nslookup set port](nslookup-set-port.md)
  - [nslookup set querytype](nslookup-set-querytype.md)
  - [nslookup set recurse](nslookup-set-recurse.md)
  - [nslookup set retry](nslookup-set-retry.md)
  - [nslookup set root](nslookup-set-root.md)
  - [nslookup set search](nslookup-set-search.md)
  - [nslookup set srchlist](nslookup-set-srchlist.md)
  - [nslookup set timeout](nslookup-set-timeout.md)
  - [nslookup set type](nslookup-set-type.md)
  - [nslookup set vc](nslookup-set-vc.md)
  - [nslookup view](nslookup-view.md)
- [ntbackup](ntbackup.md)
- [ntcmdprompt](ntcmdprompt.md)
- [ntfrsutl](ntfrsutl.md)

### <a name="o"></a>O

- [断开](offline.md)
  - [脱机磁盘](offline-disk.md)
  - [脱机卷](offline-volume.md)
- [联机](online.md)
  - [联机磁盘](online-disk.md)
  - [联机卷](online-volume.md)
- [openfiles](openfiles.md)

### <a name="p"></a>P

- [pagefileconfig](pagefileconfig.md)
- [path](path.md)
- [pathping](pathping.md)
- [pause](pause.md)
- [pbadmin](pbadmin.md)
- [pentnt](pentnt.md)
- [perfmon](perfmon.md)
- [ping](ping.md)
- [pnpunattend](pnpunattend.md)
- [pnputil](pnputil.md)
- [popd](popd.md)
- [powershell](powershell.md)
- [powershell ise](powershell_ise.md)
- [print](print.md)
- [prncnfg](prncnfg.md)
- [prndrvr](prndrvr.md)
- [prnjobs](prnjobs.md)
- [prnmngr](prnmngr.md)
- [prnport](prnport.md)
- [prnqctl](prnqctl.md)
- [prompt](prompt.md)
- [pubprn](pubprn.md)
- [pushd](pushd.md)
- [pushprinterconnections](pushprinterconnections.md)
- [pwlauncher](pwlauncher.md)

### <a name="q"></a>Q

- [qappsrv](qappsrv.md)
- [qprocess](qprocess.md)
- [查询](query.md)
  - [查询进程](query-process.md)
  - [query session](query-session.md)
  - [查询 termserver](query-termserver.md)
  - [query user](query-user.md)
- [quser](quser.md)
- [qwinsta](qwinsta.md)

### <a name="r"></a>R

- [rcp](rcp.md)
- [rd](rd.md)
- [rdpsign](rdpsign.md)
- [recover](recover.md)
- [恢复磁盘组](recover_1.md)
- [reg](reg.md)
  - [reg 添加](reg-add.md)
  - [注册表比较](reg-compare.md)
  - [注册副本](reg-copy.md)
  - [注册删除](reg-delete.md)
  - [reg export](reg-export.md)
  - [注册导入](reg-import.md)
  - [reg 负载](reg-load.md)
  - [reg 查询](reg-query.md)
  - [reg restore](reg-restore.md)
  - [注册保存](reg-save.md)
  - [注册卸载](reg-unload.md)
- [regini](regini.md)
- [regsvr32](regsvr32.md)
- [relog](relog.md)
- [rem 批处理文件](rem.md)
- [rem 脚本](rem_1.md)
- [删除](remove.md)
- [ren](ren.md)
- [rename](rename.md)
- [修复](repair.md)
  - [repair](repair-bde.md)
- [replace](replace.md)
- [扫描](rescan.md)
- [reset](reset.md)
  - [reset session](reset-session.md)
- [变化](retain.md)
- [回到](revert.md)
- [rexec](rexec.md)
- [risetup](risetup.md)
- [rmdir](rmdir.md)
- [robocopy](robocopy.md)
- [路由 ws2008](route_ws2008.md)
- [rpcinfo](rpcinfo.md)
- [rpcping](rpcping.md)
- [rsh](rsh.md)
- [rundll32](rundll32.md)
- [rundll32.exe printui.dll](rundll32-printui.md)
- [rwinsta](rwinsta.md)

### <a name="s"></a>S

- [北京](san.md)
- [sc config](sc-config.md)
- [sc create](sc-create.md)
- [sc delete](sc-delete.md)
- [sc query](sc-query.md)
- [schtasks](schtasks.md)
- [scwcmd](scwcmd.md)
  - [scwcmd 分析](scwcmd-analyze.md)
  - [scwcmd 配置](scwcmd-configure.md)
  - [scwcmd 注册](scwcmd-register.md)
  - [scwcmd 回滚](scwcmd-rollback.md)
  - [scwcmd 转换](scwcmd-transform.md)
  - [scwcmd 视图](scwcmd-view.md)
- [secedit](secedit.md)
  - [secedit 分析](secedit-analyze.md)
  - [secedit 配置](secedit-configure.md)
  - [secedit 导出](secedit-export.md)
  - [secedit generaterollback](secedit-generaterollback.md)
  - [secedit 导入](secedit-import.md)
  - [secedit 验证](secedit-validate.md)
- [select](select.md)
  - [select disk](select-disk.md)
  - [select partition](select-partition.md)
  - [选择 vdisk](select-vdisk.md)
  - [select volume](select-volume.md)
- [serverceipoptin](serverceipoptin.md)
- [servermanagercmd.exe](servermanagercmd.md)
- [serverweroptin](serverweroptin.md)
- [设置环境变量](set_1.md)
- [设置卷影副本](set_2.md)
  - [设置上下文](set-context.md)
  - [设置 id](set-id.md)
  - [setlocal](setlocal.md)
  - [设置元数据](set-metadata.md)
  - [set 选项](set-option.md)
  - [设置详细](set-verbose.md)
- [setx](setx.md)
- [sfc](sfc.md)
- [shadow](shadow.md)
- [shift](shift.md)
- [showmount](showmount.md)
- [shrink](shrink.md)
- [shutdown](shutdown.md)
- [模拟还原](simulate-restore.md)
- [sort](sort.md)
- [start](start.md)
- [子命令集设备](subcommand-set-device.md)
- [子命令集 drivergroup](subcommand-set-drivergroup.md)
- [子命令集 drivergroupfilter](subcommand-set-drivergroupfilter.md)
- [子命令集 driverpackage](subcommand-set-driverpackage.md)
- [子命令集图像](subcommand-set-image.md)
- [子命令集 imagegroup](subcommand-set-imagegroup.md)
- [子命令集服务器](subcommand-set-server.md)
- [子命令集 transportserver](subcommand-set-transportserver.md)
- [子命令集 multicasttransmission](subcommand-start-multicasttransmission.md)
- [子命令开始命名空间](subcommand-start-namespace.md)
- [子命令启动服务器](subcommand-start-server.md)
- [子命令开始 transportserver](subcommand-start-transportserver.md)
- [子命令停止服务器](subcommand-stop-server.md)
- [子命令停止 transportserver](subcommand-stop-transportserver.md)
- [subst](subst.md)
- [sxstrace](sxstrace.md)
- [sysocmgr](sysocmgr.md)
- [systeminfo](systeminfo.md)


### <a name="t"></a>T

- [takeown](takeown.md)
- [tapicfg](tapicfg.md)
- [taskkill](taskkill.md)
- [tasklist](tasklist.md)
- [tcmsetup](tcmsetup.md)
- [telnet](telnet.md)
  - [telnet 关闭](telnet-close.md)
  - [telnet 显示](telnet-display.md)
  - [telnet 打开](telnet-open.md)
  - [telnet 退出](telnet-quit.md)
  - [telnet 发送](telnet-send.md)
  - [telnet 集](telnet-set.md)
  - [telnet 状态](telnet-status.md)
  - [未设置 telnet](telnet-unset.md)
- [tftp](tftp.md)
- [time](time.md)
- [timeout](timeout_1.md)
- [title](title_1.md)
- [tlntadmn](tlntadmn.md)
- [tpmtool](tpmtool.md)
- [tpmvscmgr](tpmvscmgr.md)
- [tracerpt](tracerpt_1.md)
- [tracert](tracert.md)
- [tree](tree.md)
- [tscon](tscon.md)
- [tsdiscon](tsdiscon.md)
- [tsecimp](tsecimp_1.md)
- [tskill](tskill.md)
- [tsprof](tsprof.md)
- [type](type.md)
- [typeperf](typeperf.md)
- [tzutil](tzutil.md)

### <a name="u"></a>U

- [隐藏](unexpose.md)
- [uniqueid](uniqueid.md)
- [unlodctr](unlodctr_1.md)

### <a name="v"></a>V

- [ver](ver.md)
- [verifier](verifier.md)
- [verify](verify_1.md)
- [vol](vol.md)
- [vssadmin](vssadmin.md)
  - [vssadmin delete shadows](vssadmin-delete-shadows.md)
  - [vssadmin list shadows](vssadmin-list-shadows.md)
  - [vssadmin list writers](vssadmin-list-writers.md)
  - [vssadmin resize shadowstorage](vssadmin-resize-shadowstorage.md)

### <a name="w"></a>W

- [waitfor](waitfor.md)
- [wbadmin](wbadmin.md)
  - [wbadmin 删除目录](wbadmin-delete-catalog.md)
  - [wbadmin delete systemstatebackup](wbadmin-delete-systemstatebackup.md)
  - [wbadmin 禁用备份](wbadmin-disable-backup.md)
  - [wbadmin 启用备份](wbadmin-enable-backup.md)
  - [wbadmin 获取磁盘](wbadmin-get-disks.md)
  - [wbadmin 获取项](wbadmin-get-items.md)
  - [wbadmin 获取状态](wbadmin-get-status.md)
  - [wbadmin get 版本](wbadmin-get-versions.md)
  - [wbadmin restore catalog](wbadmin-restore-catalog.md)
  - [wbadmin 开始备份](wbadmin-start-backup.md)
  - [wbadmin 开始恢复](wbadmin-start-recovery.md)
  - [wbadmin start sysrecovery](wbadmin-start-sysrecovery.md)
  - [wbadmin start systemstatebackup](wbadmin-start-systemstatebackup.md)
  - [wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery.md)
  - [wbadmin 停止作业](wbadmin-stop-job.md)
- [wdsutil](wdsutil.md)
- [wecutil](wecutil.md)
- [wevtutil](wevtutil.md)
- [where](where_1.md)
- [whoami](whoami.md)
- [winnt](winnt.md)
- [winnt32](winnt32.md)
- [winpop](winpop.md)
- [winrs](winrs.md)
- [winsat mem](winsat-mem.md)
- [winsat mfmedia](winsat-mfmedia.md)
- [wmic](wmic.md)
- [编写器](writer.md)
- [wscript](wscript.md)

### <a name="x"></a>X

- [xcopy](xcopy.md)
