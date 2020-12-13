---
title: 從 Windows PowerShell 5.1 移轉至 PowerShell 7
description: 針對您的 Windows 平台，從 PowerShell 5.1 更新為 PowerShell 7。
ms.date: 03/25/2020
ms.openlocfilehash: cb14a4f159b6dc33f31386da4264c0ebb640aef8
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "83809204"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>從 Windows PowerShell 5.1 移轉至 PowerShell 7

PowerShell 7 是針對雲端、內部部署和混合式環境所設計，具有增強功能和[新功能](../whats-new/What-s-New-in-PowerShell-70.md)。

- 與 Windows PowerShell 並存安裝和執行
- 改善與現有 Windows PowerShell 模組的相容性
- 新的語言功能，例如三元運算子和 `ForEach-Object -Parallel`
- 提升效能
- 以 SSH 為基礎的遠端功能
- 跨平台互通性
- 支援 Docker 容器

PowerShell 7 與 Windows PowerShell 並存運作，可讓您在部署之前，輕鬆地在版本之間進行測試和比較。 移轉既簡單又快速，而且很安全。

下列 Windows 作業系統支援 PowerShell 7：

- Windows 8.1 和 10
- Windows Server 2012、2012 R2、2016 及 2019

PowerShell 7 也可以在 macOS 和數個 Linux 散發套件上執行。 如需支援的作業系統清單和支援生命週期的詳細資訊，請參閱 [PowerShell 支援生命週期](/powershell/scripting/powershell-support-lifecycle)。

## <a name="installing-powershell-7"></a>安裝 PowerShell 7

為了提供彈性並支援 IT、DevOps 工程師和開發人員的需求，有數個選項可用來安裝 PowerShell 7。 在大部分情況下，安裝選項可以縮減為下列方法：

- 使用 [MSI 套件](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)來部署 PowerShell
- 使用 [ZIP 套件](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)來部署 PowerShell

