---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 取得詳細的說明資訊
ms.openlocfilehash: e722eb8a0ca13e3d2de864314775a0a9fa578390
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417653"
---
# <a name="getting-detailed-help-information"></a>取得詳細的說明資訊

PowerShell 包含詳細的說明文章，可說明 PowerShell 概念與 PowerShell 語言。 此外，還有針對每個 Cmdlet 和提供者，以及許多函式與指令碼的說明文章。

您可以在命令提示字元中顯示這些說明文章，或在 [PowerShell](/powershell/scripting/overview) 文件中線上檢視這些文章的最近更新版本。

## <a name="getting-help-for-cmdlets"></a>取得 Cmdlet 的說明

若要取得 PowerShell Cmdlet 的相關說明，請使用 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) Cmdlet。 例如，若要取得 `Get-ChildItem` Cmdlet 的說明，請輸入：

```powershell
Get-Help Get-ChildItem
```

或

```powershell
Get-ChildItem -?
```

您甚至可以取得 Get-Help Cmdlet 的相關說明。 例如：

```powershell
Get-Help Get-Help
```

若要取得工作階段中的所有 Cmdlet 說明文章清單，請輸入：

```powershell
Get-Help -Category Cmdlet
```

若要一次顯示一頁說明文章，請使用 `help` 函式或其別名 `man`。
例如，若要顯示 `Get-ChildItem` Cmdlet 的說明，請輸入

```powershell
man Get-ChildItem
```

或

```powershell
help Get-ChildItem
```

若要顯示詳細資訊，請使用 `Get-Help` Cmdlet 的 **Detailed** 參數。 例如，若要取得 `Get-ChildItem` Cmdlet 的詳細資訊，請輸入：

```powershell
Get-Help Get-ChildItem -Detailed
```

若要顯示說明文章中的所有內容，請使用 `Get-Help` Cmdlet 的 **Full** 參數。 例如，若要顯示 `Get-ChildItem` Cmdlet 之說明文章中的所有內容，請輸入：

```powershell
Get-Help Get-ChildItem -Full
```

若要取得 Cmdlet 之參數的詳細說明，請使用 `Get-Help` Cmdlet 的 **Parameter** 參數。 例如，若要取得 `Get-ChildItem` Cmdlet 之所有參數的詳細說明，請輸入：

```powershell
Get-Help Get-ChildItem -Parameter *
```

若只要顯示說明文章中的範例，請使用 `Get-Help` 的 **Example** 參數。
例如，若只要顯示說明文章中的 `Get-ChildItem` Cmdlet 範例，請鍵入：

```powershell
Get-Help Get-ChildItem -Examples
```

如需如何為您撰寫的 Cmdlet 撰寫說明文章的相關資訊，請參閱[如何撰寫 Cmdlet 說明](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)。

## <a name="getting-conceptual-help"></a>取得概念性說明

`Get-Help` Cmdlet 也會顯示 PowerShell 中概念性文章的相關資訊，包括 PowerShell 語言的相關文章。 概念性說明文章是以 "about_" 前置詞為開頭，例如 about_line_editing (概念性文章的名稱必須以英文輸入，即使是在非英文版的 PowerShell 中也一樣)。

若要顯示概念性文章清單，請輸入：

```powershell
Get-Help about_*
```

若要顯示特定說明文章，請輸入文章名稱，例如：

```powershell
Get-Help about_command_syntax
```

`Get-Help` 的參數 (例如 **Detailed**、**Parameter** 與 **Examples**) 不會影響概念性說明文章的顯示方式。

## <a name="getting-help-about-providers"></a>取得提供者的相關說明

`Get-Help` Cmdlet 會顯示 PowerShell 提供者的相關資訊。 若要取得提供者的說明，請輸入 `Get-Help`，後面接著提供者名稱。 例如，若要取得登錄提供者的說明，請輸入：

```powershell
Get-Help registry
```

若要取得工作階段中的所有提供者說明文章清單，請輸入

```powershell
Get-Help -Category provider
```

`Get-Help` 的參數 (例如 **Detailed**、**Parameter** 與 **Examples**) 不會影響提供者說明文章的顯示方式。

## <a name="getting-help-about-scripts-and-functions"></a>取得指令碼與函式的相關說明

PowerShell 中的許多指令碼與函式都有說明文章。 使用 `Get-Help` Cmdlet 可顯示指令碼與函式的說明文章。

若要顯示函式的說明，請輸入 `Get-Help`，後面接著函式名稱。 例如，若要取得 `Disable-PSRemoting` 函式的說明，請輸入：

```powershell
Get-Help Disable-PSRemoting
```

若要顯示指令碼的說明，請輸入指令碼檔案的路徑。 如果指令碼不在 Path 環境變數所列的路徑中，您必須使用完整路徑。

例如，如果您的 C:\\PS-Test 目錄中有稱為 "TestScript.ps1" 的指令碼，若要顯示該指令碼的說明文章，請輸入：

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

設計來顯示 Cmdlet 說明的參數也適用於指令碼與函式說明。 不過，函式與指令碼的說明不會在您執行 `Get-Help *` 時顯示。

如需撰寫函式與指令碼之說明文章的相關資訊，請參閱下列文章：

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a>線上取得說明

線上檢視說明文章是取得協助的最佳方式之一。 線上文章可以更輕鬆地更新，並提供最新的內容。

若要線上取得說明，請使用 `Get-Help` Cmdlet 的 **Online** 參數。 PowerShell 隨附的所有說明文章 (包括提供者說明與概念性 (關於) 說明文章) 都可以在 [PowerShell](/powershell/scripting/powershell-scripting) 文件中線上取得。

> [!NOTE]
> 您無法對概念性 (about_\*) 或提供者說明文章使用 **Online** 參數。
> 線上說明是選擇性的，因此並非每一個 Cmdlet、函式或指令碼都適用。

例如，若要取得 `Get-ChildItem` Cmdlet 相關說明文章的線上版本，請輸入：

```powershell
Get-Help Get-ChildItem -Online
```

PowerShell 會在預設瀏覽器中開啟文章。 如果某篇說明文章支援線上說明，您也可以檢視該說明文章的 URL。 URL 會出現在說明文章的 [相關連結] 區段中。

例如，若要查看 Add-Computer Cmdlet 的線上版本 URL，請輸入︰

```powershell
Get-Help Add-Computer
```

該文章之 [相關連結] 區段中的第一行如下所示。

```Output
Online version: https://go.microsoft.com/fwlink/?LinkId=821564
```

如需如何提供說明文章線上支援的相關資訊，請參閱 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)。

## <a name="see-also"></a>另請參閱

- [about_Functions](/powershell/module/microsoft.powershell.core/about/about_functions)
- [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [Get-Help](/powershell/module/microsoft.powershell.core/get-help)
