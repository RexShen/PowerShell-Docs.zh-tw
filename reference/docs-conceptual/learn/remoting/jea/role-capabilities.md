---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: JEA 角色功能
ms.openlocfilehash: 7191b90e198ffb539da6870a8ddc3e449ad9e8ae
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017839"
---
# <a name="jea-role-capabilities"></a>JEA 角色功能

建立 JEA 端點時，您必須定義一或多個角色功能，描述某人可以在 JEA 工作階段中做什麼。 角色功能是具有 `.psrc` 副檔名的 PowerShell 資料檔案，列出可供連線使用者使用的所有 Cmdlet、函式、提供者，以及外部程式。

## <a name="determine-which-commands-to-allow"></a>決定允許哪些命令

建立角色功能檔案的第一步是考慮使用者需要存取什麼。 這項需求收集程序可能需要一段時間，但這是很重要的程序。 提供使用者太少 Cmdlet 和函式的存取權，可能會使他們無法完成工作。 允許太多 Cmdlet 和函式的存取權，可能會讓使用者執行超出您預期的項目，並降低您的安全性立場。

您進行此處理程序的方式，取決於您的組織和目標。 下列祕訣可協助確保您採用正確的方法。

1. **識別**使用者用來完成工作的命令。 這可能需要調查 IT 人員、檢查自動化指令碼，或分析 PowerShell 工作階段文字記錄和記錄檔。
2. 可能的話，將命令列工具的使用**更新**為 PowerShell 對等用法，以得到最佳的稽核和 JEA 自訂體驗。 外部程式無法像原生 PowerShell Cmdlet 和 JEA 函式那樣精細地限制。
3. **限制** Cmdlet 的範圍，只允許特定的參數或參數值。 如果使用者只應管理部分系統，則這點特別重要。
4. **建立**自訂函式來取代複雜命令或 JEA 中難以限制的命令。 包裝複雜命令或套用額外驗證邏輯的簡單函式，可以提供系統管理員更多的控制，以及使用者的簡便性。
5. **測試**使用者或自動化服務可允許命令的範圍清單，並視需要調整。

### <a name="examples-of-potentially-dangerous-commands"></a>有潛在危險的命令範例

謹慎地選取命令，對於確定 JEA 端點不會允許使用者提升其權限而言很重要。

> [!IMPORTANT]
> 協助使用者成功所需的基本資訊。JEA 工作階段通常會以提高的權限執行。

下表包含一些命令範例，如果允許其為未受限制的狀態，將可能惡意地使用它們。 這不是詳盡的清單，應該僅作為警告的起點。

|                                            風險                                            |                                範例                                |                                                                              相關的命令                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 授與連線使用者系統管理員權限以略過 JEA                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`、`Add-LocalGroupMember`、`net.exe`、`dsadd.exe`                                                                                                        |
| 執行任意程式碼，例如惡意程式碼、入侵或自訂指令碼來略過防護 | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>建立角色功能檔案

您可以使用 [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6) Cmdlet 建立新的 PowerShell 角色功能檔案。

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

您應編輯產生的角色功能檔案，以允許角色所需的命令。 PowerShell 說明文件包含數個檔案設定方式的範例。

### <a name="allowing-powershell-cmdlets-and-functions"></a>允許 PowerShell Cmdlet 和函式

若要授權使用者執行 PowerShell Cmdlet 或函式，請將 Cmdlet 或函式名稱新增至 VisibleCmdlets 或 VisibleFunctions 欄位。 如果不確定命令是 Cmdlet 或函式，您可以執行 `Get-Command <name>` 並檢查輸出中的 **CommandType** 屬性。

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

有時候特定 Cmdlet 或函式的範圍對於您使用者的需求而言過於廣泛。 例如，DNS 系統管理員可能只需要重新啟動 DNS 服務的存取權。 在多租用戶環境中，租用戶可以存取自助式管理工具。 租用戶應受限於僅可管理自己的資源。 在這些情況下，您可以限制從 Cmdlet 或函式公開哪些參數。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

在進階情況中，您可能也需要限制使用者可以透過這些參數使用的值。 角色功能可讓您定義一組值，或定義決定是否允許輸入的規則運算式模式。

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> 一律會允許[一般的 PowerShell 參數](/powershell/module/microsoft.powershell.core/about/about_commonparameters)，即使是您限制了可用的參數。
> 您不應該將其明確列在 Parameters 欄位中。

下表說明您可以自訂可見 Cmdlet 或函式的各種方式。
您可以在 **VisibleCmdlets** 欄位中混搭下列任何項目。

|                                           範例                                           |                                                             使用案例                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` 或 `@{ Name = 'My-Func' }`                                                      | 允許使用者執行 `My-Func` 而無任何參數限制。                                                      |
| `'MyModule\My-Func'`                                                                        | 允許使用者從模組 `MyModule` 執行 `My-Func` 而無任何參數限制。                           |
| `'My-*'`                                                                                    | 允許使用者使用動詞 `My` 執行任何 Cmdlet 或函式。                                                                 |
| `'*-Func'`                                                                                  | 允許使用者使用名詞 `Func` 執行任何 Cmdlet 或函式。                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | 允許使用者搭配 `Param1` 和 `Param2` 參數來執行 `My-Func`。 可以提供任何值給參數。          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | 允許使用者執行 `My-Func` 搭配 `Param1` 參數。 只能提供 "Value1" 和 "Value2" 給參數。        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | 允許使用者執行 `My-Func` 搭配 `Param1` 參數。 可以提供開頭為 "contoso" 的任何值給參數。 |

