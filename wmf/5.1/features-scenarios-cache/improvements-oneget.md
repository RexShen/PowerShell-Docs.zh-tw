---
title: "WMF 5.1 (Preview) 的 OneGet 改善"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 1d0bd545b52ef56045f2ec740b05c4e0fd93bb67

---

# OneGet 改善
WMF 5.1 包含數個修正和改善，以解決 WMF 5.0 版本中的某些使用者體驗落差。 

##已移除版本別名

**案例**︰如果您已在系統上安裝了 1.0 及 2.0 版的封裝 P1，而您想要將 1.0 版解除安裝，您可以執行 "uninstall-package -name P1 -version 1.0"，預期執行 Cmdlet 之後就會將 1.0 版解除安裝。 不過，結果卻是將 2.0 版解除安裝。 
    
這是因為 "-version" 參數是 "-minimumversion" 參數的別名。 當 OneGet 在尋找至少 1.0 版的完整封裝時，會傳回最新的版本。 正常情況下會發生此行為，因為尋找最新版本通常是我們想要的結果。 只不過，不應該套用到將封裝解除安裝的情況上。
    
**解決方案**︰WMF 5.1 完全移除 OneGet 和 PowerShellGet 中的 -version 別名。 

##多次提示啟動載入 NuGet 提供者

**案例**：當您第一次在電腦上執行 Find-Module 或 Install-module 或其他 OneGet Cmdlet 時，OneGet 嘗試啟動載入 NuGet 提供者。 它之所以如此做，是因為 PowerShellGet 提供者也使用 NuGet 提供者下載 PowerShell 模組。 接著，OneGet 會提示使用者提供安裝 NuGet 提供者的權限。 在使用者選取 [是] 啟動載入之後，就會安裝最新版的 NuGet 提供者。 
    
不過在某些情況下，當電腦上安裝了較舊版本的 NuGet 提供者時，有時 PowerShell 工作階段會先載入舊版的 NuGet (亦即 OneGet 中的競爭條件)。 不過，PowerShellGet 需要較新版本的 NuGet 提供者工作，因此 PowerShellGet 會要求 OneGet 再次啟動載入 NuGet 提供者。 以致多次提示啟動載入 NuGet 提供者。

**解決方案**︰在 WMF 5.1 中，OneGet 會載入最新版的 NuGet 提供者，避免多次提示啟動載入 NuGet 提供者。

如果 $env: ProgramFiles\PackageManagement\ProviderAssemblies $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies 有舊版的 NuGet 提供者，您也可以手動刪除舊版 (NuGet Anycpu.exe) 解決這個問題。


##只有內部網路存取權電腦的 OneGet 支援

**案例**︰以前在 WMF 5.0 中，OneGet 不支援只能存取內部網路 (不能存取網際網路) 的電腦。

**解決方案**︰在 WMF 5.1，您可以依照這些步驟允許內部網路電腦使用 OneGet：

1. 使用 Install-PackageProvider NuGet，用具有網際網路連線的其他電腦下載 NuGet 提供者。

2. 在 $env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget 或 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget 下尋找 NuGet 提供者。 

3. 將二進位檔複製到內部網路電腦可以存取的資料夾或網路共用位置，然後以 "Install-PackageProvider NuGet -Source <Path to folder>" 安裝 NuGet 提供者。


##事件記錄的改善

安裝封裝即是變更電腦的狀態。 在 WMF 5.1 中，OneGet 會將安裝、解除安裝和儲存封裝活動等事件記錄在 Windows 事件記錄檔。 事件通道和 PowerShell 的一樣，亦即 Microsoft-Windows-PowerShell、Operational。

##支援基本驗證

在 WMF 5.1 中，OneGet 支援從需要基本驗證的儲存機制尋找和安裝封裝。 您可以向 Find-Package 和 Install-Package Cmdlet 提供您的認證。 例如：

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```
##支援在 Proxy 後方使用 OneGet

在 WMF 5.1 中，OneGet 現在採用新的 Proxy 參數：-ProxyCredential 和 -Proxy。 您可以使用這些參數，在 OneGet Cmdlet 指定 Proxy URL 和認證。 預設使用系統 Proxy 設定。 例如：

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```



<!--HONumber=Jul16_HO3-->


