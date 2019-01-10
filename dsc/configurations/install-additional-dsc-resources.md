---
ms.date: 12/12/2018
keywords: dsc，powershell、 資源、 資源庫、 安裝程式
title: 安裝額外的 DSC 資源
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400835"
---
# <a name="install-additional-dsc-resources"></a>安裝額外的 DSC 資源

PowerShell 包含幾個的立即可用資源的 Desired State Configuration (DSC)。 **PSDesiredStateConfiguration**模組包含的所有 OOB DSC 資源可在您的 PowerShell 的特定執行個體上取得。

這是包含在 PowerShell 4.0 和資源的功能描述的 OOB 資源的清單。

> [!NOTE]
> 這是不完整的清單中，OOB 資源數目變得與每個版本的 PowerShell。

|資源  |描述  |
|---------|---------|
|**File**|控制檔案和目錄的狀態。 將從檔案複製**來源**要**目的地**，加以更新時**來源**藉由比較日期、 總和檢查碼，以及雜湊的變更。|
|**Archive**|解壓縮封存和指定的位置。 驗證具有指定的封存**總和檢查碼**。|
|**Environment**|管理的環境變數。|
|**群組**|管理本機群組，並控制群組成員資格。|
|**Log**|寫入訊息至`Microsoft-Windows-Desired State Configuration/Analytic`事件記錄檔。|
|**套件**|安裝或解除安裝使用的套件**引數**， **LogPath**， **ReturnCode**，其他設定。|
|**Registry**|管理登錄機碼和值。|
|**Script**|可讓您設計您自己[取得測試設定](../resources/get-test-set.md)指令碼區塊。|
|**Service**|設定 Windows 服務。|
|**User** |管理本機使用者和屬性。|
|**WindowsFeature**|管理角色和功能。|
|**WindowsProcess**|設定 Windows 處理程序。|

OOB 資源可讓一般作業的不錯的起點。 如果 OOB 資源不符合您的需求，您可以撰寫您自己[自訂資源](../resources/authoringResource.md)。 撰寫自訂的資源，為您解決問題之前，您應該瀏覽大量已由 Microsoft 和 PowerShell 社群的 DSC 資源。

您可以在同時尋找 DSC 資源[PowerShell 資源庫](https://www.powershellgallery.com/)並[GitHub](https://github.com/)。 您也可以直接從 PowerShell 主控台中使用安裝 DSC 資源[PowerShellGet](/powershell/module/powershellget/)。

## <a name="installing-powershellget"></a>安裝 PowerShellGet

若要判斷您是否已有**PowerShell**取得，或若要取得安裝協助，請參閱下列指南：[安裝 PowerShellGet](/powershell/gallery/installing-psget)

## <a name="finding-dsc-resources-using-powershellget"></a>尋找使用 PowerShellGet 的 DSC 資源

一次**PowerShellGet**安裝在您系統上，您可以尋找並安裝在裝載的 DSC 資源[PowerShell 資源庫](https://www.powershellgallery.com/)。

首先，使用[Find-dscresource](/powershell/module/powershellget/find-dscresource) cmdlet 來尋找 DSC 資源。 當您執行`Find-DSCResource`第一次，您會看到下列提示來安裝 「 NuGet 提供者 」。

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

之後按 'y' 安裝"NuGet"提供者，您會看到一份您可以從 「 PowerShell 資源庫安裝的 DSC 資源。

> [!NOTE]
> 因為它是非常大，不會顯示清單。

您也可以指定`-Name`參數中使用萬用字元，或`-Filter`不含萬用字元來縮小搜尋範圍的參數。 此範例會嘗試尋找 「 時區 」 DSC 資源使用萬用字元。

> [!IMPORTANT]
> 目前沒有中的 bug `Find-DSCResource` cmdlet，以防止在兩者中使用萬用字元`-Name`和`-Filter`參數。 下列第二個範例顯示如何因應措施，使用`Where-Object`。

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

您也可以使用`Where-Object`來尋找具有更細微的篩選的 DSC 資源。 這個方法會比使用內建的篩選參數慢。

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

如需有關篩選的詳細資訊，請參閱 < [Where-object](/powershell/module/microsoft.powershell.core/where-object)。

## <a name="installing-dsc-resources-using-powershellget"></a>安裝使用 PowerShellGet 的 DSC 資源

若要安裝 DSC 資源，請使用[Install-module](/powershell/module/PowershellGet/Install-Module) cmdlet，並指定下方顯示的模組名稱**模組**名稱在您的搜尋結果中。

「 時區 」 資源存在於"ComputerManagementDSC 」 模組，因此也就是模組此範例會安裝。

> [!NOTE]
> 如果您有不受信任 「 PowerShell 資源庫，您會看到以下要求確認，警告，並指示您要如何避免後續提示上安裝。

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

按 'y' 以繼續安裝模組。 安裝之後，您可以確認已安裝使用新的資源[Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)。

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

您也可以檢視您新安裝的模組中的其他資源，藉由指定`-ModuleName`參數。

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
