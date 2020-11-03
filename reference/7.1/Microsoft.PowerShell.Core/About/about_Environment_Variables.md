---
description: 說明如何在 PowerShell 中存取 Windows 環境變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Environment_Variables
ms.openlocfilehash: c954ee6e783b7926dbcd05a3e08b6b9b5cf9bc25
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207323"
---
# <a name="about-environment-variables"></a>關於環境變數

## <a name="short-description"></a>簡短描述
說明如何在 PowerShell 中存取 Windows 環境變數。

## <a name="long-description"></a>詳細描述

環境變數會儲存作業系統環境的相關資訊。 這項資訊包含詳細資料，例如作業系統路徑、作業系統所使用的處理器數目，以及暫存資料夾的位置。

環境變數會儲存作業系統和其他程式所使用的資料。 例如， `WINDIR` 環境變數包含 Windows 安裝目錄的位置。 程式可以查詢此變數的值，以判斷 Windows 作業系統檔案的所在位置。

PowerShell 可以存取和管理任何支援的作業系統平臺中的環境變數。 PowerShell 環境提供者可讓您輕鬆地查看和變更環境變數，以簡化此程式。

環境變數與 PowerShell 中其他類型的變數不同，子進程會繼承這些變數，例如本機背景工作和模組成員執行所在的會話。 這會使環境變數非常適合用來儲存父和子進程中所需的值。

## <a name="using-and-changing-environment-variables"></a>使用和變更環境變數

在 Windows 中，可以在三個範圍內定義環境變數：

- 電腦 (或系統) 範圍
- 使用者範圍
- 進程範圍

_進程_ 範圍包含目前進程或 PowerShell 會話中可用的環境變數。 這份變數清單繼承自父進程，而且是由 _電腦_ 和 _使用者_ 範圍中的變數所構成。 以 Unix 為基礎的平臺只有 _進程_ 範圍。

您可以使用變數語法搭配環境提供者來顯示和變更環境變數的值，而不使用 Cmdlet。 若要顯示環境變數的值，請使用下列語法：

```
$Env:<variable-name>
```

例如，若要顯示環境變數的值 `WINDIR` ，請在 PowerShell 命令提示字元中輸入下列命令：

```powershell
$Env:windir
```

在此語法中，貨幣符號 (`$`) 表示變數，而磁片磁碟機名稱 (`Env:`) 表示環境變數，後面接著變數名稱 (`windir`) 。

當您在 PowerShell 中變更環境變數時，變更只會影響目前的會話。 此行為類似于 `Set` Windows 命令 Shell 中命令的行為，以及 `Setenv` UNIX 環境中的命令。 若要變更電腦或使用者範圍中的值，您必須使用 **System. 環境** 類別的方法。

若要變更電腦範圍變數，也必須具有許可權。 如果您嘗試在沒有足夠許可權的情況下變更值，此命令將會失敗，且 PowerShell 會顯示錯誤。

您可以使用下列語法來變更變數的值，而不使用 Cmdlet：

```powershell
$Env:<variable-name> = "<new-value>"
```

例如，若要附加 `;c:\temp` 至環境變數的值 `Path` ，請使用下列語法：

```powershell
$Env:Path += ";c:\temp"
```

在 Linux 或 MacOS 上，命令中的冒號 (`:`) 會將新路徑與清單中該路徑前面的路徑隔開。

```powershell
$Env:PATH += ":/usr/local/temp"
```

您也可以使用 Item Cmdlet （例如 `Set-Item` 、和） `Remove-Item` `Copy-Item` 來變更環境變數的值。 例如，若要使用 `Set-Item` Cmdlet 附加 `;c:\temp` 至 `Path` 環境變數的值，請使用下列語法：

```powershell
Set-Item -Path Env:Path -Value ($Env:Path + ";C:\Temp")
```

在此命令中，值會以括弧括住，以將其解釋為一個單位。

## <a name="environment-variables-that-store-preferences"></a>儲存喜好設定的環境變數

