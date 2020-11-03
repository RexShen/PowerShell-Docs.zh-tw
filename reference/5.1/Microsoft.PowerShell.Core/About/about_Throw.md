---
description: 描述可產生終止錯誤的 Throw 關鍵字。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_throw?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Throw
ms.openlocfilehash: caac7679e2c7ecd21b4fa9e43ab76681ee3faed5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207528"
---
# <a name="about-throw"></a>關於擲回

## <a name="short-description"></a>簡短描述

描述可產生終止錯誤的 Throw 關鍵字。

## <a name="long-description"></a>詳細描述

Throw 關鍵字會導致終止錯誤。 您可以使用 Throw 關鍵字來停止處理命令、函數或腳本。

例如，您可以在 If 語句的腳本區塊中使用 Throw 關鍵字，以回應條件或 try-catch 語句的 Catch 區塊。 您也可以在參數宣告中使用 Throw 關鍵字，讓函式參數變成強制性。

Throw 關鍵字可以擲回任何物件，例如使用者訊息字串或造成錯誤的物件。

## <a name="syntax"></a>SYNTAX

Throw 關鍵字的語法如下所示：

```powershell
throw [<expression>]
```

Throw 語法中的運算式是選擇性的。 當 Throw 語句未出現在 Catch 區塊中，而且它不包含運算式時，它會產生 ScriptHalted 錯誤。

```powershell
C:\PS> throw

ScriptHalted
At line:1 char:6
+ throw <<<<
+ CategoryInfo          : OperationStopped: (:) [], RuntimeException
+ FullyQualifiedErrorId : ScriptHalted
```

如果在沒有運算式的 Catch 區塊中使用 Throw 關鍵字，它會再次擲回目前的 RuntimeException。 如需詳細資訊，請參閱 about_Try_Catch_Finally。

## <a name="throwing-a-string"></a>擲回字串

Throw 語句中的選擇性運算式可以是字串，如下列範例所示：

```powershell
C:\PS> throw "This is an error."

This is an error.
At line:1 char:6
+ throw <<<<  "This is an error."
+ CategoryInfo          : OperationStopped: (This is an error.:String) [], R
untimeException
+ FullyQualifiedErrorId : This is an error.
```

## <a name="throwing-other-objects"></a>擲回其他物件

運算式也可以是擲回代表 PowerShell 進程之物件的物件，如下列範例所示：

```powershell
C:\PS> throw (get-process PowerShell)

System.Diagnostics.Process (PowerShell)
At line:1 char:6
+ throw <<<<  (get-process PowerShell)
+ CategoryInfo          : OperationStopped: (System.Diagnostics.Process (Pow
erShell):Process) [],
RuntimeException
+ FullyQualifiedErrorId : System.Diagnostics.Process (PowerShell)
```

您可以使用 $error 自動變數中 ErrorRecord 物件的 TargetObject 屬性來檢查錯誤。

```powershell
C:\PS> $error[0].targetobject

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
319      26    61016      70864   568     3.28   5548 PowerShell
```

您也可以擲回 ErrorRecord 物件或 Microsoft .NET Framework 例外狀況。 下列範例會使用 Throw 關鍵字來擲回 >formatexception 物件。

```powershell
C:\PS> $formatError = new-object system.formatexception

C:\PS> throw $formatError

One of the identified items was in an invalid format.
At line:1 char:6
+ throw <<<<  $formatError
+ CategoryInfo          : OperationStopped: (:) [], FormatException
+ FullyQualifiedErrorId : One of the identified items was in an invalid
format.
```

## <a name="resulting-error"></a>產生的錯誤

Throw 關鍵字可以產生 ErrorRecord 物件。 ErrorRecord 物件的 Exception 屬性包含 RuntimeException 物件。 ErrorRecord 物件和 RuntimeException 物件的其餘部分，會隨著 Throw 關鍵字擲回的物件而不同。

RunTimeException 物件會包裝在 ErrorRecord 物件中，而 ErrorRecord 物件會自動儲存在 $Error 自動變數中。

## <a name="using-throw-to-create-a-mandatory-parameter"></a>使用 THROW 來建立必要參數

您可以使用 Throw 關鍵字來強制執行函式參數。

這是使用 Parameter 關鍵字的強制參數的替代方法。 當您使用強制參數時，系統會提示使用者輸入必要的參數值。 當您使用 Throw 關鍵字時，命令會停止並顯示錯誤記錄。

例如，在參數子運算式中的 Throw 關鍵字會讓 Path 參數成為函數中的必要參數。

在此情況下，Throw 關鍵字會擲回訊息字串，但如果未指定 Path 參數，則會產生 Throw 關鍵字來產生終止錯誤。 接下來的運算式是選擇性的。

```powershell
function Get-XMLFiles
{
  param ($path = $(throw "The Path parameter is required."))
  dir -path $path\*.xml -recurse |
    sort lastwritetime |
      ft lastwritetime, attributes, name  -auto
}
```

## <a name="see-also"></a>另請參閱

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

[about_Scopes](about_Scopes.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
