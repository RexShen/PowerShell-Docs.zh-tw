---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Command
ms.openlocfilehash: 5e76a15e8f2dcacc7f973cbc46d057bb92c3ad41
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204904"
---
# Get-Command

## 概要
取得所有命令。

## SYNTAX

### CmdletSet (預設) 

```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
 [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
 [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```

### AllCommandSet

```
Get-Command [[-Name] <String[]>] [-Module <String[]>]
 [-FullyQualifiedModule <ModuleSpecification[]>] [-CommandType <CommandTypes>] [-TotalCount <Int32>]
 [-Syntax] [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
 [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [-UseFuzzyMatching]
 [<CommonParameters>]
```

## DESCRIPTION

此 `Get-Command` Cmdlet 會取得電腦上安裝的所有命令，包括 Cmdlet、別名、函式、篩選器、腳本和應用程式。 `Get-Command` 從 PowerShell 模組和從其他會話匯入的命令取得命令。 若只要取得已經匯入目前工作階段的命令，請使用 **ListImported** 參數。

如果沒有參數，則會 `Get-Command` 取得電腦上安裝的所有 Cmdlet、函式和別名。 `Get-Command *` 取得所有類型的命令，包括 Path 環境變數中的所有非 PowerShell 檔案 (`$env:Path`) ，它會在應用程式命令類型中列出。

`Get-Command` 使用命令的完整名稱（不含萬用字元），會自動匯入包含命令的模組，讓您可以立即使用命令。 若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。 如需詳細資訊，請參閱 [about_Preference_Variables](About/about_Preference_Variables.md)。

`Get-Command` 從命令代碼直接取得其資料，不同于從 `Get-Help` 說明主題取得其資訊。

從 Windows PowerShell 5.0 開始，Cmdlet 的結果 `Get-Command` 預設會顯示 **版本** 資料行。 已將新的 **版本** 屬性加入至 **CommandInfo** 類別。

## 範例

### 範例1：取得 Cmdlet、函式和別名

此命令會取得電腦上安裝的 PowerShell Cmdlet、函式和別名。

```powershell
Get-Command
```

### 範例2：取得目前會話中的命令

此命令使用 **ListImported** 參數，只取得目前工作階段中的命令。

```powershell
Get-Command -ListImported
```

### 範例3：取得 Cmdlet 並依序顯示

此命令會取得所有的 Cmdlet，接著依照 Cmdlet 名稱中之名詞的字母順序排序，然後將它們顯示於依名詞分類的群組中。 此顯示方式可協助您尋找某個工作的 Cmdlet。

```powershell
Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun
```

### 範例4：取得模組中的命令

此命令會使用 **Module** 參數來取得 Microsoft. 安全性和 microsoft.. a. powershell 模組中的命令。

```powershell
Get-Command -Module Microsoft.PowerShell.Security, Microsoft.PowerShell.Utility
```

### 範例5：取得 Cmdlet 的相關資訊

此命令會取得 Cmdlet 的相關資訊 `Get-AppLockerPolicy` 。 它也會匯入 **AppLocker** 模組，這會將 **AppLocker** 模組中的所有命令新增至目前的工作階段。

```powershell
Get-Command Get-AppLockerPolicy
```

自動匯入模組時，效果會與使用 Import-Module Cmdlet 相同。
模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。 若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。 如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

### 範例6：取得 Cmdlet 的語法

此命令會使用 **ArgumentList** 和 **語法** 參數來取得 `Get-ChildItem` Cmdlet 在 Cert：磁片磁碟機中使用時的語法。 Cert：磁片磁碟機是憑證提供者新增至會話的 PowerShell 磁片磁碟機。

```powershell
Get-Command Get-Childitem -Args Cert: -Syntax
```

當您比較輸出中所顯示的語法與省略 **Args** ( **ArgumentList** ) 參數時所顯示的語法時，您會看到 **憑證提供者** 將動態參數 **CodeSigningCert** 新增至 `Get-ChildItem` Cmdlet。

如需有關憑證提供者的詳細資訊，請參閱 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)。

### 範例7：取得動態參數

此範例中的命令會使用函式 `Get-DynamicParameters` 來取得憑證提供者在 `Get-ChildItem` Cert：磁片磁碟機中使用時，新增至 Cmdlet 的動態參數。

```powershell
function Get-DynamicParameters
{
    param ($Cmdlet, $PSDrive)
    (Get-Command $Cmdlet -ArgumentList $PSDrive).ParameterSets | ForEach-Object {$_.Parameters} | Where-Object { $_.IsDynamic } | Select-Object -Property Name -Unique
}
Get-DynamicParameters -Cmdlet Get-ChildItem -PSDrive Cert:
```