PowerShell 功能可以使用環境變數來儲存使用者喜好設定。
這些變數的運作方式類似喜好設定變數，但它們是由其建立所在之會話的子會話所繼承。 如需喜好設定變數的詳細資訊，請參閱 [about_preference_variables](about_Preference_Variables.md)。

儲存喜好設定的環境變數包括：

- PSExecutionPolicyPreference

  儲存目前會話的執行原則集。 只有當您為單一會話設定執行原則時，才會有這個環境變數。
  您可以透過兩種不同的方式來完成這項作業。

  - 從命令列使用 **ExecutionPolicy** 參數來設定會話的執行原則，以啟動會話。

  - 使用 `Set-ExecutionPolicy` 指令程式。 使用具有 "Process" 值的 Scope 參數。

    如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

- PSModuleAnalysisCachePath

  PowerShell 可讓您控制用來快取模組及其 Cmdlet 相關資料的檔案。 當您搜尋命令時，會在啟動時讀取快取，而且在匯入模組之後，會在背景執行緒上寫入快取。

  快取的預設位置為：

  - Windows PowerShell 5.1：`$env:LOCALAPPDATA\Microsoft\Windows\PowerShell`
  - PowerShell 6.0 和更新版本： `$env:LOCALAPPDATA\Microsoft\PowerShell`
  - 非 Windows 預設： `~/.cache/powershell`

  快取的預設檔案名為 `ModuleAnalysisCache` 。 當您安裝多個 PowerShell 實例時，檔案名會包含十六進位尾碼，以便每次安裝都有唯一的檔案名。

  > [!NOTE]
  > 如果命令探索無法正常運作，例如 Intellisense 會顯示不存在的命令，您可以刪除快取檔案。 下次您啟動 PowerShell 時，即會重新建立快取。

  若要變更快取的預設位置，請在啟動 PowerShell 之前設定環境變數。 對此環境變數所做的變更只會影響子進程。 該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。

  若要停用檔案快取，請將此值設定於無效的位置，例如︰

  ```powershell
  # `NUL` here is a special device on Windows that cannot be written to,
  # on non-Windows you would use `/dev/null`
  $env:PSModuleAnalysisCachePath = 'NUL'
  ```

  這會設定 **NUL** 裝置的路徑。 PowerShell 無法寫入路徑，但不會傳回錯誤。 您可以使用追蹤來查看報告的錯誤：

  ```powershell
  Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
  ```

- PSDisableModuleAnalysisCacheCleanup

  寫出模組分析快取時，PowerShell 會檢查不再存在的模組，以避免不必要的大型快取。 有時不需要這些檢查，在此情況下，您可以藉由將此環境變數值設定為來關閉這些檢查 `1` 。

  設定此環境變數會立即在目前的進程中生效。

- PSModulePath

  `$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。

  依預設，指派給的有效位置 `$env:PSModulePath` 為：

  - 全系統位置：這些資料夾包含 PowerShell 隨附的模組。 這些模組會儲存在 `$PSHOME\Modules` 位置中。 此外，這是安裝 Windows 管理模組的位置。

  - 使用者安裝的模組：這些是使用者所安裝的模組。
    `Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。 如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。

    - 在 Windows 中，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME\Documents\PowerShell\Modules` 資料夾。 **AllUsers** 範圍的位置是 `$env:ProgramFiles\PowerShell\Modules` 。
    - 在非 Windows 系統上，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME/.local/share/powershell/Modules` 資料夾。 **AllUsers** 範圍的位置是 `/usr/local/share/powershell/Modules` 。

  此外，在其他目錄中安裝模組的安裝程式（例如 [Program Files] 目錄）可以將其位置附加至的值 `$env:PSModulePath` 。

  如需詳細資訊，請參閱 [about_PSModulePath](about_PSModulePath.md)。

## <a name="managing-environment-variables"></a>管理環境變數

PowerShell 提供數種不同的方法來管理環境變數。

- 環境提供者磁片磁碟機
- Item Cmdlet
- .NET **System. 環境** 類別
- 在 Windows 中，系統主控台

### <a name="using-the-environment-provider"></a>使用環境提供者

