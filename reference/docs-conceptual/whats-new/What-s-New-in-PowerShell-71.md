---
title: PowerShell 7.1 的新功能
description: PowerShell 7.1 中發行的新功能與變更
ms.date: 11/11/2020
ms.openlocfilehash: 5596d3ca69f5d8ea47f01ff0915e6fa33c1c463f
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625715"
---
# <a name="whats-new-in-powershell-71"></a>PowerShell 7.1 的新功能

PowerShell 7.1 為開放原始碼、跨平台 (Windows、macOS 與 Linux) 的 PowerShell 版本，建置來管理異質環境與混合式雲端。

依據 PowerShell 7.0 所建立的基礎，我們將目標專注在社群問題上，並包含了數個改進與修正。 我們致力於確保 PowerShell 能持續成為穩定且高效能的平台。

PowerShell 7.1 也包含 PSReadLine 2.1.0。 此版本包含預測性 IntelliSense。 如需預測性 IntelliSense 功能的詳細資訊，請參閱 PowerShell 部落格中的[公告](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) \(英文\)。

## <a name="where-can-i-install-powershell"></a>我可以在哪裡安裝 PowerShell？

<!-- TODO: Update list of OS below - make sure this is consistent across all docs -->

PowerShell 7.1 目前支援下列 x64 作業系統，包括：

- Windows 8.1/10 (包含 ARM64)
- Windows Server 2012 R2、2016、2019 與半年通道 (SAC)
- Ubuntu 16.04/18.04/20.04 (包含 ARM64)
- Ubuntu 19.10 (透過 Snap 套件)
- Debian 9/10
- CentOS 與 RHEL 7/8
- Fedora 32
- Alpine 3.11+ (包含 ARM64)
- macOS 10.13+

我們也針對下列作業系統提供社群支援：

- Arch Linux
- Raspbian Linux
- Kali Linux

如需支援的作業系統與支援生命週期的最新詳細資訊，請參閱 [PowerShell 支援生命週期](/powershell/scripting/powershell-support-lifecycle)

PowerShell 7.1 已經發佈至 Microsoft Store。 您可以在 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 網站上或 Windows 的 [Store] 應用程式中找到該 PowerShell 版本。

Microsoft Store 套件的優點：

- 直接內建於 Windows 10 的自動更新
- 與其他軟體散發機制 (例如 Intune 與 SCCM) 的整合

> [!NOTE]
> 儲存在 `$PSHOME` 中的所有系統層級組態設定都無法修改。 這包含 WSMAN 設定。 這會防止遠端工作階段連線到 PowerShell 的 Store 型安裝。 支援使用者層級設定與 SSH 遠端功能。

請查看適用於您慣用作業系統的安裝指示：

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

此外，PowerShell 7.1 支援 Debian、Ubuntu 與 ARM64 Alpine Linux 的 ARM32 和 ARM64 變體。

