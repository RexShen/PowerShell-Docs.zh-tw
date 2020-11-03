---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PSSession
ms.openlocfilehash: fafc4da46eb6b6f7cf252d5ca2aa50f6bd42b49f
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201180"
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

**Import-module** Cmdlet 會從本機或遠端電腦上的 PSSession 將命令匯入至目前的會話，例如 Cmdlet、函式和別名。
您可以匯入 Get-Command Cmdlet 可在 PSSession 中找到的任何命令。

使用 **import-module** 命令從自訂的命令介面（例如 Microsoft Exchange Server shell）匯入命令，或從包含 PowerShell 模組和嵌入式管理單元或不在目前會話中之其他元素的會話匯入命令。

若要匯入命令，請先使用 New-PSSession Cmdlet 來建立 PSSession。
然後，使用 **Import-PSSession** Cmdlet 匯入命令。
根據預設， **Import-PSSession** 會匯入除了與目前工作階段中具有相同命令名稱以外的所有命令。
若要匯入所有命令，請使用 *AllowClobber* 參數。

您可以使用匯入的命令，就像您使用工作階段中的任何命令一樣。
當您使用匯入的命令時，匯入的命令部份會隱含地在從匯入的工作階段中執行。
不過，遠端作業是由 PowerShell 完全處理。
您甚至不需要知道這些操作，不過必須讓其他工作階段 (PSSession) 的連線保持開啟。
如果您關閉它，匯入的命令就不再可用。

因為匯入的命令可能會比本機命令需要花費較長的時間，所以 **Import-PSSession** 會對每個匯入的命令加入 *AsJob* 參數。
此參數可讓您以 PowerShell 背景工作執行命令。
如需詳細資訊，請參閱 about_Jobs。

當您使用匯 **入-PSSession** 時，PowerShell 會將匯入的命令加入只存在於您會話中的暫存模組，並傳回代表該模組的物件。
若要建立可在未來的會話中使用的持續性模組，請使用 Export-PSSession Cmdlet。

**Import-module** Cmdlet 會使用 PowerShell 的隱含遠端功能。
當您將命令匯入目前的會話時，它們會以隱含方式在原始會話中或在來源電腦上類似的會話中執行。

從 Windows PowerShell 3.0 開始，您可以使用 Import-Module Cmdlet 將遠端會話的模組匯入到目前的會話。
這項功能使用隱含的遠端執行功能。
它等同於使用 **Import-PSSession** 將遠端工作階段中選取的模組匯入目前的工作階段。

## 範例

### 範例1：從 PSSession 匯入所有命令

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S
```

此命令將 Server01 電腦上 PSSession 的所有命令 (除了與目前工作階段中具有相同命令名稱的命令) 匯入目前的工作階段。

因為此命令沒有使用 *CommandName* 參數，所以它也會將匯入命令所需的所有格式化資料匯入。

### 範例2：匯入以特定字串結尾的命令

```
PS C:\> $S = New-PSSession https://ps.testlabs.com/powershell
PS C:\> Import-PSSession -Session $S -CommandName *-test -FormatTypeName *
PS C:\> New-Test -Name Test1
PS C:\> Get-Test test1 | Run-Test
```

這些命令會從 PSSession 將名稱結尾為 "-test" 的命令匯入本機工作階段，然後顯示如何使用匯入的 Cmdlet。

第一個命令會使用 New-PSSession Cmdlet 來建立 PSSession。
它會將 PSSession 儲存在 $S 變數中。

第二個命令使用 **import-module** Cmdlet 從 $S 中的 PSSession 將命令匯入到目前的會話。
它使用 *CommandName* 參數指定具有 Test 名詞的命令，以及使用 *FormatTypeName* 參數匯入各種 Test 命令的格式化資料。

第三個和第四個命令在目前的工作階段中使用匯入的命令。
因為匯入的命令已經實際新增到目前的工作階段中，所以您要使用本機語法執行它們。
您不需要使用 Invoke-Command Cmdlet 來執行匯入的命令。

### 範例3：從 PSSession 匯入 Cmdlet

```
PS C:\> $S1 = New-PSSession -ComputerName s1
PS C:\> $S2 = New-PSSession -ComputerName s2
PS C:\> Import-PSSession -Session s1 -Type cmdlet -Name New-Test, Get-Test -FormatTypeName *
PS C:\> Import-PSSession -Session s2 -Type Cmdlet -Name Set-Test -FormatTypeName *
PS C:\> New-Test Test1 | Set-Test -RunType Full
```

此範例示範使用匯入的 Cmdlet 就如同使用本機 Cmdlet 一樣。

這些命令從 Server01 電腦的 PSSession 匯入 New-Test 和 Get-Test Cmdlet，以及從 Server02 電腦的 PSSession 匯入 Set-Test Cmdlet。

即使是從不同的 PSSession 匯入 Cmdlet，您還是可以使用管線將物件從一個 Cmdlet 傳送到另一個 Cmdlet 而不會發生錯誤。

### 範例4：以背景工作的形式執行匯入的命令

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Import-PSSession -Session $S -CommandName *-test* -FormatTypeName *
PS C:\> $batch = New-Test -Name Batch -AsJob
PS C:\> Receive-Job $batch
```