```Output
Name
----
CodeSigningCert
```

此範例中的函式會 `Get-DynamicParameters` 取得 Cmdlet 的動態參數。 這是上一個範例中所使用之方法的替代方法。 動態參數可透過其他 Cmdlet 或提供者新增至 Cmdlet。

### 範例8：取得所有類型的所有命令

此命令會取得本機電腦上所有類型的所有命令，包括 **Path** 環境變數路徑中的可執行檔 (`$env:path`) 。

```powershell
Get-Command *
```

它會傳回每個檔案的 **ApplicationInfo** 物件 (System.Management.Automation.ApplicationInfo)，而不是傳回 **FileInfo** 物件 (System.IO.FileInfo)。

### 範例9：使用參數名稱和類型取得 Cmdlet

此命令會取得具有參數的 Cmdlet，其名稱包含 Auth，而其型別為 **AuthenticationMechanism** 。

```powershell
Get-Command -ParameterName *Auth* -ParameterType AuthenticationMechanism
```

您可以使用類似的命令，來尋找可讓您指定用來驗證使用者之方法的 Cmdlet。

**ParameterType** 參數會區分接受 **AuthenticationMechanism** 值的參數與接受 **AuthenticationLevel** 參數的參數，即使它們有類似的名稱。

### 範例10：取得別名

此範例示範如何搭配使用 `Get-Command` Cmdlet 與別名。

```powershell
Get-Command dir
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Alias           dir -> Get-ChildItem
```

雖然它通常用於 Cmdlet 和函式，但 `Get-Command` 也會取得腳本、函式、別名和可執行檔。

命令的輸出顯示別名之 **Name** 屬性值的特別檢視。 該檢視顯示別名和完整命令名稱。

### 範例11：取得記事本命令的所有實例

此範例會使用 Cmdlet 的 **all** 參數 `Get-Command` 顯示本機電腦上 "Notepad" 命令的所有實例。

```powershell
Get-Command Notepad -All | Format-Table CommandType, Name, Definition
```

```Output
CommandType     Name           Definition
-----------     ----           ----------
Application     notepad.exe    C:\WINDOWS\system32\notepad.exe
Application     NOTEPAD.EXE    C:\WINDOWS\NOTEPAD.EXE
```

當工作階段中有多個相同名稱的命令時， **All** 參數會非常有用。

從 Windows PowerShell 3.0 開始，當會話中包含多個具有相同名稱的命令時， `Get-Command` 只會取得您輸入命令名稱時執行的命令。 使用 **all** 參數， `Get-Command` 取得具有指定名稱的所有命令，並依執行優先順序傳回它們。 若要執行清單中第一個命令以外的某個命令，請輸入該命令的完整路徑。

如需命令優先順序的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。

### 範例12：取得包含 Cmdlet 的模組名稱

此命令會取得 Cmdlet 來源的模組名稱 `Get-Date` 。
此命令會使用所有命令的 **ModuleName** 屬性。

```powershell
(Get-Command Get-Date).ModuleName
```

```Output
Microsoft.PowerShell.Utility
```

此命令格式適用于 PowerShell 模組中的命令，即使它們未匯入會話中也一樣。

### 範例13：取得有輸出類型的 Cmdlet 和函式

```powershell
Get-Command -Type Cmdlet | Where-Object OutputType | Format-List -Property Name, OutputType
```

此命令會取得具有有輸出類型的 Cmdlet 和函式，以及它們傳回之物件的類型。

命令的第一個部份會取得所有 Cmdlet。
管線運算子 (|) 將指令程式傳送至 `Where-Object` Cmdlet，此 Cmdlet 只會選取已填入 **OutputType** 屬性的 Cmdlet。
另一個管線運算子會將選取的 Cmdlet 物件傳送至 `Format-List` Cmdlet，此 Cmdlet 會顯示清單中每個 Cmdlet 的名稱和輸出類型。

**CommandInfo** 物件的 **OutputType** 屬性只有在 Cmdlet 程式碼定義了 Cmdlet 的 **OutputType** 屬性時才會具有非 Null 的值。

### 範例14：取得可採用特定物件類型做為輸入的 Cmdlet

```powershell
Get-Command -ParameterType (((Get-NetAdapter)[0]).PSTypeNames)
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Disable-NetAdapter                                 NetAdapter
Function        Enable-NetAdapter                                  NetAdapter
Function        Rename-NetAdapter                                  NetAdapter
Function        Restart-NetAdapter                                 NetAdapter
Function        Set-NetAdapter                                     NetAdapter
```

