---
description: 變數
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 變數提供者
ms.openlocfilehash: c58ec641db0902088bf931d8bf4a48f5f7fa2ab8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206815"
---
# <a name="variable-provider"></a>變數提供者

## <a name="provider-name"></a>提供者名稱
變數

## <a name="drives"></a>磁碟機

`Variable:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>簡短描述

提供對 PowerShell 變數和其值的存取。

## <a name="detailed-description"></a>詳細描述

PowerShell **變數** 提供者可讓您取得、新增、變更、清除及刪除目前主控台中的 PowerShell 變數。

PowerShell **變數** 提供者支援 powershell 所建立的變數，包括自動變數、喜好設定變數，以及您所建立的變數。

**變數** 磁片磁碟機是只包含變數物件的一般命名空間。 變數沒有任何子項目。

**變數** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell 也包含一組特別設計來查看和變更變數的 Cmdlet。 當您使用 **變數** Cmdlet 時，不需要 `Variable:` 在名稱中指定磁片磁碟機。 本文未涵蓋使用 **變數** Cmdlet。

- [Get-Variable](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [New-Variable](xref:Microsoft.PowerShell.Utility.New-Variable)
- [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> 您也可以使用 PowerShell 運算式剖析器來建立、查看和變更變數的值，而不需要使用 Cmdlet。 直接使用變數時，請使用貨幣符號 (`$`) 將名稱識別為變數，並使用指派運算子 (`=`) 建立和變更其值。 例如， `$p = Get-Process` `p` 會建立變數，並將命令的結果儲存 `Get-Process` 在其中。

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

變數可以是數種不同類型的其中一種。 大部分的變數都是類別的實例 `PSVariable` 。 以下列出其他變數和其類型。

- `?`變數是類別的實例 `QuestionMarkVariable` 。
- `null`變數是類別的實例 `NullVariable` 。
- 最大計數變數是類別的實例 `SessionStateCapacityVariable` 。
- `LocalVariable` 實例包含目前執行的相關資訊，例如：
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a>流覽變數磁片磁碟機

**變數** 提供者會在磁片磁碟機中公開它的資料存放區 `Variable:` 。 若要使用變數，您可以將位置變更為 `Variable:` 磁片磁碟機 (`Set-Location Variable:`) ，也可以從任何其他的 PowerShell 磁片磁碟機工作。 若要從另一個位置參考變數，請在路徑中使用磁片磁碟機名稱 (`Variable:`) 。

```powershell
Set-Location Variable:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

您也可以從任何其他 PowerShell 磁片磁碟機使用 **變數** 提供者。 若要從另一個位置參考變數，請在路徑中使用磁片磁碟機名稱 `Variable:` 。

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

## <a name="displaying-the-value-of-variables"></a>顯示變數的值

### <a name="get-all-variables-in-the-current-session"></a>取得目前會話中的所有變數

此命令會取得目前工作階段中所有變數及其值的清單。 您可以從任何 PowerShell 磁片磁碟機使用此命令。

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a>使用其提供者路徑取得變數

此命令會使用前面加上貨幣符號 () 的提供者路徑來抓取變數值 `$` 。 這與在變數名稱前面加上貨幣符號 () 的效果相同 `$` 。

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a>使用萬用字元取得變數

此命令會取得名稱以 "max" 開頭的變數。 您可以從任何 PowerShell 磁片磁碟機使用此命令。

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a>取得的值？ 變動

此命令會使用 `-LiteralPath` [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 的參數， `?` 從磁片磁碟機中取得變數的值 `Variable:` 。 在 `?` 路徑中是萬用字元，但不 `Get-ChildItem` 會嘗試解析參數值中的任何萬用字元 `-LiteralPath` 。

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a>取得 ReadOnly 和常數變數

此命令會取得 `ReadOnly` `Constant` 其 **Options** 屬性的值為或的變數。

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a>建立變數

### <a name="create-a-new-variable"></a>建立新的變數

此命令會建立 `services` 變數，並將命令的結果儲存 `Get-Service` 在其中。 因為目前的位置是在 `Variable:` 磁片磁碟機中，所以參數的值 `-Path` 為點 (`.`) ，代表目前的位置。

命令周圍的括弧 `Get-Service` 可確保在建立變數之前執行此命令。 如果沒有括號，新變數的值就是 "Get-Service" 字串。

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a>使用絕對路徑建立變數

此命令會建立 `services` 變數，並將命令的結果儲存 `Get-Service` 在其中。

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 若要建立不含值的變數，請省略指派運算子。

## <a name="changing-variables"></a>變更變數

### <a name="rename-a-variable"></a>重新命名變數

此命令會使用 `Rename-Item` Cmdlet 將變數名稱變更 `a` 為 `processes` 。

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a>變更變數的值

此命令會使用 `Set-Item` Cmdlet 將變數的值變更 `ErrorActionPreference` 為 "Stop"。

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a>複製變數

此命令會使用 `Copy-Item` Cmdlet 將變數複製 `processes` 到 `old_processes` 。 這會建立名為的新變數 `old_processes` ，其值與 `processes` 變數相同。

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a>刪除變數

此命令會 `serv` 從目前的會話刪除變數。 您可以在任何 PowerShell 磁片磁碟機中使用此命令。

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a>使用-Force 參數刪除變數

此命令會從目前的會話刪除所有變數，但 **Options** 屬性具有值的變數除外 `Constant` 。 如果沒有 `-Force` 參數，命令就不會刪除 **Options** 屬性具有值的變數 `ReadOnly` 。

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a>將變數的值設定為 Null

此命令會使用 `Clear-Item` Cmdlet 將變數的值變更 `processes` 為 Null。

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a>使用管線

提供者 Cmdlet 接受管線輸入。 您可以使用管線將提供者資料從一個 Cmdlet 傳送到另一個提供者 Cmdlet，以簡化工作。
若要深入瞭解如何搭配使用管線與提供者 Cmdlet，請參閱本文中提供的 Cmdlet 參考。

## <a name="getting-help"></a>取得說明

從 Windows PowerShell 3.0 開始，您可以取得提供者 Cmdlet 的自訂說明主題，這些主題說明這些 Cmdlet 在檔案系統磁碟機中的行為方式。

若要取得針對檔案系統磁片磁碟機自訂的說明主題，請在檔案系統磁片磁碟機中執行 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 命令，或使用 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 的參數來指定檔案系統磁片磁碟機。

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a>另請參閱

[about_Variables](../About/about_Variables.md)

[about_Automatic_Variables](../About/about_Automatic_Variables.md)

[about_Providers](../About/about_Providers.md)
