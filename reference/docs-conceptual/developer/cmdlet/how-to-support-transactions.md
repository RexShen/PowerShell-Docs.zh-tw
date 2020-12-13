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
# <a name="how-to-support-transactions"></a>如何支援交易

這個範例會示範將交易支援新增至 Cmdlet 的基本程式碼專案。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理交易的詳細資訊，請參閱 [關於交易][about_Transactions]。

## <a name="to-support-transactions"></a>若要支援交易

1. 當您宣告 Cmdlet 屬性時，請指定此 Cmdlet 支援交易。
   當 Cmdlet 支援交易時，Windows PowerShell 會在 `UseTransaction` Cmdlet 執行時將參數新增至 Cmdlet。

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 在其中一個輸入處理方法內，加入 `if` 區塊以判斷是否有可用的交易。
   如果 `if` 語句解析為 `true` ，則可以在目前交易的內容中執行此語句內的動作。

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
