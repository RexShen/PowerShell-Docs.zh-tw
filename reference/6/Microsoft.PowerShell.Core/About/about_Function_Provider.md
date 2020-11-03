---
description: 函式
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 函式提供者
ms.openlocfilehash: 0323433d5ab9114dd1bb21afc47b7fa7db3d6f8f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207095"
---
# <a name="function-provider"></a>函數提供者

## <a name="provider-name"></a>提供者名稱
函式

## <a name="drives"></a>磁碟機

`Function:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>簡短描述

提供 PowerShell 中定義之函式的存取權。

## <a name="detailed-description"></a>詳細描述

PowerShell 函 **式提供者** 可讓您在 powershell 中取得、新增、變更、清除和刪除函式和篩選器。

函式是可執行動作的具名程式碼區塊。 當您輸入函式名稱時，函式中的程式碼就會執行。 篩選條件是可建立執行動作條件的具名程式碼區塊。 您可以輸入篩選器的名稱來取代條件，例如在 `Where-Object` 命令中。

函 **式磁片磁碟機** 是只包含函式和篩選物件的一般命名空間。 函式和篩選條件都沒有子項目。

函 **式提供者** 支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

每個函數都是 [FunctionInfo](/dotnet/api/system.management.automation.functioninfo) 類別的實例。 每個篩選器都是 [都是 system.management.automation.filterinfo](/dotnet/api/system.management.automation.filterinfo) 類別的實例。

## <a name="navigating-the-function-drive"></a>導覽函式磁片磁碟機

函 **式提供者會在** 磁片磁碟機中公開它的資料存放區 `Function:` 。 若要使用函式，您可以將位置變更為 `Function:` 磁片磁碟機 (`Set-Location Function:`) 。 或者，您可以從另一個 PowerShell 磁片磁碟機工作。 若要從另一個位置參考函式，請使用路徑中 () 的磁片磁碟機名稱 `Function:` 。

```powershell
Set-Location Function:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

您也可以從任何其他 PowerShell 磁片磁碟機使用 **函數** 提供者。 若要從另一個位置參考函式，請使用路徑中的磁片磁碟機名稱 `Function:` 。

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

## <a name="getting-functions"></a>取得函式

此命令會取得目前工作階段中的所有函式清單。 您可以從任何 PowerShell 磁片磁碟機使用此命令。

```powershell
Get-ChildItem -Path Function:
```

函式提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Function:
```

您可以藉由存取 **定義** 屬性來取出函數的定義，如下所示。

```powershell
(Get-Item -Path function:more).Definition
```

您也可以使用前面加上貨幣符號 () 的提供者路徑來取得函式的定義 `$` 。

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>取得選取的函式

此命令會 `man` 從 `Function:` 磁片磁碟機取得函數。 它會使用 `Get-Item` Cmdlet 來取得函數。 管線運算子 (`|`) 將結果傳送至 `Format-Table` 。 `-Wrap`參數會將不符合該行的文字導向到下一行。 `-Autosize`參數會調整資料表資料行的大小來容納文字。

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>使用函數提供者路徑

這些命令都會取得名為的函式 `c:` 。 第一個命令適用於任何磁碟機。 第二個命令用於 `Function:` 磁片磁碟機。 由於名稱結尾是冒號 (此為磁碟機的語法)，因此，您必須使用磁碟機名稱來限定路徑。 在 `Function:` 磁片磁碟機中，您可以使用任一種格式。 在第二個命令中， (`.`) 的點代表目前的位置。

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>建立函式

此命令會使用 `New-Item` Cmdlet 來建立名為的函式 `Win32:` 。
使用括號括起來的運算式是函式名稱所代表的指令碼區塊。

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

您也可以在 PowerShell 命令列中輸入函式來建立函式。 例如，tpe `Function:Win32: {Set-Location C:\Windows\System32}` 。 如果您是在 `Function:` 磁片磁碟機中，您可以省略磁片磁碟機名稱。

## <a name="deleting-a-function"></a>刪除函式

此命令會 `more:` 從目前的會話刪除函數。

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>變更函數

此命令會使用 `Set-Item` Cmdlet 來變更函式， `prompt` 讓它顯示路徑之前的時間。

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>重新命名函數

此命令會使用 `Rename-Item` Cmdlet 將函數的名稱變更 `help` 為 `gh` 。

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>複製函式

此命令會將 `prompt` 函數複製到 `oldPrompt` ，以有效地為與提示函式相關聯的腳本區塊建立新名稱。
如果您想要變更它，就可以使用此命令來儲存原始提示函式。
新函數的 **Options** 屬性的值為 `None` 。 若要變更 **Options** 屬性的值，請使用 `Set-Item` 。

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。

### <a name="options-systemmanagementautomationscopeditemoptions"></a>選項 < [ScopedItemOptions] >

決定函數的 **Options** 屬性值。

- `None`：沒有選項。 `None` 是預設值。
- `Constant`：無法刪除函數，而且無法變更其屬性。 `Constant` 只有在您建立函式時才能使用。
  您無法將現有函式的選項變更為 `Constant` 。
- `Private`：函式只會在目前的範圍中顯示
-  (不在子範圍) 。
- `ReadOnly`：除非使用參數，否則無法變更函數的屬性 `-Force` 。 您可以使用 `Remove-Item` 刪除函數。
- `AllScope`：函式會複製到所建立的任何新範圍。

### <a name="cmdlets-supported"></a>支援的 Cmdlet

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

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
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>另請參閱

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)
