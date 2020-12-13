---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 程式碼範例
description: Cmdlet 程式碼範例
ms.openlocfilehash: 91dd2019300504697ad9a7a0c155a04600d09c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652926"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 程式碼範例

本章節包含 Cmdlet 程式碼的範例，您可以用來開始撰寫自己的 Cmdlet。

> [!IMPORTANT]
> 如果您想要撰寫 Cmdlet 的逐步指示，請參閱 [撰寫 Cmdlet 的教學](./tutorials-for-writing-cmdlets.md)課程。

## <a name="in-this-section"></a>本節內容

[如何撰寫簡單的 Cmdlet](./how-to-write-a-simple-cmdlet.md) 此範例顯示 Cmdlet 程式碼的基本結構。

[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md) 此範例顯示如何宣告不同類型的參數。

[如何宣告參數集](./how-to-declare-parameter-sets.md) 此範例示範如何宣告可變更 Cmdlet 所執行之動作的參數集。

[如何驗證參數輸入](./how-to-validate-parameter-input.md) 這些範例會示範如何驗證參數輸入。

[如何宣告動態參數](./how-to-declare-dynamic-parameters.md) 這個範例示範如何宣告在執行時間加入的參數。

[如何在 Cmdlet 中叫用腳本](./how-to-invoke-scripts-within-a-cmdlet.md) 此範例說明如何叫用提供給 Cmdlet 的腳本。

[如何覆寫輸入處理方法](./how-to-override-input-processing-methods.md) 這些範例顯示用來覆寫 BeginProcessing、ProcessRecord 和 EndProcessing 方法的基本結構。

[如何支援 ShouldProcess 呼叫](./how-to-request-confirmations.md)這個範例會示範如何從 Cmdlet 內呼叫 ShouldProcess 和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的方法。（可能為[system.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)管理方法）。

[如何支援交易](./how-to-support-transactions.md) 此範例示範如何指示 Cmdlet 支援交易，以及如何執行在交易中使用 Cmdlet 時所採取的動作。

[如何支援作業](./how-to-support-jobs.md) 此範例示範如何在撰寫 Cmdlet 時支援工作。

[如何從 Cmdlet 內叫用 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md) 此範例示範如何從另一個 Cmdlet 中叫用 Cmdlet，此 Cmdlet 可讓您將叫用 Cmdlet 的功能新增到您正在開發的 Cmdlet。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
