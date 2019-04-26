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
# <a name="how-to-support-transactions"></a>如何支援交易

這個範例會示範交易的支援新增至 cmdlet 的基本程式碼項目。

> [!IMPORTANT]
> 如需有關 Windows PowerShell 如何處理交易的詳細資訊，請參閱 <<c0> [ 解交易][about_Transactions]。

## <a name="to-support-transactions"></a>若要支援交易

1. 當您宣告 Cmdlet 屬性時，指定此 cmdlet 支援交易。
   當 cmdlet 支援交易時，Windows PowerShell 會將新增`UseTransaction`參數到此 cmdlet 會在執行時。

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. 其中一個內的輸入處理方法，新增`if`區塊來判斷交易是否可用。
   如果`if`陳述式會解析成`true`，可以在目前交易內容中執行此陳述式內的動作。

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
