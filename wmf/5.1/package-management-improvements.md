---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
contributor: jianyunt, quoctruong
title: "WMF 5.1 中套件管理的改善"
ms.openlocfilehash: b55a1742530b7cd48d60d79b7d4866ebee80a3b6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-to-package-management-in-wmf-51"></a>WMF 5.1 中套件管理的改善#

## <a name="improvements-in-packagemanagement"></a>封裝管理的改善 ##
以下是 WMF 5.1 中所做的修正︰ 

### <a name="version-alias"></a>版本別名

**案例**︰您的系統上若是安裝了 1.0 及 2.0 版的 P1 套件，而您想要解除安裝 1.0 版，可以執行 `Uninstall-Package -Name P1 -Version 1.0`。預期在執行 Cmdlet 之後，應會解除安裝 1.0 版， 但卻解除安裝了 2.0 版。  
    
這是因為 `-Version` 參數是 `-MinimumVersion` 參數的別名。 當 PackageManagement 在尋找符合資格的套件 (最低 1.0 版) 時，會傳回最新的版本。 正常情況下會發生此行為，因為尋找最新版本通常是我們想要的結果。 但 `Uninstall-Package` 案例應不會發生此情況。
    
**解決方法**︰將 `-Version` 從 PackageManagement (又稱為 OneGet) 及 PowerShellGet 中完全移除。 

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a>多次提示啟動載入 NuGet 提供者

**案例**︰當您第一次在電腦上執行 `Find-Module`、`Install-Module` 或其他 PackageManagement Cmdlet 時，PackageManagement 會嘗試啟動 NuGet 提供者。 這是因為 PowerShellGet 提供者也使用 NuGet 提供者下載 PowerShell 模組。 PackageManagement 會提示使用者提供安裝 NuGet 提供者的權限。 在使用者選取 [是] 啟動載入之後，就會安裝最新版的 NuGet 提供者。 
    
但在某些情況下，您的電腦如有安裝舊版的 NuGet 提供者，有時候會先將舊版的 NuGet 載入 PowerShell 工作階段 (亦即 PackageManagement 會出現競爭狀況)。 但因為 PowerShellGet 需要新版的 NuGet 提供者才能運作，所以 PowerShellGet 會要求 PackageManagement 重新啟動 NuGet 提供者。 以致多次提示啟動載入 NuGet 提供者。

**解決方法**︰在 WMF 5.1 中，PackageManagement 會載入最新版的 NuGet 提供者，以避免多次提示啟動 NuGet 提供者。

如果 $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies 有舊版的 NuGet 提供者，您也可以手動刪除舊版 (NuGet Anycpu.exe) 解決這個問題。


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a>只有可以存取內部網路的電腦才支援 PackageManagement

**案例**︰在企業環境中，員工的工作環境通常無法存取網際網路，而只能存取內部網路。 在 WMF 5.0 中，PackageManagement 不支援此狀況。

**案例**︰在 WMF 5.0 中，PackageManagement 不支援只能存取內部網路 (無法存取網際網路) 的電腦。

**解決方案**︰在 WMF 5.1，您可以執行下列步驟，將電腦設定成可以使用 PackageManagement：

1. 利用其他可以連線到網際網路的電腦執行 `Install-PackageProvider -Name NuGet`，以下載 NuGet 提供者。

2. 在 `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 或 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget` 下尋找 NuGet 提供者。

3. 將二進位檔複製到內部網路電腦能夠存取的資料夾或網路共用位置，然後使用 `Install-PackageProvider -Name NuGet -Source <Path to folder>` 安裝 NuGet 提供者。


### <a name="event-logging-improvements"></a>事件記錄的改善

安裝封裝即是變更電腦的狀態。 現在在 WMF 5.1 中，PackageManagement 已會將事件記錄到 `Install-Package`、`Uninstall-Package` 及 `Save-Package` 活動的 Windows 事件記錄檔中。 事件記錄檔與 PowerShell 相同，亦即 `Microsoft-Windows-PowerShell, Operational`。

### <a name="support-for-basic-authentication"></a>支援基本驗證

在 WMF 5.1 中，PackageManagement 可讓您從需要基本驗證的存放庫尋找及安裝套件。 您可以將您的認證提供給 `Find-Package` 及 `Install-Package` Cmdlet。 例如：

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
### <a name="support-for-using-packagemanagement-behind-a-proxy"></a>在 Proxy 後方使用 PackageManagement 的支援

現在在 WMF 5.1 l 中，PackageManagement 也接受新的 Proxy 參數 `-ProxyCredential` 及 `-Proxy`。 您可以使用這些參數，在 PackageManagement Cmdlet 中指定 Proxy URL 及認證。 預設使用系統 Proxy 設定。 例如：

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```

