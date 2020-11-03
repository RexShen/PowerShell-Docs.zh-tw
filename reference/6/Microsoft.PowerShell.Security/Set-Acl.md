---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-acl?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Acl
ms.openlocfilehash: 0f5757d7e9fb2615149fd08473685491bfccada7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204731"
---
# Set-Acl

## 概要
變更指定項目的安全性描述元，例如檔案或登錄機碼。

## SYNTAX

### ByPath (預設值)

```
Set-Acl [-Path] <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByInputObject

```
Set-Acl [-InputObject] <PSObject> [-AclObject] <Object> [-Passthru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Set-Acl -LiteralPath <String[]> [-AclObject] <Object> [-ClearCentralAccessPolicy] [-Passthru]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

指令程式會 `Set-Acl` 變更指定專案（例如，檔案或登錄機碼）的安全描述項，以符合您提供的安全描述項中的值。

若要使用 `Set-Acl` ，請使用 **Path** 或 **InputObject** 參數來識別您想要變更其安全描述項的專案。 然後使用 **AclObject** 或 **SecurityDescriptor** 參數，提供擁有您想要套用之值的安全性描述元。 `Set-Acl` 套用提供的安全描述項。 它使用 **AclObject** 參數的值作為模型，並變更項目安全性描述元中的值，以符合 **AclObject** 參數中的值。

## 範例

### 範例1：將安全描述項從一個檔案複製到另一個檔案

```powershell
$DogACL = Get-Acl -Path "C:\Dog.txt"
Set-Acl -Path "C:\Cat.txt" -AclObject $DogACL
```

這些命令會將值從 Dog.txt 檔案的安全性描述元複製到 Cat.txt 檔案的安全性描述元。 當命令完成時，Dog.txt 和 Cat.txt 檔案的安全性描述元會完全相同。

第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。
指派運算子 () 會將 `=` 安全描述項儲存在 $DogACL 變數的值中。

第二個命令會使用 `Set-Acl` 將 Cat.txt 之 ACL 中的值變更為中的值 `$DogACL` 。

**Path** 參數的值是 Cat.txt 檔案的路徑。 **AclObject** 參數的值為模型 acl，在此案例中，會將 Dog.txt 的 acl 儲存在 `$DogACL` 變數中。

### 範例2：使用管線運算子來傳遞描述項

```powershell
Get-Acl -Path "C:\Dog.txt" | Set-Acl -Path "C:\Cat.txt"
```

此命令與上一個範例中的命令幾乎相同，不同之處在于它會使用管線運算子 (`|`) 將安全描述項從 `Get-Acl` 命令傳送至 `Set-Acl` 命令。

第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。 管線運算子 (`|`) 會將代表 Dog.txt 安全描述項的物件傳遞給 `Set-Acl` Cmdlet。

第二個命令會使用將 `Set-Acl` Dog.txt 的安全描述項套用至 Cat.txt。
當命令完成時，Dog.txt 和 Cat.txt 檔案的 ACL 會完全相同。

### 範例3：將安全描述項套用至多個檔案

```powershell
$NewAcl = Get-Acl File0.txt
Get-ChildItem -Path "C:\temp" -Recurse -Include "*.txt" -Force | Set-Acl -AclObject $NewAcl
```

這些命令會將 File0.txt 檔案中的安全描述項套用至 `C:\Temp` 目錄及其所有子目錄中的所有文字檔。

第一個命令會取得目前目錄中 File0.txt 檔案的安全描述項，並使用指派運算子 (`=`) 將它儲存在 `$NewACL` 變數中。

管線中的第一個命令會使用 Get-ChildItem Cmdlet 來取得目錄中的所有文字檔 `C:\Temp` 。 **遞迴** 參數會將命令延伸至的所有子目錄 `C:\temp` 。 **Include** 參數會將取出的檔案限制為副檔名為的檔案 `.txt` 。 **Force** 參數可取得隱藏的檔案，若沒有使用此參數則會排除這些檔案。  (您無法使用 `c:\temp\*.txt` ，因為 **遞迴** 參數適用于目錄，而不是在檔案上。 ) 

管線運算子 () 會將代表抓取之檔案的 `|` 物件傳送至 `Set-Acl` Cmdlet，此 Cmdlet 會將 **AclObject** 參數中的安全描述項套用至管線中的所有檔案。

在實務上，最好是將 **WhatIf** 參數與所有 `Set-Acl` 可能影響一個以上專案的命令搭配使用。 在此情況下，管線中的第二個命令會是 `Set-Acl -AclObject $NewAcl -WhatIf` 。 此命令可列出會受命令影響的檔案。 查看結果之後，您可以在沒有 **WhatIf** 參數的情況下再次執行命令。

### 範例4：停用繼承並保留繼承的存取規則

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
$isProtected = $true
$preserveInheritance = $true
$NewAcl.SetAccessRuleProtection($isProtected, $preserveInheritance)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

這些命令會停用從父資料夾繼承的存取，同時仍然保留現有的繼承存取規則。

第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。

接下來，會建立變數，以將繼承的存取規則轉換成明確的存取規則。 若要保護與這個繼承的存取規則，請將 `$isProtected` 變數設為 `$true` 。若要允許繼承，請將設定 `$isProtected` 為 `$false` 。 如需詳細資訊，請參閱 [設定存取規則保護](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)。
將 `$preserveInheritance` 變數設為 `$true` 以保留繼承的存取規則; false 則會移除繼承的存取規則。 然後使用 **SetAccessRuleProtection ( # B1** 方法更新存取規則保護。

最後一個命令會使用將的 `Set-Acl` 安全描述項套用至 Dog.txt。 當命令完成時，繼承自 [寵物] 資料夾的 Dog.txt Acl 將會直接套用至 Dog.txt，而新增至寵物的新存取原則將不會變更 Dog.txt 的存取權。

### 範例5：將檔案的完整控制權授與系統管理員

```powershell
$NewAcl = Get-Acl -Path "C:\Pets\Dog.txt"
# Set properties
$identity = "BUILTIN\Administrators"
$fileSystemRights = "FullControl"
$type = "Allow"
# Create new rule
$fileSystemAccessRuleArgumentList = $identity, $fileSystemRights, $type
$fileSystemAccessRule = New-Object -TypeName System.Security.AccessControl.FileSystemAccessRule -ArgumentList $fileSystemAccessRuleArgumentList
# Apply new rule
$NewAcl.SetAccessRule($fileSystemAccessRule)
Set-Acl -Path "C:\Pets\Dog.txt" -AclObject $NewAcl
```

此命令會將 Dog.txt 檔案的完整控制權授與 **BUILTIN\Administrators** 群組。

第一個命令會使用 `Get-Acl` Cmdlet 取得 Dog.txt 檔案的安全描述項。

系統會建立下一個變數，以授與 **BUILTIN\Administrators** 群組 Dog.txt 檔案的完整控制權。 `$identity`設定為[使用者帳戶](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)名稱的變數。
將 `$fileSystemRights` 變數設定為 FullControl，而且可以是任何一個指定與存取規則相關聯之作業類型的 [FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights) 值。 將 `$type` 變數設定為「允許」以指定是否要允許或拒絕作業。 `$fileSystemAccessRuleArgumentList`變數是在建立新的 **system.security.accesscontrol.filesystemaccessrule** 物件時，要傳遞的引數清單。 然後會建立新的 **system.security.accesscontrol.filesystemaccessrule** 物件，並將 **system.security.accesscontrol.filesystemaccessrule** 物件傳遞給 **SetAccessRule ( # B1** 方法，以加入新的存取規則。

最後一個命令會使用將的 `Set-Acl` 安全描述項套用至 Dog.txt。
當命令完成時， **BUILTIN\Administrators** 群組將擁有 Dog.txt 的完整控制權。

## PARAMETERS

### -AclObject

將所要的屬性值指定給 ACL。 `Set-Acl` 變更 **Path** 或 **InputObject** 參數所指定之專案的 ACL，以符合指定之安全性物件中的值。

您可以將命令的輸出儲存 `Get-Acl` 在變數中，然後使用 **AclObject** 參數傳遞變數或輸入 `Get-Acl` 命令。

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClearCentralAccessPolicy

從指定項目移除集中存取原則。

從 Windows Server 2012 開始，系統管理員可以使用 Active Directory 和群組原則為使用者和群組設定集中存取原則。 如需詳細資訊，請參閱 [動態存取控制：案例總覽](/windows-server/identity/solution-guides/dynamic-access-control--scenario-overview)。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ByPath, ByLiteralPath
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Exclude

省略指定的項目。 此參數的值會限定 **Path** 參數。 輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

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

### -Filter

以提供者的格式或語言指定篩選。 此參數的值會限定 **Path** 參數。 篩選的語法 (包括是否使用萬用字元) 取決於提供者。 篩選比其他參數更有效率，因為提供者會在抓取物件時套用篩選，而不是在抓取物件之後，讓 PowerShell 篩選物件。

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

只變更指定的項目。 此參數的值會限定 **Path** 參數。
輸入路徑元素或模式，例如 `*.txt`。 允許使用萬用字元。

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

### -InputObject

變更指定物件的安全性描述元。 輸入包含物件的變數，或輸入可取得物件的命令。

您無法將要變更的物件傳送至 `Set-Acl` 。 請改為在命令中明確地使用 **InputObject** 參數。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

變更指定項目的安全性描述元。 與 **Path** 不同， **LiteralPath** 參數值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請將它括在單引號中 (`'`) 。
單引號可告知 PowerShell 不要將任何字元解釋為 escape 序列。

此參數是在 Windows PowerShell 3.0 引進。

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Passthru

傳回代表已變更安全性描述元的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Path

變更指定項目的安全性描述元。 輸入項目的路徑，例如檔案或登錄機碼的路徑。 允許使用萬用字元。

如果您 `Set-Acl` 使用 **AclObject** 或 **SecurityDescriptor** 參數將安全性物件傳遞給 (，或將安全性物件從 Get-Acl 傳遞至 `Set-Acl`) ，而您省略 **路徑** 參數 (名稱和值) ，則 `Set-Acl` 會使用安全性物件中包含的路徑。

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 Cmdlet 並不會執行。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### AccessControl. ObjectSecurity，AccessControl.. CommonSecurityDescriptor

您可以使用管線將 ACL 物件或安全描述項傳送至 `Set-Acl` 。

## 輸出

### AccessControl. System.security.accesscontrol.filesecurity

依預設，不 `Set-Acl` 會產生任何輸出。
不過，如果您使用 **Passthru** 參數，它會產生安全性物件。
安全性物件的類型需視項目的類型而定。

## 注意

 `Set-Acl`PowerShell 檔案系統和登錄提供者支援此 Cmdlet。 這表示您可以用它來變更檔案、目錄和登錄機碼的安全性描述元。

## 相關連結

[Get-Acl](Get-Acl.md)

[System.security.accesscontrol.filesystemaccessrule](/dotnet/api/system.security.accesscontrol.filesystemaccessrule.-ctor)

[ObjectSecurity. SetAccessRuleProtection](/dotnet/api/system.security.accesscontrol.objectsecurity.setaccessruleprotection)

[FileSystemRights](/dotnet/api/system.security.accesscontrol.filesystemrights)
