---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: 3d0e1ffbb18bcc44de87faca60e45a83b6c15743
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388003"
---
# Import-PSSession

## 概要
將另一個工作階段的命令匯入目前的工作階段。

## SYNTAX

```
Import-PSSession [-Prefix <String>] [-DisableNameChecking] [[-CommandName] <String[]>] [-AllowClobber]
 [-ArgumentList <Object[]>] [-CommandType <CommandTypes>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [[-FormatTypeName] <String[]>]
 [-Certificate <X509Certificate2>] [-Session] <PSSession> [<CommonParameters>]
```

## DESCRIPTION

此 `Import-PSSession` Cmdlet 會從本機或遠端電腦上的 PSSession 將命令匯入至目前的會話，例如 Cmdlet、函式和別名。 您可以匯入 `Get-Command` Cmdlet 可在 PSSession 中找到的任何命令。

使用 `Import-PSSession` 命令從自訂的 shell （例如 Microsoft Exchange Server shell）匯入命令，或從包含 Windows PowerShell 模組和嵌入式管理單元或不在目前會話中之其他元素的會話匯入命令。

若要匯入命令，請先使用 `New-PSSession` Cmdlet 來建立 PSSession。 然後，使用 `Import-PSSession` Cmdlet 匯入命令。 根據預設， `Import-PSSession` 會匯入所有命令，但與目前會話中的命令名稱相同的命令除外。 若要匯入所有命令，請使用 **AllowClobber** 參數。

您可以使用匯入的命令，就像您使用工作階段中的任何命令一樣。 當您使用匯入的命令時，匯入的命令部份會隱含地在從匯入的工作階段中執行。 不過，遠端操作則會完全由 Windows PowerShell 處理。 您甚至不需要知道這些操作，不過必須讓其他工作階段 (PSSession) 的連線保持開啟。 如果您關閉它，匯入的命令就不再可用。

由於匯入的命令可能會比本機命令需要更長的時間來執行，因此會 `Import-PSSession` 將 **AsJob** 參數加入每個匯入的命令。 此參數可讓您以 Windows PowerShell 背景工作方式執行命令。 如需詳細資訊，請參閱 [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md)。

當您使用時 `Import-PSSession` ，Windows PowerShell 會將匯入的命令加入只存在於您會話中的暫存模組，並傳回代表該模組的物件。 若要建立可在未來的會話中使用的持續性模組，請使用 `Export-PSSession` Cmdlet。

此 `Import-PSSession` Cmdlet 會使用 Windows PowerShell 的隱含遠端功能。 當您將命令匯入目前的會話時，它們會以隱含方式在原始會話中或在來源電腦上類似的會話中執行。

從 Windows PowerShell 3.0 開始，您可以使用 `Import-Module` Cmdlet 將遠端會話的模組匯入到目前的會話。 這項功能使用隱含的遠端執行功能。 它相當於使用 `Import-PSSession` 將選取的模組從遠端會話匯入到目前的會話。

## 範例

### 範例1：從 PSSession 匯入所有命令

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

此命令將 Server01 電腦上 PSSession 的所有命令 (除了與目前工作階段中具有相同命令名稱的命令) 匯入目前的工作階段。

因為此命令沒有使用 **CommandName** 參數，所以它也會將匯入命令所需的所有格式化資料匯入。

### 範例2：匯入以特定字串結尾的命令

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

這些命令會從 PSSession 將名稱結尾為 "-test" 的命令匯入本機工作階段，然後顯示如何使用匯入的 Cmdlet。

第一個命令會使用 `New-PSSession` Cmdlet 來建立 PSSession。 它會將 PSSession 儲存在 `$S` 變數中。

第二個命令會使用 `Import-PSSession` Cmdlet，將來自 PSSession 的命令匯入 `$S` 到目前的會話中。 它使用 **CommandName** 參數指定具有 Test 名詞的命令，以及使用 **FormatTypeName** 參數匯入各種 Test 命令的格式化資料。

第三個和第四個命令在目前的工作階段中使用匯入的命令。 因為匯入的命令已經實際新增到目前的工作階段中，所以您要使用本機語法執行它們。 您不需要使用 `Invoke-Command` Cmdlet 來執行匯入的命令。

