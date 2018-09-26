---
ms.date: 06/12/2017
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: bd0a995adc60e50049ff99d6b23e7c2aeb745a18
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522934"
---
# <a name="jea-role-capabilities"></a>JEA 角色功能

> 適用對象：Windows PowerShell 5.0

建立 JEA 端點時，您必須定義一或多個「角色功能」，描述某人可以在 JEA 工作階段中做「什麼」。
角色功能是具有 .psrc 副檔名的 PowerShell 資料檔案，列出應該供連線使用者使用的所有 Cmdlet、函式、提供者，以及外部程式。

本主題說明如何建立 JEA 使用者的 PowerShell 角色功能檔案。

## <a name="determine-which-commands-to-allow"></a>決定允許哪些命令

建立角色功能檔案時的第一步是考慮被指派該角色的使用者將需要存取什麼。
這項需求收集程序可能需要一段時間，但這是非常重要的程序。
提供使用者太少 Cmdlet 和函式的存取權，可能會使他們無法完成工作。
允許存取太多 Cmdlet 和函式則可能會導致使用者執行比您想要其隱含系統管理員權限更多的事情，削弱您的安全性立場。

您如何執行此程序將取決於您的組織和目標，但下列秘訣可以協助確保您的路徑正確。

1. **識別**使用者用來完成工作的命令。 這可能需要調查 IT 人員、檢查自動化指令碼，或分析 PowerShell 工作階段文字記錄或記錄檔。
2. 可能的話，將命令列工具的使用**更新**為 PowerShell 對等用法，以得到最佳的稽核和 JEA 自訂體驗。 外部程式無法像原生 PowerShell Cmdlet 和 JEA 函式那樣精細地限制。
3. 視需要**限制** Cmdlet 的範圍，只允許特定的參數或參數值。 如果使用者應該只能管理系統的一部分，這點尤其重要。
4. **建立**自訂函式，取代複雜命令或 JEA 中難以限制的命令。 包裝複雜命令或套用額外驗證邏輯的簡單函式，可以提供系統管理員更多的控制，以及使用者的簡便性。
5. **測試**使用者和/或自動化服務允許命令的範圍清單，並視需要調整。

請務必記得，JEA 工作階段中的命令通常會使用系統管理員 (或以其他方式提高權限) 的權限來執行。
謹慎地選取可用的命令，對於確定 JEA 端點不會允許連線使用者提升其權限而言很重要。
以下是一些命令範例，如果允許其為未受限制的狀態，將可能惡意地使用它們。
請注意，這不是詳盡的清單，應該僅作為警告的起點。

### <a name="examples-of-potentially-dangerous-commands"></a>有潛在危險的命令範例

風險 | 範例 | 相關的命令
-----|---------|-----------------
授與連線使用者系統管理員權限以略過 JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`
執行任意程式碼，例如惡意程式碼、入侵或自訂指令碼來略過防護 | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>建立角色功能檔案

您可以使用 [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) Cmdlet 建立新的 PowerShell 角色功能檔案。

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

所產生的角色功能檔案可以在文字編輯器中開啟並修改，以允許角色所需的命令。
PowerShell 說明文件包含數個檔案設定方式的範例。

### <a name="allowing-powershell-cmdlets-and-functions"></a>允許 PowerShell Cmdlet 和函式

若要授權使用者執行 PowerShell Cmdlet 或函式、新增 Cmdlet 或函式名稱至 VisbibleCmdlets 或 VisibleFunctions 欄位。
如果您不確定命令是 Cmdlet 或函式，可以執行 `Get-Command <name>` 並檢查輸出中的 "CommandType" 屬性。

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

有時候特定 Cmdlet 或函式的範圍對於您使用者的需求而言過於廣泛。
例如，DNS 系統管理員可能只需要重新啟動 DNS 服務的存取權。
在多租用戶環境中，租用戶被授與自我服務管理工具的存取權，並且應該受限於管理自己的資源。
在這些情況下，您可以限制從 Cmdlet 或函式公開哪些參數。

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

在進階情況中，您可能也需要限制某人可以提供給這些參數的值。
角色功能可讓您定義一組允許的值或評估以決定是否允許指定輸入的規則運算式模式。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> 一律會允許[一般的 PowerShell 參數](https://technet.microsoft.com/library/hh847884.aspx)，即使是您限制了可用的參數。
> 您不應該將其明確列在 Parameters 欄位中。

下表說明您可以自訂可見 Cmdlet 或函式的各種方式。
您可以在 VisibleCmdlets 欄位中混搭下列任何項目。

範例                                                                                      | 使用案例
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` 或 `@{ Name = 'My-Func' }`                                                       | 允許使用者執行 `My-Func` 而無任何參數限制。
`'MyModule\My-Func'`                                                                         | 允許使用者從模組 `MyModule` 執行 `My-Func` 而無任何參數限制。
`'My-*'`                                                                                     | 允許使用者使用動詞 `My` 執行任何 Cmdlet 或函式。
`'*-Func'`                                                                                   | 允許使用者使用名詞 `Func` 執行任何 Cmdlet 或函式。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | 允許使用者執行 `My-Func` 搭配 `Param1` 和/或 `Param2` 參數。 可以提供任何值給參數。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | 允許使用者執行 `My-Func` 搭配 `Param1` 參數。 只能提供 "Value1" 和 "Value2" 給參數。
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | 允許使用者執行 `My-Func` 搭配 `Param1` 參數。 可以提供開頭為 "contoso" 的任何值給參數。


