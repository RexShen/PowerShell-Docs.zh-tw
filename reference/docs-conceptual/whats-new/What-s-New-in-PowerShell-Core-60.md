# <a name="whats-new-in-powershell-core-60"></a>PowerShell Core 6.0 的新功能

[PowerShell Core 6.0][github] 是新的 PowerShell 版本，其為跨平台 (Windows、macOS 和 Linux)、開放原始碼，並針對異質環境和混合式雲端所建置。

## <a name="moved-from-net-framework-to-net-core"></a>從 .NET Framework 移至 .NET Core

PowerShell Core 使用 [.NET Core 2.0][] 作為其執行階段。
.NET Core 2.0 可讓 PowerShell Core 作用於多個平台 (Windows、macOS 和 Linux)。
PowerShell Core 也會公開 .NET Core 2.0 所提供的 API 集，以用於 PowerShell Cmdlet 和指令碼中。

Windows PowerShell 已使用 .NET Framework 執行階段來裝載 PowerShell 引擎。
這表示 Windows PowerShell 會公開 .NET Framework 所提供的 API 集。

.NET Core 與 .NET Framework 之間共用的 API 定義為 [.NET Standard][] 的一部分。

如需這如何影響 PowerShell Core 與 Windows PowerShell 之間模組/指令碼相容性的詳細資訊，請參閱[與 Windows PowerShell 的回溯相容性](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>macOS 和 Linux 支援

PowerShell 現在正式支援 macOS 和 Linux，包含：

- Windows 7、8.1 和 10
- Windows Server 2008 R2、2012 R2、2016
- [Windows Server 半年通道][semi-annual]
- Ubuntu 14.04、16.04 和 17.04
- Debian 8.7+ 和 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25、26
- macOS 10.12+

我們的社群也提供下列平台的套件，但未正式進行支援：

- Arch Linux
- Kali Linux
- AppImage (作用於多個 Linux 平台)

我們也會有下列平台的實驗性 (不支援) 版本：

- ARM32/ARM64 上的 Windows
- Raspbian (Stretch)

已對 PowerShell Core 6.0 進行許多變更，讓它在非 Windows 系統上運作地更好。
其中有些是也會影響 Windows 的最新變更。
其他只會出現或適用於 PowerShell Core 的非 Windows 安裝。

- 已在 Unix 平台上新增原生命令萬用字元支援。
- `more` 功能會使用 Linux `$PAGER`，且預設為 `less`。
  這表示，您現在可以搭配使用萬用字元與原生二進位檔/命令 (例如，`ls *.txt`)。 (#3463)
- 在處理原生命令引數時自動逸出結尾反斜線。 (#4965)
- 因為目前不支援 Script 簽署，所以在非 Windows 平台上執行 PowerShell 時會忽略 `-ExecutionPolicy` 參數。 (#3481)
- 已修正 ConsoleHost，可在 Unix 平台上使用 `NoEcho`。 (#3801)
- 已修正 `Get-Help`，支援 Unix 平台上的不區分大小寫模式比對。 (#3852)
- `powershell` 手冊頁已新增至套件

### <a name="logging"></a>記錄

在 macOS 上，PowerShell 使用原生 `os_log` API 來登入 Apple 的[統一記錄系統][os_log]。
在 Linux 上，PowerShell 使用 [Syslog][]，這是一種通用記錄解決方案。

### <a name="filesystem"></a>Filesystem

已在 macOS 和 Linux 上進行許多變更，可支援 Windows 上傳統不支援的檔案名稱字元：

- 提供給 Cmdlet 的路徑現在不區分斜線 (/ 和 \ 都是作為目錄分隔符號)
- 現在預設會支援並使用 XDG 基底目錄規格：
  - Linux/macOS 設定檔路徑位於 `~/.config/powershell/profile.ps1`
  - 歷程記錄儲存路徑位於 `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`
  - 使用者模組路徑位於 `~/.local/share/powershell/Modules`
- 支援 Unix 上包含冒號字元的檔案和資料夾名稱。 (#4959)
- 支援包含逗號的指令碼名稱或完整路徑。 (#4136) (感謝 @TimCurwick！)
- 偵測何時使用 `-LiteralPath` 來抑制導覽 Cmdlet 的萬用字元展開。 (#5038)
- 已更新 `Get-ChildItem`，使其運作更像 *nix `ls -R` 和 Windows `DIR /S` 原生命令。
  `Get-ChildItem` 現在會傳回在遞迴式搜尋期間發生的符號連結，而且不會搜尋這些連結設為目標的目錄。 (#3780)

### <a name="case-sensitivity"></a>區分大小寫

Linux 和 macOS 是要區分大小寫，而 Windows 不區分大小寫，同時保留大小寫。
一般情況下，PowerShell 不區分大小寫。

例如，在 macOS 和 Linux 上，環境變數區分大小寫，因此已標準化 `PSModulePath` 環境變數的大小寫。 (#3255) `Import-Module` 在使用檔案路徑來決定模組名稱時不區分大小寫。 (#5097)

## <a name="support-for-side-by-side-installations"></a>並存安裝支援

分別從 Windows PowerShell 安裝、設定和執行 PowerShell Core。
PowerShell Core 具有「可攜式」ZIP 套件。
使用 ZIP 套件，即可在磁碟的任何位置安裝任意數目的版本，包含採用 PowerShell 作為相依性之應用程式的本機版本。
並存安裝可以更輕鬆地測試新的 PowerShell 版本，並在一段時間移轉現有指令碼。
因為指令碼可以固定到其所需的特定版本，所以並存也會啟用回溯相容性。

> [!NOTE]
> 根據預設，Windows 上以 MSI 為基礎的安裝程式會執行就地更新安裝。
>

## <a name="renamed-powershellexe-to-pwshexe"></a>已將 `powershell(.exe)` 重新命名為 `pwsh(.exe)`

已將 PowerShell Core 的二進位檔名稱從 `powershell(.exe)` 變更為 `pwsh(.exe)`。
這項變更提供決定性方式，讓使用者在電腦上執行 PowerShell Core，以支援並存 Windows PowerShell 和 PowerShell Core 安裝。
`pwsh` 也會較短，而且更容易鍵入。

其他從 `powershell.exe` 到 `pwsh(.exe)` 的變更：

- 已將第一個位置參數從 `-Command` 變更為 `-File`。
  這項變更會修正 PowerShell 指令碼中 `#!` 的使用方式 (也稱為狀況)，而 PowerShell 指令碼要在非 Windows 平台上從非 PowerShell 殼層執行。
  這也表示您可以執行 `pwsh foo.ps1` 或 `pwsh fooScript` 這類命令，但未指定 `-File`。
  不過，這項變更需要您在嘗試執行 `pwsh.exe -Command Get-Command` 這類命令時明確指定 `-c` 或 `-Command`。 (#4019)
- PowerShell Core 接受 `-i` (或 `-Interactive`) 參數，指出互動式殼層。 (#3558) 這可讓 PowerShell 用作 Unix 平台上的預設殼層。
- 已從 `pwsh.exe` 移除 `-importsystemmodules` 和 `-psconsoleFile` 參數。 (#4995)
- 已變更 `pwsh -version` 以及 `pwsh.exe` 的內建說明，以配合其他原生工具。 (#4958 & #4931) (感謝 @iSazonov)
- `-File` 和 `-Command` 的引數錯誤訊息無效，而且結束碼符合 Unix 標準 (#4573)
- 已在 Windows 上新增 `-WindowStyle` 參數。 (#4573) 同樣地，非 Windows 平台上以套件為基礎的安裝更新就是就地更新。

## <a name="backwards-compatibility-with-windows-powershell"></a>與 Windows PowerShell 的回溯相容性

PowerShell Core 的目標是盡可能保持與 Windows PowerShell 相容。
PowerShell Core 會使用 [.NET Standard][] 2.0，以提供與現有 .NET 組件的二進位相容性。
許多 PowerShell 模組都與這些組件相依 (通常是 DLL)，因此 .NET Standard 可讓它們繼續使用 .NET Core。
PowerShell Core 也包含查看已知資料夾 (例如，全域組件快取通常在磁碟上的位置) 的啟發學習法，以尋找 .NET Framework DLL 相依性。

您可以在 [.NET 部落格][]、此 [YouTube][] 影片以及 GitHub 上的這個[常見問題集][]中，深入了解 .NET Standard。

已致力於確定 PowerShell 語言和「內建」模組 (例如 `Microsoft.PowerShell.Management`、`Microsoft.PowerShell.Utility` 等) 的運作方式與在 Windows PowerShell 中一樣。
在許多情況下，於社群的協助下，我們已將新功能和 Bug 修正新增至這些 Cmdlet。
在某些情況下，因為基礎.NET 層中遺失相依性，所以功能已移除或無法使用。

隨附為 Windows 一部分的大部分模組 (例如，`DnsClient`、`Hyper-V`、`NetTCPIP`、`Storage` 等) 以及包含 Azure 和 Office 的其他 Microsoft 產品都尚未「明確地」移植到 .NET Core。
PowerShell 小組正在與這些產品小組和團隊合作，驗證其現有模組並將其移植到 PowerShell Core。
使用 .NET Standard 和 [CDXML][]，其中許多傳統 Windows PowerShell 模組似乎作用於 PowerShell Core，但尚未正式驗證而且未正式支援。

安裝 [`WindowsPSModulePath`][windowspsmodulepath] 模組，即可將 Windows PowerShell `PSModulePath` 附加至 PowerShell Core `PSModulePath`，以使用 Windows PowerShell 模組。

首先，從 PowerShell 資源庫安裝 `WindowsPSModulePath` 模組：

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin 
Install-Module WindowsPSModulePath -Force
```

安裝此模組之後，請執行 `Add-WindowsPSModulePath` Cmdlet，以將 Windows PowerShell `PSModulePath` 新增至 PowerShell Core：

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker 支援

PowerShell Core 支援所有支援之主要平台 (包含多個 Linux 發行版本、Windows Server Core 和 Nano Server) 的 Docker 容器。

如需完整清單，請參閱 [`microsoft/powershell`Docker Hub][docker-hub] 之上的標記。
如需 Docker 和 PowerShell Core 的詳細資訊，請參閱 GitHub 上的 [Docker][]。

## <a name="ssh-based-powershell-remoting"></a>以 SSH 為基礎的 PowerShell 遠端

除了傳統以 WinRM 為基礎的 PSRP 之外，PowerShell 遠端通訊協定 (PSRP) 現在還可以與 Secure Shell (SSH) 通訊協定搭配運作。

這表示您可以使用 `Enter-PSSession` 和 `New-PSSession` 這類 Cmdlet，並使用 SSH 進行驗證。
您只需要向以 OpenSSH 為基礎的 SSH 伺服器註冊 PowerShell 作為子系統，而且您可以使用具有傳統 `PSSession` 語意且以現有 SSH 為基礎的驗證機制 (例如密碼或私密金鑰)。

如需設定和使用以 SSH 為基礎的遠端的詳細資訊，請參閱[透過 SSH 的 PowerShell 遠端][ssh-remoting]。

## <a name="default-encoding-is-utf-8-without-a-bom"></a>預設編碼是沒有 BOM 的 UTF-8

過去，`Get-Content`、`Set-Content` 這類 Windows PowerShell Cmdlet 已使用不同編碼，例如 ASCII 和 UTF-16。
編碼預設值中的變化已在混合使用 Cmdlet 但未指定編碼時產生問題。

非 Windows 平台傳統上會使用 UTF-8，但未使用位元組順序標記 (BOM) 作為文字檔的預設編碼。
其他 Windows 應用程式和工具不會使用 UTF-16，而是使用無 BOM 的 UTF-8 編碼。
PowerShell Core 會變更預設編碼，以符合更廣泛的生態系統。

這表示，使用 `-Encoding` 參數的所有內建 Cmdlet 預設都會使用 `UTF8NoBOM` 值。
這項變更會影響下列 Cmdlet：

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- New-ModuleManifest
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

這些 Cmdlet 也已進行更新，讓 `-Encoding` 參數普遍接受 `System.Text.Encoding`。

`$OutputEncoding` 的預設值也已變更為 UTF-8。

最佳做法是您應該使用 `-Encoding` 參數明確設定指令碼中編碼，跨平台產生決定性行為。

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>支援含 & 符號 (`&`) 之管線的背景 (#3360)

將 `&` 置於管線結尾，會將管線執行為 PowerShell 作業。
管線在背景時，會傳回作業物件。
管線執行為作業之後，即可使用所有標準 `*-Job` Cmdlet 來管理作業。
管線中所使用的變數 (忽略處理序特定變數) 會自動複製至作業，因此 `Copy-Item $foo $bar &` 就會運作。
作業也會在目前目錄中執行，而不是使用者的主目錄。
如需 PowerShell 作業的詳細資訊，請參閱 [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs)。

## <a name="semantic-versioning"></a>語意化版本控制系統

- 讓 `SemanticVersion` 與 `SemVer 2.0` 相容。 (#5037) (感謝 @iSazonov！)
- 已將 `New-ModuleManifest` 中的預設 `ModuleVersion` 變更為 `0.0.1`，以符合 SemVer。 (#4842) (感謝 @LDSpits)
- 已將 `semver` 新增為 `System.Management.Automation.SemanticVersion` 的類型加速器。 (#4142) (感謝 @oising！)
- 已啟用 `SemanticVersion` 執行個體與只使用 `Major` 和 `Minor` 版本值所建構之 `Version` 執行個體之間的比較。

## <a name="language-updates"></a>語言更新

- 實作 Unicode 逸出剖析，讓使用者可以使用 Unicode 字元作為引數、字串或變數名稱。 (#3958) (感謝 @rkeithhill！)
- 已新增 ESC 的新逸出字元：`` `e``
- 已新增將列舉轉換為字串的支援 (#4318) (感謝 @KirkMunro)
- 已修正將單一項目陣列轉型為泛型集合。 (#3170)
- 已新增多載至 `..` 運算子的字元範圍，讓 `'a'..'z'` 傳回從 'a' 到 'z' 的字元。 (#5026) (感謝 @IISResetMe！)
- 已修正變數指派不會覆寫唯讀變數
- 將指令碼 Cmdlet 加上點時，將自動變數的區域變數推送至 'DottedScopes' (#4709)
- 在分割運算子中啟用「單行、多行」選項的使用 (#4721) (感謝 @iSazonov)

## <a name="engine-updates"></a>引擎更新

- `$PSVersionTable` 有四個新屬性：
  - `PSEdition`：這在 PowerShell Core 上設為 `Core`，而在 Windows PowerShell 上設為 `Desktop`
  - `GitCommitId`：這是在其中建置 PowerShell 之 Git 分支或標記的 Git 認可識別碼。
    在發行的組建上，它可能會與 `PSVersion` 相同。
  - `OS`：這是 `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription` 所傳回的作業系統版本字串
  - `Platform`：這是 `[System.Environment]::OSVersion.Platform` 所傳回。它在 Windows 上設為 `Win32NT`、在 macOS 上設為 `MacOSX`，而在 Linux 上設為 `Unix`。
- 已從 `$PSVersionTable` 移除 `BuildVersion` 屬性。
  此屬性已緊密繫結至 Windows 組建版本。
  相反地，建議您使用 `GitCommitId` 擷取 PowerShell Core 的確切組建版本。 (#3877) (感謝 @iSazonov！)
- 已從 `$PSVersionTable` 移除 `ClrVersion` 屬性。
  此屬性與 .NET Core 無關，而且基於不適用於 PowerShell 的特定舊版用途，已在 .NET Core 中予以保留。
- 已新增三個新的自動變數，以決定是否在指定的 OS 中執行 PowerShell：`$IsWindows`、`$IsMacOs` 和 `$IsLinux`。
- 將 `GitCommitId` 新增至 PowerShell Core 橫幅。
  現在，啟動 PowerShell 取得版本之後，不需要立即執行 `$PSVersionTable`！ (#3916) (感謝 @iSazonov)
- 在 `$PSHome` 中新增稱為 `powershell.config.json` 的 JSON 設定檔，以儲存啟動時間之前所需的一些設定 (例如 `ExecutionPolicy`)。
- 執行 Windows 的 EXE 時不會封鎖管線
- 已啟用 COM 集合的列舉。 (#4553)

## <a name="cmdlet-updates"></a>Cmdlet 更新

### <a name="new-cmdlets"></a>新的 Cmdlet

- 將 `Get-Uptime` 新增至 `Microsoft.PowerShell.Utility`。
- 新增 `Remove-Alias` 命令。 (#5143) (感謝 @PowershellNinja！)
- 將 `Remove-Service` 新增至管理模組。 (#4858) (感謝 @joandrsn！)

### <a name="web-cmdlets"></a>Web Cmdlet

- 新增 Web Cmdlet 的憑證驗證支援。 (#4646) (感謝 @markekraus)
- 將內容標頭的支援新增至 Web Cmdlet。 (#4494 & #4640) (感謝 @markekraus)
- 將多個連結標頭支援新增至 Web Cmdlet。 (#5265) (感謝 @markekraus！)
- Web Cmdlet 中支援連結標頭分頁 (#3828)
  - 針對 `Invoke-WebRequest`，回應包含連結標頭時，我們會將 RelationLink 屬性 (property) 建立為呈現 URL 和 `rel` 屬性 (attribute) 的 Dictionary，並確定 URL 是絕對 URL，讓開發人員更方便使用。
  - 針對 `Invoke-RestMethod`，回應包含連結標頭時，我們會公開 `-FollowRelLink` 參數以自動遵循 `next` `rel` 連結，直到它們不再存在或叫用選擇性 `-MaximumFollowRelLink` 參數值。
- 將 `-CustomMethod` 參數新增至 Web Cmdlet，以允許非標準方法動詞。 (#3142) (感謝 @Lee303！)
- 將 `SslProtocol` 支援新增至 Web Cmdlet。 (#5329) (感謝 @markekraus！)
- 將多部分支援新增至 Web Cmdlet。 (#4782) (感謝 @markekraus)
- 將 `-NoProxy` 新增至 Web Cmdlet，讓它們忽略整個系統 Proxy 設定。 (#3447) (感謝 @TheFlyingCorpse！)
- Web Cmdlet 的使用者代理程式現在報告作業系統平台 (#4937) (感謝 @LDSpits)
- 將 `-SkipHeaderValidation` 參數新增至 Web Cmdlet 以支援新增標頭，而不驗證標頭值。 (#4085)
- 必要時，讓 Web Cmdlet 不驗證伺服器的 HTTPS 憑證。
- 將驗證參數新增至 Web Cmdlet。 (#5052) (感謝 @markekraus)
  - 新增提供三個選項的 `-Authentication`：Basic、OAuth 和持有人。
  - 新增 `-Token`，以取得 [OAuth] 和 [持有人] 選項的持有人權杖。
  - 新增 `-AllowUnencryptedAuthentication`，以略過任何非 HTTPS 的傳輸配置所提供的驗證。
- 將 `-ResponseHeadersVariable` 新增至 `Invoke-RestMethod`，以啟用擷取回應標頭。 (#4888) (感謝 @markekraus)
- 修正 Web Cmdlet，以在回應狀態碼為不成功時於例外狀況中包含 HTTP 回應。 (#3201)
- 將 Web Cmdlet `UserAgent` 從 `WindowsPowerShell` 變更為 `PowerShell`。 (#4914) (感謝 @markekraus)
- 將明確 `ContentType` 偵測新增至 `Invoke-RestMethod` (#4692)
- 修正 Web Cmdlet `-SkipHeaderValidation`，以使用非標準使用者代理程式標頭。 (#4479 & #4512) (感謝 @markekraus)

### <a name="json-cmdlets"></a>JSON Cmdlet

- 將 `-AsHashtable` 新增至 `ConvertFrom-Json`，以改回傳回 `Hashtable`。 (#5043) (感謝 @bergmeister！)
- 搭配使用更美觀的格式器與 `ConvertTo-Json` 輸出。 (#2787) (感謝 @kittholland！)
- 將 `Jobject` 序列化支援新增至 `ConvertTo-Json`。 (#5141)
- 修正 `ConvertFrom-Json`，以還原序列化管線中一起建構完整 JSON 字串的字串陣列。
  這會修正新行破壞 JSON 剖析的情況。 (#3823)
- 移除針對 `System.Array` 所定義的 `AliasProperty "Count"`。
  這會移除部分 `ConvertFrom-Json` 輸出的多餘 `Count` 屬性。 (#3231) (感謝 @PetSerAl)

### <a name="csv-cmdlets"></a>CSV Cmdlet

- 新增對 `Import-Csv` 和 `ConvertFrom-Csv` 的 `PSTypeName` 支援。 (#5389) (感謝 @markekraus！)
- 讓 `Import-Csv` 支援 `CR`、`LF` 和 `CRLF` 作為行分隔符號。 (#5363) (感謝 @iSazonov！)
- 將 `-NoTypeInformation` 設為 `Export-Csv` 和 `ConvertTo-Csv` 的預設值。 (#5164) (感謝 @markekraus)

### <a name="service-cmdlets"></a>服務 Cmdlet

- 將 `UserName`、`Description`、`DelayedAutoStart`、`BinaryPathName` 和 `StartupType` 屬性新增至 `Get-Service` 所傳回的 `ServiceController` 物件。 (#4907) (感謝 @joandrsn)
- 新增功能以在 `Set-Service` 命令上設定認證。 (#4844) (感謝 @joandrsn)

### <a name="other-cmdlets"></a>其他 Cmdlet

- 將參數新增至稱為 `-FollowSymlink` 並依需求周遊符號連結的 `Get-ChildItem` ，同時檢查連結迴圈。 (#4020)
- 更新 `Add-Type` 以支援 `CSharpVersion7`。 (#3933) (感謝 @iSazonov)
- 在找到較好的解決方案之前，因使用不支援的 API 而移除 `Microsoft.PowerShell.LocalAccounts` 模組。 (#4302)
- 在找到較好的解決方案之前，因使用不支援的 API 而移除 `Microsoft.PowerShell.Diagnostics` 中的 `*-Counter` Cmdlet。 (#4303)
- 新增對 `Invoke-Item -Path <folder>` 的支援。 (#4262)
- 將 `-Extension` 和 `-LeafBase` 參數新增至 `Split-Path`，讓您可以分割副檔名與檔案名稱其餘部分之間的路徑。 (#2721) (感謝 @powercode！)
- 將 `-Top` 和 `-Bottom` 參數新增至 `Sort-Object` 以進行「前/後 N 個」排序
- 將 `CodeProperty "Parent"` 新增至 `System.Diagnostics.Process`，以公開處理序的父處理序。 (#2850) (感謝 @powercode！)
- 針對 `Get-Process` 的記憶體資料行，使用 MB，而非 KB
- 新增 `Out-String` 的 `-NoNewLine` 參數。 (#5056) (感謝 @raghav710)
- `Move-Item` Cmdlet 接受 `-Include`、`-Exclude` 和 `-Filter` 參數。 (#3878)
- 允許在 `Remove-Item` 的登錄路徑中使用 `*`。 (#4866)
- 將 `-Title` 新增至 `Get-Credential`，並統一跨平台的提示體驗。
- 將 `-TimeOut` 參數新增至 `Test-Connection`。 (#2492)
- `Get-AuthenticodeSignature` Cmdlet 現在可以取得檔案簽章時間戳記。 (#4061)
- 從 `Get-Help` 移除不支援的 `-ShowWindow` 參數。 (#4903)
- 修正 `Get-Content -Delimiter`，以在所傳回陣列元素中不包含分隔符號 (#3706) (感謝 @mklement0)
- 將 `Meta`、`Charset` 和 `Transitional` 參數新增至 `ConvertTo-HTML` (#4184) (感謝 @ergo3114)
- 將 `WindowsUBR` 和 `WindowsVersion` 屬性新增至 `Get-ComputerInfo` 結果
- 將 `-Group` 參數新增至 `Get-Verb`
- 將 `ShouldProcess` 支援新增至 `New-FileCatalog` 和 `Test-FileCatalog` (修正 `-WhatIf` 和 `-Confirm`)。 (#3074) (感謝 @iSazonov！)
- 將 `-WhatIf` 參數新增至 `Start-Process` Cmdlet (#4735) (感謝 @sarithsutha)
- 針對 `ValidateNotNullOrEmpty` 新增太多現有參數。

## <a name="tab-completion"></a>Tab 鍵自動完成

- 已根據執行階段變數值增強 Tab 鍵自動完成中的型別推斷。 (#2744) (感謝 @powercode！)在下列情況下，這會啟用 Tab 鍵自動完成：

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- 新增 `Select-Object` 之 `-Property` 的雜湊表 Tab 鍵自動完成。 (#3625) (感謝 @powercode)
- 啟用 `Select-Object` 之 `-ExcludeProperty` 和 `-ExpandProperty` 的引數自動完成。 (#3443) (感謝 @iSazonov！)
- 修正 Tab 鍵自動完成中的 Bug，讓 `native.exe --<tab>` 呼叫原生完成器。 (#3633) (感謝 @powercode！)

## <a name="breaking-changes"></a>最新變更

我們已引進 PowerShell Core 6.0 中的許多最新變更。
若要更詳細地深入閱讀這些變更，請參閱 [PowerShell Core 6.0 的最新變更][breaking-changes]。

## <a name="debugging"></a>偵錯

- `Invoke-Command -ComputerName` 的遠端逐步執行偵錯支援。 (#3015)
- 啟用 PowerShell Core 中的繫結器偵錯記錄

## <a name="filesystem-updates"></a>Filesystem 更新

- 從 UNC 路徑啟用 Filesystem 提供者的使用。 ($4998)
- `Split-Path` 現在使用 UNC root
- 現在，無引數之 `cd` 的行為會如同 `cd ~`
- 已修正 PowerShell Core，允許使用長度超過 260 個字元的路徑。 (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>Bug 修正和效能改善

我們已跨 PowerShell 進行「許多」效能改善，包含在啟動時間、各種內建 Cmdlet 以及與原生二進位檔的互動中。

我們也已修正 PowerShell Core 內的一些 Bug。
如需修正和變更的完整清單，請參閱 GitHub 上的[變更記錄][]。

## <a name="telemetry"></a>遙測

- PowerShell Core 6.0 已將遙測新增至主控台主機，以報告兩個值 (#3620)：
  - 作業系統平台 (`$PSVersionTable.OSDescription`)
  - 確切 PowerShell 版本 (`$PSVersionTable.GitCommitId`)

如果您想要退出此遙測，只需要刪除 `$PSHome\DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY`。
刪除此檔案會略過第一次執行 PowerShell 之前的所有遙測資料。
我們也想要公開此遙測資料，以及我們在[社群儀表板][community-dashboard]中從遙測搜集到的深入資訊。
您可以深入了解我們如何在這個[部落格文章][telemetry-blog]中使用這項資料。

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/en-us/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/en-us/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: https://github.com/PowerShell/PowerShell/tree/master/docs/BREAKINGCHANGES.md
[變更記錄]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET 部落格]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[常見問題集]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/en-us/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[Docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