### 範例3：從 PSSession 匯入 Cmdlet

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

此範例示範使用匯入的 Cmdlet 就如同使用本機 Cmdlet 一樣。

這些命令會 `New-Test` `Get-Test` 從 Server01 電腦上的 Pssession 以及 Server02 電腦上的 pssession，匯入和 Cmdlet `Set-Test` 。

即使是從不同的 PSSession 匯入 Cmdlet，您還是可以使用管線將物件從一個 Cmdlet 傳送到另一個 Cmdlet 而不會發生錯誤。

### 範例4：以背景工作的形式執行匯入的命令

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

此範例示範如何以背景工作的方式執行匯入的命令。

由於匯入的命令可能會比本機命令需要更長的時間來執行，因此會 `Import-PSSession` 將 **AsJob** 參數加入每個匯入的命令。 **AsJob** 參數可讓您以背景工作的方式執行命令。

第一個命令在 Server01 電腦上建立 PSSession，並將 PSSession 物件儲存在 `$S` 變數中。

第二個命令會使用 `Import-PSSession` ，將中 PSSession 的測試 Cmdlet 匯入 `$S` 至目前的會話。

第三個命令會使用匯入 Cmdlet 的 **AsJob** 參數 `New-Test` ，以 `New-Test` 背景工作的方式執行命令。 此命令會儲存在變數中傳回的工作物件 `New-Test` `$batch` 。

第四個命令會使用 `Receive-Job` Cmdlet 來取得變數中的作業結果 `$batch` 。

### 範例5：從 Windows PowerShell 模組匯入 Cmdlet 和函數

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

此範例示範如何從遠端電腦的 Windows PowerShell 模組將 Cmdlet 和函式匯入目前的工作階段。

第一個命令在 Server01 電腦上建立 PSSession，並將它儲存在 `$S` 變數中。

第二個命令會使用指令 `Invoke-Command` 程式，在 `Import-Module` 中的 PSSession 中執行命令 `$S` 。

一般來說，模組會透過 `Import-Module` Windows PowerShell 設定檔中的命令新增至所有會話，但不會在 pssession 中執行設定檔。

第三個命令使用的 **模組** 參數 `Import-PSSession` ，將模組中的 Cmdlet 和函式匯入至目前的會話。

### 範例6：在暫存檔案中建立模組

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1
zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

此範例示範如何 `Import-PSSession` 在磁片上的暫存檔案中建立模組。 它也會顯示所有命令在匯入目前工作階段之前，都已轉換成函式。

此命令會使用 `Import-PSSession` Cmdlet 將 Cmdlet 和 SearchHelp 函式匯入至 `Get-Date` 目前的會話。

`Import-PSSession`Cmdlet 會傳回代表暫存模組的 **PSModuleInfo** 物件。 [ **路徑** ] 屬性的值顯示 `Import-PSSession` 在暫存位置中建立了腳本模組 ( .psm1) 檔。 **ExportedFunctions** 屬性顯示 `Get-Date` Cmdlet 和 SearchHelp 函式都已匯入為函數。

### 範例7：執行匯入的命令所隱藏的命令

```
PS C:\> Import-PSSession $S -CommandName Get-Date -FormatTypeName * -AllowClobber

PS C:\> Get-Command Get-Date -All

CommandType   Name       Definition
-----------   ----       ----------
Function      Get-Date   ...
Cmdlet        Get-Date   Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>]

PS C:\> Get-Date
09074

PS C:\> (Get-Command -Type Cmdlet -Name Get-Date).PSSnapin.Name
Microsoft.PowerShell.Utility

PS C:\> Microsoft.PowerShell.Utility\Get-Date
Sunday, March 15, 2009 2:08:26 PM
```

此範例示範如何執行被匯入的命令隱藏的命令。

第一個命令會 `Get-Date` 從變數中的 PSSession 匯入 Cmdlet `$S` 。 因為目前的會話包含 `Get-Date` Cmdlet，所以命令中必須要有 **AllowClobber** 參數。

