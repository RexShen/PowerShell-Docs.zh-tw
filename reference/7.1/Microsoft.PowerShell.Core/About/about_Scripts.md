---
description: 說明如何在 PowerShell 中執行和寫入腳本。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: c877627f8caeab8309326826caa4ec13d65d5d9d
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206708"
---
# <a name="about-scripts"></a>關於腳本

## <a name="short-description"></a>簡短描述
說明如何在 PowerShell 中執行和寫入腳本。

## <a name="long-description"></a>完整描述

腳本是純文字檔案，其中包含一或多個 PowerShell 命令。
PowerShell 腳本有 `.ps1` 副檔名。

執行腳本很像是執行 Cmdlet。 您可以輸入腳本的路徑和檔案名，並使用參數來提交資料和設定選項。 您可以在電腦或不同電腦上的遠端會話中執行腳本。

撰寫腳本會儲存命令以供稍後使用，並可讓您輕鬆地與其他人共用。 最重要的是，它可讓您直接輸入腳本路徑和檔案名來執行命令。 腳本可以像是檔案中的單一命令一樣簡單，也可以像複雜程式一樣廣泛。

腳本具有其他功能，例如 `#Requires` 特殊批註、使用參數、支援資料區段，以及用於安全性的數位簽章。
您也可以撰寫腳本的說明主題，以及腳本中的任何函數。

## <a name="how-to-run-a-script"></a>如何執行腳本

您必須先變更預設的 PowerShell 執行原則，才能在 Windows 上執行腳本。 執行原則並不適用于在非 Windows 平臺上執行的 PowerShell。

預設的執行原則 `Restricted` 會防止所有腳本執行，包括您在本機電腦上撰寫的腳本。 如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

執行原則會儲存在登錄中，因此您只需要在每部電腦上變更一次。

若要變更執行原則，請使用下列程式。

在命令提示字元中，輸入：

```powershell
Set-ExecutionPolicy AllSigned
```

或

```powershell
Set-ExecutionPolicy RemoteSigned
```

變更會立即生效。

若要執行腳本，請輸入腳本檔案的完整名稱和完整路徑。

例如，若要在 C：\Scripts 目錄中執行 Get-ServiceLog.ps1 腳本，請輸入：

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

