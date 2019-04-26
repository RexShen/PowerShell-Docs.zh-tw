---
title: Cmdlet 程式碼範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6fed2f68-ce6d-4a8f-bf21-f94f27a155c2
caps.latest.revision: 9
ms.openlocfilehash: 936728d64f30a08fb9e2fa9ccef103683594aa3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068193"
---
# <a name="examples-of-cmdlet-code"></a>Cmdlet 程式碼範例

本節包含 cmdlet 程式碼可供您開始撰寫自己的 cmdlet 的範例。

> [!IMPORTANT]
> 如果您想撰寫 cmdlet 的逐步指示，請參閱[撰寫的 cmdlet 的教學課程](./tutorials-for-writing-cmdlets.md)。

## <a name="in-this-section"></a>在本節中

[如何撰寫一個簡單的 Cmdlet](./how-to-write-a-simple-cmdlet.md)此範例會顯示 cmdlet 的程式碼的基本結構。

[如何宣告 Cmdlet 參數](./how-to-declare-cmdlet-parameters.md)本範例示範如何宣告不同類型的參數。

[如何宣告參數集](./how-to-declare-parameter-sets.md)本範例示範如何宣告的參數，可以變更在 cmdlet 執行的動作集。

[如何驗證參數輸入](./how-to-validate-parameter-input.md)這些範例示範如何驗證參數的輸入。

[如何宣告動態參數](./how-to-declare-dynamic-parameters.md)這個範例示範如何宣告的參數，在執行階段加入。

[如何叫用指令碼內 Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)本範例示範如何叫用的指令碼，提供給 cmdlet。

[如何覆寫輸入處理方法](./how-to-override-input-processing-methods.md)這些範例示範用來覆寫 BeginProcessing、 ProcessRecord 和 EndProcessing 方法的基本結構。

[如何支援 ShouldProcess 呼叫](./how-to-request-confirmations.md)這個範例示範如何[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法應從呼叫中的 cmdlet。

[如何支援交易](./how-to-support-transactions.md)這個範例示範如何指出此 cmdlet 支援交易，以及如何實作指令程式用在交易內時所要採取的動作。

[如何支援工作](./how-to-support-jobs.md)這個範例示範如何撰寫 cmdlet 時支援作業。

[如何叫用 Cmdlet 從內 Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)本範例示範如何叫用另一個 cmdlet，可讓您叫用的指令程式的功能新增至您正在開發的 cmdlet 中的 cmdlet。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
