---
title: "PackageManagement (即 OneGet) 改善"
contributor: jianyunt, quoctruong
translationtype: Human Translation
ms.sourcegitcommit: 4c1b57f221d0f502313eecb21dd36b5e85c2de4d
ms.openlocfilehash: e2646a59c7a241491ef934c62fdfb6d649d16191

---

>注意︰請提供建議的描述性標題和簡短描述

## PackageManagement (即 OneGet) 改善 ##
以下是 WMF 5.1 的修正，以解決 WMF 5.0 版本中的一些使用者體驗落差。 

1 **版本別名**

**案例**︰假設系統上已安裝 1.0 及 2.0 版的封裝 P1，而您想要將 1.0 版解除安裝，所以執行 "uninstall-package -name P1 -version 1.0"。 您希望執行 Cmdlet 後會將 1.0 版解除安裝。 不過，結果卻是將 2.0 版解除安裝。 
    
此問題的成因是 "-version" 參數是 "-minimumversion" 參數的別名。 當 OneGet 在尋找至少 1.0 版的完整封裝時，會傳回最新的版本。 正常情況下會發生此行為，因為大多數的人都想尋找最新版本。 只不過，不應該套用到將封裝解除安裝的情況上。
    
**解決方案**︰完全移除 OneGet 和 PowerShellGet 中的 -version 別名。 

2 **多次提示啟動載入 NuGet 提供者**

**案例**：當您第一次在電腦上執行 Find-Module 或 Install-module 或其他 OneGet Cmdlet 時，OneGet 嘗試啟動載入 NuGet 提供者。 這是因為 PowerShellGet 提供者也使用 NuGet 提供者下載 PowerShell 模組。 接著，OneGet 會提示使用者提供安裝 NuGet 提供者的權限。 在使用者選取 [是] 啟動載入之後，就會安裝最新版的 NuGet 提供者。 
    
不過，當電腦上安裝了較舊版本的 NuGet 提供者時，有時 PowerShell 工作階段會先載入舊版的 NuGet (亦即 OneGet 中的競爭條件)。 不過，PowerShellGet 需要較新版本的 NuGet 提供者工作，因此 PowerShellGet 會要求 OneGet 再次啟動載入 NuGet 提供者。 這就是您會看到多次提示啟動載入 NuGet 提供者的原因。

**解決方案**︰OneGet 會載入最新版的 NuGet 提供者，避免多次提示啟動載入 NuGet 提供者。

如果 $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies 有舊版的 NuGet 提供者，因應措施是手動刪除舊版 (NuGet Anycpu.exe)。


3 **僅限具有內部網路的電腦**

**案例**︰企業案例中，員工的工作環境只能存取內部網路，不能存取網際網路。 在 WMF 5.0 中，OneGet 不支援此種案例。

**解決方案**：
- 您可以使用有網際網路連線的其他電腦，以 Install-PackageProvider NuGet 命令下載 NuGet 提供者。

- 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下尋找 NuGet 提供者。 

- 將二進位檔複製到 (沒有網際網路的) 電腦也可以存取的資料夾或網路共用位置，然後以 "Install-PackageProvider NuGet -Source <Path to folder>" 安裝 NuGet 提供者。


4 **事件記錄檔**

安裝封裝即是變更電腦的狀態。 在 WMF 5.1 中，OneGet 會將安裝、解除安裝和儲存封裝等事件記錄在 Windows 事件記錄檔，供診斷之用。 事件通道和 PowerShell 一樣，亦即 Microsoft-Windows-PowerShell、Operational。

5 **驗證支援** OneGet 支援從需要基本驗證的儲存機制尋找和安裝封裝。 您可以向 Find-Package 和 Install-Package Cmdlet 提供您的認證。 例如：
``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
6 **使用 Proxy 後方的 OneGet**

OneGet 現在採用 Proxy 參數：-ProxyCredential 和 -Proxy。 使用這些參數，您可以在 OneGet Cmdlet 指定 Proxy URL 和 Proxy 認證 (預設使用系統 Proxy 設定)。 例如：
``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO1-->