> [!NOTE]
> 您可以使用 [System Center Configuration Manager (SCCM)](/configmgr/apps/) 之類的管理產品來部署及更新 MSI 套件。 從 [GitHub 版本頁面](https://github.com/PowerShell/PowerShell/releases)下載套件。

部署 MSI 套件需要系統管理員權限。 任何使用者都可以部署 ZIP 套件。 在認可完整安裝之前，ZIP 套件是安裝 PowerShell 7 以進行測試最簡單的方式。

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>與 Windows PowerShell 5.1 並存使用 PowerShell 7

PowerShell 7 的設計是與 Windows PowerShell 5.1 並存。 下列功能可確保您在 PowerShell 中的投資受到保護，且您移轉至 PowerShell 7 很簡單。

- 個別安裝路徑和可執行檔名稱
- 個別 PSModulePath
- 每個版本都有個別設定檔
- 改良的模組相容性
- 新的遠端端點
- 群組原則支援
- 個別事件記錄檔

### <a name="separate-installation-path-and-executable-name"></a>個別安裝路徑和可執行檔名稱

PowerShell 7 會安裝到新目錄，並與 Windows PowerShell 5.1 並存執行。

依版本的安裝位置：

- Windows PowerShell 5.1：`$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6.x：`$env:ProgramFiles\PowerShell\6`
- PowerShell 7：`$env:ProgramFiles\PowerShell\7`

新的位置會新增至您的 PATH，讓您能夠同時執行 Windows PowerShell 5.1 和 PowerShell 7。 如果您要從 PowerShell Core 6.x 遷移至 PowerShell 7，則會移除 PowerShell 6 並取代 PATH。

在 Windows PowerShell 中，PowerShell 可執行檔的名稱為 `powershell.exe`。 在第 6 版和更新版本中，可執行檔的名稱為 `pwsh.exe`。 新的名稱可讓您輕鬆地支援這兩個版本的並存執行。

### <a name="separate-psmodulepath"></a>個別 PSModulePath

根據預設，Windows PowerShell 和 PowerShell 7 會在不同的位置儲存模組。 PowerShell 7 會將這些位置合併到 `$Env:PSModulePath` 環境變數中。 依名稱匯入模組時，PowerShell 會檢查 `$Env:PSModulePath` 所指定的位置。 這可讓 PowerShell 7 同時載入核心和桌面模組。

|            安裝範圍            |                Windows PowerShell 5.1                 |             PowerShell 7.0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| PowerShell 模組                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| 使用者已安裝<br>AllUsers 範圍    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| 使用者已安裝<br>CurrentUser 範圍 | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

下列範例會顯示每個版本的 `$Env:PSModulePath` 預設值。

- 若是 Windows PowerShell 5.1：

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- 若是 PowerShell 7：

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

請注意，PowerShell 7 包含 Windows PowerShell 路徑和 PowerShell 7 路徑，以提供模組的自動載入。

> [!NOTE]
> 如果您已變更 PSModulePath 環境變數或已安裝自訂模組或應用程式，則可能會有其他路徑。

如需詳細資訊，請參閱 [about_Environment_Variables](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences) 中的 `PSModulePath`。

如需有關模組的詳細資訊，請參閱 [about_Modules](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules)。

### <a name="separate-profiles"></a>個別設定檔

PowerShell 設定檔是在 PowerShell 啟動時執行的指令碼。 此指令碼會藉由新增命令、別名、函式、變數、模組和 PowerShell 磁碟機，以自訂您的環境。 設定檔指令碼可讓您在每個工作階段中使用這些自訂項目，而不必手動重新建立。

在 PowerShell 7 中，設定檔位置的路徑已變更。

- 在 Windows PowerShell 5.1 中，設定檔的位置是 `$HOME\Documents\WindowsPowerShell`。
- 在 PowerShell 7 中，設定檔的位置是 `$HOME\Documents\PowerShell`。

設定檔檔名也已變更：

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

如需詳細資訊，請參閱 [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)。

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>PowerShell 7 與 Windows PowerShell 5.1 模組的相容性

您在 Windows PowerShell 5.1 中使用的大部分模組都已經與 PowerShell 7 搭配使用，包括 Azure PowerShell 和 Active Directory。 我們會繼續與其他小組合作，以新增更多模組的原生 PowerShell 7 支援，包括 Microsoft Graph、Office 365 和其他模組。 如需目前支援模組的清單，請參閱 [PowerShell 7 模組相容性](/powershell/scripting/whats-new/module-compatibility)。

> [!NOTE]
> 在 Windows 上，我們也將 **UseWindowsPowerShell** 參數新增至 `Import-Module`，讓使用不相容模組的程式能夠更容易轉換至 PowerShell 7。 如需此功能的詳細資訊，請參閱 [about_Windows_PowerShell_Compatibility](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility)。

### <a name="powershell-remoting"></a>PowerShell 遠端功能

PowerShell 遠端功能可讓您在一或多部遠端電腦上執行任何 PowerShell 命令。 您可以建立持續連線、啟動互動式工作階段，以及在遠端電腦上執行指令碼。

#### <a name="ws-management-remoting"></a>WS-MANAGEMENT 遠端功能

Windows PowerShell 5.1 和較舊版本使用 WS-Management (WSMAN) 通訊協定進行連線協商和資料傳輸。 Windows 遠端管理 (WinRM) 使用 WSMAN 通訊協定。 如果已啟用 WinRM，PowerShell 7 會使用名為 `Microsoft.PowerShell` 的現有 Windows PowerShell 5.1 端點來進行遠端連線。 若要更新 PowerShell 7 以包含其自己的端點，請執行 `Enable-PSRemoting` Cmdlet。 如需連線至特定端點的詳細資訊，請參閱 [PowerShell Core 中的 WS-Management 遠端功能](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)

若要使用 Windows PowerShell 遠端執行功能，必須針對遠端管理設定遠端電腦。
如需包括指示的詳細資訊，請參閱[關於遠端需求](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)。

如需有關使用遠端功能的詳細資訊，請參閱[關於遠端](/powershell/module/microsoft.powershell.core/about/about_remote)

#### <a name="ssh-based-remoting"></a>以 SSH 為基礎的遠端功能

PowerShell Core 6.x 中已新增以 SSH 為基礎的遠端功能，以支援無法使用 Windows 原生元件 (例如 **WinRM**) 的其他作業系統。 SSH 遠端功能會在目標電腦上建立 PowerShell 裝載處理序作為 SSH 子系統。 如需在 Windows 或 Linux 上設定以 SSH 為基礎的遠端功能的詳細資訊和範例，請參閱：[透過 SSH 的 PowerShell 遠端功能](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)

> [!NOTE]
> PowerShell 資源庫 (PSGallery) 包含可自動設定以 SSH 為基礎的遠端功能的模組和 Cmdlet。 從 [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) 安裝 `Microsoft.PowerShell.RemotingTools` 模組，然後執行 `Enable-SSH` Cmdlet。

`New-PSSession`、`Enter-PSSession` 和 `Invoke-Command` Cmdlet 都有新的參數集，可支援 SSH 連線。

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

若要建立遠端工作階段，請使用 **HostName** 參數來指定目標電腦，並使用 **UserName** 來提供使用者名稱。 以互動方式執行 Cmdlet 時，系統會提示您輸入密碼。

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

或者，使用 **HostName** 參數時，請提供使用者名稱資訊，後面加上 at 符號 (`@`)，後面接著電腦名稱。

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

您可以搭配 **KeyFilePath** 參數使用私密金鑰檔案，來設定 SSH 金鑰驗證。
如需詳細資訊，請參閱 [OpenSSH 金鑰管理](/windows-server/administration/openssh/openssh_keymanagement)。

### <a name="group-policy-supported"></a>支援的群組原則

PowerShell 包含群組原則設定，可協助您為企業環境中的伺服器定義一致的選項值。 這些設定包括：

- 主控台工作階段設定：設定 PowerShell 執行所在的設定端點。
- 開啟模組記錄：設定模組的 LogPipelineExecutionDetails 屬性。
- 開啟 PowerShell 指令碼區塊記錄：啟用所有 PowerShell 指令碼的詳細記錄。
- 開啟指令碼執行：設定 PowerShell 執行原則。
- 開啟 PowerShell 轉譯：將 PowerShell 命令的輸入和輸出，擷取到以文字為基礎的文字記錄。
- 設定 Update-Help 的預設來源路徑：將「可更新的說明」來源設定為目錄，而不是網際網路。

如需詳細資訊，請參閱 [about_Group_Policy_Settings](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings)。

PowerShell 7 包含群組原則範本，以及 `$PSHOME` 中的安裝指令碼。

群組原則工具會使用系統管理範本檔案 (`.admx`、`.adml`)，在使用者介面中填入原則設定。 這樣可讓系統管理員管理以登錄為基礎的原則設定。 `InstallPSCorePolicyDefinitions.ps1` 指令碼會在本機電腦上安裝 PowerShell Core 系統管理範本。

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>個別事件記錄檔

Windows PowerShell 和 PowerShell 7 將事件記錄到個別事件記錄檔。 使用下列命令來取得 PowerShell 記錄的清單。

```powershell
Get-WinEvent -ListLog *PowerShell*
```

如需詳細資訊，請參閱 [about_Logging_Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows)。

## <a name="improved-editing-experience-with-visual-studio-code"></a>改善 Visual Studio Code 的編輯體驗

[Visual Studio Code (VSCode)](https://code.visualstudio.com/) 與 [PowerShell 延伸模組](https://code.visualstudio.com/docs/languages/powershell)是 PowerShell 7 的支援指令碼環境。 Windows PowerShell 整合式指令碼環境 (ISE) 僅支援 Windows PowerShell。

更新的 PowerShell 延伸模組包括：

- 新的 ISE 相容性模式
- 整合式主控台中的 PSReadLine，包括語法醒目提示、多行編輯和上一頁搜尋
- 穩定性與效能提升
- 新的 CodeLens 整合
- 已改善路徑自動完成

若要更輕鬆地轉換為 Visual Studio Code，請使用 [命令選擇區] 中提供的 **Enable ISE Mode** 函式。 此函式會將 VSCode 切換為 ISE 樣式配置。 ISE 樣式配置以熟悉的使用者體驗，為您提供 PowerShell 的所有新特性和功能。

若要切換至新的 ISE 配置，請按 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> 以開啟 [命令選擇區]，輸入 `PowerShell` 並選取 [**PowerShell：啟用 ISE 模式**]。

若要將配置設定為原始配置，請開啟 [命令選擇區]，然後選取 [**PowerShell：停用 ISE 模式 (還原為預設值)**]。

如需有關自訂 VSCode 配置至 ISE 的詳細資訊，請參閱[如何在 Visual Studio Code 中複寫 ISE 體驗](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)

> [!NOTE]
> 沒有計劃要以新功能更新 ISE。 ISE 現在是最新版本 Windows 10 和 Windows Server 中的使用者可解除安裝功能。 沒有計劃要永久移除 ISE。 PowerShell 小組及其合作夥伴著重於改善適用於 Visual Studio Code 的 PowerShell 延伸模組指令碼體驗。

## <a name="next-steps"></a>後續步驟

有了有效遷移的知識，立即[安裝 PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows)！