此範例示範如何以背景工作的方式執行匯入的命令。

因為匯入的命令可能會比本機命令需要花費較長的時間，所以 **Import-PSSession** 會對每個匯入的命令加入 *AsJob* 參數。
*AsJob* 參數可讓您以背景工作的方式執行命令。

第一個命令在 Server01 電腦上建立 PSSession，並將 PSSession 物件儲存在 $S 變數中。

第二個命令會使用 **import-module** 將 $S 中 PSSession 的測試 Cmdlet 匯入至目前的會話。

第三個命令使用匯入的 New-Test Cmdlet 的 *AsJob* 參數，以背景工作的方式執行 New-Test 命令。
命令會將 New-Test 傳回的工作物件儲存在 $batch 變數中。

第四個命令使用 Receive-Job Cmdlet 取得 $batch 變數中工作的結果。

### 範例5：從 PowerShell 模組匯入 Cmdlet 和函式

```
PS C:\> $S = New-PSSession -ComputerName Server01
PS C:\> Invoke-Command -Session $S {Import-Module TestManagement}
PS C:\> Import-PSSession -Session $S -Module TestManagement
```

此範例示範如何從遠端電腦上的 PowerShell 模組將 Cmdlet 和函式匯入至目前的會話。

第一個命令在 Server01 電腦上建立 PSSession，並將它儲存在 $S 變數中。

第二個命令使用 **Invoke 命令** Cmdlet，在 $S 中的 PSSession 中執行 Import-Module 命令。

通常，模組會透過 PowerShell 設定檔中的 **import-module** 命令新增至所有會話，但不會在 pssession 中執行設定檔。

第三個命令使用 Import-module 的 *module*  參數將模組中的 Cmdlet 和函 **式** 匯入至目前的會話。

### 範例6：在暫存檔案中建立模組

```
PS C:\> Import-PSSession $S -CommandName Get-Date, SearchHelp -FormatTypeName * -AllowClobber

Name              : tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
Path              : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf\tmp_79468106-4e1d-4d90-af97-1154f9317239_
tcw1zunz.ttf.psm1
Description       : Implicit remoting for http://server01.corp.fabrikam.com/wsman
Guid              : 79468106-4e1d-4d90-af97-1154f9317239
Version           : 1.0
ModuleBase        : C:\Users\User01\AppData\Local\Temp\tmp_79468106-4e1d-4d90-af97-1154f9317239_tcw1zunz.ttf
ModuleType        : Script
PrivateData       : {ImplicitRemoting}
AccessMode        : ReadWrite
ExportedAliases   : {}
ExportedCmdlets   : {}
ExportedFunctions : {[Get-Date, Get-Date], [SearchHelp, SearchHelp]}
ExportedVariables : {}
NestedModules     : {}
```

此範例顯示 **Import-PSSession** 在磁碟上的暫存檔案中建立模組。
它也會顯示所有命令在匯入目前工作階段之前，都已轉換成函式。

