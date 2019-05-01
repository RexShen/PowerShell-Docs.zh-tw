---
ms.date: 05/17/2018
keywords: powershell, core
title: PowerShell 6.0 的中斷性變更
ms.openlocfilehash: d25cf07baa11040af57f330feede44635c00c551
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085927"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6.0 的中斷性變更

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell Core 中已不再提供的功能

### <a name="powershell-workflow"></a>PowerShell 工作流程

[PowerShell 工作流程][workflow] 是 Windows PowerShell 中建置在 [Windows Workflow Foundation (WF)][workflow-foundation] 上的功能，可讓您建立適用於長時間執行或平行化工作的強固 Runbook。

由於 .NET Core 中缺少對 Windows Workflow Foundation 的支援，因此我們將不在 PowerShell Core 中繼續支援 PowerShell 工作流程。

未來，我們想要在 PowerShell 語言中啟用原生平行處理原則/並行處理，而不需要 PowerShell 工作流程。

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>自訂嵌入式管理單元

[PowerShell 嵌入式管理單元][snapin] 是 PowerShell 模組的前身，並未受到 PowerShell 社群廣泛採用。

由於支援嵌入式管理單元相當複雜，且其在社群中的使用率不高，因此我們已不再於 PowerShell Core 中支援自訂嵌入式管理單元。

目前，這會導致 Windows 和 Windows Server 中的 `ActiveDirectory` 與 `DnsClient` 模組中斷。

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 Cmdlet

由於支援兩組 WMI 型模組相當複雜，因此我們已從 PowerShell Core 中移除 WMI v1 Cmdlet：

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

建議您改用 CIM (也稱為 WMI v2) Cmdlet，這些 Cmdlet 以新的功能和重新設計的語法提供相同的功能：

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

由於使用不支援的 API，因此已從 PowerShell Core 中移除 `Microsoft.PowerShell.LocalAccounts`，直到找到更好的解決方案為止。

### <a name="-computer-cmdlets"></a>`*-Computer` Cmdlet

由於使用不支援的 API，因此已從 PowerShell Core 中移除下列 Cmdlet，直到找到更好的解決方案為止。

- Add-Computer
- Checkpoint-Computer
- Remove-Computer
- Restore-Computer

### <a name="-counter-cmdlets"></a>`*-Counter` Cmdlet

由於使用不支援的 API，因此已從 PowerShell Core 中移除 `*-Counter`，直到找到更好的解決方案為止。

### <a name="-eventlog-cmdlets"></a>`*-EventLog` Cmdlet

由於使用不支援的 API，因此已從 PowerShell Core 中移除 `*-EventLog`。 直到找到更好的解決方案。 `Get-WinEvent` 和 `Create-WinEvent` 可在 Windows 上取得並建立事件。