雖然尚未正式支援，但該社群也會提供適用於 [Arch](https://aur.archlinux.org/packages/powershell/) 和 Kali Linux 的套件。

> [!NOTE]
> Debian 10+、CentOS 8+、Ubuntu 20.04、Alpine 與 Arm 目前不支援 WinRM 遠端處理。 如需設定 SSH 型遠端處理的詳細資訊，請參閱[透過 SSH 的 PowerShell 遠端處理](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)。

## <a name="running-powershell-71"></a>執行 PowerShell 7.1

PowerShell 7.1 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。
PowerShell 7.1 是會取代 PowerShell 6.x 或 PowerShell 7.0 的就地升級。

- PowerShell 7.1 會安裝到 `%programfiles%\PowerShell\7`
- 系統會在 `$env:PATH` 中新增 `%programfiles%\PowerShell\7` 資料夾

PowerShell 7.1 安裝程式套件會升級舊版的 PowerShell Core 6.x：

- Windows 上的 PowerShell Core 6.x：`%programfiles%\PowerShell\6` 已由 `%programfiles%\PowerShell\7` 取代
- Linux：`/opt/microsoft/powershell/6` 已由 `/opt/microsoft/powershell/7` 取代
- macOS：`/usr/local/microsoft/powershell/6` 已由 `/usr/local/microsoft/powershell/7` 取代

> [!NOTE]
> 在 Windows PowerShell 中，啟動 PowerShell 的可執行檔名稱為 `powershell.exe`。 在版本 6 和更新版本中，已將這個可執行檔變更為支援並存執行。 啟動 PowerShell 7.1 的新可執行檔為 `pwsh.exe`。 預覽版將以 `pwsh-preview` (而不是 `pwsh`) 就地保留於 7-preview 目錄下。

## <a name="breaking-changes-and-improvements"></a>中斷性變更和改進

如需變更與改善的最新資訊，請參閱 GitHub 存放庫中的[變更記錄](https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG) \(英文\)。

### <a name="breaking-changes"></a>重大變更

<!-- TODO: Add descriptions for each breaking change - this might need to be a separate article that we link to -->

- 修正 `$?` 以使其在原生命令寫入 `stderr` 時不會是 `$false` (#13395)
- 將 `Get-Date` 上的 `-FromUnixTime` 重新命名為 `-UnixTimeSeconds` 以允許 Unix 時間輸入 (#13084) (感謝 @aetos382！)
- 使 `$ErrorActionPreference` 不會影響原生命令的 `stderr` 輸出 (#13361)
- 允許明確指定具名參數以取代來自雜湊表展開的相同參數 (#13162)
- 使 `-Qualifier` 切換參數針對 `Split-Path` 為非位置 (#12960) (感謝 @yecril71pl！)
- 在未加以指定的情況下，針對 `Start-Process` 將工作目錄解析為常值路徑 (#11946) (感謝 @NoMoreFood！)
- 使 Web Cmdlet 中 `-OutFile` 參數的運作方式與 `-LiteralPath` 相同 (#11701) (感謝 @iSazonov！)
- 修正 `BigInteger` 數值常值的字串參數繫結 (#11634) (感謝 @vexx32！)
- 在 Windows 上，`Start-Process` 會透過使用 `-UseNewEnvironment` 建立新的預設處理環境，以搭配來自目前工作階段的所有環境變數建立處理環境 (#10830) (感謝 @iSazonov！)
- 將 ScriptBlock 轉換成委派時，不要將傳回結果包裝成 `PSObject` (#10619)
- 針對 `-replace` 運算子使用不因文化特性而異的字串轉換 (#10954) (感謝 @iSazonov！)

### <a name="experimental-features"></a>實驗性功能

如需實驗性功能的詳細資訊，請參閱[使用實驗性功能](../learn/experimental-features.md)。

- 將 `PSNullConditionalOperators` 功能移出實驗性階段 (#13529)
- 將 `PSUnixFileStat` 功能移出實驗性階段
- 將 `-Runspace` 參數新增到所有 `*-PSBreakpoint` Cmdlet (#10492) (感謝 @KirkMunro！)
- 新增 `PSNativePSPathResolution` 以支援將 `PSPath` 傳遞到原生命令 (#12386)
- 針對 `-replace` 運算子使用不因文化特性而異的字串轉換 (#10954) (感謝 @iSazonov！)
- 新增 `PSSubsystemPluginModel` 以支援未來的預測性 IntelliSense 外掛程式

### <a name="general-cmdlet-updates-and-fixes"></a>一般 Cmdlet 更新與修正

- 在 `ConvertTo-Json` 超過 `-Depth` 值的情況下發出警告 (#13692)
- 修正 Windows 上例外狀況訊息只會包含 ``"`n"`` 的情況 (#13684)
- 將 `CONOUT$` 與 `CONIN$` 辨識為保留的裝置名稱 (#13508) (感謝 @davidreis97！)
- 針對寫入錯誤時的互動式進階函式修正 `ConciseView` (#13623)
- 在 Web Cmdlet 中新增對 `TLS` 1.3 的支援 (#13409) (感謝 @iSazonov！)
- 針對 `CommandLineParser` 中的 `args` 新增 Null 檢查 (#13451) (感謝 @iSazonov！)
- 處理 Microsoft Store 應用程式的重新分析點 (#13481) (感謝 @iSazonov！)
- 針對容器使用 PowerShell Direct 時，在屬性針對 `ObRoot` 不存在的情況下使用欄位 (#13375) (感謝 @hemisphera！)
- 隱藏 `UTF-7` 過時警告 (#13484)
- 避免 `Compiler.cs` 中 `IEnumerable<Expression>` 執行個體的多個列舉 (#13491)
- 變更 `Add-Type -OutputType` 以不支援 `ConsoleApplication` 與 `WindowsApplication` (#13440)
- 在將 `UTF-7` 指定為編碼時建立警告 (#13430)
- 修正新符號連結遺失目標的錯誤訊息 (#13085) (感謝 @yecril71pl！)
- 使公用 `ConsoleHost` API 中的 `args` 參數為不可為 Null (#13429)
- 新增 `CancellationTokenSource` 的遺失處置 (#13420) (感謝 @Youssef1313！)
- 修正 `Get-Help` 無法正確顯示參數是否支援萬用字元的問題 (#13353) (感謝 @ThomasNieto！)
- 更新 `-InputFormat` 參數的 `pwsh` 說明 (#13355) (感謝 @sethvs！)
- 針對從 Roslyn 複製的檔案宣告 MIT 授權 (#13305) (感謝 @xtqqczze！)
- 改善 `BigInteger` 轉換行為 (#12629) (感謝 @vexx32！)
- 修正 `Get-Acl -LiteralPath "HKLM:Software\Classes\*"` 行為 (#13107) (感謝 @Shriram0908！)
- 將 `DefaultVisit` 方法新增到訪客介面與類別 (#13258)
- 修正 `pwsh` 的衝突縮寫參數 `-s` (STA) (#13262) (感謝 @iSazonov！)
- 變更 `Read-Host -MaskInput` 以使用現有的 `SecureString` 路徑，但以純文字形式傳回 (#13256)
- 移除 `ComEnumerator`，因為 .NET 5.0 現已支援使用 `IEnumerator` 的 COM 物件 (#13259)
- 在未定義 'HOME' 環境變數的情況下，於 Runspace 啟動時使用暫時個人路徑 (#13239)
- 修正 `Invoke-Command` 以偵測相同歷程記錄輸入的遞迴呼叫 (#13197)
- 將 `pwsh` 可執行檔 `-inputformat` 參數前置詞 `-in` 變更為 `-inp` 以修正與 `-interactive` 的衝突 (#13205) (感謝 @iSazonov！)
- 在分析檔案的安全性區域時處理 WSL 檔案系統路徑 (#13120)
- 在 `Split-Path` 中使其他參數為必要參數 (#13150) (感謝 @kvprasoon！)
- 適用於 PowerShell 7 的新 Fluent Design 圖示 (#13100) (感謝 @sarthakmalik！)
- 修正 `Move-Item` 以在 Unix 上支援跨掛接移動 (#13044)
- 修正 `CommandSearcher.GetNextCmdlet` 中的 `NullReferenceException` (#12659) (感謝 @powercode！)
- 防止在測試攔截作用中的情況下於 Unix 電腦 Cmdlet 中使用 `NullReferenceException` (#12651) (感謝 @vexx32！)
- 修正 `Select-Object` 中的問題，其中 `Hashtable` 成員 (例如 `Keys`) 會無法搭配 `-Property` 或 `-ExpandProperty` 使用 (#11097) (感謝 @vexx32！)
- 修正 pwsh 的衝突縮寫參數 `-w` (#12945)
- 將 `CimCmdlet` 資源檔案重新命名 (#12955) (感謝 @iSazonov！)
- 移除在 `ConciseView` 中使用 `Test-Path` 的能力 (#12778)
- 將 `default` 參數陳述式條件子句標記為關鍵字 (#10487) (感謝 @msftrncs！)
- 將 `SchemaFile` 參數新增至 `Test-Json` Cmdlet (#11934) (感謝 @beatcracker！)
- 帶回憑證提供者參數 (#10622) (感謝 @iSazonov！)
- 修正 `New-Item` 以針對相對路徑目標建立符號連結 (#12797) (感謝 @iSazonov！)
- 將 `CommandLine` 屬性新增到 Process (#12288) (感謝 @iSazonov！)
- 將 `-MaskInput` 參數新增到 `Read-Host` (#10908) (感謝 @davinci26！)
- 變更 `CimCmdlets` 以使用 `AliasAttribute` (#12617) (感謝 @thlac！)
- 修正 ParameterBinderBase 格式字串中不正確的索引 (#12630) (感謝 @powercode！)
- 複製 `Command.Clone()` 中的 `CommandInfo` 屬性 (#12301) (感謝 @TylerLeonhardt！)
- 在指定 `-ExcludeDifferent` 時套用 `Compare-Object` 中的 `-IncludeEqual` (#12317) (感謝 @davidseibel！)
- 變更 `Get-FileHash` 以在寫入輸出之前關閉檔案控制代碼 (#12474) (感謝 @HumanEquivalentUnit！)
- 修正 `-replace` 運算子中不一致的例外狀況訊息 (#12388) (感謝 @jackdcasey！)
- 修正 `WinCompat` 模組載入以將 PowerShell 7 模組視為具有較高的優先順序 (#12269)
- 實作 `ForEach-Object -Parallel` Runspace 重複使用 (#12122)
- 修正 `Get-Service` 以不要在對集合進行列舉時加以修改 (#11851) (感謝 @NextTurn！)
- 在 PowerShell 結束時清除 IPC 具名管道 (#12187)
- 修正 Web Cmdlet 中的 `<img />` 偵測 RegEx (#12099) (感謝 @vexx32！)
- 允許具有適當類型尾碼的較短帶正負號十六進位常值 (#11844) (感謝 @vexx32！)
- 更新 Windows 上 `Start-Process` Cmdlet 的 `UseNewEnvironment` 參數行為 (#10830) (感謝 @iSazonov！)
- 將 `-Shuffle` 參數新增至 `Get-Random` 命令 (#11093) (感謝 @eugenesmlv！)
- 使 `GetWindowsPowerShellModulePath` 與多個 PS 安裝相容 (#12280)
- 修正 `Start-Job` 使其能在未將 Windows PowerShell 註冊為預設殼層的系統上運作 (#12296)
- 將別名與 `-Syntax` 指定為 `Get-Command` 會傳回別名命令語法 (#10784) (感謝 @ChrisLGardner！)
- 使 CSV Cmdlet 能在使用 `-AsNeeded` 且有不完整資料列時運作 (#12281) (感謝 @iSazonov！)
- 在本機叫用中，針對 `Get-FormatData` 不需要 `-PowerShellVersion 5.1` 便能查看所有格式資料。 (#11270) (感謝 @mklement0！)
- 新增對位元組由大到小 `UTF-32` 的支援 (#11947) (感謝 @NoMoreFood！)
- 修正 `ForEach-Object -Parallel` 中會洩漏 PowerShell 物件處置的可能競爭 (#12227)
- 將 `-FromUnixTime` 新增到 `Get-Date` 以允許 Unix 時間輸入 (#12179) (感謝 @jackdcasey！)
- 變更預設進度前景與背景色彩以提供改善的對比 (#11455) (感謝 @rkeithhill！)
- 修正目前磁碟機無法使用時的 `foreach -parallel` (#12197)
- 將 `ScriptBlock` 轉換成 `delegate` 時，不要將傳回結果包裝成 `PSObject` (#10619)
- 不要在 `Test-Connection -Quiet` 上寫入 DNS 解析錯誤 (#12204) (感謝 @vexx32！)
- 使用專用執行緒來針對跨處理序作業從子處理序讀取重新導向的輸出與錯誤資料流 (#11713)
- 修正繫結器程式碼中的運算子喜好設定順序問題 (#12075) (感謝 @DamirAinullin！)
- 修正繫結 `ActionPreference` 類型的通用參數時的 `NullReferenceException` (#12124)
- 修正還原序列化之 `MatchInfo` 的預設格式 (#11728) (感謝 @iSazonov！)
- 在 `Invoke-RestMethod` 中使用非同步資料流 (#11095) (感謝 @iSazonov！)
- 解決 `Get-Content -Tail` 中的 UTF-8 偵測 (#11899) (感謝 @NoMoreFood！)
- 處理 `Get-FileHash` 中的 `IOException` (#11944) (感謝 @iSazonov！)
- 將資源字串中的 `PowerShell Core` 變更為 `PowerShell` (#11928) (感謝 @alexandair！)
- 帶回 `PSHostProcessInfo` 中的 `MainWindowTitle` (#11885) (感謝 @iSazonov！)
- 對 Windows 相容性的其他次要更新 (#11980)
- 修正 `ConciseView` 以使用 `[Environment]::NewLine` 分割 `PositionMessage` (#12010)
- 移除互動式工作階段的網路躍點限制 (#11920)
- 修正 `SuspendStoppingPipeline()` 與 `RestoreStoppingPipeline()` 中的 `NullReferenceException` (#11870) (感謝 @iSazonov！)
- 在未提供 `FormatViewDefinition` `InstanceId` 之 GUID 的情況下加以產生 (#11896)
- 修正 `ConciseView` 問題，其中錯誤訊息的寬度會超過視窗寬度且沒有空白 (#11880)
- 允許跨平台的 `CAPI-compatible` 遠端金鑰交換 (#11185) (感謝 @silijon！)
- 修正錯誤訊息 (#11862) (感謝 @NextTurn！)
- 修正 `ConciseView` 以處理沒有主控台可取得寬度的情況 (#11784)
- 更新 `CmsCommands` 以使用 Store 而非憑證提供者 (#11643) (感謝 @mikeTWC1984！)
- 讓 `pwsh` 可以在無法使用 `mpr.dll` 與 STA 的 Windows 系統上運作 (#11748)
- 針對 `Un*x` 與 macOS 重構並實作 `Restart-Computer` (#11319)
- 針對 Linux 與 macOS 新增 `Stop-Computer` 的實作 (#11151)
- 修正 `help` 函式以在使用 `less` 之前先檢查其是否可供使用 (#11737)
- 更新 `certificate_format_ps1.xml` 中的 `PSPath` (#11603) (感謝 @xtqqczze！)
- 變更規則運算式以符合 Link 標頭中沒有引號的關聯類型 (#11711) (感謝 @Marusyk！)
- 修正符號連結刪除期間的錯誤訊息 (#11331)
- 只將自訂的 `Selected.*` 類型新增到 `Select-Object` 中的 `PSCustomObject` 一次 (#11548) (感謝 @iSazonov！)
- 將 `-AsUTC` 新增到 `Get-Date` Cmdlet (#11611)
- 修正 `Format-Hex` 中的布林值分組行為 (#11587) (感謝 @vexx32！)
- 使 `Test-Connection` 針對傳送 Ping 要求一律會使用預設的同步處理內容 (#11517)
- 修正啟動錯誤訊息 (#11473) (感謝 @iSazonov！)
- 忽略 Web Cmdlet 中具有 Null 值的標頭 (#11424) (感謝 @iSazonov！)
- 重新新增針對 `Invoke-Command` 作業處置的檢查。 (#11388)
- 還原「更新格式器以在內容為空的時不寫入新行 (#11193)」(#11342) (感謝 @iSazonov！)
- 允許 `CompleteInput` 在 `AST` 或 Script 具有相符的函式定義時，傳回來自 `ArgumentCompleter` 的結果 (#10574) (感謝 @M1kep！)
- 更新格式器以在內容為空的時不寫入新行 (#11193)

<!-- TODO: add more general contributor thank you listing -->