此命令會使用 **import-module** Cmdlet 將 Get-Date Cmdlet 和 SearchHelp 函式匯入目前的會話中。

**Import-PSSession** Cmdlet 傳回代表暫存模組的 **PSModuleInfo** 物件。
**Path** 屬性的值顯示 **Import-PSSession** 在暫存位置中建立了指令碼模組 (.psm1) 檔案。
**ExportedFunctions** 屬性顯示 **Get-Date** Cmdlet 與 SearchHelp 函式兩者都已匯入成為函式。

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

第一個命令會從 $S 變數中的 PSSession 匯入 Get-Date Cmdlet。
因為目前的工作階段包含 **Get-Date** Cmdlet，所以命令中必須要有 *AllowClobber* 參數。

第二個命令使用 Get-Command Cmdlet 的 **all** 參數，取得目前會話中的所有 **取得日期** 命令。
輸出顯示工作階段包含原始的 **Get-Date** Cmdlet 和 **Get-Date** 函式。
**取得日期函式** 會在 $S 中的 PSSession 中執行匯入的 **取得日期** Cmdlet。

第三個命令執行 **Get-Date** 命令。
因為函式優先于 Cmdlet，所以 PowerShell 會執行匯入的 **Get date** 函數，以傳回 Julian 日期。

第四個和第五個命令示範如何使用限定的名稱執行被匯入的命令隱藏的命令。

第四個命令會取得 PowerShell 嵌入式管理單元的名稱，此嵌入式管理單元會將原始的 **Get Date** Cmdlet 新增至目前的會話。

第五個命令使用 **Get-Date** Cmdlet 的嵌入式管理單元限定名稱執行 **Get-Date** 命令。

如需有關命令優先順序和隱藏命令的詳細資訊，請參閱 about_Command_Precedence。

### 範例8：匯入名稱中有特定字串的命令

```
PS C:\> Import-PSSession -Session $S -CommandName *Item* -AllowClobber
```

此命令會匯入名稱包含 $S 中 PSSession 之專案的命令。
因為此命令包含 *CommandName* 參數，而不是 *FormatTypeData* 參數，所以只會匯入命令。

當您使用 **Import-PSSession** 在遠端電腦上執行命令，且在目前工作階段中已經有命令的格式化資料時，請使用此命令。

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

此命令示範如何使用 **get-help** 的 *Module* 參數，找出由 **import-module** 命令匯入會話的命令。

第一個命令會使用 **import-module** Cmdlet 從 $S 變數中的 PSSession 匯入名稱包含 "bits" 的命令。
**Import-PSSession** 命令傳回一個暫存模組，而且命令將模組儲存在 $m 變數中。

第二個命令使用 Get-Command Cmdlet 來取得 $M 變數中的模組所匯出的命令。

*Module* 參數會使用設計來做為模組名稱的字串值。
不過，當您提交模組物件時，PowerShell 會在模組物件上使用 **ToString** 方法，它會傳回模組名稱。

**Get 命令** 命令相當於 `Get-Command $M.Name` "。

## PARAMETERS

### -AllowClobber

指出此 Cmdlet 會匯入指定的命令，即使它們的名稱與目前會話中的命令相同。

如果您匯入與目前工作階段中的命令同名的命令，匯入的命令將會隱藏或取代原始命令。
如需詳細資訊，請參閱 about_Command_Precedence。

根據預設， **Import-PSSession** 不會匯入與目前工作階段中的命令具有相同名稱的命令。

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

例如，若要將 Get-Item 命令的變異數匯入 $S 中 PSSession 的憑證 (Cert： ) 磁片磁碟機，請輸入 `Import-PSSession -Session $S -Command Get-Item -ArgumentList cert:` 。

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

指定用來簽署格式檔案 (*.Format.ps1xml)，或是簽署由 **Import-PSSession** 建立之暫存模組中的指令碼模組檔案 (.psm1) 的用戶端憑證。

輸入包含憑證的變數，或可取得憑證的命令或運算式。

