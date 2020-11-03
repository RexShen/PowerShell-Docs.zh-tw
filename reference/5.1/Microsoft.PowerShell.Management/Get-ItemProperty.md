---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203996"
---
# Get-ItemProperty

## 概要
取得指定項目的屬性。

## SYNTAX

### 路徑 (預設值)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## DESCRIPTION

`Get-ItemProperty`Cmdlet 會取得指定專案的屬性。
例如，您可以使用這個 Cmdlet 取得檔案物件的 LastAccessTime 屬性值。
您也可以使用這個 Cmdlet 來查看登錄專案和其值。

## 範例

### 範例1：取得特定目錄的相關資訊

此命令會取得 "C：\Windows" 目錄的相關資訊。

```powershell
Get-ItemProperty C:\Windows
```

### 範例2：取得特定檔案的屬性

此命令會取得 "C:\Test\Weather.xls" 檔案的屬性。
結果會透過管道傳送至 `Format-List` Cmdlet，以將輸出顯示為清單。

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### 範例3：顯示登錄子機碼中登錄專案的值名稱和資料

此命令顯示 "CurrentVersion" 登錄子機碼中包含之每個登錄專案的值名稱和資料。
請注意，此命令會要求將名為的 PowerShell 磁片磁碟機 `HKLM:` 對應至登錄的 "HKEY_LOCAL_MACHINE" hive。
具有該名稱和對應的磁片磁碟機預設可在 PowerShell 中使用。
或者，您可以使用下列替代路徑 (開頭為提供者名稱，後面是兩個冒號) 來指定此登錄子機碼的路徑：

"Registry：： HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion"。

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### 範例4：取得登錄子機碼中登錄專案的值名稱和資料

此命令會取得 "CurrentVersion" 登錄子機碼中 "ProgramFilesDir" 登錄專案的值名稱和資料。
命令使用 **Path** 參數指定子機碼和 Name 參數，以指定專案的值名稱。

此命令會使用反向刻度或抑音符 \` 號 () （PowerShell 接續字元）來繼續第二行的命令。

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### 範例5：取得登錄機碼中登錄專案的值名稱和資料

此命令會取得 "PowerShellEngine" 登錄機碼中登錄專案的值名稱和資料。
結果顯示在下列範例輸出中。

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### 範例6：取得、格式化及顯示登錄值和資料的結果

此範例顯示如何格式化 `Get-ItemProperty` 清單中命令的輸出，讓您輕鬆查看登錄值和資料，並讓您輕鬆地解讀結果。

第一個命令會使用 `Get-ItemProperty` Cmdlet 取得 **Microsoft PowerShell** 子機碼中的登錄專案。
此子機碼會儲存 PowerShell 預設 shell 的選項。
結果顯示在下列範例輸出中。

輸出顯示有兩個登錄專案： "Path" 和 "ExecutionPolicy"。
當登錄機碼包含的項目少於五個時，預設會顯示在表格中，但在清單中檢視通常更容易。

第二個命令使用相同的 `Get-ItemProperty` 命令。
不過，這次命令會使用管線運算子 (`|`) 將命令的結果傳送至 `Format-List` Cmdlet。
此 `Format-List` 命令會使用值為 ' * ' 的 Property 參數 (所有) 來顯示清單中物件的所有屬性。
結果顯示在下列範例輸出中。

產生的顯示會顯示 "Path" 和 "ExecutionPolicy" 登錄專案，以及數個較不熟悉的登錄機碼物件屬性。
其他以 PS 開頭的屬性是 PowerShell 自訂物件的屬性，例如代表登錄機碼的物件。

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## PARAMETERS

### -Credential

指定具有執行此動作權限的使用者帳戶。
預設為目前使用者。

輸入使用者名稱，例如 "User01" 或 "Domain01\User01"，或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。
若您輸入使用者名稱時，會提示您輸入密碼。

> [!WARNING]
> 與 Windows PowerShell 一起安裝的任何提供者皆不支援此參數。

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Exclude

以字串陣列指定此 Cmdlet 在作業中排除的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

以提供者的格式或語言指定篩選。
此參數的值會限定 **Path** 參數。

篩選的語法 (包括是否使用萬用字元) 取決於提供者。
篩選比其他參數更有效率，因為提供者會在 Cmdlet 取得物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Include

以字串陣列指定此 Cmdlet 在作業中納入的項目。
此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 "*.txt"。
允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定屬性之目前位置的路徑。
與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。
沒有字元會被視為萬用字元。
如果路徑包含逸出字元，請將它括在單引號中。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要抓取之一或多個屬性的名稱。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定一或多個項目的路徑。

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

將命令加入使用中交易。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱＜將命令加入使用中交易＞。
只有交易為處理中狀態時，此參數才有效。
如需詳細資訊，請參閱 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至 `Get-ItemProperty` 。

## 輸出

### System.Boolean、System.String、System.DateTime

`Get-ItemProperty` 針對它取得的每個專案屬性，各傳回一個物件。
物件類型取決於所抓取的物件。
例如，在檔案系統磁碟機中，它可能會傳回檔案或資料夾。

## 注意

此 `Get-ItemProperty` Cmdlet 是針對與任何提供者公開的資料搭配使用所設計。 若要列出會話中可用的提供者，請輸入 " `Get-PSProvider` "。 如需詳細資訊，請參閱 about_Providers。

## 相關連結

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)
