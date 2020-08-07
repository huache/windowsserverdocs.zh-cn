---
ms.assetid: cd4d4902-dcdf-49dd-8059-82a56bf4b585
title: 导出服务器身份验证证书的私钥部分
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: dcc6332881fa4ff0143604eebb491f8ed48283c2
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87972214"
---
# <a name="export-the-private-key-portion-of-a-server-authentication-certificate"></a>导出服务器身份验证证书的私钥部分

Active Directory 联合身份验证服务 AD FS 场中的每个联合服务器都 \( \) 必须有权访问服务器身份验证证书的私钥。 如果要实现联合服务器或 Web 服务器的服务器场，则必须具有单个身份验证证书。 必须由企业证书颁发机构 CA 颁发此证书 \( \) ，并且该证书必须具有可导出的私钥。 服务器身份验证证书的私钥必须可导出，以便使其可用于该服务器场中的所有服务器。

对于服务器场中的所有联合服务器代理必须共享相同服务器身份验证证书的私钥部分，这是联合服务器代理场的相同概念。

> [!NOTE]
> "AD FS 管理" 管理单元 \- 是指作为服务通信证书的联合服务器的服务器身份验证证书。

根据此计算机将扮演的角色，在使用私钥安装了服务器身份验证证书的联合服务器计算机或联合服务器代理计算机上使用此过程。 当完成该过程时，就可以在服务器场中的每个服务器的默认网站上导入此证书。 有关详细信息，请参阅将[服务器身份验证证书导入到默认](Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)网站。

若要完成此过程，至少需要是本地计算机上的**管理员**组或等效组中的成员。  查看有关使用适当帐户和[本地和域默认组](https://go.microsoft.com/fwlink/?LinkId=83477)中组成员身份的详细信息。

### <a name="to-export-the-private-key-portion-of-a-server-authentication-certificate"></a>导出服务器身份验证证书的私钥部分

1. 在 "**开始**" 屏幕上，键入 "**Internet Information Services \( IIS \) 管理器**"，然后按 enter。

2. 在控制台树中单击 **“ComputerName”**。

3. 在中心窗格中，双击 \- "**服务器证书**"。

4. 在中心窗格中，右键 \- 单击要导出的证书，然后单击 "**导出**"。

5. 在 "**导出证书**" 对话框中，单击 " **...** " 按钮。

6. 在 **"文件名"** 中，键入**C： \\ **<em>NameofCertificate</em>，然后单击 "**打开**"。

7. 键入证书的密码、进行确认，然后单击“确定”****。

8. 通过确认指定的文件创建在指定的位置上来验证导出成功。

   > [!IMPORTANT]
   > 必须将该文件传输到物理媒体，并在传输到新服务器的过程中保护其安全，以便可以将此证书导入到新服务器上的本地证书存储中。 保护私钥的安全非常重要。 如果此密钥泄露，则整个 AD FS 部署的安全性 \( （包括你的组织中的资源和资源伙伴组织中的资源） \) 将受到威胁。

9. 请在安装联合身份验证服务之前，将已导出的服务器身份验证证书导入到新的服务器上的证书存储区。 有关如何导入证书的信息，请参阅导入服务器证书 \( [http： \/ \/ go.microsoft.com \/ fwlink \/ ？LinkId \= 108283](https://go.microsoft.com/fwlink/?LinkId=108283) \) 。

## <a name="additional-references"></a>其他参考
[清单：设置联合服务器](Checklist--Setting-Up-a-Federation-Server.md)

[清单：设置联合服务器代理](Checklist--Setting-Up-a-Federation-Server-Proxy.md)

[联合服务器的证书要求](../design/certificate-requirements-for-federation-servers.md)

[联合服务器代理的证书要求](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807054(v=ws.11))

