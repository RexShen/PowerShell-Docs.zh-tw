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
# <a name="how-to-support-transactions"></a>如何支援交易

這個範例會顯示將交易支援新增至 Cmdlet 的基本程式碼專案。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理交易的詳細資訊，請參閱[關於交易][about_Transactions]。

## <a name="to-support-transactions"></a>支援交易

1. 當您宣告 Cmdlet 屬性時，請指定此 Cmdlet 支援交易。
   當 Cmdlet 支援交易時，Windows PowerShell 會在 `UseTransaction` 執行時將參數新增至 Cmdlet。

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 在其中一個輸入處理方法中，加入 `if` 區塊來判斷交易是否可用。
   如果 `if` 語句解析成 `true` ，就可以在目前交易的內容中執行此語句中的動作。

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
