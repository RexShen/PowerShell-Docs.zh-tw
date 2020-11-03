---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 別名提供者
ms.openlocfilehash: b143a7aea71fcc6227d6287a4f87b49262098efb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207863"
---
# <a name="alias-provider"></a>別名提供者

## <a name="provider-name"></a>提供者名稱
Alias

## <a name="drives"></a>磁碟機

`Alias:`

## <a name="capabilities"></a>功能

**ShouldProcess**

## <a name="short-description"></a>簡短描述

提供 PowerShell 別名和它們所代表之值的存取權。

## <a name="detailed-description"></a>詳細描述

PowerShell **別名** 提供者可讓您在 powershell 中取得、新增、變更、清除和刪除別名。

別名是 Cmdlet、函式、可執行檔（包括腳本）的替代名稱。 PowerShell 包含一組內建的別名。 您可以將自己的別名新增至目前的會話和您的 PowerShell 設定檔。

**別名** 磁片磁碟機是只包含別名物件的一般命名空間。
別名沒有任何子項目。

**別名** 提供者支援下列 Cmdlet，這些 Cmdlet 將在本文中討論。

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell 包含一組設計來查看和變更別名的 Cmdlet。 當您使用 **Alias** Cmdlet 時，不需要 `Alias:` 在名稱中指定磁片磁碟機。 本文未涵蓋 **別名** Cmdlet 的使用方式。

- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>此提供者公開的類型

每個別名都是 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 類別的實例。

## <a name="navigating-the-alias-drive"></a>流覽別名磁片磁碟機

**別名** 提供者會在磁片磁碟機中公開它的資料存放區 `Alias:` 。 若要使用別名，您可以使用下列命令將位置變更為 `Alias:` 磁片磁碟機：

```powershell
Set-Location Alias:
```

若要返回檔案系統磁碟機，請輸入磁碟機名稱。 例如，輸入：

```powershell
Set-Location C:
```

您也可以從任何其他 PowerShell 磁片磁碟機使用別名提供者。 若要從其他位置參照別名，請 `Alias:` 在路徑中使用磁片磁碟機名稱。

> [!NOTE]
> PowerShell 會使用別名，讓您有熟悉的方式來處理提供者路徑。 和等命令 `dir` `ls` 現在是 [get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)的別名， `cd` 它是 [設定位置](xref:Microsoft.PowerShell.Management.Set-Location)的別名。 和 `pwd` 是 [取得位置](xref:Microsoft.PowerShell.Management.Get-Location)的別名。

### <a name="displaying-the-contents-of-the-alias-drive"></a>顯示 Alias：磁片磁碟機的內容

當目前位置是磁片磁碟機時，此命令會取得所有別名的清單 `Alias:` 。 它會使用萬用字元 `*` 來指出目前位置的所有內容。

```powershell
PS Alias:\> Get-Item -Path *
```

在 `Alias:` 磁片磁碟機中，代表目前位置的點， `.` 以及 `*` 代表目前位置中所有專案的萬用字元，都具有相同的效果。 例如， `Get-Item -Path .` 或 `Get-Item \*` 產生相同的結果。

別名提供者沒有任何容器，因此在搭配使用時，上述命令具有相同的效果 `Get-ChildItem` 。

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>取得選取的別名

此命令會取得 `ls` 別名。
因為它包含路徑，所以您可以在任何 PowerShell 磁片磁碟機中使用它。

```powershell
Get-Item -Path Alias:ls
```

如果您是在 `Alias:` 磁片磁碟機中，您可以省略路徑中的磁片磁碟機名稱。

您也可以在提供者路徑前面加上貨幣符號 () ，以取得別名的定義 `$` 。

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>取得特定 Cmdlet 的所有別名

此命令會取得與 Cmdlet 相關聯的別名清單 `Get-ChildItem` 。 它會使用 **定義** 屬性，它會儲存 Cmdlet 名稱。

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>建立別名

### <a name="create-an-alias-from-the-alias-drive"></a>從 Alias：磁片磁碟機建立別名

此命令會建立 `serv` Cmdlet 的別名 `Get-Service` 。 因為目前的位置是在 `Alias:` 磁片磁碟機中，所以 `-Path` 不需要參數。

