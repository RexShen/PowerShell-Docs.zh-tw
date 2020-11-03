---
description: 說明如何在 PowerShell 中使用命令參數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: fe241331d3faca97010221fd228b04d80765819b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208103"
---
# <a name="about-parameters"></a>關於參數

## <a name="short-description"></a>簡短描述
說明如何在 PowerShell 中使用命令參數。

## <a name="long-description"></a>完整描述

大部分的 PowerShell 命令（例如 Cmdlet、函式和腳本）都會依賴參數，讓使用者選取選項或提供輸入。 參數會遵循命令名稱，且具有下列格式：

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

參數的名稱前面會加上連字號 (-) ，它會向 PowerShell 表示連字號後面的單字是參數名稱。 參數名稱和值可以用空格或冒號字元分隔。 某些參數不需要或接受參數值。 其他參數則需要值，但不需要在命令中使用參數名稱。

參數的類型和這些參數的需求會有所不同。 若要尋找命令參數的相關資訊，請使用 `Get-Help` Cmdlet。 例如，若要尋找有關 Cmdlet 參數的資訊 `Get-ChildItem` ，請輸入：

```powershell
Get-Help Get-ChildItem
```

若要尋找腳本參數的相關資訊，請使用指令檔的完整路徑。 例如：

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

Cmdlet 會傳回 `Get-Help` 與命令相關的各種詳細資料，包括描述、命令語法、參數的相關資訊，以及示範如何在命令中使用參數的範例。

您也可以使用 Cmdlet 的參數參數 `Get-Help` 來尋找特定參數的相關資訊。 或者，您可以使用 **參數** 參數搭配萬用字元 ( `*` ) 值來尋找命令之所有參數的相關資訊。 例如，下列命令會取得 Cmdlet 之所有參數的相關資訊 `Get-Member` ：

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a>預設參數值

選擇性參數有預設值，也就是當命令中未指定參數時，所使用或假設的值。

例如，許多 Cmdlet 的 **ComputerName** 參數預設值是本機電腦的名稱。 如此一來，除非指定 **ComputerName** 參數，否則命令會使用本機電腦名稱稱。

若要尋找預設參數值，請參閱 Cmdlet 的說明主題。 參數描述應該包含預設值。

您也可以為 Cmdlet 或 advanced 函數的任何參數設定自訂的預設值。 如需設定自訂預設值的詳細資訊，請參閱 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)。

### <a name="parameter-attribute-table"></a>參數屬性工作表

當您使用指令程式的 **完整** 、 **參數** 或 **線上** 參數時 `Get-Help` ，會 `Get-Help` 顯示參數屬性工作表，其中包含參數的詳細資訊。

此資訊包含使用參數所需知道的詳細資料。
例如，Cmdlet 的說明主題 `Get-ChildItem` 包含其 Path 參數的下列詳細資料：

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

參數資訊包括參數語法、參數的描述，以及參數屬性。 下列各節說明參數屬性。

#### <a name="parameter-required"></a>需要參數

這項設定會指出參數是否為強制性，也就是使用此 Cmdlet 的所有命令都必須包含此參數。 當此值為 **True** ，且命令缺少參數時，PowerShell 會提示您輸入參數的值。

#### <a name="parameter-position"></a>參數位置

如果設定為 `Position` 正整數，則不需要參數名稱。 這種類型的參數稱為位置參數，而數位則表示參數必須與其他位置參數相對應的出現位置。 具名引數可以列在 Cmdlet 名稱後面的任何位置。 如果您包含位置參數的參數名稱，參數可以列在 Cmdlet 名稱後面的任何位置。

例如， `Get-ChildItem` Cmdlet 具有 Path 和 Exclude 參數。 `Position`**路徑** 的設定為 **0** ，表示它是位置參數。 [ `Position` **排除** ] 的設定 **名** 為。

這表示 **路徑** 不需要參數名稱，但其參數值必須是命令中的第一個或唯一未命名的參數值。
不過，因為 Exclude 參數是一個具名引數，所以您可以將它放在命令中的任何位置。

由於 `Position` 這兩個參數的設定，您可以使用下列任何一個命令：

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

如果您要包含不包含參數名稱的另一個位置參數，該參數必須依照設定所指定的順序來放置 `Position` 。

#### <a name="parameter-type"></a>參數類型

這項設定會指定 Microsoft .NET Framework 類型的參數值。 例如，如果類型是 **Int32** ，則參數值必須是整數。 如果類型是字串，參數值必須是字元字串。 如果字串包含空格，則值必須以引號括住，或空格前面必須加上 escape 字元 ( ' ) 。

#### <a name="default-value"></a>預設值

如果未提供其他值，此設定會指定參數將假設的值。 例如，Path 參數的預設值通常是目前的目錄。 必要參數永遠沒有預設值。
針對許多選擇性參數，沒有預設值，因為參數未使用時，不會有任何作用。

#### <a name="accepts-multiple-values"></a>接受多個值

這項設定會指出參數是否接受多個參數值。
當參數接受多個值時，您可以在命令中輸入以逗號分隔的清單做為參數的值，或將逗號分隔清單儲存 (變數中的陣列) ，然後將變數指定為參數值。

例如，Cmdlet 的 ServiceName 參數 `Get-Service` 接受多個值。 下列命令都有效：

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a>接受管線輸入

此設定會指出您是否可以使用管線運算子 ( `|` ) 將值傳送至參數。

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

當參數為 "True (by Value) " 時，PowerShell 會嘗試將任何輸送的值與該參數產生關聯，然後再嘗試其他方法來解讀命令。

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

例如，只有當值具有名為 **name** 的屬性時，您才可以使用管線將值傳送至 **name** 參數。

> [!NOTE]
> 接受管線輸入 (`by Value`) 或 (`by PropertyName`) 可在參數上使用 **延遲** 系結腳本區塊的型別參數。
>
> **延遲** 系結腳本區塊會在 **ParameterBinding** 期間自動執行。 結果會系結至參數。 延遲系結 **不適用於** 定義為類型 `ScriptBlock` 或的參數 `System.Object` ，而是在未叫用的 **情況** 下傳遞腳本區塊。
>
> 您可以在這裡閱讀 **延遲** 系結腳本區塊 [about_Script_Blocks md](about_Script_Blocks.md)

#### <a name="accepts-wildcard-characters"></a>接受萬用字元

這項設定會指出參數的值是否可以包含萬用字元，以便讓參數值符合目標容器中的一個以上現有專案。

#### <a name="common-parameters"></a>一般參數

一般參數是您可以搭配任何 Cmdlet 使用的參數。 如需一般參數的詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。

## <a name="see-also"></a>另請參閱

[about_Command_syntax](about_Command_syntax.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Parameters_Default_Values](about_Parameters_Default_Values.md)

[about_Pipelines](about_Pipelines.md)

[about_Wildcards](about_Wildcards.md)
