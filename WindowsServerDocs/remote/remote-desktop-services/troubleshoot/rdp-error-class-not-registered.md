---
title: 客户端无法连接，收到“没有注册类”错误
description: 排查远程桌面连接出现的“没有注册类”错误。
audience: itpro
ms.custom: na
ms.reviewer: rklemen
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: troubleshooting
ms.assetid: ''
author: kaushika-msft
manager: dcscontentpm
ms.author: delhan
ms.date: 07/24/2019
ms.localizationpriority: medium
ms.openlocfilehash: 7a98e894f3eaf47e257ab39c640e93101fd76fc8
ms.sourcegitcommit: c5709021aa98abd075d7a8f912d4fd2263db8803
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/18/2020
ms.locfileid: "76265899"
---
# <a name="clients-cant-connect-and-get-the-class-not-registered-error"></a>客户端无法连接，收到“没有注册类”错误

尝试使用运行 Windows 10 版本 1709 或更高版本的客户端连接到远程计算机时，该客户端无法连接，同时，远程桌面会话主机服务器报告一条包含“没有注册类(0x80040154)”错误代码的消息。

如果尝试建立连接的用户必须要提供某个用户配置文件，则会发生此问题。 若要解决此问题，请安装 [2018 年 7 月 24 日 — KB4338817（OS 内部版本 16299.579）](https://support.microsoft.com/help/4338817/windows-10-update-kb4338817)Windows 10 更新。
