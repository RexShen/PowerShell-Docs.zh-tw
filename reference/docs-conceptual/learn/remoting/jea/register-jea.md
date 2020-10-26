---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: 登錄 JEA 設定
description: 向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。
ms.openlocfilehash: 6e7f8cdc1e7a666bddaa42034d70fcbcf55c1972
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499904"
---
# <a name="registering-jea-configurations"></a>登錄 JEA 設定

在您建立[角色功能](role-capabilities.md)和[工作階段設定檔](session-configurations.md)之後，最後一個步驟即是登錄 JEA 端點。 向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。

## <a name="single-machine-configuration"></a>單一電腦設定

針對小型環境，您可以藉由使用 [Register-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/register-pssessionconfiguration) Cmdlet 登錄工作階段設定檔來部署 JEA。

開始之前，請確定符合下列先決條件：

- 已建立一或多個角色並放置在 PowerShell 模組的 **RoleCapabilities** 資料夾中。
- 建立並測試工作階段設定檔。
- 登錄 JEA 設定的使用者在系統上具有系統管理員權限。
- 您已選取您的 JEA 端點名稱。

當使用者使用 JEA 連線到系統時，便會需要 JEA 端點的名稱。 [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 會列出系統上的端點名稱。 開頭為 `microsoft` 的端點通常隨附於 Windows。 `microsoft.powershell` 端點是在連線到遠端 PowerShell 端點時使用的預設端點。

```powershell
Get-PSSessionConfiguration | Select-Object Name
```

```Output
Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

執行下列命令以登錄端點。

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 上一個命令會重新啟動系統上的 WinRM 服務。 這會終止所有 PowerShell 遠端工作階段，以及任何正在進行的 DSC 設定。 建議您先將實際執行電腦離線再執行命令，以免中斷營運。

登錄之後，即可[使用 JEA](using-jea.md)。 您可以隨時刪除工作階段設定檔。 端點登錄後即不再使用設定檔。

## <a name="multi-machine-configuration-with-dsc"></a>DSC 的多電腦設定

在多部電腦上部署 JEA 時，最簡單的部署模型是使用 JEA [Desired State Configuration (DSC)](../../../dsc/overview/overview.md) 資源快速且一致地在每部機器上部署 JEA。

若要搭配 DSC 部署 JEA，請務必符合下列先決條件︰

- 已撰寫一或多個角色功能並新增至 PowerShell 模組。
- 包含角色的 PowerShell 模組儲存在每一部機器可存取的 (唯讀) 檔案共用上。
- 已確定工作階段設定的設定。 使用 JEA DSC 資源時，您不需要建立工作階段設定檔。
- 您的認證可在每部電腦上執行系統管理動作，或存取用來管理電腦的 DSC 提取伺服器。
- 您已下載 [JEA DSC 資源](https://github.com/powershell/JEA/tree/master/DSC%20Resource)。

在目標電腦或提取伺服器上建立 JEA 端點的 DSC 設定。 在此設定中， **JustEnoughAdministration** DSC 資源會定義工作階段設定檔，而 **File** 資源則會從檔案共用複製角色功能。

下列屬性可以使用 DSC 資源來設定︰

- 角色定義
- 虛擬帳戶群組
- 群組受控服務帳戶名稱
- 文字記錄目錄
- 使用者磁碟機
- 條件式存取原則
- JEA 工作階段的啟動指令碼

DSC 設定中的這些屬性，每個的語法都與 PowerShell 工作階段設定檔一致。

以下是一般伺服器維護模組的範例 DSC 設定。 假設包含角色功能的有效 PowerShell 模組位於 `\\myfileshare\JEA` 檔案共用上。

```powershell
Configuration JEAMaintenance
{
    Import-DscResource -Module JustEnoughAdministration, PSDesiredStateConfiguration

    File MaintenanceModule
    {
        SourcePath = "\\myfileshare\JEA\ContosoMaintenance"
        DestinationPath = "C:\Program Files\WindowsPowerShell\Modules\ContosoMaintenance"
        Checksum = "SHA-256"
        Ensure = "Present"
        Type = "Directory"
        Recurse = $true
    }

    JeaEndpoint JEAMaintenanceEndpoint
    {
        EndpointName = "JEAMaintenance"
        RoleDefinitions = "@{ 'CONTOSO\JEAMaintenanceAuditors' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit' }; 'CONTOSO\JEAMaintenanceAdmins' = @{ RoleCapabilities = 'GeneralServerMaintenance-Audit', 'GeneralServerMaintenance-Admin' } }"
        TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
        DependsOn = '[File]MaintenanceModule'
    }
}
```

接著，這個設定便可透過直接叫用[本機設定管理員](/powershell/scripting/dsc/managing-nodes/metaConfig)或更新[提取伺服器設定](/powershell/scripting/dsc/pull-server/pullServer)來套用在系統上。

DSC 資源也可讓您取代預設的 **Microsoft.PowerShell** 端點。 取代後，此資源會自動登錄名為 **Microsoft.PowerShell.Restricted** 的備份端點。 備份端點都具有預設的 WinRM ACL，允許 Remote Management Users 與本機 Administrators 群組成員存取它。

## <a name="unregistering-jea-configurations"></a>取消登錄 JEA 設定

[Unregister-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/Unregister-PSSessionConfiguration) Cmdlet 會移除 JEA 端點。 取消登錄 JEA 端點會使新使用者無法在系統上建立新的 JEA 工作階段。 它也可讓您藉由使用相同的端點名稱重新登錄已更新的工作階段設定檔來更新 JEA 設定。

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> 取消登錄 JEA 端點會導致 WinRM 服務重新啟動。 這會中斷大部分正在進行中的遠端管理作業，包括其他的 PowerShell 工作階段、WMI 引動過程，以及某些管理工具。 只在計劃的維護期間取消登錄 PowerShell 端點。

## <a name="next-steps"></a>下一步

[測試 JEA 端點](using-jea.md)
