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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365537"
---
# <a name="how-to-support-transactions"></a>如何支援交易

這個範例會顯示將交易支援新增至 Cmdlet 的基本程式碼專案。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理交易的詳細資訊，請參閱[關於交易][about_Transactions]。

## <a name="to-support-transactions"></a>支援交易

1. 當您宣告 Cmdlet 屬性時，請指定此 Cmdlet 支援交易。
   當 Cmdlet 支援交易時，Windows PowerShell 會在執行時，將 `UseTransaction` 參數新增至 Cmdlet。

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 在其中一個輸入處理方法中，加入 @no__t 0 區塊，以判斷是否有可用的交易。
   如果 @no__t 0 的語句解析成 `true`，就可以在目前交易的內容中執行此語句中的動作。

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
