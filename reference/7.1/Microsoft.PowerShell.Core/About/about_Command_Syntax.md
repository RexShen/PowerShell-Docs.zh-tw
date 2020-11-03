---
description: 描述 PowerShell 中使用的語法圖表。
keywords: powershell,cmdlet
ms.date: 06/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_command_syntax?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Command_Syntax
ms.openlocfilehash: a9da31213e76f5d28fbcb2cf4f4f6e9c49d51866
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208292"
---
# <a name="about-command-syntax"></a>關於命令語法

## <a name="short-description"></a>簡短描述
描述 PowerShell 中使用的語法圖表。

## <a name="long-description"></a>詳細描述

[Get-help](xref:Microsoft.PowerShell.Core.Get-Help)和[get 命令](xref:Microsoft.PowerShell.Core.Get-Command)Cmdlet 會顯示語法圖表，以協助您正確地建立命令。 本主題說明如何解讀語法圖表。

## <a name="syntax-diagrams"></a>語法圖表

命令語法圖表中的每個段落都代表一種有效的命令格式。

若要建立命令，請從左至右追蹤語法圖表。 從選擇性參數中選取，並提供預留位置的值。

PowerShell 會針對語法圖表使用下列標記法。

```powershell
<command-name> -<Required Parameter Name> <Required Parameter Value>
[-<Optional Parameter Name> <Optional Parameter Value>]
[-<Optional Switch Parameters>]
[-<Optional Parameter Name>] <Required Parameter Value>
```

以下是 [新別名](xref:Microsoft.PowerShell.Utility.New-Alias) Cmdlet 的語法。

```powershell
New-Alias [-Name] <string> [-Value] <string> [-Description <string>]
[-Force] [-Option {None | ReadOnly | Constant | Private | AllScope}]
[-PassThru] [-Scope <string>] [-Confirm] [-WhatIf] [<CommonParameters>]
```

為了方便起見，語法是大寫的，但 PowerShell 不區分大小寫。

語法圖表有下列元素。

## <a name="command-name"></a>命令名稱

命令的開頭一律是命令名稱，例如 `New-Alias` 。 輸入命令名稱或其別名，例如的 "gcm" `Get-Command` 。

## <a name="parameters"></a>參數

命令的參數是決定命令功能的選項。
某些參數會採用「值」，這是使用者輸入的命令。

例如， `Get-Help` 命令具有 **Name** 參數，可讓您指定說明顯示的主題名稱。 主題名稱是 **name** 參數的值。

在 PowerShell 命令中，參數名稱的開頭一律為連字號。
連字號會告訴 PowerShell 命令中的專案是參數名稱。

例如，若要使用的 Name 參數 `New-Alias` ，請輸入下列內容：

```powershell
-Name
```

參數可以是強制性或選擇性參數。 在語法圖中，選擇性的專案會以括弧括住 `[ ]` 。

如需參數的詳細資訊，請參閱 [about_Parameters](about_Parameters.md)。

## <a name="parameter-values"></a>參數值

參數值是參數所採用的輸入。 因為 Windows PowerShell 是以 Microsoft .NET Framework 為基礎，所以參數值會以其 .NET 類型以語法圖表表示。

例如，的 Name 參數會 `Get-Help` 採用「字串」值，這是一個文字字串，例如以引號括住的單一單字或多個字。

```powershell
[-Name] <string>
```

參數值的 .NET 類型會以角括弧括住， `< >` 表示它是值的預留位置，而不是您在命令中輸入的常值。

若要使用參數，請將 .NET 型別預留位置取代為具有指定 .NET 類型的物件。

例如，若要使用 **Name** 參數，請輸入 "-Name"，後面接著字串，如下所示：

```powershell
-Name MyAlias
```

## <a name="parameters-with-no-values"></a>沒有值的參數

