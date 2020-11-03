---
description: 提供 PowerShell Desired State Configuration (DSC) 功能的簡介。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_desiredstateconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_DesiredStateConfiguration
ms.openlocfilehash: 2f043104c67078b98355b3e54171a8993e534837
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "93208731"
---
# <a name="about_desiredstateconfiguration"></a>about_DesiredStateConfiguration

## <a name="short-description"></a>簡短描述

提供 PowerShell Desired State Configuration (DSC) 功能的簡介。

## <a name="long-description"></a>詳細描述

DSC 是 PowerShell 中的管理平臺，可讓您部署和管理軟體服務的設定資料，以及管理這些服務執行所在的環境。

DSC 提供一組 PowerShell 語言擴充功能、新的 Cmdlet 和資源，您可以用來以宣告方式指定要如何設定軟體環境的狀態。 它也提供方法來維護和管理現有的設定。

DSC 是在 PowerShell 4.0 中引進。

如需 DSC 的詳細資訊，請參閱 TechNet Library 中的 [PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/overview) 。

## <a name="developing-dsc-resources-with-classes"></a>使用類別開發 DSC 資源

從 PowerShell 5.0 開始，您可以使用類別來開發 DSC 資源。
如需詳細資訊，請參閱 Microsoft TechNet 上的 [about_Classes](about_Classes.md)，以及 [使用 PowerShell 類別撰寫自訂 DSC 資源](/previous-versions//dn948461(v=technet.10)) 。

## <a name="using-dsc"></a>使用 DSC

若要使用 DSC 來設定您的環境，請先使用設定關鍵字來定義 PowerShell 腳本區塊，後面接著識別碼，後面接著成對的大括弧來分隔區塊。 在設定區塊內，您可以定義節點區塊，以指定環境中 (電腦) 的每個節點所需的設定狀態。 節點區塊會以 Node 關鍵字開頭，後面接著目的電腦的名稱（可以是變數）。 在電腦名稱稱之後，以大括弧分隔節點區塊。 在節點區塊內，您可以定義用來設定特定資源的資源區塊。 資源區塊會以資源的類型名稱為開頭，後面接著您想要為該區塊指定的識別碼，後面接著用來分隔區塊的大括弧，如下列範例所示。

```powershell
Configuration MyWebConfig {
    # Parameters are optional
    param ($MachineName, $WebsiteFilePath)
    # A Configuration block can have one or more Node blocks
    Node $MachineName
    {
        # Next, specify one or more resource blocks
        # WindowsFeature is one of the resources you can use in a Node block
        # This example ensures the Web Server (IIS) role is installed
        WindowsFeature IIS
        {
            # To ensure that the role is not installed, set Ensure to "Absent"
            Ensure = "Present"
            Name = "Web-Server" # Use the Name property from Get-WindowsFeature
        }

        # You can use the File resource to create files and folders
        # "WebDirectory" is the name you want to use to refer to this instance
        File WebDirectory
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File"
            Recurse = $true
            SourcePath = $WebsiteFilePath
            DestinationPath = "C:\inetpub\wwwroot"

            # Ensure that the IIS block is successfully run first before
            # configuring this resource
            DependsOn = "[WindowsFeature]IIS"  # Use for dependencies
        }
    }
}
```

若要建立設定，請以您叫用 PowerShell 函式的相同方式叫用設定區塊，傳遞您可能已在上述範例中定義 (兩個參數的任何預期參數) 。 例如，在此情況下：

```powershell
MyWebConfig -MachineName "TestMachine" -WebsiteFilePath `
  "\\filesrv\WebFiles" -OutputPath "C:\Windows\system32\temp"
# OutputPath is optional
```

這會在您指定的路徑上每個節點產生一個 MOF 檔案。 這些 MOF 檔案會指定每個節點所需的設定。 接下來，使用下列 Cmdlet 來剖析設定 MOF 檔案、將每個節點傳送到其對應的設定，並制定這些設定。 請注意，您不需要為以類別為基礎的 DSC 資源建立個別的 MOF 檔案。

```powershell
Start-DscConfiguration -Verbose -Wait -Path "C:\Windows\system32\temp"
```

## <a name="using-dsc-to-maintain-configuration-state"></a>使用 DSC 維護設定狀態

使用 DSC 時，設定為等冪。 這表示，如果您使用 DSC 來進行相同的設定，則產生的設定狀態一律會相同。 基於這個原因，如果您懷疑環境中的任何節點可能已從所需的設定狀態漂移，您可以再次制定相同的 DSC 設定，使其回到預期的狀態。 您不需要修改設定腳本來處理其狀態已從所需狀態漂移的資源。

下列範例示範如何確認指定節點上設定的實際狀態是否已從節點上的最後一個 DSC 設定漂移。 在此範例中，我們會檢查本機電腦的設定。

```powershell
$session = New-CimSession -ComputerName "localhost"
Test-DscConfiguration -CimSession $session
```

## <a name="built-in-dsc-resources"></a>內建 DSC 資源

您可以在設定腳本中使用下列內建資源：

|Name                  |屬性                                         |
|----------------------|---------------------------------------------------|
|檔案                  |{DestinationPath，屬性，總和檢查碼，內容 ...}|
|封存               |{Destination、Path、Checksum、Credential ...}       |
|環境           |{Name，DependsOn，確定，Path ...}                 |
|Group                 |{身分、Credential、DependsOn、Description ...} |
|記錄                   |{Message，DependsOn，PsDscRunAsCredential}         |
|套件               |{Name、Path、ProductId、Arguments ...}              |
|登錄              |{Key，ValueName，DependsOn，確定 ...}             |
|指令碼                |{>getscript，SetScript，>testscript，Credential ...}  |
|服務               |{Name，>builtinaccount，Credential，相依性 ...}|
|User                  |{UserName，DependsOn，Description，Disabled ...}    |
|WaitForAll            |{NodeName，CoNtext.resourcename，DependsOn，PsDscRunAsC ...}|
|WaitForAny            |{NodeName，CoNtext.resourcename，DependsOn，PsDscRunAsC ...}|
|WaitForSome           |{NodeCount，NodeName，CoNtext.resourcename，DependsOn ...}  |
|WindowsFeature        |{Name，Credential，DependsOn，確定 ...}           |
|WindowsOptionalFeature|{Name，DependsOn，確定，LogLevel ...}             |
|WindowsProcess        |{Arguments，Path，Credential，DependsOn ...}        |

若要取得您系統上可用的 DSC 資源清單，請執行 `Get-DscResource` Cmdlet。

> [!NOTE]
> 在 7.0 版以前的 PowerShell 中，`Get-DscResource` 不會尋找類別型的 DSC 資源。

本主題中的範例將示範如何使用 File 和的資源。 若要查看您可以搭配資源使用的所有屬性，請在資源關鍵字中插入游標 (例如，在 PowerShell ISE 的設定腳本內的檔案) ，按住<kbd>CTRL</kbd> + <kbd>空格鍵</kbd>

## <a name="find-more-resources"></a>尋找更多資源

您可以下載、安裝及瞭解 PowerShell 和 DSC 使用者群體和 Microsoft 所建立的許多其他可用的 DSC 資源。 請流覽 [PowerShell 資源庫](https://www.powershellgallery.com/) ，以流覽及瞭解可用的 DSC 資源。

## <a name="see-also"></a>另請參閱

[PowerShell Desired State Configuration 總覽](/powershell/scripting/dsc/overview/overview)

[內建 PowerShell Desired State Configuration 資源](/powershell/scripting/dsc/resources/resources)

[建立自訂的 PowerShell Desired State Configuration 資源](/powershell/scripting/dsc/resources/authoringResource)