此命令會尋找使用網路介面卡物件做為輸入項目的 Cmdlet。 您可以使用此命令格式來尋找接受任一命令傳回之物件類型的 Cmdlet。

此命令會使用所有物件的 **PSTypeNames** 內建屬性，它會取得描述物件的類型。 為取得網路介面卡的 **PSTypeNames** 屬性，而不是網路介面卡集合的 **PSTypeNames** 屬性，該命令會使用陣列標記法來取得 Cmdlet 傳回的第一個網路介面卡。

### 範例15：使用模糊相符取得命令

在此範例中，命令的名稱刻意以 ' commnd ' 的形式出現。
使用 `-UseFuzzyMatching` 參數時，Cmdlet 判斷出最符合的 `Get-Command` 系統上的其他原生命令之後，會有相同的相符項。

```powershell
Get-Command get-commnd -UseFuzzyMatching
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Command                                        6.2.0.0    Microsoft.PowerShell.Core
Application     getconf                                            0.0.0.0    /usr/bin/getconf
Application     command                                            0.0.0.0    /usr/bin/command
```

## PARAMETERS

### -All

指出此 Cmdlet 會取得所有命令，包括具有相同名稱之相同類型的命令。 根據預設， `Get-Command` 只會取得您輸入命令名稱時所執行的命令。

如需 PowerShell 在多個命令名稱相同時用來選取要執行之命令的方法的詳細資訊，請參閱 [about_Command_Precedence](About/about_Command_Precedence.md)。
如需模組合格命令名稱和執行命令的相關資訊（因為名稱衝突而不會預設執行），請參閱 [about_Modules](About/about_Modules.md)。

此參數是在 Windows PowerShell 3.0 引進。

在 Windows PowerShell 2.0 中， `Get-Command` 預設會取得所有命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ArgumentList

指定引數的陣列。 當 Cmdlet 或函式搭配指定的參數使用時，此 Cmdlet 會取得 Cmdlet 或函式的相關資訊 ( 「引數」 ) 。 **ArgumentList** 的別名是 **Args** 。

若要偵測只有在使用特定的其他參數時才能使用的動態參數，請將 **ArgumentList** 的值設為觸發動態參數的參數。

若要偵測提供者新增至 Cmdlet 的動態參數，請將 **ArgumentList** 參數的值設定為提供者磁片磁碟機中的路徑，例如 WSMan：、HKLM：或 Cert：。 當命令為 PowerShell 提供者 Cmdlet 時，請在每個命令中只輸入一個路徑。 提供者 Cmdlet 只會傳回 **ArgumentList** 值的第一個路徑的動態參數。 如需提供者 Cmdlet 的詳細資訊，請參閱 [about_Providers](About/about_Providers.md)。

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CommandType

指定此 Cmdlet 取得的命令類型。 輸入一或多個命令類型。 使用 **CommandType** 或它的別名 **Type** 。 依預設，會 `Get-Command` 取得所有 Cmdlet、函式和別名。

此參數可接受的值為：

