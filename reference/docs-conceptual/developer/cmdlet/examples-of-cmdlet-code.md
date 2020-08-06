---
title: Cmdlet 程式碼範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2d2597d3d3f64cae1c1494eb2f05873f6feae5e0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784328"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 程式碼範例

本節包含 Cmdlet 程式碼的範例，可讓您用來開始撰寫自己的 Cmdlet。

> [!IMPORTANT]
> 如果您想要撰寫 Cmdlet 的逐步指示，請參閱[撰寫 Cmdlet 的教學](./tutorials-for-writing-cmdlets.md)課程。

## <a name="in-this-section"></a>本節內容

[如何撰寫簡單的 Cmdlet](./how-to-write-a-simple-cmdlet.md)這個範例會顯示 Cmdlet 程式碼的基本結構。

[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)這個範例顯示如何宣告不同類型的參數。

[如何宣告參數集](./how-to-declare-parameter-sets.md)這個範例示範如何宣告可變更 Cmdlet 所執行之動作的參數集合。

[如何驗證參數輸入](./how-to-validate-parameter-input.md)這些範例示範如何驗證參數輸入。

[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)這個範例示範如何宣告在執行時間新增的參數。

[如何在 Cmdlet 內叫用腳本](./how-to-invoke-scripts-within-a-cmdlet.md)這個範例示範如何叫用提供給 Cmdlet 的腳本。

[如何覆寫輸入處理方法](./how-to-override-input-processing-methods.md)這些範例顯示用來覆寫 BeginProcessing、ProcessRecord 和 EndProcessing 方法的基本結構。

[如何支援 ShouldProcess 呼叫](./how-to-request-confirmations.md)這個範例會示範如何從 Cmdlet 內呼叫 ShouldProcess 和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的操作方式（可能為[系統管理](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)）。

[如何支援交易](./how-to-support-transactions.md)這個範例示範如何指示 Cmdlet 支援交易，以及如何執行在交易中使用 Cmdlet 時所採取的動作。

[如何支援作業](./how-to-support-jobs.md)這個範例示範如何在您撰寫 Cmdlet 時支援作業。

[如何從 Cmdlet 內叫用 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)這個範例示範如何從另一個 Cmdlet 叫用 Cmdlet，這可讓您將叫用 Cmdlet 的功能新增至您正在開發的 Cmdlet 中。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
