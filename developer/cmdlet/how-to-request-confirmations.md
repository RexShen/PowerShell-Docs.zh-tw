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
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863404"
---
# <a name="how-to-request-confirmations"></a>如何要求確認

此範例示範如何呼叫[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)要求確認的方法之前採取動作的使用者。

> [!IMPORTANT]
> 如需有關 Windows PowerShell 如何處理這些要求的詳細資訊，請參閱 <<c0> [ 要求確認](./requesting-confirmation-from-cmdlets.md)。

## <a name="to-request-confirmation"></a>要求確認

1. 請確認`SupportsShouldProcess`參數的 Cmdlet 屬性設定為`true`。 （函式就 CmdletBinding 屬性的參數。）

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. 新增`Force`到您的 cmdlet 參數，讓使用者可以覆寫確認要求。

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. 新增`if`使用的傳回值的陳述式[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，可判斷[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法呼叫。

4. 新增第二`if`使用的傳回值的陳述式[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)方法，而`Force`參數，來判斷作業是否應該是執行。

## <a name="example"></a>範例

在下列程式碼範例中， [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)並[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)內呼叫方法覆寫[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法。 不過，您也可以從其他輸入處理方法呼叫這些方法。

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
