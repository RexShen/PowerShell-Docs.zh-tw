---
description: 描述 PowerShell 如何決定要執行哪個命令。
keywords: powershell,cmdlet
ms.date: 02/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Precedence
ms.openlocfilehash: 0fc514f8e7e7894ae9da281867fd3d2fe61b89b6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208351"
---
# <a name="about-command-precedence"></a>關於命令優先順序

## <a name="short-description"></a>簡短描述
描述 PowerShell 如何決定要執行哪個命令。

## <a name="long-description"></a>完整描述

命令優先順序描述當會話包含一個以上具有相同名稱的命令時，PowerShell 如何決定要執行哪個命令。 使用相同名稱的命令可以隱藏或取代會話中的命令。 本文說明如何執行隱藏的命令，以及如何避免命令名稱衝突。

## <a name="command-precedence"></a>命令優先順序

當 PowerShell 會話包含一個以上具有相同名稱的命令時，PowerShell 會使用下列規則來決定要執行的命令。

如果您指定命令的路徑，PowerShell 會在路徑指定的位置執行命令。

例如，下列命令會執行 "C： TechDocs" 目錄中的 FindDocs.ps1 腳本 \\ ：

```
C:\TechDocs\FindDocs.ps1
```

除了命令位於 Path 環境變數中所列的路徑中， `$env:path` 或除非您指定腳本檔案的路徑，powershell 仍不會以安全性功能 (原生) 命令執行可執行檔（包括 PowerShell 腳本）。