> [!WARNING]
> 關於最佳安全性做法，不建議在定義可見 Cmdlet 或函式時使用萬用字元。 相反地，您應該明確列出每個受信任的命令，以確保沒有其他共用相同命名配置的命令意外地獲得授權。

您無法將 **ValidatePattern** 和 **ValidateSet** 同時套用至相同的 Cmdlet 或函式。

如果您這樣做，**ValidatePattern** 會覆寫 **ValidateSet**。

如需 **ValidatePattern** 的詳細資訊，請參閱[這篇 *Hey, Scripting Guy!* 文章](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/)和 [PowerShell 規則運算式](/powershell/module/microsoft.powershell.core/about/about_regular_expressions)參考內容。

### <a name="allowing-external-commands-and-powershell-scripts"></a>允許外部命令及 PowerShell 指令碼

若要允許使用者在 JEA 工作階段中執行可執行檔和 PowerShell 指令碼 (.ps1)，您必須在 **VisibleExternalCommands** 欄位中新增每個程式的完整路徑。

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

在可能的情況下，請使用任何外部可執行檔的對等 PowerShell Cmdlet 或函式，因為您可以控制 PowerShell Cmdlet 和函式允許哪些參數。

許多可執行檔允許您讀取目前的狀態，然後提供不同參數來變更。

例如，考慮裝載於管理系統上的網路共用檔案伺服器管理員角色。 管理共用的其中一種方法是使用 `net share`。 不過，允許 **net.exe** 很危險，因為使用者可以透過 `net group Administrators unprivilegedjeauser /add` 使用命令取得管理員權限。 較安全的選項是允許 [Get-SmbShare](/powershell/module/smbshare/get-smbshare)，這可達到相同結果但具有非常多的範圍限制。

在 JEA 工作階段中將外部命令提供給使用者時，請一律指定可執行檔的完整路徑。 這可防止名稱類似和潛在惡意程式在系統上的其他位置執行。

### <a name="allowing-access-to-powershell-providers"></a>允許存取 PowerShell 提供者

根據預設，在 JEA 工作階段中不能使用 PowerShell 提供者。 這是為了降低將敏感性資訊和組態設定公開給連線使用者的風險。

如有必要，您可以使用 `VisibleProviders` 命令允許存取 PowerShell 提供者。 如需完整的提供者清單，請執行 `Get-PSProvider`。

```powershell
VisibleProviders = 'Registry'
```

