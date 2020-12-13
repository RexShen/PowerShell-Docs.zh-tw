---
ms.date: 09/13/2016
ms.topic: reference
title: 如何要求確認
description: 如何要求確認
ms.openlocfilehash: 3e29803407bd9fbf13e6db0d0a02239c34e9c4fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666989"
---
# <a name="how-to-request-confirmations"></a>如何要求確認

這個範例會示範如何呼叫 [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法，在採取動作之前，要求使用者提出確認的方法，並在採取動作之前要求使用者確認。

> [!IMPORTANT]
> 如需 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱 [要求確認](./requesting-confirmation-from-cmdlets.md)。

## <a name="to-request-confirmation"></a>要求確認

1. 確定 `SupportsShouldProcess` Cmdlet 屬性的參數設定為 `true` 。 函數的 (這是 CmdletBinding 屬性的參數。 ) 

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 將 `Force` 參數新增至 Cmdlet，讓使用者可以覆寫確認要求。

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. 加入 `if` 使用[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之傳回值的語句，以判斷是否已呼叫 ShouldContinue 方法，以判斷是否已呼叫[](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法。

4. 新增第二個 `if` 語句，此語句會使用 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法的傳回值和參數的值， `Force` 以判斷是否應執行作業。

## <a name="example"></a>範例

在下列程式碼範例中， [ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 和 [ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 方法是從 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 方法的覆寫中呼叫的方法所呼叫的程式碼中的程式碼範例。 不過，您也可以從其他輸入處理方法呼叫這些方法。

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
