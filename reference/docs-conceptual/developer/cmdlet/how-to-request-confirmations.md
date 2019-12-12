---
title: 如何要求確認 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369677"
---
# <a name="how-to-request-confirmations"></a>如何要求確認

這個範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以在採取動作之前向使用者要求確認的情況下，進行這種方式。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

## <a name="to-request-confirmation"></a>若要要求確認

1. 請確定 Cmdlet 屬性的 `SupportsShouldProcess` 參數已設為 `true`。 （針對函式，這是 CmdletBinding 屬性的參數。）

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 將 `Force` 參數新增至您的 Cmdlet，讓使用者可以覆寫確認要求。

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. 加入 `if` 語句，其會使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的傳回值，以判斷是否呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以判斷是否已呼叫。

4. 加入第二個 `if` 語句，它會使用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的傳回值和 `Force` 參數的值，來判斷是否應該執行運算。

## <a name="example"></a>範例

在下列程式碼範例中，系統會從的覆寫 中呼叫 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，以進行呼叫。[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法的.。 不過，您也可以從其他輸入處理方法呼叫這些方法。

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