此命令也會使用 `-Options` 動態參數來設定別名上的 **AllScope** 選項。 `-Options` `New-Item` 只有當您在磁片磁碟機中時，才可以在 Cmdlet 中使用參數 `Alias:` 。 點 (`.`) 表示目前的目錄，也就是別名磁片磁碟機。

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>建立具有絕對路徑的別名

您可以針對任何叫用命令的項目建立別名。
此命令會建立的 `np` 別名 `Notepad.exe` 。

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>建立新函式的別名

您可以針對任何函式建立別名。 您可以使用此功能來建立包含 Cmdlet 及其參數的別名。

第一個命令會建立函式，此函式會將 `CD32` 目前的目錄變更為 `System32` 目錄。 第二個命令會建立函式的 `go` 別名 `CD32` 。

當命令完成時，您可以使用 `CD32` 或來叫用 `go` 函數。

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>變更別名

### <a name="change-the-options-of-an-alias"></a>變更別名的選項

您可以使用 `Set-Item` Cmdlet 搭配 `-Options` 動態參數來變更 `-Options` 別名的屬性值。

此命令會為別名設定 **AllScope** 和 **ReadOnly** 選項 `dir` 。 此命令會使用 `-Options` Cmdlet 的動態參數 `Set-Item` 。 `-Options` `Set-Item` 當您搭配 **別名** 或 **函數** 提供者使用參數時，就可以使用參數。

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>變更別名參考命令

此命令會使用 `Set-Item` Cmdlet 來變更 `gp` 別名，使其代表 Cmdlet， `Get-Process` 而不是 `Get-ItemProperty` Cmdlet。
此 `-Force` 參數為必要參數，因為別名的 **Options** 屬性值 `gp` 設定為 `ReadOnly` 。 因為命令是從磁片磁碟機中提交的 `Alias:` ，所以不會在路徑中指定磁片磁碟機。

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

變更會影響定義別名與命令之間的關聯的四個屬性。 若要查看變更的效果，請輸入下列命令：

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>重新命名別名

此命令會使用 `Rename-Item` Cmdlet 將別名變更 `popd` 為 `pop` 。

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>複製別名

此命令會複製 `pushd` 別名，以 `push` 建立 Cmdlet 的新別名 `Push-Location` 。

建立新的別名時，其 **Description** 屬性會有 null 值。
而且，它的 **Option** 屬性值為 `None` 。 如果命令是從磁片磁碟機內發出的 `Alias:` ，您可以從參數的值中省略磁片磁碟機名稱 `-Path` 。

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>刪除別名

此命令會刪除 `serv` 目前會話中的別名。
您可以在任何 PowerShell 磁片磁碟機中使用此命令。

```powershell
Remove-Item -Path Alias:serv
```

此命令會刪除開頭為 "s" 的別名。
它不會刪除唯讀的別名。

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>刪除唯讀別名

此命令會刪除目前會話中的所有別名，但 `Constant` 其 **Options** 屬性的值除外。 `-Force`參數可讓命令刪除 **Options** 屬性具有值的別名 `ReadOnly` 。

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>動態參數

動態參數是 PowerShell 提供者新增的 Cmdlet 參數，而且只有在提供者啟用的磁片磁碟機中使用 Cmdlet 時才能使用。

### <a name="options-systemmanagementautomationscopeditemoptions"></a>選項 [ScopedItemOptions]

判斷別名的 **Options** 屬性值。

- **無** ：無選項。 這是預設值。
- **常數** ：無法刪除別名，而且無法變更其屬性。
  只有在您建立別名時才能使用 **常數** 。 您無法將現有別名的選項變更為 **常數** 。
- **私** 用：別名只會顯示在目前的範圍中，而不是在子範圍中。
- **ReadOnly** ：除非使用參數，否則無法變更別名的屬性 `-Force` 。 您可以使用 `Remove-Item` 刪除別名。
- **AllScope** ：別名會複製到所建立的任何新範圍。

#### <a name="cmdlets-supported"></a>支援的 Cmdlet

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
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>另請參閱

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)
