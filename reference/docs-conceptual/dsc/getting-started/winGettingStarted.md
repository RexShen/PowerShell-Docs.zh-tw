---
ms.date: 08/15/2019
keywords: dsc,powershell,設定,安裝
title: 開始使用適用於 Windows 的 Desired State Configuration (DSC)
ms.openlocfilehash: a9346b96693acdbad9bacbd4b6ca85971e17a3d1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417757"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a>開始使用適用於 Windows 的 Desired State Configuration (DSC)

此主題說明如何開始使用適用於 Windows 的 PowerShell Desired State Configuration (DSC)。
如需 DSC 的一般資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](../overview/overview.md)。

## <a name="supported-windows-operation-system-versions"></a>支援的 Windows 作業系統版本

下面是支援的版本：

- Windows Server 2019
- Windows Server 2016
- Windows Server 2012R2
- Windows Server 2012
- Windows Server 2008 R2 SP1
- Windows 10
- Windows 8.1
- Windows 7

[Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) 獨立產品 SKU 不包含 Desired State Configuration 的實作，因此無法由 PowerShell DSC 或 Azure 自動化狀態設定管理。

## <a name="installing-dsc"></a>安裝 DSC

PowerShell Desired State Configuration 包含在 Windows 中，而且透過 Windows Management Framework 來更新。
最新版本是 [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616) \(英文\)。

> [!NOTE]
> 您不需要啟用 Windows Server 功能 'DSC-Service'，即可使用 DSC 來管理電腦。
> 只有在建置 Windows 提取伺服器執行個體時，才需要該功能。

## <a name="using-dsc-for-windows"></a>使用適用於 Windows 的 DSC

下列各節說明如何在 Windows 電腦上建立並執行 DSC 設定。

### <a name="creating-a-configuration-mof-document"></a>建立設定 MOF 文件

Windows PowerShell Configuration 關鍵字可用來建立設定。
下列步驟說明如何使用 Windows PowerShell 建立設定文件。

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a>定義設定，然後產生設定文件：

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a>安裝包含 DSC 資源的模組

Windows PowerShell Desired State Configuration 包含內有 DSC 資源的內建模組。
您也可以使用 PowerShellGet Cmdlet，從外部來源 (例如，PowerShell 資源庫) 載入模組。

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a>將設定套用至機器

您可以使用 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) Cmdlet 將設定檔 (MOF 檔案) 套用至機器。

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a>取得設定的目前狀態

[Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) Cmdlet 會查詢機器的目前狀態，並傳回設定的目前值。

`Get-DscConfiguration`

[Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) Cmdlet 會傳回套用至電腦的目前中繼設定。

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a>將目前設定從電腦移除

[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a>設定本機 Configuration Manager 中的設定

使用 [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) Cmdlet，將中繼設定 MOF 檔案套用至電腦。
需要中繼設定 MOF 路徑。

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a>Windows PowerShell Desired State Configuration 記錄檔

DSC 的記錄會寫入在路徑 `Microsoft-Windows-Dsc/Operational` 中的 Windows 事件記錄檔。
您可以遵循 [DSC 事件記錄檔在哪裡](/powershell/scripting/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs)中的步驟，啟用用於偵錯工具的其他記錄檔。
