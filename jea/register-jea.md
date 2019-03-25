---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: 登錄 JEA 設定
ms.openlocfilehash: 6fa0ce434c8e70eb718545e99417bfe034cda6bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "58059434"
---
# <a name="registering-jea-configurations"></a>登錄 JEA 設定

> 適用於：Windows PowerShell 5.0

在您建立[角色功能](role-capabilities.md)和[工作階段設定檔](session-configurations.md)之後，使用 JEA 前所需進行的最後步驟，便是註冊 JEA 端點。
向系統註冊 JEA 端點，將能使該端點可供使用者和自動化引擎使用。

## <a name="single-machine-configuration"></a>單一電腦設定

針對小型環境，您可以藉由使用 [Register-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/register-pssessionconfiguration) Cmdlet 登錄工作階段設定檔來部署 JEA。

開始之前，請確定符合下列先決條件：
- 建立一或多個角色並放置在有效 PowerShell 模組的 'RoleCapabilities' 資料夾中。
- 建立並測試工作階段設定檔。
- 登錄 JEA 設定的使用者在系統上具有系統管理員權限。

您也必須選取 JEA 端點的名稱。
當使用者想要使用 JEA 連線到系統時，便會需要 JEA 端點的名稱。
您可以使用 [Get-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/get-pssessionconfiguration) Cmdlet 來檢查系統上的現有端點名稱。
開頭為 'microsoft' 的端點通常都與 Windows 一起出貨。
'microsoft.powershell' 端點是在連線到遠端 PowerShell 端點時使用的預設端點。

```powershell
PS C:\> Get-PSSessionConfiguration | Select-Object Name

Name
----
microsoft.powershell
microsoft.powershell.workflow
microsoft.powershell32
```

當您決定好 JEA 端點的適當名稱時，請執行下列命令來登錄端點。

```powershell
Register-PSSessionConfiguration -Path .\MyJEAConfig.pssc -Name 'JEAMaintenance' -Force
```

> [!WARNING]
> 上述命令會重新啟動系統上的 WinRM 服務。
> 這會終止所有 PowerShell 遠端工作階段，以及任何進行中的 DSC 設定。
> 建議您讓任何實際執行電腦離線，然後才執行命令，以避免中斷營運。

如果登錄成功，您便可以[使用 JEA](using-jea.md)。
您可以隨時刪除工作階段設定檔；在註冊之後，便不會再度使用它。

## <a name="multi-machine-configuration-with-dsc"></a>DSC 的多電腦設定

如果您要在多部電腦上部署 JEA，最簡單的部署模型是使用 JEA [期望狀態設定](https://msdn.microsoft.com/powershell/dsc/overview)資源快速且一致地在每部機器上部署 JEA。

若要搭配 DSC 部署 JEA，您必須確定符合下列先決條件︰
- 已撰寫一或多個角色功能並新增至有效的 PowerShell 模組。
- 包含角色的 PowerShell 模組儲存在每一部機器可存取的 (唯讀) 檔案共用上。
- 已確定工作階段設定的設定。 使用 JEA DSC 資源時，您不需要建立工作階段設定檔。
- 您有可讓您在每部電腦上執行系統管理動作的認證，或是能夠存取用來管理電腦的 DSC 提取伺服器。
- 您已下載 [JEA DSC 資源](https://github.com/PowerShell/JEA/tree/master/DSC%20Resource)

在目標電腦 (或提取伺服器上，如果您有使用的話)，建立 JEA 端點的 DSC 設定。
在此設定中，您會使用 JustEnoughAdministration DSC 資源來設定工作階段設定檔和 File 資源，以便從檔案共用複製角色功能。

下列屬性可以使用 DSC 資源來設定︰
- 角色定義
- 虛擬帳戶群組
- 群組受管理的服務帳戶名稱
- 文字記錄目錄
- 使用者磁碟機
- 條件式存取原則
- JEA 工作階段的啟動指令碼

DSC 設定中的這些屬性，每個的語法都與 PowerShell 工作階段設定檔一致。

以下是一般伺服器維護模組的範例 DSC 設定。

它假設在 'RoleCapabilities' 子資料夾中包含角色功能的有效 PowerShell 模組位於 '\\\\我的檔案期用\\JEA' 檔案共用上。


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

這個設定便可以藉由[直接叫用本機設定管理員](https://msdn.microsoft.com/powershell/dsc/metaconfig)或更新[提取伺服器設定](https://msdn.microsoft.com/powershell/dsc/pullserver)，以套用在系統上。

DSC 資源也可讓您取代預設的 Microsoft.PowerShell 遠端端點。
若您這麼做，資源會自動註冊名為 "Microsoft.PowerShell.Restricted" 的備份無限制端點，它具有預設 WinRM ACL (允許遠端管理使用者與本機系統管理員群組成員存取它)。

## <a name="unregistering-jea-configurations"></a>取消登錄 JEA 設定

若要移除系統上的 JEA 端點，請使用 [Unregister-PSSessionConfiguration](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Unregister-PSSessionConfiguration) Cmdlet。
取消登錄 JEA 端點會使新使用者無法在系統上建立新的 JEA 工作階段。
它也可讓您藉由使用相同的端點名稱重新登錄已更新的工作階段設定檔來更新 JEA 設定。

```powershell
# Unregister the JEA endpoint called "ContosoMaintenance"
Unregister-PSSessionConfiguration -Name 'ContosoMaintenance' -Force
```

> [!WARNING]
> 取消登錄 JEA 端點會導致 WinRM 服務重新啟動。
> 這會中斷大部分正在進行中的遠端管理作業，包括其他的 PowerShell 工作階段、WMI 引動過程，以及某些管理工具。
> 只在計劃的維護期間取消登錄 PowerShell 端點。

## <a name="next-steps"></a>接下來的步驟

- [測試 JEA 端點](using-jea.md)
