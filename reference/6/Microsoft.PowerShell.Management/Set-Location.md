---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: e1432a8ae6826e7f2c47f35c9cc01df20edde85c
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2020
ms.locfileid: "93206067"
---
# Set-Location

## 概要
將目前的工作位置設定為指定的位置。

## SYNTAX

### 路徑 (預設值)

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### Stack

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## DESCRIPTION

`Set-Location`Cmdlet 會將工作位置設定為指定的位置。 該位置可以是目錄、子目錄、登錄位置或任何提供者路徑。

PowerShell 6.2 已新增的支援 `-` 和 `+` 作為 **Path** 參數的值。 PowerShell 會維護可使用和存取之最後20個位置的歷程 `-` 記錄 `+` 。 這份清單獨立于使用 **StackName** 參數存取的位置堆疊。

## 範例

### 範例1：設定目前的位置

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

此命令會將目前的位置設定為 `HKLM:` 磁片磁碟機的根目錄。

### 範例2：設定目前的位置，並顯示該位置

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

此命令會將目前的位置設定為 `Env:` 磁片磁碟機的根目錄。 它使用 **PassThru** 參數指示 PowerShell 傳回代表位置的 **system.management.automation.pathinfo** 物件 `Env:\` 。

### 範例3：將位置設定為 C：磁片磁碟機中的目前位置

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

第一個命令會將位置設定為 `HKLM:` 登錄提供者中磁片磁碟機的根目錄。
第二個命令會將位置設定為 `C:` FileSystem 提供者中磁片磁碟機的目前位置。
當磁片磁碟機名稱是以格式 `<DriveName>:` (沒有反斜線) 指定時，此 Cmdlet 會將位置設定為 new-psdrive 中的目前位置。
以取得 New-psdrive use 命令中的目前位置 `Get-Location -PSDrive <DriveName>` 。

### 範例4：將目前位置設定為命名堆疊

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

第一個命令會將目前的位置新增至路徑堆疊。
第二個命令會讓路徑位置堆疊成為目前的位置堆疊。
第三個命令會顯示目前位置堆疊中的位置。

`*-Location`除非在命令中指定不同的位置堆疊，否則 Cmdlet 會使用目前的位置堆疊。 如需位置堆疊的相關資訊，請參閱 [附注](#notes)。

### 範例5：使用或來導覽位置歷程記錄 `+``-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

使用別名， `cd -` 或者 `cd +` 是在您的終端機中流覽位置歷程記錄的簡單方式。 如需有關導覽的詳細資訊 `-` / `+` ，請參閱 **Path** 參數。

## PARAMETERS

### -LiteralPath

指定位置的路徑。 **LiteralPath** 參數的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含逸出字元，請將它括在單引號中。 單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

傳回代表位置的 **system.management.automation.pathinfo** 物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

指定新工作位置的路徑。 如果未提供路徑，則 `Set-Location` 預設為目前使用者的主目錄。 使用萬用字元時，此 Cmdlet 會選擇符合萬用字元模式的第一個路徑。

PowerShell 會保留您已設定之最近20個位置的歷程記錄。 如果 **Path** 參數值為 `-` 字元，則新的工作位置將會是記錄 (中的先前工作位置（如果存在) ）。 同樣地，如果值為 `+` 字元，則新的工作位置將會是歷程記錄 (中的下一個工作位置（如果存在) ）。 這類似于使用 `Pop-Location` 和， `Push-Location` 不同之處在于歷程記錄是清單，而不是堆疊，而且會以隱含的方式加以追蹤，而不是以手動方式控制。 目前沒有任何方法可查看歷程記錄清單。

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

指定此 Cmdlet 用來建立目前位置堆疊的現有位置堆疊名稱。 請輸入位置堆疊名稱。 若要指出未命名的預設位置堆疊，請輸入 `$null` 或 () 的空字串 `""` 。

`*-Location`Cmdlet 會在目前的堆疊上作用，除非您使用 **StackName** 參數來指定不同的堆疊。 如需位置堆疊的詳細資訊，請參閱 [附注](#notes)。

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑 (但不是常值路徑) 的字串傳送至此 Cmdlet。

## 輸出

### 無、System.Management.Automation.PathInfo、System.Management.Automation.PathInfoStack

除非您指定 **PassThru** 參數，否則這個 Cmdlet 不會產生任何輸出。 使用 **PassThru** 搭配 **Path** 或 **LiteralPath** 會產生代表新位置的 **system.management.automation.pathinfo** 物件。 使用 **PassThru** with **StackName** 會產生代表新堆疊內容的 **PathInfoStack** 物件。

## 注意

PowerShell 支援每個進程有多個空間。 每個運行空間都有自己的 _目前的目錄_ 。
這與不同 `[System.Environment]::CurrentDirectory` 。 呼叫 .NET Api 或執行原生應用程式而不提供明確的目錄路徑時，此行為可能會產生問題。

即使位置 Cmdlet 已設定整個進程的目錄，您也無法依賴它，因為另一個執行時間可能會隨時變更。 您應該使用 location Cmdlet 來執行以路徑為基礎的作業，並使用目前的運行時特定的工作目錄。

此 `Set-Location` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出工作階段中可用的提供者，請輸入 `Get-PSProvider`。 如需詳細資訊，請參閱 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)。

堆疊是一份後進先出的清單，其中只能存取最近新增的項目。 將項目新增到堆疊中時，順序與您使用它們的順序相同，然後抓取它們來使用時的順序則相反。 PowerShell 可讓您將提供者位置儲存在位置堆疊中。 PowerShell 會建立未命名的預設位置堆疊。 您可以建立多個命名位置堆疊。 如果您未指定堆疊名稱，PowerShell 會使用目前的位置堆疊。 根據預設，未命名的預設位置為目前的位置堆疊，但您可以使用 `Set-Location` Cmdlet 來變更目前的位置堆疊。

若要管理位置堆疊，請使用 Cmdlet，如下所示 `*-Location` ：

- 若要將位置新增至位置堆疊，請使用 `Push-Location` Cmdlet。

- 若要從位置堆疊取得位置，請使用 `Pop-Location` Cmdlet。

- 若要顯示目前位置堆疊中的位置，請使用 Cmdlet 的 **stack** 參數 `Get-Location` 。 若要顯示命名位置堆疊中的位置，請使用的 **StackName** 參數 `Get-Location` 。

- 若要建立新的位置堆疊，請使用的 **StackName** 參數 `Push-Location` 。 如果您指定的堆疊不存在，就會 `Push-Location` 建立堆疊。

- 若要將位置堆疊設為目前的位置堆疊，請使用的 **StackName** 參數 `Set-Location` 。

未命名的預設位置堆疊只有在做為目前的位置堆疊時，才能供完整存取。
如果您將指定的位置堆疊設為目前的位置堆疊，您便無法再使用 `Push-Location` 或 `Pop-Location` Cmdlet 來加入或取得預設堆疊中的專案，或使用 `Get-Location` Cmdlet 來顯示未命名堆疊中的位置。 若要將未命名的堆疊設為目前的堆疊，請使用 Cmdlet 的 **StackName** 參數搭配的 `Set-Location` 值 `$null` 或 () 的空字串 `""` 。

## 相關連結

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)