若要在目前的目錄中執行腳本，請輸入目前的目錄的路徑，或使用點來代表目前的目錄，後面接著路徑反斜線 (`.\`) 。

例如，若要在本機目錄中執行 ServicesLog.ps1 腳本，請輸入：

```powershell
.\Get-ServiceLog.ps1
```

如果腳本有參數，請在指令檔名之後輸入參數和參數值。

例如，下列命令會使用 Get-ServiceLog 腳本的 ServiceName 參數來要求 WinRM 服務活動的記錄檔。

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

做為安全性功能，當您按兩下檔案總管中的腳本圖示時，或是當您輸入腳本名稱但沒有完整路徑時（即使腳本是在目前的目錄中），PowerShell 並不會執行腳本。 如需在 PowerShell 中執行命令和腳本的詳細資訊，請參閱 [about_Command_Precedence](about_Command_Precedence.md)。

### <a name="run-with-powershell"></a>使用 PowerShell 執行

從 PowerShell 3.0 開始，您可以從檔案總管執行腳本。

若要使用「使用 PowerShell 執行」功能：

執行檔案總管，以滑鼠右鍵按一下指令檔名，然後選取 [使用 PowerShell 執行]。

「使用 PowerShell 執行」功能的設計目的是要執行沒有必要參數的腳本，而不會將輸出傳回命令提示字元。

如需詳細資訊，請參閱 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)。

### <a name="running-scripts-on-other-computers"></a>在其他電腦上執行腳本

若要在一或多部遠端電腦上執行腳本，請使用 Cmdlet 的 **FilePath** 參數 `Invoke-Command` 。

輸入腳本的路徑和檔案名作為 **FilePath** 參數的值。 指令碼必須位於本機電腦上，或在本機電腦可以存取的目錄中。

下列命令會 `Get-ServiceLog.ps1` 在名為 Server01 和 Server02 的遠端電腦上執行腳本。

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>取得腳本的說明

Get-Help Cmdlet 會取得腳本的說明主題，以及 Cmdlet 和其他命令類型的說明主題。 若要取得腳本的說明主題，請輸入，然後輸入 `Get-Help` 腳本的路徑和檔案名。 如果腳本路徑是在您的 `Path` 環境變數中，則您可以省略路徑。

例如，若要取得 ServicesLog.ps1 腳本的說明，請輸入：

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>如何撰寫腳本

腳本可以包含任何有效的 PowerShell 命令，包括單一命令、使用管線的命令、函數，以及 If 語句和 For 迴圈等控制結構。

若要撰寫腳本，請在文字編輯器中開啟新檔案、輸入命令，然後將它們儲存在副檔名為有效的檔案名的檔案中 `.ps1` 。

下列範例是一個簡單的腳本，可取得目前系統上執行的服務，並將它們儲存至記錄檔。 記錄檔檔案名會從目前的日期建立。

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

若要建立此腳本，請開啟文字編輯器或腳本編輯器、輸入這些命令，然後將它們儲存在名為的檔案中 `ServiceLog.ps1` 。

### <a name="parameters-in-scripts"></a>腳本中的參數

若要在腳本中定義參數，請使用 Param 語句。 `Param`語句必須是腳本中的第一個語句，除了批註和任何語句之外 `#Require` 。

腳本參數的運作方式類似于函式參數。 參數值可供腳本中的所有命令使用。 函數參數的所有功能（包括參數屬性和其具名引數）在腳本中也有效。

執行腳本時，腳本使用者在腳本名稱之後輸入參數。

下列範例顯示 `Test-Remote.ps1` 具有 **ComputerName** 參數的腳本。 這兩個腳本函數都可以存取 **ComputerName** 參數值。

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

若要執行此腳本，請在腳本名稱後面輸入參數名稱。 例如：

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

如需 Param 語句和函數參數的詳細資訊，請參閱 [about_Functions](about_Functions.md) 和 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

### <a name="writing-help-for-scripts"></a>撰寫腳本的說明

您可以使用下列兩種方法之一來撰寫腳本的說明主題：

- 腳本的 Comment-Based 說明

  使用批註中的特殊關鍵字來建立說明主題。 若要為腳本建立以批註為基礎的說明，必須將批註放在腳本檔案的開頭或結尾。 如需以批註為基礎的說明的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。

- 腳本的 XML-Based 說明

  建立以 XML 為基礎的說明主題，例如通常為 Cmdlet 建立的類型。 如果您要將說明主題翻譯成多種語言，則需要以 XML 為基礎的說明。

若要將腳本與以 XML 為基礎的說明主題產生關聯，請使用。.Externalhelp Help comment 關鍵字。 如需 .Externalhelp 關鍵字的詳細資訊，請參閱 [about_Comment_Based_Help](about_Comment_Based_Help.md)。 如需以 XML 為基礎之說明的詳細資訊，請參閱 [如何撰寫 Cmdlet 說明](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。

### <a name="returning-an-exit-value"></a>傳回結束值

根據預設，腳本結束時，腳本不會傳回結束狀態。 您必須使用 `exit` 語句來傳回腳本的結束代碼。 根據預設， `exit` 語句會傳回 `0` 。 您可以提供數值來傳回不同的結束狀態。 非零的結束代碼通常會發出錯誤信號。

在 Windows 上，允許和之間的任何數位 `[int]::MinValue` `[int]::MaxValue` 。

在 Unix 上，只 `[byte]::MinValue` 允許 (0) 和 `[byte]::MaxValue` (255) 之間的正數。 範圍中的負數會 `-1` `-255` 自動轉譯為正數，方法是新增
256. 例如， `-2` 會轉換成 `254` 。

在 PowerShell 中， `exit` 語句會設定變數的值 `$LASTEXITCODE` 。 在 Windows 命令 Shell ( # A0) 中，exit 語句會設定環境變數的值 `%ERRORLEVEL%` 。

任何非數位或外部平臺特定範圍的引數，都會轉譯為的值 `0` 。

## <a name="script-scope-and-dot-sourcing"></a>腳本範圍和點的來源

每個腳本都是在它自己的範圍中執行。 在腳本中建立的函式、變數、別名和磁片磁碟機只存在於腳本範圍中。 您無法在腳本執行的範圍中存取這些專案或其值。

若要在不同範圍中執行腳本，您可以指定範圍（例如 Global 或 Local），或在腳本中使用點（source）。

「點為來源」功能可讓您在目前的範圍中執行腳本，而不是在腳本範圍中執行。 當您執行以點為來源的腳本時，腳本中的命令會以您在命令提示字元中輸入它們的方式執行。 腳本所建立的函式、變數、別名和磁片磁碟機會在您工作的範圍內建立。 腳本執行之後，您可以使用所建立的專案，並存取其在會話中的值。

若為點來源 a 腳本，請在腳本路徑前面輸入一個點 (. ) 和一個空格。

例如：

```powershell
. C:\scripts\UtilityFunctions.ps1
```

或

```powershell
. .\UtilityFunctions.ps1
```

`UtilityFunctions.ps1`腳本執行之後，腳本所建立的函式和變數就會新增至目前的範圍。

例如，腳本會 `UtilityFunctions.ps1` 建立 `New-Profile` 函數和 `$ProfileName` 變數。

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

如果您 `UtilityFunctions.ps1` 在自己的腳本範圍中執行腳本，則 `New-Profile` 只有在腳本執行時，函式和 `$ProfileName` 變數才會存在。 當腳本結束時，會移除函式和變數，如下列範例所示。

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

當您的點來源為腳本並執行時，腳本會在您的範圍內的會話中建立函式 `New-Profile` 和 `$ProfileName` 變數。 腳本執行之後，您可以 `New-Profile` 在會話中使用函數，如下列範例所示。

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

如需範圍的詳細資訊，請參閱 about_Scopes。

## <a name="scripts-in-modules"></a>模組中的腳本

模組是一組相關的 PowerShell 資源，可作為一個單位來散發。 您可以使用模組來組織您的腳本、函數和其他資源。 您也可以使用模組，將程式碼散發給其他人，並取得來自信任來源的程式碼。

您可以將腳本包含在模組中，也可以建立腳本模組，這是完全或主要由腳本和支援資源所組成的模組。 腳本模組只是副檔名為 .psm1 的腳本。

如需模組的詳細資訊，請參閱 [about_Modules](about_Modules.md)。

## <a name="other-script-features"></a>其他腳本功能

PowerShell 有許多有用的功能，可供您在腳本中使用。

- `#Requires` -您可以使用 `#Requires` 語句來防止腳本在沒有指定的模組或嵌入式管理單元和指定的 PowerShell 版本的情況下執行。 如需詳細資訊，請參閱 about_Requires。

- `$PSCommandPath` -包含正在執行之腳本的完整路徑和名稱。 此參數在所有腳本中都是有效的。 此自動變數是在 PowerShell 3.0 中引進。

- `$PSScriptRoot` -包含執行腳本的目錄。 在 PowerShell 2.0 中，此變數僅適用于腳本模組 (`.psm1`) 。
  從 PowerShell 3.0 開始，它在所有腳本中都是有效的。

- `$MyInvocation` - `$MyInvocation` 自動變數包含目前腳本的相關資訊，包括其啟動或「叫用」的相關資訊。 當腳本正在執行時，您可以使用此變數及其屬性來取得腳本的相關資訊。 例如， `$MyInvocation` 。MyCommand： Path 變數包含腳本的路徑和檔案名。 `$MyInvocation`.行包含啟動腳本的命令，包括所有參數和值。

  從 PowerShell 3.0 開始， `$MyInvocation` 有兩個新的屬性，提供呼叫或叫用目前腳本之腳本的相關資訊。 只有當啟動程式或呼叫端為腳本時，才會填入這些屬性的值。

  - **PSCommandPath** 包含呼叫或叫用目前腳本之腳本的完整路徑和名稱。

  - **PSScriptRoot** 包含呼叫或叫用目前腳本之腳本的目錄。

  不同于 `$PSCommandPath` 和 `$PSScriptRoot` 自動變數（包含目前腳本的相關資訊），變數的 **PSCommandPath** 和 **PSScriptRoot** 屬性 `$MyInvocation` 會包含呼叫目前腳本之腳本的相關資訊。

- 資料區段-您可以使用 `Data` 關鍵字來分隔腳本中的邏輯資料。 資料區段也可以簡化當地語系化作業。 如需詳細資訊，請參閱 [about_Data_Sections](about_Data_Sections.md) 和 [about_Script_Internationalization](about_Script_Internationalization.md)。

- 腳本簽署-您可以將數位簽章新增至腳本。 視執行原則而定，您可以使用數位簽章來限制可能包含 unsafe 命令的腳本執行。 如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md) 和 [about_Signing](about_Signing.md)。

## <a name="see-also"></a>另請參閱

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