若要尋找憑證，請使用 Get-PfxCertificate Cmdlet，或在憑證 (Cert： ) 磁片磁碟機中使用 Get-ChildItem Cmdlet。
若憑證無效或權限不足，則命令會失敗。

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

指定具有指定名稱或名稱模式的命令。
允許使用萬用字元。
使用 *CommandName* 或其別名 *Name* 。

根據預設， **Import-PSSession** 會從工作階段中匯入除了與目前工作階段中具有相同命令名稱以外的所有命令。
這可防止匯入的命令隱藏或取代工作階段中的命令。
若要匯入所有命令，包含那些會隱藏或取代其他命令的命令，請使用 *AllowClobber* 參數。

您使用 *CommandName* 參數時，除非您使用 *FormatTypeName* 參數，否則不會匯入命令的格式設定檔案。
同樣地，使用 *FormatTypeName* 參數時，除非您使用 *CommandName* 參數，否則不會匯入任何命令。

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

指定命令物件的類型。
預設值為 Cmdlet。
使用 *CommandType* 或它的別名 *Type* 。
此參數可接受的值為：

- 別名。
遠端會話中的 PowerShell 別名。
- 全部。
遠端工作階段中的 Cmdlet 與函式。
- 應用程式。
Path 環境變數所列路徑中的 PowerShell 檔案以外的所有檔案 ($env:p 路徑 a) ) 在遠端會話中，包括 .txt、.exe 和 .dll 檔案。
- Cmdlet。
遠端工作階段中的 Cmdlet。
"Cmdlet" 為預設值。
- ExternalScript.
在遠端工作階段中，Path 環境變數 ($env:path) 所列出路徑裡的 .ps1 檔案。
- 篩選和函數。
遠端會話中的 PowerShell 函式。
- 指令碼：
遠端工作階段中的指令碼區塊。

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

依預設，當您匯入的模組會匯出其名稱中具有未核准動詞的 Cmdlet 或函式時，PowerShell 會顯示下列警告訊息：

「警告：某些匯入的命令名稱包含未核准的動詞命令，可能會讓它們更不容易探索。
請使用 Verbose 參數取得詳細資訊，或輸入 Get-Verb 查看核准的動詞清單。」

這則訊息只是一個警告。
模組仍然完整匯入，包括不合格的命令。
雖然訊息是顯示給模組的使用者，但命名的問題應該由模組作者修正。

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

這個參數的值必須是從中匯入命令之來源工作階段中的 Get-FormatData 命令所傳回之類型的名稱。
若要取得遠端工作階段中的所有格式設定資料，請輸入 *。

如果命令未包含 *CommandName* 或 *FormatTypeName* 參數，則在遠端會話中， **import-module** 會匯入 **FormatData** 命令所傳回之所有 .NET Framework 類型的格式設定指示。

如果您使用 *FormatTypeName* 參數，除非使用 *CommandName* 參數，否則不會匯入任何命令。

同樣地，如果您使用 *CommandName* 參數，除非使用 *FormatTypeName* 參數，否則不會匯入命令的格式化檔案。

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

