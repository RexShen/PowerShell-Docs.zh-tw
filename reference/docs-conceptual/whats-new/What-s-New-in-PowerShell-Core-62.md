---
title: PowerShell Core 6.2 的新功能
description: PowerShell Core 6.2 中發行的新功能與變更
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96833761"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2 的新功能

PowerShell Core 6.2 版著重於效能改進、錯誤修復，以及可提升軟體品質的較小 Cmdlet 和語言增強功能。 若要查看增強功能的完整清單，請參閱 GitHub 上的詳細[變更記錄](https://github.com/PowerShell/PowerShell/releases)。

## <a name="experimental-features"></a>實驗性功能

先前我們已啟用對[實驗性功能][]的支援。 在 6.2 版中，我們提供了四個試用的實驗性功能。請提供意見反應，協助我們進行改善，以及決定是否值得升級為主流功能。

請使用 `Get-ExperimentalFeature` 取得一份可用實驗性功能的清單。 您可以使用 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` 啟用或停用這些功能。

### <a name="command-not-found-suggestions"></a>找不到命令建議項目

此功能會使用模糊比對方式，尋找您可能拼字錯誤的命令或 Cmdlet 的建議項目。

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>範例

在此範例中，系統在 Cmdlet 名稱拼字錯誤的情況下，透過模糊比對方式找出幾個最有可能和最不可能的建議項目。

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>隱含遠端批次處理

在管線中使用[隱含遠端](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) \(英文\) 時，PowerShell 會將管線中的每個命令視為獨立。 用戶端和遠端系統之間的物件，會在管線執行時重複序列化和 `de-serialized`。

使用此功能時，PowerShell 會分析管線，判斷命令是否安全地執行以及它是否存在於目標系統上。 若為 true，PowerShell 會從遠端執行整個管線，並只將結果序列化並 `de-serializes` 回用戶端。

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

實際測試`Get-Process | Sort-Object`透過 localhost 會從 10-15 秒減少至 20-30 **毫秒**。 此功能只需要在用戶端上啟用。 伺服器端不需要任何變更。

### <a name="temp-drive"></a>暫存磁碟機

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

如果在不同的作業系統上使用 PowerShell Core，會發現尋找暫存目錄的環境變數和 Windows、macOS 與 Linux 中的不一樣！ 您可以透過此功能，取得稱為 `Temp:` 的 [PSDrive][]，它會自動對應至您所使用作業系統的暫存資料夾。

#### <a name="example"></a>範例

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

請注意，原生檔案命令 (例如 Linux 上的 `ls`) 不會察覺 PSDrives 且不會看到這個 `Temp:` 磁碟機。

### <a name="abbreviation-expansion"></a>展開縮寫

PowerShell Cmdlet 都應該有描述性名詞。 這會導致較難輸入完整名稱。 此功能可讓您只要輸入 Cmdlet 的大寫字元，然後使用 Tab 鍵自動完成來尋找相符項目。

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>範例

```powershell
PS> i-arsavsf
```

如果按下 Tab 鍵，並已安裝 Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 模組，它會自動完成為：

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> 此功能採用需透過互動方式使用的設計。 Cmdlet 的縮寫形式無法在系統中執行。
> 這並不是要取代別名的功能。

## <a name="breaking-changes"></a>重大變更

- 修正 `Write-Output` 中的 `-NoEnumerate` 行為，以與 Windows PowerShell 一致。 (#9069)
- 讓 `Join-String -InputObject 1,2,3` 的結果和 `1,2,3 | Join-String` 相同 (#8611) (感謝 @sethvs！)
- 新增 `-Stable` 至 `Sort-Object` 和相關測試 (#7862) (感謝 @KirkMunro！)
- 改善 `Start-Sleep`Cmdlet 以接受小數秒數 (#8537) (感謝 @Prototyyppi！)
- 變更雜湊表以在所有文化特性 (Culture) 中以 `case-insensitive` 的方式使用 OrdinalIgnoreCase (#8566)
- 修正 `Import-Csv` 中的 **LiteralPath**，以繫結至 `Get-ChildItem` 輸出 (#8277) (感謝 @iSazonov！)
- 在 `Import-Csv` 中使用雙引號分隔符號時，不會再跳過沒有名稱的資料行 (#7899) (感謝 @Topping！)
- `Get-ExperimentalFeature` 不再有 `-ListAvailable` 切換功能 (#8318)
- 偵錯參數現在會將 `$DebugPreference` 設定為 **Continue**，而非 **Inquire** (#8195) (感謝 @KirkMunro！)
- 如果在與 pwsh 搭配使用的非互動式、重新導向、編碼命令中指定，請接受 `-OutputFormat` (#8115)
- 請先從模組基底路徑載入組件，然後再嘗試從 GAC 載入 (#8073)
- 從 Linux 預覽套件中移除波狀符號 (#8244)
- 將 `-WorkingDirectory` 的處理順序移到設定檔前面 (#8079)
- 不要在 Unix 中新增 `PATHEXT` 環境變數 (#7697) (感謝 @iSazonov！)

## <a name="known-issues"></a>已知問題

- 遠端登入 Windows IOT ARM 平台時，會在載入模組時發生問題。 請參閱 (#8053)

## <a name="general-updates-and-fixes"></a>一般更新與修正

- 支援在區分大小寫的檔案系統中，使用檔案和資料夾不區分大小寫的 Tab 鍵自動完成功能 (#8128)
- 公開 PSVersionInfo.PSVersion 和 PSVersionInfo.PSEdition (#8054) (感謝 @KirkMunro！)
- 在 `catch{ }` 區塊中新增 `$_` / `$PSItem` 的型別推斷 (#8020) (感謝 @vexx32！)
- 修正靜態方法引動過程型別推斷 (#8018) (感謝 @SeeminglyScience！)
- 建立 `Select-Object`、`Group-Object`、**PSObject** 和 **雜湊表** 的推斷型別 (#7231) (感謝 @powercode！)
- 支援包含 `ByRef-like` 型別參數的呼叫方法 (#7721)
- 處理 Windows PowerShell 模組路徑已在環境 PSModulePath 中的情況 (#7727)
- 透過儲存純文字以啟用非 Windows 的 `SecureString` Cmdlet (#9199)
- 改善使用 securestring 匯入 clixml 時，非 Windows 上顯示的錯誤訊息 (#7997)
- 新增 ReplyTo 參數至 `Send-MailMessage`(#8727) (感謝 @replicaJunction！)
- 新增已淘汰的訊息至 `Send-MailMessage` (#9178)
- 修正 `Restart-Computer` 以在沒有 WinRM 時於 `localhost` 中運作 (#9160)
- 讓 `Start-Job` 在裝載 PowerShell 時擲回終止錯誤 (#9128)
- 為 ushort、uint、ulong 及 short 常值新增 C# 樣式類型加速器和尾碼 (#7813) (感謝 @vexx32！)
- 已為數值常值新增新的尾碼 - 請參閱 [about_Numeric_Literals][] (#7901) (感謝 @vexx32！)
- 在 SupportsShouldProcess 未設定為 'true' 時，正確地報告影響層級 (#8209) (感謝 @vexx32！)
- 修正 Web Cmdlet 中的要求字元集問題 (#8742) (感謝 @markekraus！)
- 修正 Web Cmdlet 中的預期 `100-continue` 問題 (#8679) (感謝 @markekraus！)
- 修正 Web Cmdlet 中的檔案封鎖問題 (#7676) (感謝 @Claustn！)
- 修正 `Invoke-RestMethod` 中的字碼頁剖析問題 (#8694) (感謝 @markekraus！)
- 重構 `ConvertTo-Json` 以將 JsonObject.ConvertToJson 公開為公用 API (#8682)
- 透過 -Depth 增加 `ConvertFrom-Json` 中可設定的最大深度 (#8199) (感謝 @louistio！)
- 在 `ConvertTo-Json` Cmdlet 中新增 EscapeHandling 參數 (#7775) (感謝 @iSazonov！)
- 新增 `-CustomPipeName` 至 pwsh 和 `Enter-PSHostProcess` (#8889)
- 支援在 Windows 上建立與 `New-Item` 的相對符號連結 (#8783)
- 允許 Windows 使用者在不需要提高權限的情況下，使用開發人員模式建立符號連結 (#8534)
- 支援 `Write-Information` 以接受 `$null` (#8774)
- 修正進階函式的 `Get-Help` 以包含 MAML 說明內容 (#8353)
- 修正只宣告一個參數時，-Parameter 會發生的 `Get-Help`PSTypeName 問題 (#8754) (感謝 @pougetat！)
- 修正在 ScriptBlock 上執行以取得註解說明之 `Get-Help` 的權杖計算。 (#8238) (感謝 @hubuk！)
- 變更 `Get-Help` Cmdlet 的 -Parameter 參數，讓它能接受字串陣列 (#8454) (感謝 @sethvs！)
- 解析其路徑中包含空格的呼叫器 (#8571) (感謝 @pougetat！)
- 新增在函式 'help' 中使用 `less` 來指示使用者如何結束的提示 (#7998)
- 在 `Format-Hex`Cmdlet 中新增對列舉和 char 類型的支援 (#8191) (感謝 @iSazonov！)
- 將 ShouldProcess 自 `Format-Hex` 移除 (#8178)
- 在 `Format-Hex` 中新增 Offset 和 Count 參數並重構 Cmdlet (#7877) (感謝 @iSazonov！)
- 允許在 `ConvertTo-Html` 中將 'name' 做為 'label' 的別名索引鍵，允許 'width' 項目為整數 (#8426) (感謝 @mklement0！)
- 讓以 scriptblock 為基礎的計算屬性再次於 `ConvertTo-Html` 中運作 (#8427) (感謝 @mklement0！)
- 新增 Cmdlet `Join-String` 以從管線輸入建立文字 (#7660) (感謝 @powercode！)
- 修正 `Join-String` Cmdlet FormatString 參數邏輯 (#8449) (感謝 @sethvs！)
- 將 `Clear-Host` 變更回使用 `$RAWUI` 並清除，以透過遠端運作 (#8609)
- 將 `Clear-Host` 變更為簡單的 `[console]::clear` 並自 Unix 移除明確的別名 (#8603)
- 修正 `Import-Csv` 中的 LiteralPath，以繫結至 `Get-ChildItem` 輸出 (#8277) (感謝 @iSazonov！)
- help 函式不應使用 AliasHelpInfo 的呼叫器 (#8552)
- 新增 `-UseMinimalHeader` 至 `Start-Transcript` 以將文字記錄標題最小化 (#8402) (感謝 @lukexjeremy！)
- 新增 `Enable-ExperimentalFeature` 和 `Disable-ExperimentalFeature` Cmdlet (#8318)
- 公開 **PSDiagnostics** 的所有 Cmdlet (如果 logman.exe 可用) (#8366)
- 將 **Persist** 參數自 `non-Windows` 平台上的 `New-PSDrive` 中移除 (#8291) (感謝 @lukexjeremy！)
- 新增對 `cd +` 的支援 (#7206) (感謝 @bergmeister！)
- 讓 `Set-Location -LiteralPath` 能處理名為 - 與 + 的資料夾 (#8089)
- 在指定空值或 `$null` 路徑值時，`Test-Path` 會傳回 `$false` (#8080) (感謝 @vexx32！)
- 允許即使路徑不符合任何提供者時也會傳回動態參數 (#7957)
- 支援 Unix 平台上的 `Get-PSHostProcessInfo` 和 `Enter-PSHostProcess` (#8232)
- 減少 `Get-Content` Cmdlet 中的配置數 (#8103) (感謝 @iSazonov！)
- 支援 `Add-Content` 在寫入內容時與其他工具共用讀取權限 (#8091)
- `Get/Add-Content` 以容器為目標時，會擲回改良的錯誤 (#7823) (感謝 @kvprasoon！)
- 將 `-Name`、`-NoUserOverrides` 和 `-ListAvailable` 參數新增至 `Get-Culture` Cmdlet (#7702) (感謝 @iSazonov！)
- 新增整合的屬性以完成 **Encoding** 參數。 (#7732) (感謝 @ThreeFive-O！)
- 允許在 **Encoding** 參數中使用已註冊字碼頁的數字識別碼和名稱 (#7636) (感謝 @iSazonov！)
- 修正 `Rename-Item -Path` 以包含萬用字元 (#7398) (感謝 @kwkam！)
- 使用 `Start-Transcript` 且檔案存在時，會將檔案清空而不是刪除 (#8131) (感謝 @paalbra！)
- 讓 `Add-Type` 開啟具有 **FileAccess.Read** 和 **FileShare.Read** 的原始程式碼檔案 (#7915) (感謝 @IISResetMe！)
- 針對最新的 Windows 修正 `Enter-PSSession -ContainerId` (#7883)
- 確保 `Test-ModuleManifest` 會填入 **NestedModules** 屬性 (#7859)
- 新增 `%F` 案例至 `Get-Date` -UFormat (#7630) (感謝 @britishben！)
- 修正 `Set-Service -Status Stopped` 以停止具有相依性的服務 (#5525) (感謝 @zhenggu！)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[實驗性功能]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
