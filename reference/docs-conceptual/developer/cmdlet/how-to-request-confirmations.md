---
title: 如何要求確認 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebe928724f1b750afc11c1e3c1207375f4ec8e42
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784090"
---
# <a name="how-to-request-confirmations"></a>如何要求確認

這個範例會示範如何呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以在採取動作之前向使用者要求確認的情況下，進行這種方式。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

## <a name="to-request-confirmation"></a>若要要求確認

1. 請確定 `SupportsShouldProcess` Cmdlet 屬性的參數設定為 `true` 。 函式的 (這是 CmdletBinding 屬性的參數。 ) 

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

3. 加入 `if` 使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之傳回值的語句，以判斷是否已呼叫[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，以判斷是否已呼叫該方法。

4. 加入第二個 `if` 語句，以使用[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的傳回值和參數的值， `Force` 來判斷是否應該執行作業。

## <a name="example"></a>範例

在下列程式碼範例中，會從[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法的覆寫中呼叫. [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法中的.........。 不過，您也可以從其他輸入處理方法呼叫這些方法。

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
