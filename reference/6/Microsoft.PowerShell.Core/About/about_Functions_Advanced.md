---
description: 介紹可使用腳本建立 Cmdlet 的 advanced 函數。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced
ms.openlocfilehash: f7e100122169b3ecb25be4d32fc72a67fea7b7cf
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207091"
---
# <a name="about-functions-advanced"></a>關於函式 Advanced

## <a name="short-description"></a>簡短描述
介紹可使用腳本建立 Cmdlet 的 advanced 函數。

## <a name="long-description"></a>詳細描述

Cmdlet 是參與 PowerShell 管線語義的單一命令。 這包括二元 Cmdlet、advanced script 函數、CDXML 和工作流程。

Advanced 函數可讓您建立以 PowerShell 函數撰寫的 Cmdlet。 Advanced 函數可讓您更輕鬆地建立 Cmdlet，而不需要撰寫和編譯二進位 Cmdlet。 二元 Cmdlet 是以 .NET 語言（如 c #）撰寫的 .NET 類別。

Advanced 函數會使用 `CmdletBinding` 屬性，將其識別為函式，如同 Cmdlet。 `CmdletBinding`屬性類似于編譯的 Cmdlet 類別中用來將類別識別為 Cmdlet 的 Cmdlet 屬性。 如需此屬性的詳細資訊，請參閱 [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)。

下列範例顯示接受名稱的函式，然後使用所提供的名稱來列印問候語。 另請注意，此函式會定義包含動詞的名稱 (傳送) 和名詞 (問候) 組，例如已編譯 Cmdlet 的動詞-名詞配對。 不過，函式不需要具有動詞-名詞名稱。

```powershell
function Send-Greeting
{
    [CmdletBinding()]
    Param(
        [Parameter(Mandatory=$true)]
        [string] $Name
    )

    Process
    {
        Write-Host ("Hello " + $Name + "!")
    }
}
```

函數的參數是使用參數屬性來宣告。
這個屬性可以單獨使用，也可以與 Alias 屬性或其他數個參數驗證屬性結合使用。 如需如何宣告參數的詳細資訊 (包括在執行時間) 加入的動態參數，請參閱 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)。

先前函式的實際工作是在進程區塊中執行，這相當於編譯的 Cmdlet 用來處理傳遞給 Cmdlet 之資料的 ProcessingRecord 方法。 此區塊以及開始和結束區塊將在 [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md) 主題中說明。

Advanced 函式與編譯的 Cmdlet 有下列不同之處：

- 當字串陣列系結至布林值參數時，Advanced 函數參數系結不會擲回例外狀況。
- ValidateSet 屬性和 ValidatePattern 屬性無法傳遞具名引數。
- Advanced 函數不能用在交易中。

## <a name="see-also"></a>另請參閱

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)
