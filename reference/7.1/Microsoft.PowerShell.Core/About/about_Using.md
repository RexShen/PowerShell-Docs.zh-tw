---
description: 可讓您指定要在會話中使用的命名空間。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_using?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Using
ms.openlocfilehash: eaf983ad03676b4ac57a3b35bc44f72036da55b4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207451"
---
# <a name="about-using"></a>關於使用

## <a name="short-description"></a>簡短描述
可讓您指定要在會話中使用的命名空間。

## <a name="long-description"></a>詳細描述

`using`語句可讓您指定要在會話中使用的命名空間。 新增命名空間可簡化 .NET 類別和成員的使用，並可讓您從腳本模組和元件匯入類別。

`using`語句必須在腳本中的任何其他語句之前。

`using`語句不應該與 `using:` 變數的範圍修飾詞混淆。 如需詳細資訊，請參閱 [about_Remote_Variables](about_Remote_Variables.md)。

## <a name="syntax"></a>Syntax

若要指定要從中解析類型的 .NET 命名空間：

```
using namespace <.NET-namespace>
```

若要從 PowerShell 模組載入類別：

```
using module <module-name>
```

若要從 .NET 元件預先載入類型：

```
using assembly <.NET-assembly-path>
```

指定命名空間可讓您依名稱的簡短名稱來更輕鬆地參考類型。

將元件從該元件載入的 .NET 型別載入至腳本的剖析階段。 這可讓您建立新的 PowerShell 類別，以使用預先載入之元件中的類型。

如果您不是建立新的 PowerShell 類別，請改用 `Add-Type` Cmdlet。 如需詳細資訊，請參閱 [Add 類型](xref:Microsoft.PowerShell.Utility.Add-Type)。

## <a name="examples"></a>範例

### <a name="example-1---add-namespaces-for-typename-resolution"></a>範例 1-新增 typename 解析的命名空間

下列腳本會取得 "Hello World" 字串的密碼編譯雜湊。

請注意 `using namespace System.Text` ，和如何簡化在和和中對的 `using namespace System.IO` 參考 `[UnicodeEncoding]` `System.Text` `[Stream]` `[MemoryStream]` `System.IO` 。

```powershell
using namespace System.Text
using namespace System.IO

[string]$string = "Hello World"
## Valid values are "SHA1", "SHA256", "SHA384", "SHA512", "MD5"
[string]$algorithm = "SHA256"

[byte[]]$stringbytes = [UnicodeEncoding]::Unicode.GetBytes($string)

[Stream]$memorystream = [MemoryStream]::new($stringbytes)
$hashfromstream = Get-FileHash -InputStream $memorystream `
  -Algorithm $algorithm
$hashfromstream.Hash.ToString()
```

### <a name="example-2---load-classes-from-a-script-module"></a>範例 2-從腳本模組載入類別

在此範例中，我們有一個名為 **CardGames** 的 PowerShell 腳本模組，可定義下列類別：

- **CardGames**
- **CardGames 卡片**

`Import-Module` 和語句只會匯入模組函式 `#requires` 、別名和變數，如模組所定義。 未匯入類別。 此 `using module` 命令會匯入模組，也會載入類別定義。

```powershell
using module CardGames
using namespace CardGames

[Deck]$deck = [Deck]::new()
$deck.Shuffle()
[Card[]]$hand1 = $deck.Deal(5)
[Card[]]$hand2 = $deck.Deal(5)
[Card[]]$hand3 = $deck.Deal(5)
```

### <a name="example-3---load-classes-from-an-assembly"></a>範例 3-從元件載入類別

這個範例會載入元件，讓它的類別可以用來建立新的 PowerShell 類別。 下列腳本會建立一個衍生自 **DirectoryCoNtext** 類別的新 PowerShell 類別。

```powershell
using assembly 'C:\Program Files\PowerShell\7\System.DirectoryServices.dll'
using namespace System.DirectoryServices.ActiveDirectory

class myDirectoryClass : System.DirectoryServices.ActiveDirectory.DirectoryContext
{

  [DirectoryContext]$domain

  myDirectoryClass([DirectoryContextType]$ctx) : base($ctx)
  {
    $this.domain = [DirectoryContext]::new([DirectoryContextType]$ctx)
  }

}

$myDomain = [myDirectoryClass]::new([DirectoryContextType]::Domain)
$myDomain
```

```Output
domain                                                    Name UserName ContextType
------                                                    ---- -------- -----------
System.DirectoryServices.ActiveDirectory.DirectoryContext                    Domain
```

