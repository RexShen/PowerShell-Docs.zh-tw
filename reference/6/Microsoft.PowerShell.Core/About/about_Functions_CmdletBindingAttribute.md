---
description: 描述可讓函式運作的屬性，例如已編譯的 Cmdlet。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_CmdletBindingAttribute
ms.openlocfilehash: c4090910a72e2f68b5a710c76b20cc8af532c04b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207083"
---
# <a name="about-functions-cmdletbindingattribute"></a>關於函式 CmdletBindingAttribute

## <a name="short-description"></a>簡短描述
描述可讓函式運作的屬性，例如已編譯的 Cmdlet。

## <a name="long-description"></a>完整描述

`CmdletBinding`屬性是函式的屬性，可讓它們的運作方式就像以 c # 撰寫的編譯 Cmdlet。 它可讓您存取 Cmdlet 的功能。

PowerShell 會系結具有屬性之函式的參數，其方式與系結 `CmdletBinding` 已編譯 Cmdlet 的參數相同。 具有屬性的函式 `$PSCmdlet` 可使用自動變數 `CmdletBinding` ，但 `$Args` 變數無法使用。

在具有屬性的函式中 `CmdletBinding` ，未知的參數和沒有相符位置參數的位置引數會導致參數系結失敗。

> [!NOTE]
> 已編譯的 Cmdlet 會使用必要的 `Cmdlet` 屬性，其類似于 `CmdletBinding` 本主題中所述的屬性。

## <a name="syntax"></a>Syntax

下列範例顯示指定屬性之所有選擇性引數的函數格式 `CmdletBinding` 。 以下是每個引數的簡短描述。

```powershell
{
    [CmdletBinding(ConfirmImpact=<String>,
    DefaultParameterSetName=<String>,
    HelpURI=<URI>,
    SupportsPaging=<Boolean>,
    SupportsShouldProcess=<Boolean>,
    PositionalBinding=<Boolean>)]

    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

## <a name="confirmimpact"></a>ConfirmImpact

**ConfirmImpact** 引數會指定何時應透過呼叫 **ShouldProcess** 方法來確認函式的動作。 只有當 **ConfirmImpact** 引數等於或大於喜好設定變數的值時， **ShouldProcess** 方法的呼叫才會顯示確認提示 `$ConfirmPreference` 。  (引數的預設值為 [ **中** ]。只有在同時指定 **SupportsShouldProcess** 引數時，才 ) 指定此引數。

如需確認要求的詳細資訊，請參閱 [要求確認](/powershell/scripting/developer/cmdlet/requesting-confirmation)。

## <a name="defaultparametersetname"></a>DefaultParameterSetName

**DefaultParameterSetName** 引數會指定當 PowerShell 無法判斷要使用哪個參數集時，所要嘗試使用的參數集名稱。 您可以讓每個參數的 unique 參數設定必要參數，以避免這個問題。

## <a name="helpuri"></a>HelpURI

**HelpURI** 引數會指定描述函式之說明主題的線上版本的網際網路位址。 **HelpURI** 引數的值必須以 "HTTP" 或 "HTTPs" 開頭。

**HelpURI** 引數值會用於針對函式所傳回之 **CommandInfo** 物件的 **HelpURI** 屬性值 `Get-Command` 。

不過，當說明檔安裝在電腦上，且說明檔的 **RelatedLinks** 區段中的第一個連結值為 uri，或批註式說明中第一個指示詞的值為 `.Link` uri 時，說明檔中的 uri 會用來做為函式之 **HelpUri** 屬性的值。

`Get-Help`當命令中指定的 **online** 參數時，此 Cmdlet 會使用 **HelpURI** 屬性的值來尋找線上版本的函數說明主題 `Get-Help` 。

## <a name="supportspaging"></a>SupportsPaging

**SupportsPaging** 引數會將 **First** 、 **Skip** 和 **IncludeTotalCount** 參數新增至函式。 這些參數可讓使用者從非常大的結果集選取輸出。 此引數是針對從支援資料選取的大型資料存放區（例如 SQL 資料庫）傳回資料的 Cmdlet 和函式所設計。

此引數是在 Windows PowerShell 3.0 中引進。

- **First** ：只取得第一個 ' n ' 物件。
- **Skip** ：忽略第一個 ' n ' 物件，然後取得剩餘的物件。
- **IncludeTotalCount** ：報告資料集中的物件數目 (整數) 後面接著物件。 如果 Cmdlet 無法判斷總計數，則會傳回「未知的總計數」。

PowerShell 包含 **NewTotalCount** ，這是一個 helper 方法，可取得要傳回的總計數值，並包含總計計數值的精確度估計值。

下列範例函式示範如何將分頁參數的支援新增至 advanced 函數。

```powershell
function Get-Numbers {
    [CmdletBinding(SupportsPaging = $true)]
    param()

    $FirstNumber = [Math]::Min($PSCmdlet.PagingParameters.Skip, 100)
    $LastNumber = [Math]::Min($PSCmdlet.PagingParameters.First +
      $FirstNumber - 1, 100)

    if ($PSCmdlet.PagingParameters.IncludeTotalCount) {
        $TotalCountAccuracy = 1.0
        $TotalCount = $PSCmdlet.PagingParameters.NewTotalCount(100,
          $TotalCountAccuracy)
        Write-Output $TotalCount
    }
    $FirstNumber .. $LastNumber | Write-Output
}
```

## <a name="supportsshouldprocess"></a>SupportsShouldProcess

**SupportsShouldProcess** 引數會將 **Confirm** 和 **WhatIf** 參數新增至函式。 **Confirm** 參數會先提示使用者，然後才在管線中的每個物件上執行命令。 **WhatIf** 參數會列出命令所做的變更，而不是執行命令。

## <a name="positionalbinding"></a>PositionalBinding

**PositionalBinding** 引數會決定函式中的參數是否預設為位置。 預設值是 `$True`。 您可以使用 **PositionalBinding** 引數搭配的值 `$False` 來停用位置系結。

**PositionalBinding** 引數是在 Windows PowerShell 3.0 中引進。

當參數是位置時，參數名稱為選擇性。
PowerShell 會根據函數命令中未命名之參數值的順序或位置，將未命名的參數值與函式參數產生關聯。

當參數不是位置時 (它們是「命名」 ) ，參數名稱 (或名稱的縮寫或別名) 在命令中都是必要的。

當 **PositionalBinding** 為時 `$True` ，函數參數預設為位置。 PowerShell 會依照在函式中宣告的順序，將位置編號指派給參數。

當 **PositionalBinding** 為時，函式 `$False` 參數預設不是位置。 除非在參數上宣告 **parameter** 屬性的 **Position** 引數，否則在函式中使用參數時，必須包含參數名稱 (或別名或縮寫) 。

**Parameter** 屬性的 **Position** 引數優先于 **PositionalBinding** 預設值。 您可以使用 **Position** 引數來指定參數的位置值。 如需 **Position** 引數的詳細資訊，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

## <a name="notes"></a>備忘稿

Advanced 函數中不支援 **SupportsTransactions** 引數。

## <a name="keywords"></a>關鍵字

about_Functions_CmdletBinding_Attribute

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
