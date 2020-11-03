---
description: 環境
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 環境提供者
ms.openlocfilehash: afa9f17333e09f31b130e24d9ede289f9621faf8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208047"
---
# <a name="environment-provider"></a>環境提供者

## <a name="provider-name"></a>提供者名稱

環境

## <a name="drives"></a>磁碟機

`Env:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>簡短描述

提供 Windows 環境變數的存取。

## <a name="detailed-description"></a>詳細描述

PowerShell **環境** 提供者可讓您在 powershell 中取得、新增、變更、清除及刪除環境變數和值。

**環境** 變數是動態命名的變數，可描述您的程式執行所在的環境。 Windows 和 PowerShell 使用環境變數來儲存會影響系統和進程執行的持續性資訊。 不同于 PowerShell 變數，環境變數不受限於範圍條件約束。

**環境** 磁片磁碟機是一般命名空間，其中包含目前使用者會話特有的環境變數。 環境變數沒有任何子專案。

**環境** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

每個環境變數都是 [DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) 類別的實例。 變數的名稱是字典索引鍵。 環境變數的值是字典值。

## <a name="navigating-the-environment-drive"></a>流覽環境磁片磁碟機

**環境** 提供者會在磁片磁碟機中公開它的資料存放區 `Env:` 。 若要使用環境變數，請將您的位置變更為 `Env:` 磁片磁碟機 (`Set-Location Env:`) ，或從另一個 PowerShell 磁片磁碟機工作。 若要從另一個位置參考環境變數，請使用 `Env:` 路徑中的磁片磁碟機名稱。

```powershell
Set-Location Env:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

您也可以從任何其他 PowerShell 磁片磁碟機使用 **環境** 提供者。 若要從另一個位置參考環境變數，請使用路徑中的磁片磁碟機名稱 `Env:` 。

**環境** 提供者也會使用的變數前置詞來公開環境變數 `$env:` 。  下列命令會查看 **ProgramFiles** 環境變數的內容。 `$env:`變數前置詞可以從任何 PowerShell 磁片磁碟機使用。

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

您也可以使用變數前置詞來變更環境變數的值 `$env:` 。  只要目前的 PowerShell 會話處於作用中狀態，任何變更都只適用于目前的 PowerShell 會話。

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

## <a name="getting-environment-variables"></a>取得環境變數

此命令會列出目前會話中的所有環境變數。

```powershell
Get-Item -Path Env:
```

您可以從任何 PowerShell 磁片磁碟機使用此命令。

環境提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>取得選取的環境變數

此命令會取得 `WINDIR` 環境變數。

```powershell
Get-ChildItem -Path Env:windir
```

您也可以使用變數前置詞格式。

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>建立環境變數

此命令會建立 `USERMODE` 一個值為 "非 Admin" 的環境變數。 `-Path`參數值會在磁片磁碟機中建立新專案 `Env:` 。 新的環境變數僅適用于目前的 PowerShell 會話，只要它是使用中。

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>變更環境變數

### <a name="rename-an-environment-variable"></a>重新命名環境變數

此命令會使用 `Rename-Item` Cmdlet 來變更 `USERMODE` 您建立的環境變數名稱 `USERROLE` 。 請勿變更系統所使用的環境變數名稱。 雖然這些變更只會影響目前的工作階段，但它們可能會造成系統或程式運作錯誤。

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>變更環境變數

此命令會使用 `Set-Item` Cmdlet 將環境變數的值變更 `USERROLE` 為 "Administrator"。

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>複製環境變數

此命令會將環境變數的值複製 `USERROLE` 到 `USERROLE2` 環境變數。

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>移除環境變數

此命令會 `USERROLE2` 從目前的會話中刪除環境變數。

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>使用 Clear-Item 移除環境變數

此命令會藉 `USERROLE` 由清除其值來刪除環境變數。

```powershell
Clear-Item -Path Env:USERROLE
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
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>另請參閱

[about_Providers](../About/about_Providers.md)
