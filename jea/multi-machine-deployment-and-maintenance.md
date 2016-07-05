---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "多電腦部署和維護"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 784806197a64eb30af1ecea4af55575434ce7b87

---

# 多電腦部署和維護
此時，您已多次將 JEA 部署到本機系統。
因為您的生產環境可能是由多部電腦所組成，所以請務必逐步執行部署處理程序中必須在每部電腦上重複的重要步驟。

## 高階步驟︰
1.  將您的模組 (及角色功能) 複製到每個節點。
2.  將您的工作階段設定檔複製到每個節點。
3.  使用您的工作階段設定執行 `Register-PSSessionConfiguration`。
4.  將一份工作階段設定和工具組複本保留在安全的位置。
當您修改時，最好有一個「單一信任來源」。

## 範例指令碼
以下是部署的範例指令碼。
若要在您的環境中使用，您必須使用實際檔案共用和模組的名稱/路徑。
```PowerShell
# First, copy the session configuration and modules (containing role capability files) onto a file share you have access to.
Copy-Item -Path 'C:\Demo\Demo.pssc' -Destination '\\FileShare\JEA\Demo.pssc'
Copy-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\SomeModule\' -Recurse -Destination '\\FileShare\JEA\SomeModule'

# Next, author a setup script (C:\JEA\Deploy.ps1) to run on each individual node
    # Contents of C:\JEA\Deploy.ps1
    New-Item -ItemType Directory -Path C:\JEADeploy
    Copy-Item -Path '\\FileShare\JEA\Demo.pssc' -Destination 'C:\JEADeploy\'
    Copy-Item -Path '\\FileShare\JEA\SomeModule' -Recurse -Destination 'C:\Program Files\WindowsPowerShell\Modules' # Remember, Role Capability Files are found in modules
    if (Get-PSSessionConfiguration -Name JEADemo -ErrorAction SilentlyContinue)
    {
        Unregister-PSSessionConfiguration -Name JEADemo -ErrorAction Stop
    }

    Register-PSSessionConfiguration -Name JEADemo -Path 'C:\JEADeploy\Demo.pssc'
    Remove-Item -Path 'C:\JEADeploy' # Don't forget to clean up!

# Now, invoke the script on all of the target machines.
# Note: this requires PowerShell Remoting be enabled on each machine. Enabling PowerShell remoting is a requirement to use JEA as well.
# You may need to provide the "-Credential" parameter if your current user account does not have admin permissions on these machines.
Invoke-Command –ComputerName 'Node1', 'Node2', 'Node3', 'NodeN' -FilePath 'C:\JEA\Deploy.ps1'

# Finally, delete the session configuration and role capability files from the file share.
Remove-Item -Path '\\FileShare\JEA\Demo.pssc'
Remove-Item -Path '\\FileShare\JEA\SomeModule' -Recurse
```
## 修改功能
當處理多部電腦時，請務必以一致的方式公開修改。
一旦 JEA 擁有 DSC 資源，這將有助於確保您的環境保持同步。
在這之前，強烈建議您保留工作階段設定的主要複本，並在每次修改時重新部署。

## 移除功能
若要從您的系統中移除 JEA 設定，請在每部電腦上使用下列命令︰
```PowerShell
Unregister-PSSessionConfiguration -Name JEADemo
```




<!--HONumber=Jun16_HO4-->