針對需要存取檔案系統、登錄、憑證存放區或其他敏感性提供者的簡單工作，請考慮撰寫代表使用者與提供者合作的自訂函式。 函式、Cmdlet 和 JEA 工作階段中可用外部程式不受限於與 JEA 相同的條件約束。 根據預設，它們可以存取任何提供者。 另外也請考慮當需要在與 JEA 端點之間複製檔案時使用[使用者磁碟機](session-configurations.md#user-drive)。

### <a name="creating-custom-functions"></a>建立自訂函式

您可以在角色功能檔案中撰寫自訂函式，簡化一般使用者的複雜工作。 當您需要 Cmdlet 參數值的進階驗證邏輯時，自訂函式也十分有用。 您可以在 **FunctionDefinitions** 欄位中撰寫簡單的函式︰

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> 別忘了將您的自訂函式名稱新增至 **VisibleFunctions** 欄位，以便 JEA 使用者可以執行它們。

自訂函式主體 (指令碼區塊) 會以系統的預設語言模式執行，且不受限於 JEA 的語言條件約束。 這表示函式可以存取檔案系統和登錄，並執行角色功能檔案中未設為可見的命令。 請在使用參數時小心避免執行任意程式碼。 避免直接將使用者輸入用於 `Invoke-Expression` 之類的 Cmdlet。

請注意，上述範例使用了完整的模組名稱 (FQMN) `Microsoft.PowerShell.Utility\Select-Object`，而不是使用速記的 `Select-Object`。
角色功能檔案中定義的函式仍受限於 JEA 工作階段的範圍，包括 JEA 建立來限制現有命令的 Proxy 函式。

根據預設，`Select-Object` 是所有 JEA 工作階段中受限制的預設 Cmdlet，不允許您選取物件上的任意屬性。 若要在函式中使用未受限制的 `Select-Object`，您必須使用 FQMN 明確地要求完整實作。 從函式叫用時，JEA 工作階段中任何受約束的 Cmdlet 都具有相同條件約束。 如需詳細資訊，請參閱 [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence)。

如果您要撰寫數個自訂函式，將它們放在 PowerShell 指令碼模組可能會比較方便。 您可以使用 **VisibleFunctions** 欄位將那些函式設為在 JEA 工作階段中可見，就像是使用內建和協力廠商模組一樣。

您必須將內建函式 `tabexpansion2` 納入 **VisibleFunctions** 清單，Tab 鍵完成才能在 JEA 工作階段中正常運作。

## <a name="place-role-capabilities-in-a-module"></a>將角色功能放置在模組中

為了讓 PowerShell 尋找角色功能檔案，PowerShell 必須儲存在 PowerShell 模組的 **RoleCapabilitie** 資料夾中。 模組可以儲存在 `$env:PSModulePath` 環境變數包含的任何資料夾中，但您不應該將其放在 System32 資料夾中 ，或是未受信任連線使用者可以修改其中檔案的資料夾。 以下範例會在 `$env:ProgramFiles` 路徑中建立基本 PowerShell 指令碼模組，稱為 **ContosoJEA**。

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

如需 PowerShell 模組的詳細資訊，請參閱[了解 PowerShell 模組](/powershell/developer/windows-powershell)。

## <a name="updating-role-capabilities"></a>更新角色功能

您可以編輯角色功能檔案以隨時更新設定。 更新角色功能之後啟動的任何新 JEA 工作階段都會反映出修改過的功能。

這就是為什麼控制角色功能資料夾的存取權如此重要。 應該只有受高度信任的系統管理員才允許變更角色功能檔案。 如果未受信任的使用者可以變更角色功能檔案，他們便可以輕鬆地讓自己能存取 Cmdlet，使其可提高權限。

針對想要鎖定角色功能存取權的系統管理員，請確定本機系統對於角色功能檔案和包含的模組具有讀取存取權。

## <a name="how-role-capabilities-are-merged"></a>如何合併角色功能

當使用者進入 JEA 工作階段時，即可存取[工作階段設定檔](session-configurations.md)中所有相符的角色功能。 JEA 會嘗試授與使用者任何角色所允許的最寬鬆命令集。

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlet 和 VisibleFunction

最複雜的合併邏輯會影響 Cmdlet 和函式，它們的參數和參數值可能會在 JEA 中受到限制。

規則如下︰

1. 如果 Cmdlet 只在一個角色中設為可見，則具有任何適用參數條件約束的使用者將可看見。
2. 如果 Cmdlet 在多個角色中設為可見，且每個角色都對 Cmdlet 具有相同的條件約束，則具有這些條件約束的使用者將可看見該 Cmdlet。
3. 如果 Cmdlet 在多個角色中設為可見，且每個角色允許不同的參數集，則使用者將可看見該 Cmdlet 及在每個角色定義的所有參數。
   如果一個角色對參數沒有條件約束，則將允許所有參數。
4. 如果一個角色針對 Cmdlet 參數定義驗證集或驗證模式，而另一個角色允許該參數但未限制參數值，則會忽略驗證集或模式。
5. 如果在多個角色中針對相同的 Cmdlet 參數定義驗證集，將允許所有驗證字元集中的所有值。
6. 如果在多個角色中針對相同的 Cmdlet 參數定義驗證模式，將允許符合任何模式的任何值。
7. 如果在一或多個角色中定義驗證集，並且在另一個角色中針對相同 Cmdlet 參數定義驗證模式，將會忽略驗證集，並套用規則 (6) 至其餘的驗證模式。

以下是角色如何根據這些規則合併的範例：

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommand, VisibleAliase, VisibleProvider, ScriptsToProcess

角色功能檔案中所有其他欄位會新增至可允許之外部命令、別名、提供者和啟動指令碼的累計集。 JEA 使用者將可以使用一個角色功能中的任何命令、別名、提供者或指令碼。

請小心確保來自一個角色功能之提供者組合集和來自另一個角色功能的 Cmdlet/函式/命令不會允許使用者意外存取系統資源。
例如，如果一個角色允許 `Remove-Item` Cmdlet，另一個允許 `FileSystem` 提供者，便會有 JEA 使用者刪除您電腦上任意檔案的風險。 如需識別使用者有效權限的詳細資訊，請參閱[稽核 JEA](audit-and-report.md) 一文。

## <a name="next-steps"></a>接下來的步驟

[建立工作階段設定檔](session-configurations.md)
