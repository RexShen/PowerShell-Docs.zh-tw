---
title: 如何支援交易 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6fda27394091195b589afef5ee53c6d3bec4efc0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786606"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="22bdd-102">如何支援交易</span><span class="sxs-lookup"><span data-stu-id="22bdd-102">How to Support Transactions</span></span>

<span data-ttu-id="22bdd-103">這個範例會顯示將交易支援新增至 Cmdlet 的基本程式碼專案。</span><span class="sxs-lookup"><span data-stu-id="22bdd-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="22bdd-104">如需 Windows PowerShell 如何處理交易的詳細資訊，請參閱[關於交易][about_Transactions]。</span><span class="sxs-lookup"><span data-stu-id="22bdd-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="22bdd-105">支援交易</span><span class="sxs-lookup"><span data-stu-id="22bdd-105">To support transactions</span></span>

1. <span data-ttu-id="22bdd-106">當您宣告 Cmdlet 屬性時，請指定此 Cmdlet 支援交易。</span><span class="sxs-lookup"><span data-stu-id="22bdd-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="22bdd-107">當 Cmdlet 支援交易時，Windows PowerShell 會在 `UseTransaction` 執行時將參數新增至 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="22bdd-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="22bdd-108">在其中一個輸入處理方法中，加入 `if` 區塊來判斷交易是否可用。</span><span class="sxs-lookup"><span data-stu-id="22bdd-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="22bdd-109">如果 `if` 語句解析成 `true` ，就可以在目前交易的內容中執行此語句中的動作。</span><span class="sxs-lookup"><span data-stu-id="22bdd-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="22bdd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22bdd-110">See Also</span></span>

[<span data-ttu-id="22bdd-111">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="22bdd-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
