---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: adf6c1ac6f6f9288233d530b7ea2101f4b7688e4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205427"
---
# Get-CimAssociatedInstance

## 概要
抓取由關聯連接到特定 CIM 實例的 CIM 實例。

## SYNTAX

### ComputerSet (預設) 

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### SessionSet

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## DESCRIPTION

指令 `Get-CimAssociatedInstance` 程式可透過關聯，抓取連接到特定 cim 實例的 cim 實例，稱為來源實例。

在關聯中，每個 CIM 實例都有一個命名角色，而且相同的 CIM 實例可以參與不同角色的關聯。

如果未指定 InputObject 參數，Cmdlet 會以下列其中一種方式運作：

- 如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。
- 如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。

## 範例

### 範例1：取得特定實例的所有相關聯實例

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

這組命令會抓取名為 Win32_LogicalDisk 之類別的實例，並將資訊儲存在使用 Cmdlet 命名的變數中 `$disk` `Get-CimInstance` 。 變數中的第一個邏輯磁片實例接著會用來做為 Cmdlet 的輸入物件， `Get-CimAssociatedInstance` 以取得指定之 cim 實例的所有相關聯 cim 實例。

### 範例2：取得特定類型的所有相關聯實例

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

這組命令會抓取 **Win32_LogicalDisk** 類別的所有實例，並將其儲存在名為的變數中 `$disk` 。 變數中的第一個邏輯磁片實例接著會用來做為 Cmdlet 的輸入物件， `Get-CimAssociatedInstance` 以取得透過指定的關聯類別 **Win32_DiskPartition** 建立關聯的所有相關聯實例。

### 範例3：透過特定類別的辨識符號取得所有相關聯的實例

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

這組命令會抓取相依于 WMI 服務的服務，並將其儲存在名為的變數中 `$s` 。 使用 Cmdlet 來抓取 **Win32_DependentService** 的關聯類別名稱， `Get-CimClass` 方法是指定 **association** 做為辨識符號，然後使用 $s 傳遞至 Cmdlet， `Get-CimAssociatedInstance` 以取得已抓取之關聯類別的所有相關聯實例。

## PARAMETERS

### -關聯

指定關聯類別的名稱。 如果您未指定此參數，Cmdlet 會傳回任何類型的所有現有關聯物件。

例如，如果類別 A 透過兩個關聯（AB1 和 AB2）與類別 B 相關聯，則這個參數可以用來指定關聯的類型，也就是 AB1 或 AB2。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -CimSession

使用指定的 CIM 會話來執行命令。 輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` 。 如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
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
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

指定此 Cmdlet 的輸入。 您可以使用這個參數，或者您可以透過管線將輸入傳送到此 Cmdlet。

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -KeyOnly

傳回只填入索引鍵屬性的物件。 這會減少透過網路傳輸的資料量。

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

### -Namespace

指定 CIM 作業的命名空間。 預設命名空間為 root/cimv2。

> [!NOTE]
> 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

```yaml
Type: System.String
Parameter Sets: (All)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ResourceUri

指定資源類別或實例 (URI) 的資源統一資源識別元。 URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。

URI 是由前置詞與資源路徑所組成。 例如：

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。

**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。 如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，則會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。

如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResultClassName

指定相關聯實例的類別名稱。 CIM 實例可以與一或多個 CIM 實例相關聯。 如果您未指定結果類別名稱，則會傳回所有相關聯的 CIM 實例。

根據預設，此參數的值為 null，而且會傳回所有相關聯的 CIM 實例。

您可以篩選關聯結果，使其符合特定的類別名稱。 篩選會在伺服器上進行。 如果未指定此參數，則會傳回 `Get-CIMAssociatedInstance` 所有現有的關聯。 例如，如果類別 A 與類別 B、C 和 D 相關聯，則這個參數可以用來將輸出限制為特定類型， (B、C 或 D) 。

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

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### System.Object

此 Cmdlet 會傳回物件。

## 注意

## 相關連結

[Get-CimClass](get-cimclass.md)

[Get-CimInstance](get-ciminstance.md)
