---
description: 描述函式 `Prompt` ，並示範如何建立自訂 `Prompt` 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_prompts?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Prompts
ms.openlocfilehash: 15746fe1ce2c79189dd604b5b6244e337ad389a1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207600"
---
# <a name="about-prompts"></a>關於提示字元

## <a name="short-description"></a>簡短描述
描述函式 `Prompt` ，並示範如何建立自訂 `Prompt` 函數。

## <a name="long-description"></a>完整描述

PowerShell 命令提示字元指出 PowerShell 已準備好執行命令：

```
PS C:\>
```

PowerShell 提示字元是由內建函數所決定 `Prompt` 。 您可以藉由建立自己的函 `Prompt` 式，並將它儲存在您的 PowerShell 設定檔中，來自訂提示。

## <a name="about-the-prompt-function"></a>關於 Prompt 函數

此函式會 `Prompt` 判斷 PowerShell 提示字元的外觀。
PowerShell 隨附內建 `Prompt` 功能，但您可以藉由定義自己的函式來覆寫它 `Prompt` 。

`Prompt`函數具有下列語法：

```powershell
function Prompt { <function-body> }
```

`Prompt`函數必須傳回物件。 最佳做法是傳回字串或格式化為字串的物件。 建議的最大長度為 80 個字元。

例如，下列函數會傳回 `Prompt` "Hello，World" 字串，後面接著右角括弧 (`>`) 。

```powershell
PS C:\> function prompt {"Hello, World > "}
Hello, World >
```

### <a name="getting-the-prompt-function"></a>取得提示字元函式

若要取得函式 `Prompt` ，請使用 `Get-Command` Cmdlet 或使用函式 `Get-Item` 磁片磁碟機中的 Cmdlet。

例如：

```powershell
PS C:\> Get-Command Prompt

CommandType     Name      ModuleName
-----------     ----      ----------
Function        prompt
```

若要取得設定提示值的腳本，請使用點方法來取得函數的 **ScriptBlock** 屬性 `Prompt` 。

例如：

```powershell
(Get-Command Prompt).ScriptBlock
```

```Output
"PS $($executionContext.SessionState.Path.CurrentLocation)$('>' * ($nestedPromptLevel + 1)) "
# .Link
# https://go.microsoft.com/fwlink/?LinkID=225750
# .ExternalHelp System.Management.Automation.dll-help.xml
```

就像所有的函式一樣，此函式 `Prompt` 會儲存在 `Function:` 磁片磁碟機中。
若要顯示用來建立目前函數的腳本 `Prompt` ，請輸入：

```powershell
(Get-Item function:prompt).ScriptBlock
```

### <a name="the-default-prompt"></a>預設提示字元

只有當 `Prompt` 函數產生錯誤或未傳回物件時，才會顯示預設提示字元。

預設的 PowerShell 提示字元是：

```
PS>
```

例如，下列命令會將函數設定 `Prompt` 為 `$null` ，這是不正確。 因此會顯示預設提示字元。

```powershell
PS C:\> function prompt {$null}
PS>
```

因為 PowerShell 隨附內建提示，所以您通常不會看到預設提示字元。

### <a name="built-in-prompt"></a>內建提示

PowerShell 包含內建 `Prompt` 函數。

