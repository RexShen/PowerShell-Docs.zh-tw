---
ms.date: 05/17/2018
keywords: powershell, core
title: PowerShell Core 6.0 的已知問題
ms.openlocfilehash: ce40a1925e564fbd2c661e70ec36d3842d915dfe
ms.sourcegitcommit: 47becf2823ece251a7264db2387bb503cf3abaa9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49450991"
---
# <a name="known-issues-for-powershell-60"></a>PowerShell Core 6.0 的已知問題

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>非 Windows 平台上的 PowerShell 已知問題

Linux 和 macOS 上的 Alpha 版 PowerShell 大部分功能都可運作，但有一些重大的限制和可用性問題。 Linux 和 macOS 上的 Beta 版 PowerShell 比 Alpha 版功能完整且穩定，但仍可能缺少某個功能集，而且可能包含錯誤 (bug)。 在某些情況下，這些問題只是尚未修正的錯誤 (bug)。 而針對其他情況 (像是 ls、cp 等的預設別名情況)，我們則正在向社群尋求有關我們所做選擇的意見反應。

注意：由於許多基礎子系統都很相似，因此 Linux 和 macOS 上的 PowerShell 在功能和錯誤 (bug) 方面都趨向於擁有相同的成熟度。 除了下列所述之外，本節中的問題都同時適用於這兩種作業系統。

### <a name="case-sensitivity-in-powershell"></a>PowerShell 中的大小寫之分

在過去，除了幾個例外之外，PowerShell 一直是一律不區分大小寫。 在 UNIX 型作業系統中，是由檔案系統主導區分大小寫，而 PowerShell 則是遵守檔案系統的標準；這會透過一些明顯和不明顯的方式公開。

#### <a name="directly"></a>直接

- 在 PowerShell 中指定檔案時，必須使用正確的大小寫。

#### <a name="indirectly"></a>間接

- 如果指令碼嘗試載入某個模組，而該模組名稱的大小寫不正確，載入模組時就會失敗。 如果參考模組時所依據的名稱與實際的檔案名稱不符，可能會導致現有的指令碼發生問題。
- 如果檔案名稱大小寫錯誤，Tab 鍵自動完成將不會自動完成。 要完成的片段必須大小寫正確。 (用於完成類型名稱和類型成員的完成會區分大小寫)。

### <a name="ps1-file-extensions"></a>.PS1 副檔名

PowerShell 指令碼的結尾必須是 `.ps1`，解譯器才能瞭解如何在目前的處理序中載入並執行它們。 在目前的處理序中執行指令碼是預期的 PowerShell 平常行為。 您可以將 `#!` 魔術數字新增到沒有 `.ps1` 副檔名的指令碼中，但這會導致指令碼在新的 PowerShell 執行個體中執行，而使得指令碼在交換物件時無法正確運作。 (注意：從 `bash` 或另一個殼層執行 PowerShell 指令碼時，可能會需要這樣的行為)。

### <a name="missing-command-aliases"></a>缺少命令別名

在 Linux/macOS 上，已移除基本命令的「便利別名」`ls`、`cp`、`mv`、`rm`、`cat`、`man`、`mount`、`ps`。 在 Windows 上，為了使用者方便，PowerShell 提供一組與 Linux 命令名稱對應的別名。 在 Linux/macOS 發行版本上的預設 PowerShell 中則已移除這些別名，以允許在不指定路徑的情況下，即可執行原生可執行檔。

此做法有優缺點。 移除別名可讓 PowerShell 使用者接觸到原生命令體驗，但會降低殼層中的功能，因為原生命令會傳回字串而不是物件。