## <a name="enginelanguage-changes"></a>引擎/語言變更

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>將 `powershell.exe` 重新命名為 `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

為了提供使用者一個呼叫 Windows 上 PowerShell Core (而不是 Windows PowerShell) 的決定性方式，PowerShell Core 二進位檔在 Windows 上已變更為 `pwsh.exe`，而在非 Windows 平台上則變更為 `pwsh`。

該簡短名稱也與非 Windows 平台上殼層的命名一致。

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>不在輸出中插入分行符號 (資料表除外) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

先前，輸出會與主控台的寬度對齊，而在主控台的結束寬度會加上分行符號，意謂著當終端機調整大小時，不會如預期般重新製作輸出格式。 此變更不會套用至資料表，因為必須要有分行符號，才能讓資料行保持對齊。

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>針對元素類型是值類型的集合略過 Null 元素檢查 [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

如果集合的元素類型是值類型，便針對 `Mandatory` 參數及 `ValidateNotNull` 和 `ValidateNotNullOrEmpty` 屬性，略過 Null 元素檢查。

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>將 `$OutputEncoding` 變更為使用 `UTF-8 NoBOM` 編碼，而不是 ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

先前的編碼 ASCII (7 位元) 在某些情況下會造成不正確的輸出變更。 此變更是要將 `UTF-8 NoBOM` 設定為預設值，這會使用大多數工具和作業系統所支援的編碼來保留 Unicode 輸出。

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>從大多數預設別名中移除 `AllScope` [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

為了加快建立範圍的速度，已從大多數預設別名中移除 `AllScope`。 針對一些經常使用且查閱速度較快的別名則保留了 `AllScope`。

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` 和 `-Debug` 已不再覆寫 `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

先前，如果指定了 `-Verbose` 或 `-Debug`，就會覆寫 `$ErrorActionPreference` 的行為。 藉由此變更，`-Verbose` 和 `-Debug` 便不再影響 `$ErrorActionPreference` 的行為。

## <a name="cmdlet-changes"></a>Cmdlet 變更

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>未傳回任何資料時，Invoke-RestMethod 不會傳回有用的資訊。 [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

當 API 只傳回 `null`時，Invoke-RestMethod 會將其序列化為字串 `"null"`，而不是 `$null`。 此變更會修正 `Invoke-RestMethod` 中的邏輯，將有效的單一值 JSON `null` 常值序列化為 `$null`。

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>從 `*-Computer` Cmdlet 中移除 `-ComputerName` [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

由於 CoreFX 中的 RPC 遠端處理問題 (特別是在非 Windows 平台上)，以及確保 PowerShell 中有一致的遠端處理體驗，因此已從 `\*-Computer` Cmdlet 中移除 `-ComputerName` 參數。 請改用 `Invoke-Command` 來作為從遠端執行 Cmdlet 的方式。

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>從 `*-Service` Cmdlet 中移除 `-ComputerName` [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

為了鼓勵一致地使用 PSRP，已從 `*-Service` Cmdlet 中移除 `-ComputerName` 參數。

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>將 `Get-Item -LiteralPath a*b` 修正為如果 `a*b` 未實際存在便傳回錯誤 [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

先前，將萬用字元指定給 `-LiteralPath` 時，它會將其視為與 `-Path` 相同，而如果該萬用字元找不到任何檔案，它就會以無訊息模式結束。 正確的行為應該是 `-LiteralPath` 為常值，因此如果檔案不存在，它應該發生錯誤。 此變更是要將與 `-Literal` 搭配使用的萬用字元視為常值。

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>當 CSV 中有類型資訊時，`Import-Csv` 應該在匯入時套用 `PSTypeNames` [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

先前，使用 `Export-CSV` 匯出的物件如果具有以 `ConvertFrom-Csv` 匯入的 `TypeInformation`，並不會保留該類型資訊。 此變更會在 CSV 檔案中有可用的類型資訊時，將該資訊新增至 `PSTypeNames` 成員。

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`-NoTypeInformation` 應該是 `Export-Csv` 上的預設值 [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

此變更是為了處理客戶對下列預設行為的意見反應：`Export-CSV` 會包含類型資訊。

先前，此 Cmdlet 會輸出包含物件類型名稱的註解作為第一行。 此變更是要預設抑制此行為，因為大多數工具並無法理解此註解。 若要保留先前的行為，請使用 `-IncludeTypeInformation`。

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>透過未加密的連線傳送 `-Credential` 時，Web Cmdlet 應該發出警告 [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

使用 HTTP 時，內容 (包括密碼) 會以純文字方式傳送。 此變更是要預設禁止此行為，並在以不安全方式傳遞認證時傳回錯誤。 使用者可以使用 `-AllowUnencryptedAuthentication` 參數來略過此作業。

## <a name="api-changes"></a>API 變更

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>移除 `AddTypeCommandBase` 類別 [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

已從 `Add-Type` 中移除 `AddTypeCommandBase` 類別來改善效能。 此類別僅供 Add-Type Cmdlet 使用，應該不會影響到使用者。

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>將 Cmdlet 與參數 `-Encoding` 整合成屬於類型 `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

