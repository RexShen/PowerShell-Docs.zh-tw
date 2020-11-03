---
description: 說明如何在遠端命令中使用區域和遠端變數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Variables
ms.openlocfilehash: 813b961d6e59dd85e09a461f8b5743924fecc673
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93206911"
---
# <a name="about-remote-variables"></a>關於遠端變數

## <a name="short-description"></a>簡短描述

說明如何在遠端命令中使用區域和遠端變數。

## <a name="long-description"></a>完整描述

您可以在遠端電腦上執行的命令中使用變數。 將值指派給變數，然後使用變數來取代該值。

根據預設，會假設在執行命令的會話中定義遠端命令中的變數。 在本機會話中定義的變數，必須在命令中識別為本機變數。

## <a name="using-remote-variables"></a>使用遠端變數

PowerShell 假設遠端命令中使用的變數是在命令執行所在的會話中定義。

在此範例中， `$ps` 變數是在命令執行所在的暫存會話中定義 `Get-WinEvent` 。

```powershell
Invoke-Command -ComputerName S1 -ScriptBlock {
  $ps = "*PowerShell*"; Get-WinEvent -LogName $ps
}
```

當命令在持續性會話（ **PSSession** ）中執行時，必須在該會話中定義遠端變數。

```powershell
$s = New-PSSession -ComputerName S1
Invoke-Command -Session $s -ScriptBlock {$ps = "*PowerShell*"}
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $ps}
```

## <a name="using-local-variables"></a>使用本機變數

您可以在遠端命令中使用本機變數，但必須在本機會話中定義變數。

從 PowerShell 3.0 開始，您可以使用 `Using` 範圍修飾符來識別遠端命令中的本機變數。

的語法如下所示 `Using` ：

```
$Using:<VariableName>
```

在下列範例中， `$ps` 會在本機會話中建立變數，但會在執行命令的會話中使用。 `Using`範圍修飾詞會識別 `$ps` 為本機變數。

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  Get-WinEvent -LogName $Using:ps
}
```

`Using`範圍修飾詞可用於 **PSSession** 中。

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {Get-WinEvent -LogName $Using:ps}
```

變數參考，例如 `$using:var` 從呼叫端的內容展開至變數的值 `$var` 。 您無法存取呼叫端的變數物件。
`Using`範圍修飾詞不能用來修改 **PSSession** 內的本機變數。 例如，下列程式碼無法運作：

```powershell
$s = New-PSSession -ComputerName S1
$ps = "*PowerShell*"
Invoke-Command -Session $s -ScriptBlock {$Using:ps = 'Cannot assign new value'}
```

如需的詳細資訊 `Using` ，請參閱 [about_Scopes](./about_Scopes.md)

### <a name="using-splatting"></a>使用展開

PowerShell 展開會將參數名稱和值的集合傳遞至命令。 如需詳細資訊，請參閱 [about_Splatting](about_Splatting.md)。

在此範例中，展開變數 `$Splat` 是在本機電腦上設定的雜湊表。 `Invoke-Command`連接至遠端電腦會話。 **ScriptBlock** 使用 `Using` 範圍修飾詞搭配 At (`@`) 符號來表示 splatted 變數。

```powershell
$Splat = @{ Name = "Win*"; Include = "WinRM" }
Invoke-Command -Session $s -ScriptBlock { Get-Service @Using:Splat }
```

### <a name="other-situations-where-the-using-scope-modifier-is-needed"></a>需要 ' Using ' 範圍修飾詞的其他情況

針對任何執行的腳本或命令，您必須 `Using` 要有範圍修飾詞，才能從呼叫會話範圍內嵌變數值，讓會話外的程式碼可以存取它們。 `Using`下列內容支援範圍修飾符：

- 從遠端執行的命令，從 `Invoke-Command` 使用 **ComputerName** 、 **HostName** 、 **SSHConnection** 或 **Session** 參數開始， (遠端會話) 
- 背景工作，以 `Start-Job` (跨進程會話開始) 
- 透過 `Start-ThreadJob` (個別執行緒會話啟動的執行緒作業) 

視內容而定，內嵌變數值是呼叫端範圍中資料的獨立複本，或是對它的參考。 在遠端和跨進程的會話中，它們一律是獨立的複本。 線上程會話中，它們是以傳址方式傳遞。

## <a name="serialization-of-variable-values"></a>變數值的序列化

遠端執行的命令和背景工作會跨進程執行。
跨進程會話使用以 XML 為基礎的序列化和還原序列化，讓變數的值可以跨進程界限使用。 序列化程式會將物件轉換為包含原始物件屬性但不包含其方法的 **PSObject** 。

針對一組有限的類型，還原序列化會將解除凍結物件回原始型別。 解除凍結物件是原始物件實例的複本。
它具有類型屬性和方法。 針對簡單類型（例如 **system.object** ），複本是精確的。 如果是複雜類型，則會完美複製。 例如，解除凍結憑證物件不包含私密金鑰。

所有其他類型的實例都是 **PSObject** 實例。 **PSTypeNames** 屬性包含 **前面加上** 還原序列化的原始型別名稱，例如 **Deserialized.System。Data DataTable**

## <a name="using-local-variables-with-argumentlist-parameter"></a>使用本機變數搭配 **ArgumentList** 參數

您可以在遠端命令中使用區域變數，方法是定義遠端命令的參數，並使用 Cmdlet 的 **ArgumentList** 參數 `Invoke-Command` 將區域變數指定為參數值。

- 使用 `param` 關鍵字來定義遠端命令的參數。 參數名稱是預留位置，不需要符合區域變數的名稱。

- 在命令中使用關鍵字所定義的參數 `param` 。

- 使用 Cmdlet 的 **ArgumentList** 參數 `Invoke-Command` ，將區域變數指定為參數值。

例如，下列命令 `$ps` 會定義本機會話中的變數，然後在遠端命令中使用它。 此命令會使用 `$log` 做為參數名稱和區域變數， `$ps` 做為其值。

```powershell
$ps = "*PowerShell*"
Invoke-Command -ComputerName S1 -ScriptBlock {
  param($log)
  Get-WinEvent -LogName $log
} -ArgumentList $ps
```

## <a name="see-also"></a>另請參閱

[about_PSSessions](about_PSSessions.md)

[about_Remote](about_Remote.md)

[about_Scopes](about_Scopes.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)

[Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Start-ThreadJob](xref:ThreadJob.Start-ThreadJob)
