---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: a2374e7bcd9399f2699d186537b8f674fd6c899b
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205551"
---
# New-CimInstance

## 概要
建立 CIM 實例。

## SYNTAX

### ClassNameComputerSet (預設) 

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ClassNameSessionSet

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ResourceUriSessionSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### ResourceUriComputerSet

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### CimClassSessionSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimClassComputerSet

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

此 `New-CimInstance` Cmdlet 會根據本機電腦或遠端電腦上的類別定義，建立 CIM 類別的實例。 根據預設，此 `New-CimInstance` Cmdlet 會在本機電腦上建立實例。

## 範例

### 範例1：建立 CIM 類別的實例

此範例會在電腦的 root/cimv2 命名空間中建立名為 win32_environment 的 CIM 類別實例。

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

如果類別不存在、屬性錯誤或伺服器拒絕呼叫，就不會執行用戶端驗證。 如果成功建立實例，此 Cmdlet 會輸出新建立的實例。

### 範例2：使用類別架構來建立 CIM 類別的實例

此範例會抓取 CIM 類別物件，並將它儲存在名為的變數中 `$class` 。 然後將變數的內容傳遞給 `New-CimInstance` Cmdlet。

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### 範例3：在用戶端上建立動態實例

此範例會在用戶端電腦上建立名為 **Win32_Process** 之 CIM 類別的動態實例，而不會從伺服器取得實例。 新的實例會儲存在變數中 `$a` 。 如果伺服器上有具有此索引鍵的實例，這個動態實例可以用來執行作業。

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

然後，Cmdlet 會抓取 `Get-CimInstance` 特定的單一實例。 Cmdlet 會在已抓取 `Invoke-CimMethod` 的實例上呼叫 **GetOwner** 方法。

### 範例4：建立特定命名空間之 CIM 類別的實例

這個範例會在命名空間 **根/位置** 取得名為 **MSFT_Something** 的 CIM 類別實例，並將它儲存在名為的變數中 `$class` 。 變數會傳遞至 `New-CimInstance` Cmdlet 以建立新的 CIM 實例，並在新的實例上執行用戶端驗證。

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

在此範例中，使用 **CimClass** 參數而非 **ClassName** 參數，會驗證 **Prop1** 和 **this.prop2** 確實存在，而且索引鍵的標記是否正確。

您無法使用 **ComputerName** 或 **CimSession** 參數搭配 **ClientOnly** 參數。

## PARAMETERS

### -CimClass

指定表示實例類型的 CIM 類別物件。 使用 `Get-CimClass` Cmdlet 從電腦取出類別宣告。 使用此參數會產生更佳的用戶端架構驗證。

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -CimSession

使用指定的 CIM 會話來執行命令。 輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。 如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ClassName

指定作業建立實例之 CIM 類別的名稱。 注意：您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。

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

### -ClientOnly

表示實例只會在 PowerShell 中建立，而不會進入 CIM 伺服器。 您可以使用此參數來建立記憶體中的 CIM 實例，以用於後續的 PowerShell 作業。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

指定要在其上執行 CIM 作業的電腦名稱稱。 您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。

如果您指定這個參數，此 Cmdlet 會使用 WSMan 通訊協定建立指定電腦的暫時會話。

如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。

如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Key

指定用來做為索引鍵的屬性。 指定索引 **鍵** 時，不能使用 **CimSession** 和 **ComputerName** 。

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Namespace

為新的實例指定類別的命名空間。 預設命名空間為 **root/cimv2** 。
您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OperationTimeoutSec

指定 Cmdlet 等待 CIM 伺服器回應的時間量。 根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。 如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。

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

使用雜湊表 (名稱/值組) ，指定 CIM 實例的屬性。

如果您指定 **CimClass** 參數，則此 `New-CimInstance` Cmdlet 會在用戶端上執行屬性驗證，以確保指定的屬性與伺服器上的類別宣告一致。 如果未指定 **CimClass** 參數，則會在伺服器上完成屬性驗證。

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

指定資源類別或實例 (URI) 的資源統一資源識別元。 URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。 例如：

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。

**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。 如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。

如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
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

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### System.Object

此 Cmdlet 會傳回包含 CIM 實例資訊的物件。

## 注意

## 相關連結

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)

[Remove-CimInstance](remove-ciminstance.md)

[Set-CimInstance](Set-CimInstance.md)