每個環境變數都會以 **DictionaryEntry** 類別的實例來表示。 在每個 **DictionaryEntry** 物件中，環境變數的名稱是字典索引鍵。 變數的值是字典值。

若要在 PowerShell 中顯示代表環境變數之物件的屬性和方法，請使用 `Get-Member` Cmdlet。 例如，若要顯示磁片磁碟機中所有物件的方法和屬性 `Env:` ，請輸入：

```powershell
Get-Item -Path Env:* | Get-Member
```

PowerShell 環境提供者可讓您存取 PowerShell 磁片磁碟機中的環境變數 (`Env:` 磁片磁碟機) 。 此磁片磁碟機看起來很像檔案系統磁片磁碟機。 若要移至 `Env:` 磁片磁碟機，請輸入：

```powershell
Set-Location Env:
```

使用 Content Cmdlet 來取得或設定環境變數的值。

```powershell
PS Env:\> Set-Content -Path Test -Value 'Test value'
PS Env:\> Get-Content -Path Test
Test value
```

您可以 `Env:` 從任何其他 PowerShell 磁片磁碟機查看磁片磁碟機中的環境變數，也可以移至 `Env:` 磁片磁碟機來查看和變更環境變數。

### <a name="using-item-cmdlets"></a>使用 Item Cmdlet

當您參考環境變數時，請輸入 `Env:` 磁片磁碟機名稱，後面接著變數的名稱。 例如，若要顯示環境變數的值 `COMPUTERNAME` ，請輸入：

```powershell
Get-ChildItem Env:Computername
```

若要顯示所有環境變數的值，請輸入：

```powershell
Get-ChildItem Env:
```

由於環境變數沒有子專案，因此的輸出也 `Get-Item` `Get-ChildItem` 相同。

根據預設，PowerShell 會依照其抓取環境變數的順序來顯示。 若要依變數名稱排序環境變數的清單，請使用管線將命令的輸出傳送 `Get-ChildItem` 至 `Sort-Object` Cmdlet。 例如，從任何 PowerShell 磁片磁碟機，輸入：

```powershell
Get-ChildItem Env: | Sort Name
```

您也可以 `Env:` 使用 Cmdlet 移至磁片磁碟機 `Set-Location` ：

```powershell
Set-Location Env:
```

當您位於 `Env:` 磁片磁碟機時，您可以省略路徑中的 `Env:` 磁片磁碟機名稱。 例如，若要顯示所有環境變數，請輸入：

```powershell
PS Env:\> Get-ChildItem
```

若要顯示 `COMPUTERNAME` 磁片磁碟機中的變數值 `Env:` ，請輸入：

```powershell
PS Env:\> Get-ChildItem ComputerName
```

### <a name="saving-changes-to-environment-variables"></a>將變更儲存至環境變數

若要對 Windows 上的環境變數進行持續變更，請使用系統主控台。 選取 [ **Advanced System Settings** ]。 在 [ **Advanced （Advanced** ）] 索引標籤上，按一下 [ **環境變數 ...** ]。您可以在 **使用者** 和 **系統** (機) 範圍中新增或編輯現有的環境變數。 Windows 會將這些值寫入登錄，以便在會話和系統重新開機期間保存這些值。

或者，您也可以在 PowerShell 設定檔中新增或變更環境變數。 此方法適用于任何支援平臺上的任何 PowerShell 版本。

### <a name="using-systemenvironment-methods"></a>使用 System. 環境方法

**System. 環境** 類別提供 **GetEnvironmentVariable** 和 **SetEnvironmentVariable** 方法，可讓您指定變數的範圍。

下列範例會使用 **GetEnvironmentVariable** 方法來取得的電腦設定 `PSModulePath` ，並使用 **SetEnvironmentVariable** 方法來新增值的 `C:\Program Files\Fabrikam\Modules` 路徑。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable("PSModulePath", $newpath, 'Machine')
```

如需 **System. 環境** 類別方法的詳細資訊，請參閱 [環境方法](/dotnet/api/system.environment)。

## <a name="see-also"></a>另請參閱

- [環境 (提供者) ](../About/about_Environment_Provider.md)
- [about_Modules](about_Modules.md)

