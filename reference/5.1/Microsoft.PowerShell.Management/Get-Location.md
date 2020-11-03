---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 647424d8148cad8830235abc7b238b79b552c4fb
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206071"
---
# Get-Location

## 概要
取得目前工作位置或位置堆疊的相關資訊。

## SYNTAX

### Location (預設值)

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [-UseTransaction] [<CommonParameters>]
```

### Stack

```
Get-Location [-Stack] [-StackName <String[]>] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Get-Location`Cmdlet 會取得代表目前目錄的物件，與列印工作目錄 (pwd) 命令很相似。

當您在 PowerShell 磁片磁碟機之間移動時，PowerShell 會保留您在每個磁片磁碟機中的位置。 您可以使用這個 Cmdlet 來尋找每個磁片磁碟機中的位置。

您可以使用這個指令程式，在執行時間取得目前的目錄，並將它用於函式和腳本中，例如在 PowerShell 提示字元中顯示目前目錄的函式中。

您也可以使用這個 Cmdlet 來顯示位置堆疊中的位置。 如需詳細資訊，請參閱 **Stack** 和 **StackName** 參數的附注和描述。

## 範例

### 範例1：顯示目前的磁片磁碟機位置

此命令會在目前的 PowerShell 磁片磁碟機中顯示您的位置。

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

比方說，如果您在 `Windows` 磁片磁碟機的目錄中 `C:` ，它會顯示該目錄的路徑。

### 範例2：顯示不同磁片磁碟機的目前位置

此範例示範 `Get-Location` 如何使用，在不同的 PowerShell 磁片磁碟機中顯示目前的位置。 `Set-Location` 用來將位置變更為不同 Psdrive 上的數個不同路徑。

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### 範例3：使用堆疊取得位置

這個範例會示範如何使用的 **Stack** 和 **StackName** 參數， `Get-Location` 列出目前位置堆疊中的位置和替代的位置堆疊。

此 `Push-Location` Cmdlet 會用來變更為三個不同的位置。 第三個推送使用不同的堆疊名稱。 的 **Stack** 參數會 `Get-Location` 顯示預設堆疊的內容。 的 **StackName** 參數會 `Get-Location` 顯示名為的堆疊內容 `Stack2` 。

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### 範例4：自訂 PowerShell 提示字元

此範例說明如何自訂 PowerShell 提示字元。

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

定義提示的函式包含 `Get-Location` 命令，每當主控台出現提示時，就會執行此命令。

預設 PowerShell 提示字元的格式是由名為的特殊函式所定義 `prompt` 。 您可以建立名為的新函式，以變更控制台中的提示 `prompt` 。

若要查看目前的提示字元函式，請輸入下列命令： `Get-Content Function:\prompt`

## PARAMETERS

### -PSDrive

取得指定之 PowerShell 磁片磁碟機中的目前位置。

比方說，如果您是在 `Cert:` 磁片磁碟機中，您可以使用這個參數來尋找磁片磁碟機中的目前位置 `C:` 。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

取得指定 PowerShell 提供者所支援之磁片磁碟機中的目前位置。
如果指定的提供者支援多個磁片磁碟機，此 Cmdlet 會傳回最近存取之磁片磁碟機上的位置。

例如，如果您在 `C:` 磁片磁碟機中，您可以使用此參數來尋找 PowerShell 登錄提供者之磁片磁碟機中的目前 **Registry** 位置。

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Stack

指出此 Cmdlet 會顯示新增至目前位置堆疊的位置。 您可以使用 Cmdlet 將位置新增至堆疊 `Push-Location` 。

若要顯示不同位置堆疊中的位置，請使用 **StackName** 參數。 如需位置堆疊的相關資訊，請參閱 [附注](#notes)。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

以字串陣列的形式指定命名的位置堆疊。 輸入一或多個位置堆疊名稱。

若要顯示目前位置堆疊中的位置，請使用 **stack** 參數。 若要將位置堆疊設為目前的位置堆疊，請使用 `Set-Location` Cmdlet。

此 Cmdlet 無法顯示未命名之預設堆疊中的位置，除非它是目前的堆疊。

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseTransaction
將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 about_transactions。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線傳送輸入至此 Cmdlet。

## 輸出

### System.Management.Automation.PathInfo 或 System.Management.Automation.PathInfoStack

如果您使用 **Stack** 或 **StackName** 參數，這個 Cmdlet 會傳回 **PathInfoStack** 物件。 否則，它會傳回 **system.management.automation.pathinfo** 物件。

## 注意

PowerShell 支援每個進程有多個空間。 每個運行空間都有自己的 _目前的目錄_ 。
這與不同 `[System.Environment]::CurrentDirectory` 。 呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。
Cmdlet 會傳回 `Get-Location` 目前 PowerShell 運行時的目前目錄。

此 Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出會話中的提供者，請輸入 `Get-PSProvider` 。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)。

**PSProvider** 、 **new-psdrive** 、 **Stack** 及 **StackName** 參數互動的方式取決於提供者。 某些組合將會導致錯誤，例如既指定磁碟機又指定未公開該磁碟機的提供者。 如果未指定任何參數，此 Cmdlet 會傳回提供者的 **system.management.automation.pathinfo** 物件，其中包含目前的工作位置。

堆疊是一個後進先出的清單，其中只有最近新增的專案可供存取。 將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。 PowerShell 可讓您將提供者位置儲存在位置堆疊中。 PowerShell 會建立未命名的預設位置堆疊，而且您可以建立多個命名位置堆疊。 如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。 根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。

若要管理位置堆疊，請使用 PowerShell `*-Location` Cmdlet，如下所示。

- 若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。

- 若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。

- 若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。 若要顯示命名位置堆疊中的位置，請使用 Cmdlet 的 **StackName** 參數 `Get-Location` 。

- 若要建立新的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Push-Location` 。
  如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。

- 若要將位置堆疊設為目前的位置堆疊，請使用 Cmdlet 的 **StackName** 參數 `Set-Location` 。

未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。
如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用此 Cmdlet 來顯示未命名堆疊中的位置。 若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。

## 相關連結

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

[Set-Location](Set-Location.md)