第二個命令會使用 Cmdlet 的 **all** 參數 `Get-Command` 來取得 `Get-Date` 目前會話中的所有命令。 輸出顯示會話包含原始的 `Get-Date` Cmdlet 和函式 `Get-Date` 。 函數會在 `Get-Date` 的 PSSession 中執行匯入的 `Get-Date` Cmdlet `$S` 。

第三個命令會執行 `Get-Date` 命令。 因為函式優先于 Cmdlet，所以 Windows PowerShell 會執行匯入的函式 `Get-Date` ，以傳回 Julian 日期。

第四個和第五個命令示範如何使用限定的名稱執行被匯入的命令隱藏的命令。

第四個命令會取得 Windows PowerShell 嵌入式管理單元的名稱，此嵌入式管理單元會將原始 `Get-Date` Cmdlet 新增至目前的會話。

第五個命令會使用 Cmdlet 的嵌入式管理單元限定名稱 `Get-Date` 來執行 `Get-Date` 命令。

如需有關命令優先順序和隱藏命令的詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。

### 範例8：匯入名稱中有特定字串的命令

```
PS C:\> Import-PSSession -Session $S -CommandName **Item** -AllowClobber
```

此命令會匯入名稱包含中 PSSession 之專案的命令 `$S` 。 因為此命令包含 **CommandName** 參數，而不是 **FormatTypeData** 參數，所以只會匯入命令。

當您使用在 `Import-PSSession` 遠端電腦上執行命令，且在目前會話中已經有命令的格式化資料時，請使用此命令。

### 範例9：使用 Module 參數來探索哪些命令已匯入至會話

```
PS C:\> $M = Import-PSSession -Session $S -CommandName *bits* -FormatTypeName *bits*
PS C:\> Get-Command -Module $M
CommandType     Name
-----------     ----
Function        Add-BitsFile
Function        Complete-BitsTransfer
Function        Get-BitsTransfer
Function        Remove-BitsTransfer
Function        Resume-BitsTransfer
Function        Set-BitsTransfer
Function        Start-BitsTransfer
Function        Suspend-BitsTransfer
```

此命令顯示如何使用的 **模組** 參數 `Get-Command` ，找出命令已將哪些命令匯入會話 `Import-PSSession` 。

第一個命令會使用 `Import-PSSession` Cmdlet，從變數中的 PSSession 匯入名稱包含 "bits" 的命令 `$S` 。 此 `Import-PSSession` 命令會傳回暫存模組，而且命令會將模組儲存在 `$m` 變數中。

第二個命令 `Get-Command` 會使用 Cmdlet 來取得變數中的模組所匯出的命令 `$M` 。

**Module** 參數會使用設計來做為模組名稱的字串值。 不過，當您送出模組物件時，Windows PowerShell 會對模組物件使用 **ToString** 方法，傳回模組名稱。

此 `Get-Command` 命令相當於 `Get-Command $M.Name` "。

## PARAMETERS

### -AllowClobber

指出此 Cmdlet 會匯入指定的命令，即使它們的名稱與目前會話中的命令相同。

如果您匯入與目前工作階段中的命令同名的命令，匯入的命令將會隱藏或取代原始命令。 如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。

根據預設，不 `Import-PSSession` 會匯入與目前會話中的命令同名的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ArgumentList

指定使用指定的引數 (參數值) 所產生的命令陣列。

例如，若要將命令的變異數匯入至 `Get-Item` 中 PSSession 的憑證 (Cert： ) 磁片磁碟機 `$S` ，請輸入 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Certificate

指定用來簽署格式檔案 ( * .Format.ps1xml) 的用戶端憑證，或在建立的暫存模組中 ( .psm1) 的腳本模組檔案。 `Import-PSSession`

輸入包含憑證的變數，或可取得憑證的命令或運算式。

若要尋找憑證，請使用 `Get-PfxCertificate` Cmdlet 或使用 `Get-ChildItem` 憑證 (Cert： ) 磁片磁碟機中的 Cmdlet。 若憑證無效或權限不足，則命令會失敗。

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandName

指定具有指定名稱或名稱模式的命令。 允許使用萬用字元。 使用 **CommandName** 或其別名 **Name** 。

