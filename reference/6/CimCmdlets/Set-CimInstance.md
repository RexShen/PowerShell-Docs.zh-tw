---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: e4775a9d9a37fdd448f6910e612b97a45a35351c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205420"
---
# Set-CimInstance

## 概要
藉由呼叫 CIM 類別的 ModifyInstance 方法，修改 CIM 伺服器上的 CIM 實例。

## SYNTAX

### CimInstanceComputerSet (預設) 

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### CimInstanceSessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QuerySessionSet

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會修改 CIM 伺服器上的 CIM 實例。

如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。
- 如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。

如果指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數和 **CimSession** 參數都未指定，則此 Cmdlet 會使用輸入物件中的 CIM 會話或電腦名稱稱。
- 如果指定 **ComputerName** 參數或 **CimSession** 參數，則此 Cmdlet 會使用 **CimSession** 參數值或 **ComputerName** 參數值。 這並不常見。

## 範例

### 範例1：設定 CIM 實例

這個範例會使用 **查詢** 參數，將 **VariableValue** 屬性的值設定為 **abcd** 。 您可以修改符合 Windows Management Instrumentation 查詢語言 (WQL) 查詢的實例。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### 範例2：使用管線設定 CIM 實例屬性

此範例會使用 Cmdlet 來抓取 **查詢** 參數所篩選的 CIM 實例物件 `Get-CimInstance` 。 此 `Set-CimInstance` Cmdlet 會將 **VariableValue** 屬性的值修改為 **abcd** 。

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### 範例3：使用輸入物件設定 CIM 實例屬性

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

這個範例會使用，將中查詢參數篩選的 CIM 實例物件 `$x` `Get-CimInstance` ，然後將變數的內容傳遞給 `Set-CimInstance` Cmdlet。 `Set-CimInstance` 然後，將 **VariableValue** 屬性修改為 **somevalue** 。 因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。

### 範例4：設定 CIM 實例屬性

此範例會使用 Cmdlet 將 **查詢** 參數中指定的 CIM 實例物件 `$x` ，變更為變數 `Get-CimInstance` ，並將物件的 **VariableValue** 屬性值變更為 change。 然後會使用 Cmdlet 來儲存 CIM 實例物件 `Set-CimInstance` 。
因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### 範例5：顯示要使用 WhatIf 修改的 CIM 實例清單

此範例會使用一般參數 **WhatIf** 來指定不應執行修改，但是只會輸出完成時所發生的情況。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### 範例6：在使用者確認之後設定 CIM 實例

這個範例會使用一般參數 **Confirm** 來指定只在使用者確認之後才執行修改。

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### 範例7：設定已建立的 CIM 實例

此範例會使用 Cmdlet 建立具有指定屬性的 CIM 實例 `New-CimInstance` ，並將其內容提取到變數中 `$x` 。 變數接著會傳遞至 `Set-CimInstance` Cmdlet，此 Cmdlet 會將 **VariableValue** 屬性的值修改為 **somevalue** 。
因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## PARAMETERS

### -CimSession

在遠端電腦上執行 Cmdlet。 輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName

指定要在其上執行 CIM 作業的電腦名稱稱。 您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。

如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。

如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。

如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定要做為輸入使用的 CIM 實例物件。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Namespace

指定 CIM 作業的命名空間。 預設命名空間為 root/cimv2。 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

指定 Cmdlet 等候電腦回應的時間長度。 根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。

如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

傳回代表您正在使用之項目的物件。 根據預設，此 Cmdlet 不會產生任何輸出。

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

### -Property

使用) 的名稱/值組，將 CIM 實例的屬性指定為雜湊表 (。 只有使用此參數指定的屬性才會變更。 其他 CIM 實例的屬性則不會變更。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

指定要在 CIM 伺服器上執行的查詢，以抓取要執行 Cmdlet 的 CIM 實例。 您可以使用 QueryDialect 參數來指定查詢方言。

如果指定的值包含雙引號 (`"`) 、單引號 (`'`) 或反斜線 (`\`) ，則必須在字元前面加上反斜線 () 字元來將這些字元加上引號 `\` 。 如果指定的值使用 WQL **LIKE** 運算子，則必須以方括弧括住下列字元， (`[]`) ： percent (`%`) 、底線 (`_`) 或左方括弧 () `[` 。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

指定用於查詢參數的查詢語言。 此參數可接受的值為： **WQL** 或 **CQL** 。 預設值為 **WQL** 。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

指定資源類別或實例 (URI) 的資源統一資源識別元。 URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。 例如：

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。

ResourceURI 只能搭配使用 WSMan 通訊協定所建立的 CIM 會話，或是在指定 ComputerName 參數時使用，後者會使用 WSMan 建立 CIM 會話。 如果您指定此參數但未指定 ComputerName 參數，或如果您指定使用 DCOM 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 DCOM 通訊協定不支援 ResourceURI 參數。

如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### Microsoft.Management.Infrastructure.CimInstance

## 輸出

### Microsoft.Management.Infrastructure.CimInstance

指定 **Passthru** 參數時，此 Cmdlet 會傳回修改過的 CIM 實例物件。

## 注意

## 相關連結

[Get-CimInstance](get-ciminstance.md)

[New-CimInstance](New-CimInstance.md)

[Remove-CimInstance](remove-ciminstance.md)