若要執行目前目錄中的腳本，請指定完整路徑，或輸入點 `.\` 以表示目前的目錄。

例如，若要在目前的目錄中執行 FindDocs.ps1 檔案，請輸入：

```
.\FindDocs.ps1
```

### <a name="using-wildcards-in-execution"></a>在執行中使用萬用字元

您可以在命令執行中使用萬用字元。 使用萬用字元 *也稱為萬用字元。*

PowerShell 會在常值相符之前，執行具有萬用字元比對的檔案。

例如，請考慮具有下列檔案的目錄：

```
Get-ChildItem C:\temp\test


    Directory: C:\temp\test


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        5/20/2019   2:29 PM             28 a.ps1
-a----        5/20/2019   2:29 PM             28 [a1].ps1
```

這兩個腳本檔案都具有相同的內容： `$MyInvocation.MyCommand.Path` 。
此命令會顯示所叫用之腳本的名稱。

當您執行時 `[a1].ps1` ， `a.ps1` 即使檔案 `[a1].ps1` 是常值相符，也會執行該檔案。

```powershell
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\a.ps1
```

現在讓我們刪除檔案 `a.ps1` ，然後嘗試再次執行。

```powershell
Remove-Item C:\temp\test\a.ps1
C:\temp\test\[a1].ps1
```

```Output
C:\temp\test\[a1].ps1
```

您可以從執行這次的輸出中看到， `[a1].ps1` 因為常值比對是該萬用字元模式的唯一檔案相符項。

如需 PowerShell 如何使用萬用字元的詳細資訊，請參閱 [about_Wildcards](about_Wildcards.md)。

> [!NOTE]
> 若要將搜尋限制為相對路徑，您必須在腳本名稱之前加上 `.\` 路徑。 這會將命令搜尋限制在相對路徑中的檔案。 如果沒有這個前置詞，其他 PowerShell 語法可能會衝突，而且會有一些保證可以找到檔案。

如果您未指定路徑，則 PowerShell 在針對目前會話中載入的所有專案執行命令時，會使用下列優先順序：

  1. Alias
  2. 函式
  3. Cmdlet
  4. 外部可執行檔 (程式和非 PowerShell 腳本) 

因此，如果您輸入 "help"，PowerShell 會先尋找名為的別名，然後尋找名為的函式， `help` `Help` 最後是名為的 Cmdlet `Help` 。 它會執行它所找到的第一個 `help` 專案。

例如，如果您的會話包含 Cmdlet 和函式，且兩者皆為 `Get-Map` ，當您輸入時，PowerShell 會執行函式 `Get-Map` 。

> [!NOTE]
> 這僅適用于已載入的命令。 如果有一個 `build` 可執行檔和名稱為的函式別名 `build` `Invoke-Build` 未載入至目前的會話中，則 PowerShell 會改為執行 `build` 可執行檔。 如果在此情況下找不到外部可執行檔，則不會自動載入模組。 只有在找不到任何外部可執行檔時，才會叫用具有指定名稱的別名、函式或 Cmdlet，進而觸發其模組的自動載入。

當會話包含具有相同名稱之相同類型的專案時，PowerShell 會執行較新的專案。

例如，如果您從模組匯入另一個 `Get-Date` Cmdlet，當您輸入時 `Get-Date` ，PowerShell 會在原生版本上執行匯入的版本。

## <a name="hidden-and-replaced-items"></a>隱藏和取代的專案

由於這些規則的結果，專案可以用相同的名稱取代或隱藏專案。

如果您仍然可以存取原始專案（例如，藉由使用模組或嵌入式管理單元名稱來限定專案名稱），則專案會「隱藏」或「隱藏」。

例如，如果您匯入的函式名稱與會話中的 Cmdlet 相同，則會隱藏此 Cmdlet (但不會取代) ，因為它是從嵌入式管理單元或模組匯入。

如果您無法再存取原始專案，則會「取代」或「覆寫」專案。

例如，如果您匯入的變數與會話中的變數具有相同的名稱，則原始變數會被取代，而且無法再存取。
您無法使用模組名稱來限定變數。

此外，如果您在命令列中輸入函式，然後匯入具有相同名稱的函式，就會取代原始函式，而且無法再存取該函數。

### <a name="finding-hidden-commands"></a>尋找隱藏的命令

[Get 命令](xref:Microsoft.PowerShell.Core.Get-Command)Cmdlet 的 **all** 參數會取得具有指定名稱的所有命令，即使它們已隱藏或被取代亦同。 從 PowerShell 3.0 開始，根據預設， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。

在下列範例中，會話包含函式 `Get-Date` 和 [取得日期](xref:Microsoft.PowerShell.Utility.Get-Date) Cmdlet。

下列命令會取得在 `Get-Date` 您輸入時執行的命令 `Get-Date` 。

```powershell
Get-Command Get-Date
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
```

下列命令使用 **all** 參數來取得所有 `Get-Date` 命令。

```powershell
Get-Command Get-Date -All
```

```output
CommandType     Name                      ModuleName
-----------     ----                      ----------
Function        Get-Date
Cmdlet          Get-Date                  Microsoft.PowerShell.Utility
```

### <a name="running-hidden-commands"></a>執行隱藏的命令

您可以指定專案屬性來區別命令與可能有相同名稱的其他命令，以執行特定命令。 您可以使用這個方法來執行任何命令，但它特別適用于執行隱藏的命令。

#### <a name="qualified-names"></a>限定名稱

使用 Cmdlet 的模組限定名稱，可讓您執行具有相同名稱的專案所隱藏的命令。 例如，您可以藉 `Get-Date` 由使用其模組名稱（如其模組名稱 **Microsoft.PowerShell.Utility** ）來執行 Cmdlet。

撰寫您要散發的腳本時，請使用這個慣用的方法。 您無法預測腳本執行所在的會話中可能存在哪些命令。

```powershell
New-Alias -Name "Get-Date" -Value "Get-ChildItem"
Microsoft.PowerShell.Utility\Get-Date
```

```output
Tuesday, September 4, 2018 8:17:25 AM
```

若要執行 `New-Map` 模組所新增的命令 `MapFunctions` ，請使用其模組限定名稱：

```powershell
MapFunctions\New-Map
```

若要尋找從中匯入命令的模組，請使用命令的 **ModuleName** 屬性。

```
(Get-Command <command-name>).ModuleName
```

例如，若要尋找 Cmdlet 的來源 `Get-Date` ，請輸入：

```powershell
(Get-Command Get-Date).ModuleName
```

```output
Microsoft.PowerShell.Utility
```

> [!NOTE]
> 您無法限定變數或別名。

#### <a name="call-operator"></a>呼叫運算子

您也可以使用 `Call` 運算子 `&` 來執行隱藏的命令，方法是將它與 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的呼叫結合， (別名是 "Dir" ) `Get-Command` 或 [Get 模組](xref:Microsoft.PowerShell.Core.Get-Module)。

呼叫運算子會在子範圍內執行字串和腳本區塊。 如需詳細資訊，請參閱 [about_Operators](about_Operators.md)。

例如，如果您有一個名為 `Map` 的函式，該函式是由名為的別名所隱藏 `Map` ，請使用下列命令來執行函數。

```powershell
&(Get-Command -Name Map -CommandType Function)
```

或

```powershell
&(dir Function:\map)
```

您也可以將隱藏的命令儲存在變數中，讓它更容易執行。

例如，下列命令會將函數儲存 `Map` 在變數中 `$myMap` ，然後使用 `Call` 運算子來執行它。

```powershell
$myMap = (Get-Command -Name map -CommandType function)
&($myMap)
```

### <a name="replaced-items"></a>取代的專案

「已取代」專案是指無法再存取的專案。 您可以從模組或嵌入式管理單元匯入相同名稱的專案，以取代專案。

例如，如果您 `Get-Map` 在會話中輸入函式，並匯入名為的函式 `Get-Map` ，它會取代原始的函式。 您無法在目前的會話中取得它。

無法隱藏變數和別名，因為您無法使用呼叫運算子或限定名稱來執行它們。 當您從模組或嵌入式管理單元匯入變數和別名時，會以相同的名稱取代會話中的變數。

### <a name="avoiding-name-conflicts"></a>避免名稱衝突

管理命令名稱衝突的最佳方式是防止它們。 當您為命令命名時，請使用唯一的名稱。 例如，將您的姓名縮寫或公司名稱縮寫加入命令中的名詞。

此外，當您從 PowerShell 模組或另一個會話將命令匯入會話時，請使用 `Prefix` [import-module](xref:Microsoft.PowerShell.Core.Import-Module) 的參數或

[Import-module](xref:Microsoft.PowerShell.Utility.Import-PSSession) Cmdlet 會將前置詞新增至命令名稱中的名詞。

例如， `Get-Date` `Set-Date` 當您匯入模組時，下列命令可避免與 PowerShell 隨附的和 Cmdlet 發生衝突 `DateFunctions` 。

```powershell
Import-Module -Name DateFunctions -Prefix ZZ
```

如需詳細資訊，請參閱 `Import-Module` 和 `Import-PSSession` 下文。

## <a name="see-also"></a>另請參閱

- [about_Path_Syntax](about_Path_Syntax.md)
- [about_Aliases](about_Aliases.md)
- [about_Functions](about_Functions.md)
- [Alias-Provider](../../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)
- [Function-Provider](../../Microsoft.PowerShell.Core/About/about_Function_Provider.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)
- [Import-PSSession](xref:Microsoft.PowerShell.Utility.Import-PSSession)