已從檔案系統提供者 Cmdlet 中移除 `-Encoding` 值 `Byte`。 現在是使用新參數 `-AsByteStream` 來指定必須使用位元組資料流作為輸入，或是指定輸出為位元組資料流。

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>為空白或 Null `-UFormat` 參數新增更好的錯誤訊息 [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

先前，將空白格式字串傳遞給 `-UFormat` 時，會顯示無用的錯誤訊息。 現已新增有較詳細描述的錯誤。

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>清除主控台程式碼 [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

已移除下列功能，因為 PowerShell Core 並不支援這些功能，而且也沒有任何新增支援的打算，它們之所以存在是為了滿足舊版 Windows PowerShell 需求：`-psconsolefile` 參數和程式碼、`-importsystemmodules` 參數和程式碼，以及字型變更程式碼。

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>已移除 `RunspaceConfiguration` 支援 [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

先前，使用 API 以程式設計方式建立 PowerShell Runspace 時，您可以使用舊版 [`RunspaceConfiguration`][runspaceconfig] 或較新的 [`InitialSessionState`][iss]。 此變更移除了對 `RunspaceConfiguration` 的支援，而僅支援 `InitialSessionState`。

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript` 將引數繫結至 `$input` 而不是 `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

不正確的參數位置導致引數被當作輸入來傳遞，而不是當成引數。

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>從 `Get-Help` 中移除不支援的 `-showwindow` 參數 [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow` 倚賴 WPF，但在 CoreCLR 上並不支援 WPF。

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>允許在 `Remove-Item` 的登錄路徑中使用 * [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

先前，將萬用字元指定給 `-LiteralPath` 時，它會將其視為與 `-Path` 相同，而如果該萬用字元找不到任何檔案，它就會以無訊息模式結束。 正確的行為應該是 `-LiteralPath` 為常值，因此如果檔案不存在，它應該發生錯誤。 此變更是要將與 `-Literal` 搭配使用的萬用字元視為常值。

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>修正 `Set-Service` 測試失敗 [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

先前，如果使用 `New-Service -StartupType foo`，會忽略 `foo`，並以某個預設啟動類型建立服務。 此變更是要針對無效的啟動類型明確擲回錯誤。

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>將 `$IsOSX` 重新命名為 `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

該命名在 PowerShell 中應該與我們的命名一致，並且與 Apple 一樣使用 macOS 而非 OSX。 不過，為了可讀性及一致性，我們會維持 Pascal 大小寫。

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>當傳遞給 -File 的指令碼無效時使得錯誤訊息變得一致、當傳遞的引數模稜兩可時提供更詳細的錯誤 [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

將 `pwsh.exe` 的結束代碼變更為符合 Unix 慣例

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>從 `Diagnostics` 模組中移除 `LocalAccount` 和 Cmdlet。 [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

由於 API 不是支援的 API，因此已將 `Diagnostics` 中的 `LocalAccounts` 模組和 `Counter` Cmdlet 移除，直到找到更好的解決方案為止。

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>Executing PowerShell script with bool parameter does not work[#4036](https://github.com/PowerShell/PowerShell/issues/4036) (以布林值參數執行 PowerShell 指令碼無法運作 #4036)

先前，使用 **powershell.exe** (現在為 **pwsh.exe**) 以 `-File` 執行 PowerShell 指令碼時，無法傳遞 `$true`/`$false` 作為參數值。 已新增將 `$true`/`$false` 作為參數剖析值的支援。 此外，也支援參數值，因為目前記載的語法無法運作。

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>從 `$PSVersionTable` 中移除 `ClrVersion` 屬性 [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`$PSVersionTable` 的 `ClrVersion` 屬性對 CoreCLR 來說沒有用，使用者不應該使用該值來判斷相容性。

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>將 `powershell.exe` 的位置參數從 `-Command` 變更為 `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

允許在非 Windows 平台上透過 Shebang 使用 PowerShell。 這意謂著在 Unix 型系統上，您可以建立會自動叫用 PowerShell 的指令碼可執行檔，而無須明確叫用 `pwsh`。 這也意謂著您現在可以執行 `powershell foo.ps1` 或 `powershell fooScript` 這類命令，而無須指定 `-File`。 不過，此變更現在會要求您在嘗試執行 `powershell.exe Get-Command` 這類命令時，明確指定 `-c` 或 `-Command`。

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>實作 Unicode 逸出剖析 [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u####`` 或 `` `u{####}`` 會轉換成對應的 Unicode 字元。 若要輸出常值 `` `u``，請將反單引號逸出：``` ``u```。

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>在非 Windows 平台上將 `New-ModuleManifest` 編碼變更為 `UTF8NoBOM` [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

先前，`New-ModuleManifest` 會以 UTF-16 建立含有 BOM 的 psd1 資訊清單，而導致對 Linux 工具造成問題。 這個中斷性變更會在非 Windows 平台中，將 `New-ModuleManifest` 的編碼變更為 UTF (無 BOM)。

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>防止 `Get-ChildItem` 遞迴到符號連結中 (#1875)。 [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

此變更會讓 `Get-ChildItem`與 Unix `ls -r` 及 Windows `dir /s` 原生命令更趨一致。 與所提到的命令相同，此 Cmdlet 會顯示在遞迴期間所找到目錄的符號連結，但不會遞迴到這些符號連結中。

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>將 `Get-Content -Delimiter` 修正為不在傳回的行中包含分隔符號 [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

先前，使用 `Get-Content -Delimiter` 時的輸出既不一致也不便利，因為需要進行進一步的資料處理，才能移除分隔符號。 此變更會將所傳回行中的分隔符號移除。

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>實作 C# 中的 Format-Hex [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

`-Raw` 參數現在是一個「無作業」(亦即不執行任何操作)。 今後，所有的輸出都會以真實的數字表示顯示，其中包括其類型的所有位元組 (這是在此變更之前，`-Raw` 參數所正式執行的工作)。

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>作為預設殼層的 PowerShell 並不與指令碼命令搭配運作 [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

在 Unix 上，殼層接受互動式殼層的 `-i` 是一個慣例，許多工具都預期此行為 (例如 `script`，以及將 PowerShell 設定為預設殼層時) 而會使用 `-i` 參數來呼叫殼層。 此變更之所以為中斷性變更，在於 `-i` 先前可用來作為用以比對 `-inputformat` 的簡寫，但現在則必須使用 `-in`。

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-ComputerInfo 屬性名稱中的錯字修正 [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber` 先前拼字錯誤導致變成 `BiosSeralNumber`，現已變更為正確的拼字。

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>新增 `Get-StringHash` 和 `Get-FileHash` Cmdlet [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

此變更是因為 CoreFX 不支援某些雜湊演算法，所以已不再提供這些演算法：

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>在傳遞 $null 會傳回所有物件而非錯誤的 `Get-*` Cmdlet 上新增驗證 [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

將 `$null` 傳遞給下列任何一個現在都會擲回錯誤：

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>在 `Import-Csv` 中新增對 W3C 延伸記錄檔格式的支援 [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

先前，無法使用 `Import-Csv` Cmdlet 來直接匯入 W3C 延伸記錄檔格式的記錄檔，而需要採取額外的動作。 有了此變更之後，便可支援 W3C 延伸記錄檔格式。

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>PS 函式中的 `ValueFromRemainingArguments` 參數繫結問題 [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

`ValueFromRemainingArguments` 現在會以陣列的形式傳回值，而不是傳回本身為陣列的單一值。

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>從 `$PSVersionTable` 中移除 `BuildVersion` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

從 `$PSVersionTable` 中移除 `BuildVersion` 屬性。 此屬性已繫結至 Windows 組建版本。 相反地，建議您使用 `GitCommitId` 擷取 PowerShell Core 的確切組建版本。

### <a name="changes-to-web-cmdlets"></a>Web Cmdlet 的變更

Web Cmdlet 的基礎 .NET API 已變更為 `System.Net.Http.HttpClient`。 此變更提供許多優點。 不過，此變更再加上缺乏與 Internet Explorer 的互通性，已在 `Invoke-WebRequest` 和 `Invoke-RestMethod` 內造成數個中斷性變更。

- `Invoke-WebRequest` 現在僅支援基本 HTML 剖析。 `Invoke-WebRequest` 一律會傳回 `BasicHtmlWebResponseObject` 物件。 `ParsedHtml` 和 `Forms` 屬性已被移除。
- `BasicHtmlWebResponseObject.Headers` 值現在是 `String[]`，而不是 `String`。
- `BasicHtmlWebResponseObject.BaseResponse` 現在是 `System.Net.Http.HttpResponseMessage` 物件。
- Web Cmdlet 例外狀況上的 `Response` 屬性現在是 `System.Net.Http.HttpResponseMessage` 物件。
- 嚴格 RFC 標頭剖析現在是 `-Headers` 和 `-UserAgent` 參數的預設值。 您可以使用 `-SkipHeaderValidation` 來略過此作業。
- 已不再支援 `file://` 和 `ftp://` URI 配置。
- 已不再接受 `System.Net.ServicePointManager` 設定。
- macOS 上目前未提供任何憑證型驗證。
- 透過 `http://` URI 使用 `-Credential` 將會造成錯誤。 請使用 `https://` URI 或提供 `-AllowUnencryptedAuthentication` 參數來抑制此錯誤。
- 當重新導向次數超過提供的限制時，`-MaximumRedirection` 現在會產生終止錯誤，而不是傳回最後一個重新導向的結果。
