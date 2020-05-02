---
ms.assetid: f2eefaaf-2817-4ac7-abac-d2b65fa971dc
title: Fsutil transaction
ms.prod: windows-server
manager: dmoss
ms.author: toklima
author: toklima
ms.technology: storage
audience: IT Pro
ms.topic: article
ms.date: 10/16/2017
ms.openlocfilehash: 18088bcedd077d5c8052bca91c648e2719304a78
ms.sourcegitcommit: ab64dc83fca28039416c26226815502d0193500c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/01/2020
ms.locfileid: "82720095"
---
# <a name="fsutil-transaction"></a>Fsutil transaction
> 适用于： Windows Server （半年频道），Windows Server 2019，Windows Server 2016，Windows 10，Windows Server 2012 R2，Windows 8.1，Windows Server 2012，Windows 8，Windows Server 2008 R2，Windows 7，Windows 2008，Windows Vista

管理 NTFS 事务。



## <a name="syntax"></a>语法

```
fsutil transaction [commit] <GUID>
fsutil transaction [fileinfo] <Filename>
fsutil transaction [list]
fsutil transaction [query] [{Files|All}] <GUID>
fsutil transaction [rollback] <GUID>
```

#### <a name="parameters"></a>参数

| 参数  |                                                                                                                                                     描述                                                                                                                                                     |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   提交 (commit)   |                                                                                                                      标记成功的隐式或显式指定的事务的结束。                                                                                                                      |
|   <GUID>   |                                                                                                                               指定表示事务的 GUID 值。                                                                                                                               |
|  fileinfo  |                                                                                                                              显示指定文件的事务信息。                                                                                                                               |
| <Filename> |                                                                                                                                         指定完整路径和文件名。                                                                                                                                          |
|    list    |                                                                                                                                 显示当前正在运行的事务的列表。                                                                                                                                  |
|   query    | 显示指定事务的信息。<p>-如果指定了**fsutil transaction Query Files** ，将仅为指定的事务显示文件信息。<br />-如果指定了**fsutil transaction Query all** ，则将显示该事务的所有信息。 |
|  回滚  |                                                                                                                                将指定的事务回滚到开始处。                                                                                                                                 |

### <a name="remarks"></a>备注

-   Windows Server 2008 中引入了事务性 NTFS。

### <a name="examples"></a><a name="BKMK_examples"></a>示例
若要显示文件 c:\test.txt 的事务信息，请键入：

```
fsutil transaction fileinfo c:\test.txt  
```

### <a name="additional-references"></a>其他参考
- [命令行语法项](command-line-syntax-key.md)

[Fsutil](Fsutil.md)

[事务性 NTFS](https://go.microsoft.com/fwlink/?LinkID=165402)


