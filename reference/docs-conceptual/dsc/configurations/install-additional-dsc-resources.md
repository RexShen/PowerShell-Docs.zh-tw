---
ms.date: 12/12/2018
keywords: dsc, powershell, 資源, 資源庫, 安裝, 設定
title: 安裝額外的 DSC 資源
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417788"
---
# <a name="install-additional-dsc-resources"></a>安裝額外的 DSC 資源

PowerShell 包含幾個適用於 Desired State Configuration (DSC) 的立即可用資源。 **PSDesiredStateConfiguration** 模組包含所有 OOB DSC 資源，可供您的特定 PowerShell 執行個體使用。

這是 PowerShell 4.0 中包含的 OOB 資源清單和資源功能描述。

> [!NOTE]
> 此清單並不完整，因為 OOB 資源的數量會隨著 PowerShell 的每個版本而增加。

|資源  |描述  |
|---------|---------|
|**File**|控制檔案和目錄的狀態。 在**來源**變更時將檔案從**來源**複製到**目的地**，並藉由比較日期、總和檢查碼和雜湊更新檔案。|
|**Archive**|將封存和指定位置解除封裝。 驗證封存具有指定的**總和檢查碼**。|
|**Environment**|管理環境變數。|
|**群組**|管理本機群組並控制群組成員資格。|
|**Log**|將訊息寫入至 `Microsoft-Windows-Desired State Configuration/Analytic` 事件記錄檔。|
|**套件**|使用**引數**、**LogPath**、**ReturnCode** 和其他設定安裝套件或解除安裝套件。|
|**Registry**|管理登錄機碼和值。|
|**Script**|可讓您設計自己的[取得-測試-設定](../resources/get-test-set.md)指令碼區塊。|
|**Service**|設定 Windows 服務。|
|**User** |管理本機使用者和屬性。|
|**WindowsFeature**|管理角色和功能。|
|**WindowsProcess**|設定 Windows 處理序。|

OOB 資源是適合一般作業的良好起點。 如果 OOB 資源不能滿足您的需求，您可以撰寫自己的[自訂資源](../resources/authoringResource.md)。 在撰寫自訂資源來解決問題之前，您應該先瀏覽由 Microsoft 和 PowerShell 社群建立的大量 DSC 資源。

您可以在 [PowerShell 資源庫](https://www.powershellgallery.com/)和 [GitHub](https://github.com/) 中找到 DSC 資源。 您也可以直接從 PowerShell 主控台中使用 [PowerShellGet](/powershell/module/powershellget/) 來安裝 DSC 資源。

## <a name="installing-powershellget"></a>安裝 PowerShellGet

若要判斷您是否已有 **PowerShellGet**，或是要取得安裝協助，請參閱下列指南：[安裝 PowerShellGet](/powershell/scripting/gallery/installing-psget)。

## <a name="finding-dsc-resources-using-powershellget"></a>使用 PowerShellGet 尋找 DSC 資源

一旦在系統上安裝 **PowerShellGet** 之後，您就可以尋找並安裝於 [PowerShell 資源庫](https://www.powershellgallery.com/)中裝載的 DSC 資源。

首先，使用 [Find-DSCResource](/powershell/module/powershellget/find-dscresource) Cmdlet 尋找 DSC 資源。 當您第一次執行 `Find-DSCResource` 時，您會看到以下安裝「NuGet 提供者」的提示。

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

按下 'y' 後隨即會安裝 "NuGet" 提供者，您會看到可從 PowerShell 資源庫安裝的 DSC 資源清單。

> [!NOTE]
> 因為清單非常大，故在此不顯示。

您也可以使用萬用字元指定 `-Name` 參數，或不含萬用字元的 `-Filter` 參數來縮小搜尋範圍。 此範例會使用萬用字元嘗試尋找 "TimeZone" (時區) 的 DSC 資源。

> [!IMPORTANT]
> `Find-DSCResource` Cmdlet 目前有錯誤 (Bug)，無法在 `-Name` 和 `-Filter` 參數中使用萬用字元。 下列第二個範例示範使用 `Where-Object` 的因應措施。

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

您也可以使用 `Where-Object` 以更細微的篩選來尋找 DSC 資源。 這個方法會比使用內建的篩選參數慢。

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

如需有關篩選的詳細資訊，請參閱 [Where-Object](/powershell/module/microsoft.powershell.core/where-object)。

## <a name="installing-dsc-resources-using-powershellget"></a>使用 PowerShellGet 安裝 DSC 資源

若要安裝 DSC 資源，請使用 [Install-Module](/powershell/module/PowershellGet/Install-Module) Cmdlet，指定搜尋結果中顯示在**模組**名稱底下的模組名稱。

"TimeZone" 資源存在於 "ComputerManagementDSC" 模組中，也就是此範例會安裝的模組。

> [!NOTE]
> 如果您有不受信任的 PowerShell 資源庫，則會看到要求確認的警告，以及指示您如何避免後續的安裝提示。

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

按 'y' 以繼續安裝模組。 安裝之後，您可以使用 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) 確認已安裝新的資源。

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

您也可以透過指定 `-ModuleName` 參數來檢視新安裝的其他資源。

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>另請參閱

- [何謂資源？](../resources/resources.md)
