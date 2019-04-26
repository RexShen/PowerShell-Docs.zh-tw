---
title: 如何支援交易 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067853"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="5f804-102">如何支援交易</span><span class="sxs-lookup"><span data-stu-id="5f804-102">How to Support Transactions</span></span>

<span data-ttu-id="5f804-103">這個範例會示範交易的支援新增至 cmdlet 的基本程式碼項目。</span><span class="sxs-lookup"><span data-stu-id="5f804-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f804-104">如需有關 Windows PowerShell 如何處理交易的詳細資訊，請參閱 <<c0> [ 解交易][about_Transactions]。</span><span class="sxs-lookup"><span data-stu-id="5f804-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="5f804-105">若要支援交易</span><span class="sxs-lookup"><span data-stu-id="5f804-105">To support transactions</span></span>

1. <span data-ttu-id="5f804-106">當您宣告 Cmdlet 屬性時，指定此 cmdlet 支援交易。</span><span class="sxs-lookup"><span data-stu-id="5f804-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="5f804-107">當 cmdlet 支援交易時，Windows PowerShell 會將新增`UseTransaction`參數到此 cmdlet 會在執行時。</span><span class="sxs-lookup"><span data-stu-id="5f804-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="5f804-108">其中一個內的輸入處理方法，新增`if`區塊來判斷交易是否可用。</span><span class="sxs-lookup"><span data-stu-id="5f804-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="5f804-109">如果`if`陳述式會解析成`true`，可以在目前交易內容中執行此陳述式內的動作。</span><span class="sxs-lookup"><span data-stu-id="5f804-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="5f804-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f804-110">See Also</span></span>

[<span data-ttu-id="5f804-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5f804-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