> [!NOTE]
> 這正是 PowerShell 小組尋求意見反應的領域。
> 慣用的解決方案是什麼？ 我們應該維持這個做法，還是將便利別名加回？ 請參閱[問題 #929](https://github.com/PowerShell/PowerShell/issues/929) \(英文\)。

### <a name="missing-wildcard-globbing-support"></a>缺少萬用字元支援

目前，PowerShell 執行萬用字元擴充的對象僅限 Windows 上的內建 Cmdlet、外部命令或二進位檔，以及 Linux 上的 Cmdlet。 這意謂著 `ls
*.txt` 這類命令將會失敗，因為 PowerShell 不會擴充星號來比對檔案名稱。 您可以藉由使用相當於 `ls` 的 PowerShell 內建命令來執行 `ls (gci *.txt | % name)`，或更簡單就執行 `gci *.txt`，以解決此問題。

請參閱 [#954](https://github.com/PowerShell/PowerShell/issues/954) 來提供我們有關如何改進 Linux/macOS 上萬用字元體驗的意見反應。

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework 與 .NET Core Framework 的比較

Linux/macOS 上的 PowerShell 使用 .NET Core，這是 Microsoft Windows 上完整 .NET Framework 的子集。 這相當重要，因為 PowerShell 可讓您直接存取基礎架構類型、方法等。因此，在 Windows 上執行的指令碼可能無法在非 Windows 平台上執行，因為架構差異的緣故。 如需有關 .NET Core Framework 的詳細資訊，請參閱 <https://dotnetfoundation.org/net-core> \(英文\)

隨著 [.NET Standard 2.0](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/) 的推出，.NET Core 2.0 將會帶回許多出現在完整 .NET Framework 中的傳統類型和方法。 這意謂著 PowerShell Core 將能夠原封不動地載入許多傳統 Windows PowerShell 模組。 您可以從[這裡](https://github.com/PowerShell/PowerShell/projects/4)追蹤我們的 .NET Standard 2.0 相關工作。

### <a name="redirection-issues"></a>重新導向問題

所有平台上的 PowerShell 都不支援輸入重新導向。
[問題 #1629](https://github.com/PowerShell/PowerShell/issues/1629)

請使用 `Get-Content` 將檔案的內容寫入至管線中。

使用預設的 UTF-8 編碼時，重新導向的輸出將會包含 Unicode 位元組順序標記 (BOM)。 與不預期會有 BOM 的公用程式搭配運作，或將 BOM 附加至檔案時，BOM 會導致發生問題。 請使用 `-Encoding Ascii` 來寫入 ASCII 文字 (因為不是 Unicode，所以不會有 BOM)。

> [!Note]
> 請參閱 [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71) \(英文\)，以提供有關改進在所有平台上對於 PowerShell Core 之編碼體驗的意見反應。 我們正努力支援不含 BOM 的 UTF-8，並且可能會變更各個平台上各種 Cmdlet 的編碼預設值。

### <a name="job-control"></a>工作控制

Linux/macOS 上的 PowerShell 不支援工作控制。
無法使用 `fg` 和 `bg` 命令。

目前，您可以使用 [PowerShell 工作](/powershell/module/microsoft.powershell.core/about/about_jobs)來跨所有平台執行工作。

### <a name="remoting-support"></a>遠端處理支援

目前，PowerShell Core 支援在 macOS 和 Linux 上使用基本驗證，以及在 Linux 上使用 NTLM 型驗證，透過 WSMan 進行 PowerShell 遠端處理 (PSRP)。 (不支援 Kerberos 型驗證)。

WSMan 型遠端處理的工作是在 [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) 存放庫中進行的。

PowerShell Core 也支援在所有平台上 (Windows、macOS 及 Linux) 透過 SSH 進行 PowerShell 遠端處理 (PSRP)。 雖然目前在生產環境中不支援此功能，但您可以從[這裡](../core-powershell/ssh-remoting-in-powershell-core.md)深入瞭解如何設定此功能。

### <a name="just-enough-administration-jea-support"></a>Just-Enough-Administration (JEA) 支援

Linux/macOS 上的 PowerShell 目前不支援可建立有限系統管理 (JEA) 遠端處理端點的功能。 此功能目前不在 6.0 的範圍內，但我們會考慮在 6.0 之後納入，因為它需要大量的設計工作。

### <a name="sudo-exec-and-powershell"></a>`sudo`、`exec` 及 PowerShell

由於 PowerShell 會在記憶體中執行大多數命令 (例如 Python 或 Ruby)，因此您無法將 sudo 直接與 PowerShell 內建項搭配使用。(當然，您可以從 sudo 執行 `pwsh`)。如果有必要從 PowerShell 內搭配 sudo 執行 PowerShell Cmdlet (例如 `sudo Set-Date 8/18/2016`)，則您會執行 `sudo pwsh Set-Date 8/18/2016`。 同樣地，您無法直接執行 PowerShell 內建項。 您將必須改為執行 `exec pwsh item_to_exec`。

此問題目前已納入 [#3232](https://github.com/PowerShell/PowerShell/issues/3232) 一併追蹤。

### <a name="missing-cmdlets"></a>缺少 Cmdlet

在 PowerShell 中一般可用的大量命令 (Cmdlet) 在 Linux/macOS 上並無法使用。 在許多情況下，這些命令在這些平台上並沒有意義 (例如 Windows 特定的功能，像是登錄)。 其他命令 (例如服務控制命令 Get/Start/Stop-Service) 則雖然存在，但卻沒有作用。 未來的版本將會更正這些問題，修正無效的 Cmdlet 並隨著時間新增新的 Cmdlet。

### <a name="command-availability"></a>命令可用性

下表列出已知在 Linux/macOS 上的 PowerShell 中無法運作的命令。

|命令|作業狀態|注意|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|無法使用。|系統將無法辨識這些命令。 在未來的版本中應該會修正此問題。|
|`Get-Acl`、`Set-Acl`|無法使用。|系統將無法辨識這些命令。 在未來的版本中應該會修正此問題。|
|`Get-AuthenticodeSignature`、`Set-AuthenticodeSignature`|無法使用。|系統將無法辨識這些命令。 在未來的版本中應該會修正此問題。|
|`Wait-Process`|可以使用，但無法正確運作。 |例如，`Start-Process gvim -PassThru | Wait-Process` 沒有作用；無法等候處理序。|
|`Register-PSSessionConfiguration`, `Unregister-PSSessionConfiguration`, `Get-PSSessionConfiguration`|可以使用，但沒有作用。|會撰寫一則錯誤訊息，指出命令無法運作。 在未來的版本中應該會修正這些問題。|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Register-WmiEvent`, `Remove-Event`, `Unregister-Event`|可以使用，但沒有任何可用的事件來源。|PowerShell 事件處理命令存在，但與這些命令搭配使用的大多數事件來源 (例如 System.Timers.Timer) 在 Linux 上都未提供，使得這些命令在 Alpha 版中毫無用處。|
|`Set-ExecutionPolicy`|可以使用，但沒有作用。|會傳回一則訊息，指出在此平台上並不支援。 執行原則是一個以使用者為焦點的「安全帶」，可協助防止使用者犯下重大錯誤。 它不是一個安全性界限。|
|`New-PSSessionOption`、`New-PSTransportOption`|可以使用，但 `New-PSSession` 沒有作用。|`New-PSSessionOption` 和 `New-PSTransportOption` 目前尚未通過驗證來運作以使 `New-PSSession` 產生作用。|