```powershell
function prompt {
    $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
      else { '' }) + 'PS ' + $(Get-Location) +
        $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

此函式 `Test-Path` 會使用 Cmdlet 來判斷是否 `$PSDebugContext` 已填入自動變數。 如果 `$PSDebugContext` 已填入，則您處於「偵測」模式，並且 `[DBG]:` 會新增至提示字元，如下所示：

```Output
[DBG]: PS C:\ps-test>
```

如果 `$PSDebugContext` 未填入，則函式會新增 `PS` 到提示字元。
而且，此函式會使用 `Get-Location` Cmdlet 來取得目前的檔案系統目錄位置。 然後，它會將右角括弧新增 (`>`) 。

例如：

```Output
PS C:\ps-test>
```

如果您是在嵌套的提示字元中，函式會將兩個角括弧新增 (`>>`) 到提示字元。 如果自動變數的值大於1，則 (您在嵌套提示字元中 `$NestedPromptLevel` 。 ) 

例如，當您在巢狀的提示字元中偵錯時，提示字元會類似下列提示字元︰

```Output
[DBG] PS C:\ps-test>>>
```

### <a name="changes-to-the-prompt"></a>提示的變更

Cmdlet 會將 `Enter-PSSession` 遠端電腦的名稱加到目前的函式 `Prompt` 。 當您使用 `Enter-PSSession` 指令程式來啟動遠端電腦的會話時，命令提示字元會變更為包含遠端電腦的名稱。 例如：

```Output
PS Hello, World> Enter-PSSession Server01
[Server01]: PS Hello, World>
```

其他 PowerShell 主機應用程式和替代 shell 可能會有自己的自訂命令提示字元。

如需 `$PSDebugContext` 和自動變數的詳細資訊 `$NestedPromptLevel` ，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。

### <a name="how-to-customize-the-prompt"></a>如何自訂提示

若要自訂提示，請撰寫新的函式 `Prompt` 。 函式未受保護，因此可以覆寫。

若要撰寫 `Prompt` 函數，請輸入下列內容：

```powershell
function prompt { }
```

然後在大括弧之間輸入命令或建立提示字元的字串。

例如，下列提示字元包含您的電腦名稱︰

```powershell
function prompt {"PS [$env:COMPUTERNAME]> "}
```

在 Server01 電腦上，提示字元會類似下列提示字元︰

```Output
PS [Server01] >
```

下列 `Prompt` 函數包含目前的日期和時間：

```powershell
function prompt {"$(Get-Date)> "}
```

提示字元類似下列提示字元︰

```Output
03/15/2012 17:49:47>
```

您也可以變更預設 `Prompt` 函數：

例如，下列修改過的函式 `Prompt` `[ADMIN]:` 會在使用 [以 **系統管理員身分執行** ] 選項開啟 powershell 時，新增至內建的 powershell 提示字元：

```powershell
function prompt {
  $identity = [Security.Principal.WindowsIdentity]::GetCurrent()
  $principal = [Security.Principal.WindowsPrincipal] $identity
  $adminRole = [Security.Principal.WindowsBuiltInRole]::Administrator

  $(if (Test-Path variable:/PSDebugContext) { '[DBG]: ' }
    elseif($principal.IsInRole($adminRole)) { "[ADMIN]: " }
    else { '' }
  ) + 'PS ' + $(Get-Location) +
    $(if ($NestedPromptLevel -ge 1) { '>>' }) + '> '
}
```

當您使用 [以 **系統管理員身分執行** ] 選項啟動 PowerShell 時，會出現類似下列提示的提示：

```Output
[ADMIN]: PS C:\ps-test>
```

下列函式會 `Prompt` 顯示下一個命令的歷程記錄識別碼。 若要查看命令歷程記錄，請使用 `Get-History` Cmdlet。

```powershell
function prompt {
   # The at sign creates an array in case only one history item exists.
   $history = @(Get-History)
   if($history.Count -gt 0)
   {
      $lastItem = $history[$history.Count - 1]
      $lastId = $lastItem.Id
   }

   $nextCommand = $lastId + 1
   $currentDirectory = Get-Location
   "PS: $nextCommand $currentDirectory >"
}
```

下列提示 `Write-Host` 會使用和 `Get-Random` Cmdlet 來建立隨機變更色彩的提示。 因為 `Write-Host` 寫入目前的主應用程式，但不會傳回物件，所以此函式會包含 `Return` 語句。 如果沒有，PowerShell 就會使用預設的提示字元 `PS>` 。

```powershell
function prompt {
    $color = Get-Random -Min 1 -Max 16
    Write-Host ("PS " + $(Get-Location) +">") -NoNewLine `
     -ForegroundColor $Color
    return " "
}
```

### <a name="saving-the-prompt-function"></a>儲存 Prompt 函數

就像任何函式一樣， `Prompt` 函數只存在於目前的會話中。 若要在 `Prompt` 未來的會話中儲存函式，請將它新增至您的 PowerShell 設定檔。 如需設定檔的詳細資訊，請參閱 [about_Profiles](about_Profiles.md)。

## <a name="see-also"></a>另請參閱

[Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Get-History](xref:Microsoft.PowerShell.Core.Get-History)

[Get-Random](xref:Microsoft.PowerShell.Utility.Get-Random)

[Write-Host](xref:Microsoft.PowerShell.Utility.Write-Host)

[about_Profiles](about_Profiles.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Debuggers](about_Debuggers.md)

[about_Automatic_Variables](about_Automatic_Variables.md)