根據預設， `Import-PSSession` 會從會話匯入所有命令，但與目前會話中的命令具有相同名稱的命令除外。 這可防止匯入的命令隱藏或取代工作階段中的命令。 若要匯入所有命令，包含那些會隱藏或取代其他命令的命令，請使用 **AllowClobber** 參數。

您使用 **CommandName** 參數時，除非您使用 **FormatTypeName** 參數，否則不會匯入命令的格式設定檔案。 同樣地，使用 **FormatTypeName** 參數時，除非您使用 **CommandName** 參數，否則不會匯入任何命令。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

指定命令物件的類型。 預設值為 Cmdlet。 使用 **CommandType** 或它的別名 **Type** 。 此參數可接受的值為：

- 別名。 遠端工作階段中的 Windows PowerShell 別名。
- 全部。 遠端工作階段中的 Cmdlet 與函式。
- 應用程式。 Path 環境變數所列路徑中的 Windows-PowerShell 檔案以外的所有檔案 `$env:path` ，在遠端會話中 () ，包括 .txt、.exe 和 .dll 檔案。
- Cmdlet。 遠端工作階段中的 Cmdlet。 "Cmdlet" 為預設值。
- ExternalScript. Path 環境變數所列路徑中的 ps1 檔案 (`$env:path`) 在遠端會話中。
- 篩選和函數。 遠端工作階段中的 Windows PowerShell 函式。
- 指令碼： 遠端工作階段中的指令碼區塊。

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: (All)
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableNameChecking

指出當您匯入的 Cmdlet 或函式的名稱包含未核准的動詞或禁止的字元時，此 Cmdlet 會隱藏警告您的訊息。

依預設，當您匯入的模組會匯出其名稱中具有未核准動詞的 Cmdlet 或函式時，Windows PowerShell 會顯示下列警告訊息：

「警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。 請使用 Verbose 參數取得詳細資訊，或輸入 `Get-Verb` 以查看核准的動詞清單。」

這則訊息只是一個警告。 模組仍然完整匯入，包括不合格的命令。 雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FormatTypeName

指定指定之 Microsoft .NET Framework 類型的格式設定指示。
輸入類型名稱。
允許使用萬用字元。

此參數的值必須是要從中匯 `Get-FormatData` 入命令之來源會話中的命令所傳回之類型的名稱。 若要取得遠端會話中的所有格式設定資料，請輸入 `*` 。

如果命令未包含 **CommandName** 或 **FormatTypeName** 參數，則會匯 `Import-PSSession` 入 `Get-FormatData` 遠端會話中命令所傳回之所有 .NET Framework 類型的格式設定指示。

如果您使用 **FormatTypeName** 參數，除非使用 **CommandName** 參數，否則不會匯入任何命令。

同樣地，如果您使用 **CommandName** 參數，除非使用 **FormatTypeName** 參數，否則不會匯入命令的格式化檔案。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FullyQualifiedModule

指定以 **ModuleSpecification** 物件形式指定之名稱的模組 (在 PowerShell SDK 中 [ (ModuleSpecification) 的「雜湊表](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_) 的備註」一節中所述。 例如， **FullyQualifiedModule** 參數會接受以下列格式指定的模組名稱：

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}` 或
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`.

**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。 這兩個參數是互斥的。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Module

指定 Windows PowerShell 嵌入式管理單元和模組中的命令陣列。 請輸入嵌入式管理單元和模組名稱。 不允許使用萬用字元。

`Import-PSSession` 無法從嵌入式管理單元匯入提供者。

如需詳細資訊，請參閱 [about_PSSnapins](../Microsoft.PowerShell.Core/About/about_PSSnapins.md)和 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -前置詞

在匯入的命令名稱中指定名詞的前置詞。

使用此參數來避免工作階段中不同命令具有相同名稱時可能會發生的名稱衝突。

比方說，如果您指定首碼 Remote，然後匯入 `Get-Date` Cmdlet，則在會話中會將此 Cmdlet 視為 `Get-RemoteDate` ，而不會與原始的 Cmdlet 混淆 `Get-Date` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Session

