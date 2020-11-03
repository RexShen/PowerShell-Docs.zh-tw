---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: edc67596bdb446b18635339255376a17d3f67843
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205555"
---
# Get-CimInstance

## 概要
從 CIM 伺服器取得類別的 CIM 實例。

## SYNTAX

### ClassNameComputerSet (預設) 

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### ResourceUriSessionSet

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QuerySessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### ClassNameSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### CimInstanceSessionSet

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### CimInstanceComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### ResourceUriComputerSet

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### QueryComputerSet

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## DESCRIPTION

`Get-CimInstance`Cmdlet 會從 cim 伺服器取得類別的 cim 實例。 您可以為此 Cmdlet 指定類別名稱或查詢。 這個 Cmdlet 會傳回一或多個 CIM 實例物件，代表 CIM 伺服器上的 CIM 實例的快照。

如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。
- 如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。

如果指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數和 **CimSession** 參數都未指定，則此 Cmdlet 會使用輸入物件中的 CIM 會話或電腦名稱稱。
- 如果指定 **ComputerName** 參數或 **CimSession** 參數，則此 Cmdlet 會使用 CimSession 參數值或 **ComputerName** 參數值。

## 範例

### 範例1：取得指定類別的 CIM 實例

此範例會抓取名為 **Win32_Process** 之類別的 CIM 實例。

```powershell
Get-CimInstance -ClassName Win32_Process
```

### 範例2：取得 WMI 伺服器的命名空間清單

此範例會在 WMI 伺服器的 **根** 命名空間下抓取命名空間清單。

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### 範例3：取得使用查詢篩選之類別的實例

這個範例會使用 **查詢** 參數所指定的查詢，從名為 **Win32_Process** 之類別的字母 **P** 開始，抓取所有的 CIM 實例。

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### 範例4：使用類別名稱和篩選運算式取得已篩選之類別的實例

此範例會使用篩選參數，從名稱為 **Win32_Process** 之類別的字母 **P** 開始，抓取所有的 CIM 實例。

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### 範例5：取得僅填入索引鍵屬性的 CIM 實例

此範例會使用索引鍵屬性，在記憶體中為名為 **Win32_Process** 的類別建立新的 CIM 實例 `@{ "Handle"=0 }` ，並將它儲存在名為的變數中 `$x` 。 變數會以 CIM 實例的形式傳遞至 `Get-CimInstance` Cmdlet，以取得特定的實例。

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### 範例6：取出 CIM 實例並重複使用

這個範例會取得名為 **Win32_Process** 之類別的 CIM 實例，並將它們儲存在變數 `$x` 和中 `$y` 。 然後，此變數 `$x` 會在僅包含 **Name** 和 **KernelModeTime** 屬性的資料表中格式化，並將資料表設定為自動 **調整** 。

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### 範例7：從遠端電腦取得 CIM 實例

此範例會從名為 **Server01** 和 **Server02** 的遠端電腦，抓取名為 **Win32_ComputerSystem** 之類別的 CIM 實例。

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### 範例8：只取得索引鍵屬性，而不是所有屬性

此範例只會抓取索引鍵屬性，以減少物件和網路流量的大小。

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### 範例9：只取得屬性的子集，而不是所有屬性

此範例只會抓取屬性的子集，以減少物件和網路流量的大小。

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

使用 **Property** 參數取出的實例可以用來執行其他 CIM 作業，例如 `Set-CimInstance` 或 `Invoke-CimMethod` 。

### 範例10：使用 CIM 會話取得 CIM 實例

此範例會使用 Cmdlet 在名為 **Server01** 的電腦上建立 CIM 會話 **，並將** `New-CimSession` 會話資訊儲存在名為的變數中 `$s` 。 然後使用 CimSession 參數將變數的內容傳遞至 `Get-CimInstance` ，以 **CimSession** 取得名為 **WIN32_COMPUTERSYSTEM** 之類別的 CIM 實例。

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## PARAMETERS

### -CimSession

指定要用於此 Cmdlet 的 CIM 會話。 輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。 如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

指定要為其取得 CIM 實例的 CIM 類別名稱。 您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ComputerName

指定您要執行 CIM 操作的電腦。 您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。 如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。

如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。

如果在同一部電腦上執行多個作業，請使用 CIM 會話連線，以獲得更好的效能。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

指定要做為篩選準則使用的 where 子句。 請在 **WQL** 或 **CQL** 查詢語言中指定子句。 請勿 `WHERE` 在參數的值中包含關鍵字。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

指定要做為輸入使用的 CIM 實例物件。

如果您已經在使用 CIM 實例物件，您可以使用此參數來傳遞 CIM 實例物件，以便從 CIM 伺服器取得最新的快照集。 當您傳遞 CIM 實例物件做為輸入時，會 `Get-CimInstance` 使用取得 CIM 作業（而不是列舉或查詢作業）從伺服器傳回物件。 使用「取得 CIM」作業會比取出所有實例，然後加以篩選更有效率。

如果 CIM 類別未執行 get 作業，則指定 **InputObject** 參數會傳回錯誤。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

指出只會傳回已填入索引鍵屬性的物件。 指定 **KeyOnly** 參數可減少透過網路傳輸的資料量。

使用 **KeyOnly** 參數來只傳回物件的一小部分，這可用於其他作業，例如 `Set-CimInstance` 或 `Get-CimAssociatedInstance` Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Namespace

指定 CIM 類別的命名空間。

預設命名空間為 **root/cimv2** 。 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
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

### -Property

指定要取出的實例屬性集。 當您需要在記憶體中或透過網路來減少傳回的物件大小時，請使用此參數。 傳回的物件也會包含索引鍵屬性，即使您未使用 **Property** 參數列出它們也是一樣。 類別的其他屬性存在，但不會填入。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Query

指定要在 CIM 伺服器上執行的查詢。 如果指定的值包含雙引號 `"` 、單引號 `'` 或反斜線， `\` 您必須在前面加上反斜線字元，以將這些字元加上引號。 如果指定的值使用 WQL **LIKE** 運算子，您必須以方括弧括住下列字元 `[]` ：百分比 `%` 、底線 `_` 或左方括弧 `[` 。

您無法使用中繼資料查詢來取出類別清單或事件查詢。 若要取出類別清單，請使用 `Get-CimClass` Cmdlet。 若要取出事件查詢，請使用 `Register-CimIndicationEvent` Cmdlet。

您可以使用 **QueryDialect** 參數來指定查詢方言。

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -QueryDialect

指定用於查詢參數的查詢語言。 此參數可接受的值為： **WQL** 或 **CQL** 。 預設值為 **WQL** 。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
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

**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。 如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。

如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -淺層

表示傳回類別的實例，而不包含任何子類別的實例。 根據預設，此 Cmdlet 會傳回類別的實例及其子類別。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### CIM 實例

此 Cmdlet 會接受以 InputObject 參數指定的輸入物件。

## 輸出

### CIM 實例

此 Cmdlet 會傳回一或多個 CIM 實例物件，代表 CIM 伺服器上 CIM 實例的快照集。

## 注意

## 相關連結

[Format-Table](../microsoft.powershell.utility/format-table.md)

[Get-CimAssociatedInstance](Get-CimAssociatedInstance.md)

[Get-CimClass](Get-CimClass.md)

[Invoke-CimMethod](invoke-cimmethod.md)

[New-CimInstance](New-CimInstance.md)

[Register-CimIndicationEvent](Register-CimIndicationEvent.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
