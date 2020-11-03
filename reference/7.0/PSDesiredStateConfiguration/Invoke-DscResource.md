---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 4703586008d9044ae68fd7375db65f0d0a9b9980
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2020
ms.locfileid: "93206051"
---
# Invoke-DscResource

## 概要
執行指定 PowerShell Desired State Configuration (DSC) 資源的方法。

## SYNTAX

```
Invoke-DscResource [[-Method] <Object>] [[-Name] <Object>] [[-Property] <Object>]
 [[-ModuleName] <Object>] [-AsJob] [<CommonParameters>]
```

## DESCRIPTION

`Invoke-DscResource` Cmdlet 會執行指定之 PowerShell Desired State Configuration (DSC) 資源的方法。

此 Cmdlet 會直接叫用 DSC 資源，而不需建立設定文件。 使用此 Cmdlet，設定管理產品可以使用 DSC 資源來管理 windows 或 Linux。 當 DSC 引擎在啟用了偵錯的情況下執行時，此 Cmdlet 也會啟用資源的偵錯。

> [!NOTE]
> `Invoke-DscResource` 是 PowerShell 7 中的實驗性功能。 若要使用 Cmdlet，您必須使用下列命令來啟用它。
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## 範例

### 範例1：指定資源的必要屬性來叫用資源的 Set 方法

這個範例會叫用名為 **WindowsProcess** 之資源的 **Set** 方法，並提供必要的 **Path** 和 **Arguments** 屬性來啟動指定的 Windows 進程。

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### 範例2：叫用指定模組之資源的測試方法

這個範例會叫用名為 **WindowsProcess** 之資源的 **測試** 方法，該資源位於名為 **PSDesiredStateConfiguration** 的模組中。

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETERS

### -Method

指定此 Cmdlet 叫用之資源的方法。 此參數可接受的值為： **Get** 、 **Set** 和 **Test** 。

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ModuleName

指定此 Cmdlet 用來叫用指定之資源的模組名稱。

```yaml
Type: ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

指定要啟動之 DSC 資源的名稱。

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Property

在雜湊表中指定資源的屬性名稱與其值，分別作為索引鍵和值。

```yaml
Type: Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

## 輸出

### CimInstance，system.string. 布林值

## 注意

- 先前，除非使用金鑰 **PsDscRunAsCredential** 以使用者內容指定，否則 Windows PowerShell 5.1 資源會在系統內容下執行。 在 PowerShell 7.0 中，資源會在使用者的內容中執行，且不再支援 **PsDscRunAsCredential** 。 先前使用此金鑰的設定將會擲回例外狀況。

- 從 PowerShell 7， `Invoke-DscResource` 不再支援叫用 WMI DSC 資源。 這包括 **PSDesiredStateConfiguration** 中的 **檔案** 和 **記錄** 資源。

## 相關連結

[Windows PowerShell Desired State Configuration 概觀](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscResource](Get-DscResource.md)