- 別名。 取得所有 PowerShell 命令的別名。 如需詳細資訊，請參閱 [about_Aliases](About/about_Aliases.md)。
- 全部。 取得所有命令類型。 這個參數值相當於 `Get-Command *` 。
- 應用程式。 取得 **Path** 環境變數所列路徑中的非 PowerShell 檔案 ($env:p 路徑 a) ) ，包括 .txt、.exe 和 .dll 檔案。 如需 **Path** 環境變數的詳細資訊，請參閱 about_Environment_Variables。
- Cmdlet。 取得所有 Cmdlet。
- ExternalScript. 取得 **Path** 環境變數 ($env:path) 所列出之路徑中的所有 .ps1 檔案。
- 篩選和函數。 取得所有 PowerShell advanced 和 simple 函數和篩選器。
- 指令碼： 取得所有指令碼區塊。 若要)  ( ps1 檔案取得 PowerShell 腳本，請使用 ExternalScript 值。

```yaml
Type: System.Management.Automation.CommandTypes
Parameter Sets: AllCommandSet
Aliases: Type
Accepted values: Alias, Function, Filter, Cmdlet, ExternalScript, Application, Script, Workflow, Configuration, All

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FullyQualifiedModule

以 **ModuleSpecification** 物件的形式指定具有指定名稱的模組，請參閱 [ModuleSpecification (雜湊) 表](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)的「 **備註** 」一節中所述。
例如， **FullyQualifiedModule** 參數會接受以下列其中一種格式指定的模組名稱：

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

**ModuleName** 和 **ModuleVersion** 是必要參數，但 **Guid** 是選擇性參數。

您無法在與 **模組** 參數相同的命令中指定 **FullyQualifiedModule** 參數。 這兩個參數是互斥的。

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListImported

指出此 Cmdlet 只會取得目前會話中的命令。

從 PowerShell 3.0 開始，根據預設， `Get-Command` 會取得所有已安裝的命令，包括（但不限於）目前會話中的命令。 在 PowerShell 2.0 中，它只會取得目前會話中的命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Module

指定模組的陣列。 此 Cmdlet 會取得來自指定模組的命令。
輸入模組或模組物件的名稱。

此參數接受字串值，但此參數的值也可以是 **PSModuleInfo** 物件，例如和 Cmdlet 所傳回的物件 `Get-Module` `Import-PSSession` 。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSSnapin

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Name

指定名稱陣列。 此 Cmdlet 只會取得具有指定之名稱的命令。 輸入名稱或名稱模式。 允許使用萬用字元。

若要取得名稱相同的命令，請使用 **All** 參數。 當兩個命令的名稱相同時，根據預設，會 `Get-Command` 取得當您輸入命令名稱時所執行的命令。

```yaml
Type: System.String[]
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -名詞

指定命令名詞的陣列。 此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的名詞。 輸入一或多個名詞或名詞模式。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ParameterName

指定參數名稱的陣列。 此 Cmdlet 會取得會話中具有指定參數的命令。 輸入參數名稱或參數別名。 支援使用萬用字元。

**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ParameterType

指定參數名稱的陣列。 此 Cmdlet 會取得會話中具有指定類型參數的命令。 輸入參數類型的完整名稱或部分名稱。 支援使用萬用字元。

**ParameterName** 和 **ParameterType** 參數只會搜尋目前工作階段中的命令。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSTypeName[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ShowCommandInfo

指出此 Cmdlet 會顯示命令資訊。

此參數是在 Windows PowerShell 5.0 中引進。

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

### -語法

指出此 Cmdlet 只會取得下列關於命令的指定資料：

- 別名。 取得標準名稱。
- Cmdlet。 取得語法。
- 函數和篩選準則。 取得函式定義。
- 腳本和應用程式或檔案。 取得路徑和檔案名。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

指定要取得的命令數目。 您可以使用此參數來限制命令的輸出。

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UseFuzzyMatching

表示在尋找命令時使用模糊比對演算法。 輸出的順序是從最接近的相符到最不相符的結果。 萬用字元不應與模糊比對搭配使用，因為它會嘗試比對可能包含這些萬用字元的命令。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AllCommandSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

指定命令動詞命令陣列。 此 Cmdlet 會取得包含 Cmdlet、函式和別名的命令，這些命令的名稱包含指定的動詞命令。 輸入一或多個動詞或動詞模式。 允許使用萬用字元。

```yaml
Type: System.String[]
Parameter Sets: CmdletSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](About/about_CommonParameters.md)。

## 輸入

### System.String

您可以透過管道將命令名稱傳送至此 Cmdlet。

## 輸出

### CommandInfo。

此 Cmdlet 會傳回衍生自 **CommandInfo** 類別的物件。 傳回的物件類型取決於取得的命令類型 `Get-Command` 。

### System.Management.Automation.AliasInfo

代表別名。

### ApplicationInfo。

代表應用程式和檔案。

### CmdletInfo。

代表 Cmdlet。

### System.Management.Automation.FunctionInfo

表示函數和篩選準則。

## 注意

* 當會話可以使用一個以上具有相同名稱的命令時，會傳回 `Get-Command` 當您輸入命令名稱時所執行的命令。 若要取得具有相同名稱的命令（依照執行順序列出），請使用 **All** 參數。 如需詳細資訊，請參閱 [about_Command_Precedence](../Microsoft.PowerShell.Core/About/about_Command_Precedence.md)。
* 自動匯入模組時，效果與使用 `Import-Module` Cmdlet 相同。 模組可以新增命令、類型及格式化檔案，並在工作階段中執行指令碼。
  若要啟用、停用及設定自動匯入模組，請使用 `$PSModuleAutoLoadingPreference` 喜好設定變數。 如需詳細資訊，請參閱 [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)。

## 相關連結

[Export-PSSession](../Microsoft.PowerShell.Utility/Export-PSSession.md)

[Get-Help](Get-Help.md)

[Get-Member](../Microsoft.PowerShell.Utility/Get-Member.md)

[Get-PSDrive](../Microsoft.PowerShell.Management/Get-PSDrive.md)

[Import-PSSession](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[about_Command_Precedence](About/about_Command_Precedence.md)
