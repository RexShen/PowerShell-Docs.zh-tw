---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202676"
---
# Remove-PSSnapin

## 概要
從目前的工作階段中移除 Windows PowerShell 嵌入式管理單元。

## SYNTAX

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION
**PSSnapin** 指令 Cmdlet 會從目前的會話中移除 Windows PowerShell 的嵌入式管理單元。
您可以使用它來移除您已新增的嵌入式管理單元，Windows PowerShell 無法使用這個 Cmdlet 來移除隨 Windows PowerShell 安裝的嵌入式管理單元。

從目前的會話移除嵌入式管理單元之後，仍會載入嵌入式管理單元，但該嵌入式管理單元中的 Cmdlet 和提供者將無法再于會話中使用。

## 範例

### 範例1：移除嵌入式管理單元

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

此命令會從目前的會話移除 **Microsoft. Exchange** 嵌入式管理單元。
當命令完成時，嵌入式管理單元支援的 Cmdlet 和提供者於工作階段中將無法使用。

### 範例2：使用名稱搭配管線來移除嵌入式管理單元

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

此命令會從目前會話移除名稱開頭為 smp 的 Windows PowerShell 嵌入式管理單元。

此命令會使用 **PSSnapin** Cmdlet 取得代表嵌入式管理單元的物件。管線運算子 (|) 將結果傳送至 **PSSnapin** Cmdlet，這會將它們從會話中移除。
這個嵌入式管理單元支援的提供者與 Cmdlet 於工作階段中將無法使用。

當您使用管線將物件傳送至 **PSSnapin** 時，物件的名稱會與 *name* 參數相關聯，它會接受管線中具有 **name** 屬性的物件。

### 範例3：使用名稱移除嵌入式管理單元

```
PS C:\> Remove-PSSnapin -Name *event*
```

此命令會移除所有名稱包含事件的 Windows PowerShell 嵌入式管理單元。

## PARAMETERS

### -Name
指定要從目前工作階段中移除的 Windows PowerShell 嵌入式管理單元名稱。
允許使用萬用字元 (*)。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru
傳回代表嵌入式管理單元的物件。
根據預設，此 Cmdlet 不會產生任何輸出。

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
顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

### System.Management.Automation.PSSnapInInfo
您可以使用管線將嵌入式管理單元物件傳送至此 Cmdlet。

## 輸出

### None、PSSnapInInfo、Automation。
如果您指定 *PassThru* 參數，此 Cmdlet 會產生代表嵌入式管理單元的 **PSSnapInInfo** 物件。
根據預設， **PSSnapin** 不會產生任何輸出。

## 注意

* **PSSnapin** 從會話移除嵌入式管理單元之前，不會檢查 Windows PowerShell 的版本。 如果嵌入式管理單元不可移除，則會出現警告，且命令會失敗。
* **PSSnapin** 只會影響目前的會話。 如果已將 Add-PSSnapin 命令新增到 Windows PowerShell 設定檔，您應該刪除命令以從未來工作階段移除嵌入式管理單元。 如需指示，請輸入 `Get-Help about_Profiles` 。

## 相關連結

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)
