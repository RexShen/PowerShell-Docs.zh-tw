---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204351"
---
# Get-CimClass

## 概要
取得特定命名空間中的 CIM 類別清單。

## SYNTAX

### ComputerSet (預設) 

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### SessionSet

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## DESCRIPTION

此 `Get-CimClass` Cmdlet 會抓取特定命名空間中的 CIM 類別清單。 如果未提供任何類別名稱，則 Cmdlet 會傳回命名空間中的所有類別。 與 CIM 實例不同的是，CIM 類別不包含從中抓取的 CIM 會話或電腦名稱稱。

## 範例

### 範例1：取得所有類別定義

這個範例會取得命名空間 **根/cimv2** 下的所有類別定義。

```powershell
Get-CimClass
```

### 範例2：取得具有特定名稱的類別

此範例會取得在其名稱中包含文字 **磁片** 的類別。

```powershell
Get-CimClass -ClassName *disk*
```

### 範例3：取得具有特定方法名稱的類別

這個範例會取得以名稱 **Win32** 開頭的類別，並具有以 **Term** 開頭的方法名稱。

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### 範例4：取得具有特定屬性名稱的類別

這個範例會取得以名稱 **Win32** 開頭的類別，且具有名為 **Handle** 的屬性。

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### 範例5：取得具有特定辨識符號名稱的類別

此範例會取得以名稱 **Win32** 開頭的類別，並在其名稱中包含文字 **磁片** ，並且具有指定的限定詞 **關聯** 。

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### 範例6：從特定命名空間取得類別定義

這個範例會從指定的命名空間 **根/standardCimv2** 取得名稱中包含文字 **Net** 的類別定義。

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### 範例7：從遠端伺服器取得類別定義

這個範例會從指定的遠端伺服器 **Server01** 和 **Server02** 取得名稱中包含文字 **磁片** 的類別定義。

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### 範例8：使用 CIM 會話取得類別

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

這組命令會建立具有多部電腦的會話，並使用指令程式將它儲存到變數 `$s` `New-CimSession` 中，然後使用 Cmdlet 取得類別 `Get-CimClass` 。

## PARAMETERS

### -CimSession

在遠端工作階段或遠端電腦上執行 Cmdlet。 輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。 預設為本機電腦上的目前工作階段。

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

### -ClassName

指定要執行作業之 CIM 類別的名稱。 您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ComputerName

指定要在其上執行 CIM 操作的電腦。 您可以指定完整功能變數名稱 (FQDN) NetBIOS 名稱或 IP 位址。

如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。

如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。

如果在同一部電腦上執行多個作業，使用 CIM 會話可提供較佳的效能。

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -方法名稱

尋找具有符合此名稱之方法的類別。 您可以使用萬用字元搭配此參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Namespace

指定 CIM 作業的命名空間。 預設命名空間為 **root/cimv2** 。 您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。

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

### -PropertyName

尋找具有與此名稱相符之屬性的類別。 您可以使用萬用字元搭配此參數。

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

### -QualifierName

依類別層級限定詞名稱篩選類別。 您可以使用萬用字元搭配此參數。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### 無

此 Cmdlet 不接受任何輸入物件。

## 輸出

### CimClass。

此 Cmdlet 會傳回 CIM 類別物件。

## 注意

## 相關連結

[New-CimSession](New-CimSession.md)