某些參數不接受輸入，因此沒有參數值。
沒有值的參數稱為「切換參數」，因為它們的運作方式就像是開啟/關閉切換參數。 您可以將它們包含在) 上 (，或將它們從命令) 略過 (。

若要使用切換參數，請只輸入參數名稱，並在前面加上連字號。

例如，若要使用 Cmdlet 的 **WhatIf** 參數 `New-Alias` ，請輸入下列內容：

```powershell
-WhatIf
```

## <a name="parameter-sets"></a>參數集

命令的參數會列在參數集合中。 參數集看起來像是語法圖的段落。

`New-Alias`Cmdlet 有一個參數集，但許多 Cmdlet 都有多個參數集。 某些 Cmdlet 參數是參數集的唯一參數，而其他參數則出現在多個參數集內。 每個參數集都代表有效命令的格式。 參數集只包含可在命令中一起使用的參數。 如果參數無法在相同的命令中使用，它們會出現在不同的參數集中。

例如， [取得隨機](xref:Microsoft.PowerShell.Utility.Get-Random) Cmdlet 具有下列參數集：

```powershell
Get-Random [[-Maximum] <Object>] [-Minimum <Object>] [-SetSeed <int>]
[<CommonParameters>]

Get-Random [-InputObject] <Object[]> [-Count <int>] [-SetSeed <int>]
[<CommonParameters>]
```

第一個參數集（傳回亂數字）有 **最小** 和 **最大** 參數。 第二個參數集會從一組物件傳回隨機選取的物件，包含 **InputObject** 和 **Count** 參數。 這兩個參數集都有 **SetSeed** 參數和一般參數。

這些參數集會指出您可以在同一個命令中使用 **InputObject** 和 **count** 參數，但不能在同一個命令中使用 **Maximum** 和 **count** 參數。

您可以使用該參數集中的參數，指出您想要使用的參數集。

不過，每個 Cmdlet 也都有預設參數集。 當您未指定參數集的唯一參數時，就會使用預設參數集。 例如，如果您不使用 `Get-Random` 參數，Windows PowerShell 會假設您使用的是 **number** 參數集，而且會傳回一個亂數字。

在每個參數集，參數會以位置順序顯示。 只有當您省略選擇性參數名稱時，命令中的參數順序才有意義。 當省略參數名稱時，PowerShell 會依位置和類型將值指派給參數。 如需參數位置的詳細資訊，請參閱 `about_Parameters` 。

## <a name="symbols-in-syntax-diagrams"></a>語法圖表中的符號

語法圖表會列出命令名稱、命令參數和參數值。 它也會使用符號來示範如何建立有效的命令。

語法圖表會使用下列符號：

- 連字號 `-` 表示參數名稱。 在命令中，于參數名稱前面輸入連字號，但不含中間的空格，如語法圖所示。

  例如，若要使用的 **Name** 參數 `New-Alias` ，請輸入：

  ```powershell
  -Name
  ```

- 角括弧 `<>` 表示預留位置文字。 您未在命令中輸入角括弧或預留位置文字。 相反地，您會將它取代為它所描述的專案。

  角括弧用來識別參數所採用之值的 .NET 型別。 例如，若要使用 Cmdlet 的 **Name** 參數 `New-Alias` ，請將取代為 `<string>` 字串，也就是以引號括住的單一單字或單字群組。

- 括弧 `[ ]` 表示選擇性的專案。 參數和其值可以是選擇性的，或必要參數的名稱可以是選擇性的。

  例如，的 **Description** 參數 `New-Alias` 和其值會以括弧括住，因為兩者都是選擇性的。

  ```powershell
  [-Description <string>]
  ```

  括弧也指出 Name 參數值 `<string>` 是必要的，但參數名稱 "name" 是選擇性的。

  ```powershell
  [-Name] <string>
  ```

- 附加至 .NET 類型的右括弧和左括弧 `[]` ，表示參數可以接受該類型的一或多個值。 以逗號分隔的清單方式輸入值。

  例如，Cmdlet 的 **name** 參數 `New-Alias` 只接受一個字串，但 [Get 進程](xref:Microsoft.PowerShell.Management.Get-Process)的 **name** 參數可以接受一或多個字串。

  ```powershell
  New-Alias [-Name] <string>

  New-Alias -Name MyAlias
  ```

  ```powershell
  Get-Process [-Name] <string[]>

  Get-Process -Name Explorer, Winlogon, Services
  ```

- 括弧 `{}` 表示「列舉」，這是參數的一組有效值。

  大括弧中的值是以分隔號分隔 `|` 。 這些橫條表示「專有」或「選擇」，這表示您只能從大括弧內所列的一組值中選擇一個值。

  例如，指令程式的語法 `New-Alias` 包含下列 **選項** 參數的列舉值：

  ```powershell
  -Option {None | ReadOnly | Constant | Private | AllScope}
  ```

  大括弧和垂直線指出您可以為 **Option** 參數選擇任何一個列出的值，例如 "ReadOnly" 或 "AllScope"。

  ```powershell
  -Option ReadOnly
  ```

## <a name="optional-items"></a>選擇性專案

括弧 `[]` 括住選擇性專案。 例如，在 `New-Alias` Cmdlet 語法描述中， **範圍** 參數是選擇性的。 這在語法中是以括弧括住參數名稱和類型來表示：

```powershell
[-Scope <string>]
```

下列兩個範例都是正確的 `New-Alias` Cmdlet 用法：

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd -Value Update-TypeData -Scope Global
```

即使該參數的值為必要，參數名稱也可以是選擇性的。 這是以括弧括住參數名稱（而不是參數類型）的語法指出，如此範例中的 `New-Alias` Cmdlet：

```powershell
[-Name] <string> [-Value] <string>
```

下列命令會正確地使用 `New-Alias` Cmdlet。 命令會產生相同的結果。

```powershell
New-Alias -Name utd -Value Update-TypeData
New-Alias -Name utd Update-TypeData
New-Alias utd -Value Update-TypeData
New-Alias utd Update-TypeData
```

如果參數名稱未包含在語句中做為輸入，Windows PowerShell 會嘗試使用引數的位置，將值指派給參數。

下列範例不完整：

```powershell
New-Alias utd
```

此 Cmdlet 需要 **名稱** 和 **值** 參數的值。

在語法範例中，括弧也用於命名和轉換成 .NET Framework 類型。 在此內容中，括弧不表示元素是選擇性的。

## <a name="see-also"></a>另請參閱

- [about_Parameters](about_Parameters.md)
- [Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)
- [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