指定要從中匯入 Cmdlet 的 **PSSession** 。 輸入包含會話物件的變數，或輸入可取得會話物件的命令，例如 `New-PSSession` 或 `Get-PSSession` 命令。 您只能指定一個工作階段。 這是必要參數。

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

您無法使用管線將物件傳送至此 Cmdlet。

## 輸出

### System.Management.Automation.PSModuleInfo

`Import-PSSession` 傳回與 Cmdlet 傳回的相同模組物件 `New-Module` `Get-Module` 。
不過，匯入的模組是暫時性的，而且只存在於目前的工作階段。 若要在磁片上建立永久模組，請使用 `Export-PSSession` Cmdlet。

## 注意

- `Import-PSSession` 依賴 PowerShell 遠端基礎結構。 若要使用此 Cmdlet，電腦必須設定 WS-Management 遠端執行功能。 如需詳細資訊，請參閱 [about_Remote](../Microsoft.PowerShell.Core/about/about_Remote.md) 和 [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md)。
- `Import-PSSession` 不會匯入變數或 PowerShell 提供者。
- 當您匯入與目前工作階段中具有相同命令名稱的命令時，匯入的命令可以隱藏工作階段中的別名、函式和 Cmdlet，而且可以取代工作階段中的函式和變數。 若要避免名稱衝突，請使用 **Prefix** 參數。 如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。
- `Import-PSSession` 將所有命令轉換成函式，然後再將它們匯入。 如此一來，匯入的命令行為會變得與保持其原始命令類型時有點不同。 例如，如果您從 PSSession 匯入 Cmdlet，然後從模組或嵌入式管理單元匯入具有相同名稱的 Cmdlet，則從 PSSession 匯入的命令預設一律都會執行，因為函式優先於 Cmdlet。 相反地，如果您將某個別名匯入具有相同別名名稱的工作階段，則會一律使用原始的別名，因為別名優先於函式。 如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/about/about_Command_Precedence.md)。
- `Import-PSSession` 使用 `Write-Progress` Cmdlet 來顯示命令的進度。 當命令執行時，您可以看到進度列。
- 若要尋找要匯入的命令，請 `Import-PSSession` 使用 `Invoke-Command` Cmdlet `Get-Command` 在 PSSession 中執行命令。 為了取得命令的格式設定資料，它會使用 `Get-FormatData` Cmdlet。 當您執行命令時，您可能會看到來自這些 Cmdlet 的錯誤訊息 `Import-PSSession` 。 此外，也 `Import-PSSession` 無法從未包含 `Get-Command` 、 `Get-FormatData` 、 `Select-Object` 和 Cmdlet 的 PSSession 匯入命令 `Get-Help` 。
- 匯入的命令與其他遠端命令具有相同的限制，包括無法以使用者介面啟動程式，例如「記事本」。
- 因為 Windows PowerShell 設定檔不會在 Pssession 中執行，所以無法使用設定檔新增至會話的命令 `Import-PSSession` 。 若要從設定檔匯入命令，請使用 `Invoke-Command` 命令手動執行 PSSession 中的設定檔，然後再匯入命令。
- 建立的暫存模組 `Import-PSSession` 可能會包含格式化檔案，即使命令沒有匯入格式化資料。 如果命令不會匯入格式設定資料，所建立的任何格式檔案都將不會包含格式設定資料。
- 若要使用 `Import-PSSession` ，目前會話中的執行原則無法受到限制或 AllSigned，因為建立的暫存模組 `Import-PSSession` 會包含這些原則所禁止的未簽署腳本檔案。 若要使用 `Import-PSSession` 而不變更本機電腦的執行原則，請使用的 **範圍** 參數，為 `Set-ExecutionPolicy` 單一進程設定較不嚴格的執行原則。
- 在 Windows PowerShell 2.0 中，從另一個工作階段匯入命令的說明主題不包含您使用 **Prefix** 參數指派的首碼。 若要取得在 Windows PowerShell 2.0 中匯入命令的說明，請使用原始 (未加上首碼) 的命令名稱。

## 相關連結

[Export-PSSession](Export-PSSession.md)
