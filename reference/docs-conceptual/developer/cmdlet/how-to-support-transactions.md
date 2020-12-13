---
ms.date: 09/13/2016
ms.topic: reference
title: 如何支援交易
description: 如何支援交易
ms.openlocfilehash: 5691c246830dab9f4808801c04353ebfb2c3e981
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666955"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="7d6b2-103">如何支援交易</span><span class="sxs-lookup"><span data-stu-id="7d6b2-103">How to Support Transactions</span></span>

<span data-ttu-id="7d6b2-104">這個範例會示範將交易支援新增至 Cmdlet 的基本程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-104">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d6b2-105">如需 Windows PowerShell 如何處理交易的詳細資訊，請參閱 [關於交易][about_Transactions]。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-105">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="7d6b2-106">若要支援交易</span><span class="sxs-lookup"><span data-stu-id="7d6b2-106">To support transactions</span></span>

1. <span data-ttu-id="7d6b2-107">當您宣告 Cmdlet 屬性時，請指定此 Cmdlet 支援交易。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-107">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="7d6b2-108">當 Cmdlet 支援交易時，Windows PowerShell 會在 `UseTransaction` Cmdlet 執行時將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-108">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="7d6b2-109">在其中一個輸入處理方法內，加入 `if` 區塊以判斷是否有可用的交易。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-109">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="7d6b2-110">如果 `if` 語句解析為 `true` ，則可以在目前交易的內容中執行此語句內的動作。</span><span class="sxs-lookup"><span data-stu-id="7d6b2-110">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="7d6b2-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d6b2-111">See Also</span></span>

[<span data-ttu-id="7d6b2-112">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d6b2-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