> [!WARNING]
> 關於最佳安全性做法，不建議在定義可見 Cmdlet 或函式時使用萬用字元。
> 相反地，您應該明確列出每個受信任的命令，以確保沒有其他共用相同命名配置的命令意外地獲得授權。

您無法將 ValidatePattern 和 ValidateSet 同時套用至相同的 Cmdlet 或函式。

如果您這樣做，ValidatePattern 會覆寫 ValidateSet。

如需 ValidatePattern 的詳細資訊，請參閱[這篇 *Hey, Scripting Guy!* 文章](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 規則運算式](https://technet.microsoft.com/library/hh847880.aspx)參考內容。

### <a name="allowing-external-commands-and-powershell-scripts"></a>允許外部命令及 PowerShell 指令碼

若要允許使用者在 JEA 工作階段中執行可執行檔和 PowerShell 指令碼 (.ps1)，您必須在 VisibleExternalCommands 欄位中新增每個程式的完整路徑。

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

建議您，在可能的情況下，使用任何外部可執行檔的對等 PowerShell Cmdlet/函式，因為您可以控制 PowerShell Cmdlet/函式允許哪些參數。

許多可執行檔允許您讀取目前的狀態，然後提供不同參數來變更它。

例如，請考慮檔案伺服器系統管理員的角色，系統管理員想要檢查本機電腦裝載哪些網路共用。
其中一個檢查方式是使用 `net share`。
不過，允許 net.exe 非常危險，因為系統管理員可以輕鬆地以 `net group Administrators unprivilegedjeauser /add` 使用命令取得系統管理員權限。
更好的方法是允許 [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx)，這可達到相同的結果，但範圍的限制多了許多。

當提供外部命令給使用者在 JEA 工作階段中使用時，請一律指定可執行檔的完整路徑，以確保不會改為執行放置在系統上別處、名稱類似 (且可能惡意) 的程式。

### <a name="allowing-access-to-powershell-providers"></a>允許存取 PowerShell 提供者

根據預設，在 JEA 工作階段中不能使用 PowerShell 提供者。

這主要是為了降低機密資訊和設定被公開給連線使用者的風險。

如有必要，您可以使用 `VisibleProviders` 命令允許存取 PowerShell 提供者。
如需完整的提供者清單，請執行 `Get-PSProvider`。

```powershell
VisibleProviders = 'Registry'
```

針對需要存取檔案系統、登錄、憑證存放區或其他機密提供者的簡單工作，您也可以考慮撰寫代表使用者與提供者合作的自訂函式。
函式、Cmdlet 和 JEA 工作階段中可用的外部程式不受限於與 JEA 相同的條件約束 -- 它們預設可以存取任何提供者。
另外也請考慮當需要在與 JEA 端點之間複製檔案時，使用[使用者磁碟機](session-configurations.md#user-drive)。

### <a name="creating-custom-functions"></a>建立自訂函式

您可以在角色功能檔案中撰寫自訂函式，簡化一般使用者的複雜工作。
當您需要 Cmdlet 參數值的進階驗證邏輯時，自訂函式也十分有用。
您可以在 **FunctionDefinitions** 欄位中撰寫簡單的函式︰

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> 別忘了將您的自訂函式名稱新增至 **VisibleFunctions** 欄位，以便 JEA 使用者可以執行它們。


自訂函式主體 (指令碼區塊) 會以系統的預設語言模式執行，而且不受限於 JEA 的語言條件約束。
這表示函式可以存取檔案系統和登錄，並執行角色功能檔案中未設為可見的命令。
請小心避免允許在使用參數時執行任意程式碼，並避免直接將使用者輸入以管線送到 Cmdlet，例如 `Invoke-Expression`。

在上述範例中，您會發現，使用了完整的模組名稱 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而不是使用速記的 `Select-Object`。
角色功能檔案中定義的函式仍受限於 JEA 工作階段的範圍，包括 JEA 建立來限制現有命令的 Proxy 函式。

Select-Object 是所有 JEA 工作階段中受限制的預設 Cmdlet，它不允許您選取物件上的任何屬性。
若要使用未受限制的 Select-Object，您必須指定 FQMN，以明確地要求完整實作。
JEA 工作階段中的任何受限制 Cmdlet 從函式叫用時會展現相同行為，與 PowerShell 的[命令優先順序](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence)一致。

如果您要撰寫大量自訂函式，將它們放在 [PowerShell 指令碼模組](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx)可能會比較輕鬆。
接著您可以使用 VisibleFunctions 欄位將那些函式設為在 JEA 工作階段中可見，就像是使用內建和協力廠商模組一樣。

## <a name="place-role-capabilities-in-a-module"></a>將角色功能放置在模組中

為了讓 PowerShell 尋找角色功能檔案，它必須儲存在 PowerShell 模組的 "RoleCapabilities" 資料夾中。
模組可以儲存在 `$env:PSModulePath` 環境變數中包含的任何資料夾中，但您不應該將它放在 System32 資料夾中 (保留給內建模組)，或是不受信任的連線使用者可以修改其中檔案的資料夾。
以下範例會在 "Program Files" 路徑中建立基本 PowerShell 指令碼模組，稱為 *ContosoJEA*。

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

如需 PowerShell 模組、模組資訊清單和 PSModulePath 環境變數的詳細資訊，請參閱[了解 PowerShell 模組](https://msdn.microsoft.com/library/dd878324.aspx)。

## <a name="updating-role-capabilities"></a>更新角色功能


您只要儲存對角色功能檔案的變更，即可隨時更新角色功能檔案。
更新角色功能之後啟動的任何新 JEA 工作階段都會反映出修改過的功能。

這就是為什麼控制角色功能資料夾的存取權如此重要。
應該只有受高度信任的系統管理員才能夠變更角色功能檔案。
如果不受信任的使用者可以變更角色功能檔案，他們便可以輕鬆地讓自己能存取 Cmdlet，使其可提高權限。


針對想要鎖定角色功能存取權的系統管理員，請確定本機系統對於角色功能檔案和包含的模組具有讀取存取權。

## <a name="how-role-capabilities-are-merged"></a>如何合併角色功能

可以根據[工作階段設定檔](session-configurations.md)中的角色對應，在使用者進入 JEA 工作階段時授與使用者對多個角色功能的存取權。
發生這種情況時，JEA 會嘗試授與使用者任何角色所允許的*最寬鬆*的命令集。

**VisibleCmdlets 和 VisibleFunctions**

最複雜的合併邏輯會影響 Cmdlet 和函式，它們的參數和參數值可能會在 JEA 中受到限制。

規則如下︰

1. 如果 Cmdlet 只在一個角色中設為可見，具有任何適用的參數條件約束的使用者將可看見它。
2. 如果 Cmdlet 在多個角色中設為可見，而且每個角色都對 Cmdlet 具有相同的條件約束，則具有這些條件約束的使用者將可看見該 Cmdlet。
3. 如果 Cmdlet 在多個角色中設為可見，而且每個角色允許不同的參數集，則使用者將可看見該 Cmdlet 及在每個角色定義的所有參數。 如果一個角色對參數沒有條件約束，將允許所有參數。
4. 如果一個角色針對 Cmdlet 參數定義驗證集或驗證模式，而另一個角色允許該參數，但未限制參數的值，則會忽略驗證集或模式。
5. 如果在多個角色中針對相同的 Cmdlet 參數定義驗證集，將允許所有驗證字元集中的所有值。
6. 如果在多個角色中針對相同的 Cmdlet 參數定義驗證模式，將允許符合任何模式的任何值。
7. 如果在一或多個角色中定義驗證集，並且在另一個角色中針對相同 Cmdlet 參數定義驗證模式，將會忽略驗證集，並套用規則 (6) 至其餘的驗證模式。

以下是角色如何根據這些規則合併的範例：

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

角色功能檔案中的所有其他欄位只會新增至可允許之外部命令、別名、提供者和啟動指令碼的累計集。
JEA 使用者將可以使用一個角色功能中的任何命令、別名、提供者或指令碼。

請小心確保來自一個角色功能的提供者組合集，和來自另一個角色功能的 Cmdlet/函式/命令，不會允許連線使用者意外存取系統資源。
例如，如果一個角色允許 `Remove-Item` Cmdlet，另一個允許 `FileSystem` 提供者，便會有 JEA 使用者刪除您電腦上任意檔案的風險。
如需識別使用者有效權限的詳細資訊，請參閱[稽核 JEA 主題](audit-and-report.md)。

## <a name="next-steps"></a>接下來的步驟

- [建立工作階段設定檔](session-configurations.md)