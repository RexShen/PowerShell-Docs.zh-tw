---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/push-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Push-Location
ms.openlocfilehash: 59199ee409749ed61d76f645a49890f43395885c
ms.sourcegitcommit: 01a1c253f48b61c943f6d6aca4e603118014015f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2020
ms.locfileid: "93205875"
---
# Push-Location

## 概要
在位置堆疊頂端新增目前的位置。

## SYNTAX

### 路徑 (預設值)

```
Push-Location [[-Path] <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

### LiteralPath

```
Push-Location [-LiteralPath <String>] [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Push-Location`Cmdlet 會將目前位置 )  ( 「推送」新增至位置堆疊。 如果您指定路徑，則會 `Push-Location` 將目前的位置推入至位置堆疊，然後將目前的位置變更為路徑所指定的位置。 您可以使用 `Pop-Location` Cmdlet 從位置堆疊取得位置。

根據預設，此 `Push-Location` Cmdlet 會將目前的位置推送到目前的位置堆疊，但您可以使用 **StackName** 參數來指定替代的位置堆疊。 如果堆疊不存在，則會 `Push-Location` 加以建立。

如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

## 範例

### 範例 1

這個範例會將目前的位置推入至預設位置堆疊，然後將位置變更為 `C:\Windows` 。

```
PS C:\> Push-Location C:\Windows
```

### 範例 2

此範例會將目前的位置推送至 Regfunction 上方堆疊，並將目前的位置變更為 `HKLM:\Software\Policies` 位置。

```
PS C:\> Push-Location HKLM:\Software\Policies -StackName RegFunction
```

您可以使用任何 PowerShell 磁片磁碟機中的 Location Cmdlet (New-psdrive) 。

### 範例 3

此命令將目前位置推入至預設堆疊上方。 它不會變更位置。

```
PS C:\> Push-Location
```

### 範例 4-建立和使用命名堆疊

這些命令顯示如何建立和使用命名位置堆疊。

```
PS C:\> Push-Location ~ -StackName Stack2
PS C:\Users\User01> Pop-Location -StackName Stack2
PS C:\>
```

第一個命令會將目前的位置推送至名為 Stack2 的新堆疊，然後將目前的位置變更為 home 目錄，在命令中以波狀符號符號 (`~`) （在檔案系統提供者磁片磁碟機上使用時相當於 `$HOME` 和） `$env:USERPROFILE` 。

如果 Stack2 不存在於會話中，則會 `Push-Location` 加以建立。 第二個命令會使用 `Pop-Location` Cmdlet 來 (`C:\` 從 Stack2 堆疊) 的原始位置。 如果沒有 **StackName** 參數， `Pop-Location` 會從未命名的預設堆疊中取出位置。

如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

## PARAMETERS

### -LiteralPath

指定新位置的路徑。 與 **Path** 參數不同， **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

將代表位置的物件傳遞至管線。 根據預設，此 Cmdlet 不會產生任何輸出。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

變更您的位置為此路徑所指定的位置 (在將目前位置新增 (推入) 至堆疊頂端之後)。 輸入其提供者支援此 Cmdlet 的任何位置路徑。 允許使用萬用字元。 參數名稱為選擇性。

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

指定要新增目前位置的位置堆疊。 請輸入位置堆疊名稱。
如果堆疊不存在，則會 `Push-Location` 加以建立。

如果沒有這個參數，則會 `Push-Location` 將位置新增至目前的位置堆疊。 根據預設，目前的位置堆疊是 PowerShell 所建立的未命名預設位置堆疊。
若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。 如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

> [!NOTE]
> `Push-Location` 無法將位置新增至未命名的預設堆疊，除非它是目前的位置堆疊。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default stack
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至 `Push-Location` 。

## 輸出

### 無或 System.Management.Automation.PathInfo

當您使用 **PassThru** 參數時，會 `Push-Location` 產生代表位置的 **system.management.automation.pathinfo** 物件。 否則，此 Cmdlet 不會產生任何輸出。

## 注意

PowerShell 支援每個進程有多個空間。 每個運行空間都有自己的 _目前的目錄_ 。
這與不同 `[System.Environment]::CurrentDirectory` 。 呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。

即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。 您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。

堆疊是一個後進先出的清單，其中只有最近新增的專案可供存取。
將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。 PowerShell 可讓您將提供者位置儲存在位置堆疊中。

PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。 如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。 根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。

若要管理位置堆疊，請使用 PowerShell Location Cmdlet，如下所示。

- 若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。

- 若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。

- 若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。

- 若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。

- 若要建立新的位置堆疊，請使用 Cmdlet 的 StackName 參數 `Push-Location` 。 如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。

- 若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 StackName 參數 `Set-Location` 。

未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。
如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。 若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。

您也可以 `Push-Location` 使用內建的別名來參考 `pushd` 。 如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。

此 `Push-Location` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

## 相關連結

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Set-Location](Set-Location.md)

[about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
