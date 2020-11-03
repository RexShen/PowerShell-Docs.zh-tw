---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: ''
schema: 2.0.0
ms.openlocfilehash: 34998e7c4a6876821df949019970dc1d87297397
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208551"
---
# Get-PSSubsystem

## 概要
抓取在 PowerShell 中註冊之子系統的相關資訊。

## SYNTAX

### GetAllSet (預設) 

```
Get-PSSubsystem [<CommonParameters>]
```

### GetByKindSet

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### GetByTypeSet

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## DESCRIPTION

抓取在 PowerShell 中註冊之子系統的相關資訊。

> [!NOTE]
> 這是實驗性的功能。 只有啟用此功能時，才可使用此 Cmdlet `PSSubsystemPluginModel` 。 如需詳細資訊，請參閱 [使用實驗性功能](/powershell/scripting/learn/experimental-features)。

並讓您將 `System.Management.Automation.dll` 的元件區分為本身組件中的個別子系統。 這種區隔可減少核心 PowerShell 引擎的磁碟使用量，並讓這些元件成為選用功能，只需安裝最低版本的 PowerShell。

目前僅支援 **CommandPredictor** 子系統。 這個子系統可搭配使用 PSReadLine 模組，以提供自訂預測外掛程式。 未來，您可以將 **Job** 、 **CommandCompleter** 、 **Remoting** 和其他元件區分為 `System.Management.Automation.dll` 以外的子系統組件。

## 範例

### 範例 1-顯示所有可用的子系統

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### 範例 2-顯示特定種類的所有可用子系統

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## PARAMETERS

### -種類


指定要傳回的子系統種類。 有效的值為： `CommandPredictor` 。

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -SubsystemType

指定要傳回之子系統的型別。

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### SubsystemKind （系統管理）

### System.Type

## 輸出

### SubsystemInfo （系統管理）

## 注意

## 相關連結

[about_experimental_features](about/about_experimental_features.md)

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Enable-ExperimentalFeature](Get-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

[使用實驗性功能](/powershell/scripting/learn/experimental-features)
