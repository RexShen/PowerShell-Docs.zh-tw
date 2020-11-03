---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: 8f78d57178d5cd500be3c198b59a9af12a307c44
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205347"
---
# Remove-CimInstance

## 概要
從電腦移除 CIM 實例。

## SYNTAX

### CimInstanceComputerSet (預設) 

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### QuerySessionSet

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### QueryComputerSet

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## DESCRIPTION

此 Cmdlet 會從 CIM 伺服器移除 CIM 實例。 您可以使用 Cmdlet 所抓取的 CIM 實例物件 `Get-CimInstance` ，或指定查詢來指定要移除的 cim 實例。

如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。
- 如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。

## 範例

### 範例1：移除 CIM 實例

這個範例會使用 **查詢** 參數，從名為 **Win32_Environment** 的類別中移除以字元字串 **testvar** 開頭的 CIM 實例。

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### 範例2：使用 CIM 實例物件移除 CIM 實例

此範例會取出 **查詢** 參數所篩選的 CIM 實例物件，並將它們儲存在 `$var` 使用 Cmdlet 命名的變數中 `Get-CimInstance` 。 變數的內容接著會傳遞至 `Remove-CimInstance` Cmdlet，以移除 CIM 實例。

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## PARAMETERS

### -CimSession

使用指定的 CIM 會話來執行命令。 輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。 如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

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

如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。

如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。

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

指定要從 CIM 伺服器移除的 CIM 實例物件。 傳遞給 Cmdlet 的物件不會變更，只會移除 CIM 伺服器中的實例。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Namespace

指定 CIM 作業的命名空間。 預設命名空間為 **root/cimv2** 。 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
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

### -Query

指定要在 CIM 伺服器上執行的查詢。 您可以使用 **QueryDialect** 參數來指定查詢方言。

如果指定的值包含雙引號 (`"`) 、單引號 (`'`) 或反斜線 (`\`) ，則必須在字元前面加上反斜線 () 字元來將這些字元加上引號 `\` 。 如果指定的值使用 WQL LIKE 運算子，則必須以方括弧括住下列字元， (`[]`) ： percent (`%`) 、底線 (`_`) 或左方括弧 () `[` 。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
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
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

指定資源類別或實例 (URI) 的資源統一資源識別元。 URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。 例如：

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。

ResourceURI 只能搭配使用 WSMan 通訊協定所建立的 CIM 會話，或是在指定 ComputerName 參數時使用，後者會使用 WSMan 建立 CIM 會話。 如果您指定此參數但未指定 ComputerName 參數，或如果您指定使用 DCOM 通訊協定建立的 CIM 會話，則會收到錯誤，因為 DCOM 通訊協定不支援 ResourceURI 參數。

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

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### 無

此 Cmdlet 不會產生任何輸出。

## 注意

## 相關連結

[New-CimInstance](New-CimInstance.md)

[Get-CimInstance](get-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