以 **ModuleSpecification** 物件的形式指定具有名稱的模組， (MSDN library 中的 [ModuleSpecification (表)](https://msdn.microsoft.com/library/jj136290) 的 [備註] 區段中所述) 。
例如， *FullyQualifiedModule* 參數會接受以 @ {ModuleName = "modulename" 格式指定的模組名稱;ModuleVersion = "version_number"} 或 @ {ModuleName = "modulename";ModuleVersion = "version_number";Guid = "GUID"}。
**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 *模組* 參數相同的命令中指定 *FullyQualifiedModule* 參數;這兩個參數是互斥的。

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

指定 PowerShell 嵌入式管理單元和模組中的命令陣列。
請輸入嵌入式管理單元和模組名稱。
不允許使用萬用字元。

匯 **入-PSSession** 無法從嵌入式管理單元匯入提供者。

如需詳細資訊，請參閱 about_PSSnapins和 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)。

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

比方說，如果您指定首碼 Remote，然後匯入 Get-Date Cmdlet，則在會話中會將此 Cmdlet 視為成為 get-remotedate，而且不會與原始的 **Get Date** Cmdlet 混淆。

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

指定要從中匯入 Cmdlet 的 **PSSession** 。
輸入包含會話物件的變數，或輸入可取得會話物件的命令，例如 New-PSSession 或 Get-PSSession 命令。
您只能指定一個工作階段。
這是必要參數。

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

**Import-module** 會傳回 New-Module 和 Get-Module Cmdlet 傳回的相同模組物件。
不過，匯入的模組是暫時性的，而且只存在於目前的工作階段。
若要在磁片上建立永久模組，請使用 Export-PSSession Cmdlet。

## 注意

* 匯 **入-PSSession** 依賴 PowerShell 遠端基礎結構。 若要使用此 Cmdlet，電腦必須設定 WS-Management 遠端執行功能。 如需詳細資訊，請參閱 about_Remote 和 about_Remote_Requirements。
* 匯 **入-PSSession** 不會匯入變數或 PowerShell 提供者。
* 當您匯入與目前工作階段中具有相同命令名稱的命令時，匯入的命令可以隱藏工作階段中的別名、函式和 Cmdlet，而且可以取代工作階段中的函式和變數。 若要避免名稱衝突，請使用 *Prefix* 參數。 如需詳細資訊，請參閱 about_Command_Precedence。
* **Import-module** 會先將所有命令轉換成函式，然後再將它們匯入。 如此一來，匯入的命令行為會變得與保持其原始命令類型時有點不同。 例如，如果您從 PSSession 匯入 Cmdlet，然後從模組或嵌入式管理單元匯入具有相同名稱的 Cmdlet，則從 PSSession 匯入的命令預設一律都會執行，因為函式優先於 Cmdlet。 相反地，如果您將某個別名匯入具有相同別名名稱的工作階段，則會一律使用原始的別名，因為別名優先於函式。 如需詳細資訊，請參閱 about_Command_Precedence。
* 匯 **入-PSSession** 使用 Write-Progress Cmdlet 來顯示命令的進度。 當命令執行時，您可以看到進度列。
* 若要尋找要匯入的命令， **import-module** 會使用 Invoke-Command Cmdlet 在 PSSession 中執行 Get-Command 命令。 為了取得命令的格式設定資料，它會使用 Get-FormatData Cmdlet。 當您執行「匯 **入-PSSession** 」命令時，您可能會看到來自這些 Cmdlet 的錯誤訊息。 此外， **import-module** 無法從不包含 Get 命令、FormatData、Select 物件和 Get-Help Cmdlet 的 PSSession 匯入命令。
* 匯入的命令與其他遠端命令具有相同的限制，包括無法以使用者介面啟動程式，例如「記事本」。
* 因為 PowerShell 設定檔不是在 Pssession 中執行，所以設定檔新增至會話的命令無法匯 **入 PSSession** 。 若要從設定檔匯入命令，請在匯入命令之前，使用 Invoke-Command 命令在 PSSession 中手動執行設定檔。
* **Import-PSSession** 建立的暫存模組可能會包含格式化檔案，即使命令沒有匯入格式化資料。 如果命令不會匯入格式設定資料，所建立的任何格式檔案都將不會包含格式設定資料。
* 若要使用 **Import-PSSession** ，目前工作階段中的執行原則不能是 Restricted 或 AllSigned，因為 **Import-PSSession** 建立的暫存模組會包含這些原則所禁止的未簽署指令碼檔案。 若要使用匯 **入-PSSession** 而不變更本機電腦的執行原則，請使用 Set-ExecutionPolicy 的 *Scope* 參數，為單一進程設定較不嚴格的執行原則。
* 在 Windows PowerShell 2.0 中，從另一個工作階段匯入命令的說明主題不包含您使用 *Prefix* 參數指派的首碼。 若要取得在 Windows PowerShell 2.0 中匯入命令的說明，請使用原始 (未加上首碼) 的命令名稱。

## 相關連結

[Export-PSSession](Export-PSSession.md)
