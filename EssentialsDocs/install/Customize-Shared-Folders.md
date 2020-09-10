---
title: 自定义共享文件夹
description: 描述如何使用 Windows Server Essentials
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 47bc4986-14eb-4a29-9930-83a25704a3a0
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: c1a6276199964ac7fd2eb3953cb3fac828063dfc
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623677"
---
# <a name="customize-shared-folders"></a>自定义共享文件夹

>适用于： Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

默认情况下，会在磁盘 0 上的最大数据分区中创建服务器文件夹。 合作伙伴可以使用以下步骤来自定义位置并指定其他服务器文件夹：

1. 在使用 Sysprep 之前，使用自定义分区配置创建出厂映像，然后创建新的 Storage 注册表项。 在初始配置 (IC) 过程中，存储 IC 任务会检查此注册表项。 如果此注册表项存在，则会在 C:\ServerFolders 目录中创建默认服务器文件夹。

   #### <a name="to-create-a-new-storage-registry-key"></a>创建新的 Storage 注册表项

   1.  在服务器上，将鼠标移动到屏幕右上角，然后单击 **“搜索”**。

   2.  在搜索框中，键入 **“regedit”**，然后单击 **“Regedit”** 应用程序。

   3.  在导航窗格中，依次展开 **“HKEY_LOCAL_MACHINE”**、**“SOFTWARE”** 和 **“Microsoft”**。

   4.  右键单击 **“Windows Server”**，单击 **“新建”**，然后单击 **“项”**。

   5.  将该项命名为 **Storage**。

   6.  在导航窗格中，右键单击新的 Storage 注册表项，单击 **“新建”**，然后单击 **“DWORD（32 位）值”**。

   7.  将该字符串命名为 **CreateFoldersOnSystem**。

   8.  右键单击 **“CreateFoldersOnSystem”**，然后单击 **“修改”**。 此时将显示 **“编辑字符串”** 对话框。

   9. 将此新项的值设置为 **1**，然后单击 **“确定”**。

2. 使用 PostIC.cmd 脚本将文件夹移至其他位置或创建其他文件夹。 请参阅以下示例：[示例 1：使用 Windows PowerShell 从 PostIC.cmd 创建自定义文件夹并将默认文件夹移至新位置](Customize-Shared-Folders.md#BKMK_Example1)。

3. 使用 Windows Server 解决方案 SDK 将文件夹移至其他位置或创建其他文件夹。 请参阅以下示例：[示例 2：使用 Windows Server 解决方案 SDK 创建自定义文件夹并移动现有文件夹](Customize-Shared-Folders.md#BKMK_Example2)。

   或者，合作伙伴可以将数据文件夹留在驱动器 C 中。这样可以由最终用户或经销商决定数据驱动器上的数据文件夹的布局。

###  <a name="example-1-create-a-custom-folder-and-move-the-default-folders-to-a-new-location-from-posticcmd-by-using-windows-powershell"></a><a name="BKMK_Example1"></a> 示例1：使用 Windows PowerShell 创建自定义文件夹并将默认文件夹从 Postic.cmd 移动到新位置

1.  创建用于运行后初始配置任务的 PostIC.cmd 文件，[创建用于运行后初始配置任务的 PostIC.cmd 文件](Create-the-PostIC.cmd-File-for-Running-Post-Initial-Configuration-Tasks.md)部分有详细描述。

2.  使用记事本在 C:\Windows\Setup\Scripts 文件夹中创建一个名为 **customizefolders.ps1** 的文件，然后将以下 Windows PowerShell &reg; 命令粘贴到该文件 (根据所需的行为) ，将以下 Windows PowerShell 命令粘贴到相应的行中。

    ```
    # Move the Documents folder to D:\ServerFolders
    #Get-WssFolder -name Documents| Move-WssFolder - NewDrive D:\ -Force

    # Check for last error. If last error is not null, exit with return code 1
    #If ($error[0] -ne $null) { exit 1}

    # Move all folders to D:\ServerFolders
    #foreach( $folder in Get-WssFolder )
    #{
    #    Move-WssFolder $folder -NewDrive D:\ -Force
    #}

    # Check for last error. If last error is not null, exit with return code 1
    #If ($error[0] -ne $null) { exit 1}

    # Create a custom folder named Custom Folder
    #Add-WssFolder -Name CustomFolder -Path D:\ServerFolders\CustomFolder -Description "Custom Folder"

    # Check for last error. If last error is not null, exit with return code 1
    #If ($error[0] -ne $null) { exit 1}

    exit 0
    ```

3.  向 PostIC.cmd 文件添加以下行，以运行该脚本。

    ```
    REM Lower the execution policy
    "%programfiles%\Windows Server\bin\WssPowershell.exe" "Set-ExecutionPolicy RemoteSigned"

    REM Execute the folder customization script
    "%programfiles%\Windows Server\bin\WssPowershell.exe" -NoProfile -Noninteractive -command ". %windir%\setup\scripts\customizefolders.ps1;exit $LASTEXITCODE"
    Set error_level=%ERRORLEVEL%

    REM Restore the execution policy to default
    "%programfiles%\Windows Server\bin\WssPowershell.exe" "Set-ExecutionPolicy Restricted"
    Set ERRORLEVEL=%error_level%
    ```

###  <a name="example-2-create-a-custom-folder-and-move-an-existing-folder-by-using-the-windows-server-solutions-sdk"></a><a name="BKMK_Example2"></a> 示例2：使用 Windows Server 解决方案 SDK 创建自定义文件夹并移动现有文件夹
 你所创建的代码可以编译为可执行文件，然后从 PostIC.cmd 文件或直接从安装的加载项进行调用。

```
static void Main(string[] args)
{
 StorageManager storageManager = new StorageManager();
 //Connect to the StorageManager
 storageManager.Connect();

 //Move the Documents folder to D:\ServerFolders
 Folder targetFolder = storageManager.Folders.First(folder => folder.Name == "Documents");

 MoveFolderRequest moveRequest = targetFolder.GetMoveRequest(@"D:\");
 moveRequest.MoveFolder();

 //Verify operation was successful, if so print result
 if (moveRequest.Status == OperationStatus.Succeeded)
 {
  Console.WriteLine("Folder {0} now located at {1}", targetFolder.Name, targetFolder.Path);
 }

 string newFolderName = "New Custom Folder";
 string newFolderLocation = @"C:\ServerFolders\New Custom Folder";

 //Create add request based with specific name and location
 CreateFolderRequest request = storageManager.GetCreateFolderRequest(newFolderName, newFolderLocation);

 //Give Guest user read only permission to folder
 request.PermissionsByName.Add(new NamePermission("Guest", Permission.ReadOnly));

 //Create the new folders
 request.CreateFolder();

 //Verify operation was successful, if so print result
 if( request.Status == OperationStatus.Succeeded)
 {
  Folder newFolder = storageManager.Folders.First(folder => folder.Path == newFolderLocation);

  Console.WriteLine("Folder {0} created at {1}", newFolder.Name, newFolder.Path);
 }
}
```

## <a name="see-also"></a>另请参阅
 [创建和自定义映像](Creating-and-Customizing-the-Image.md)[其他自定义](Additional-Customizations.md)[准备映像以进行部署](Preparing-the-Image-for-Deployment.md)[测试客户体验](Testing-the-Customer-Experience.md)
