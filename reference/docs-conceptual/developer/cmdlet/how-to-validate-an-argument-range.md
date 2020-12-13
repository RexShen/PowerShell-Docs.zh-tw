---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數範圍
description: 如何驗證引數範圍
ms.openlocfilehash: 1c1c53d43350a38beb2193200de3bd6b689366a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666921"
---
# <a name="how-to-validate-an-argument-range"></a>如何驗證引數範圍

這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前，用來檢查參數引數的最小值和最大值的驗證規則。 您可以藉由宣告 ValidateRange 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義這個屬性之類別的詳細資訊，請參閱 [Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。

### <a name="to-validate-an-argument-range"></a>驗證引數範圍

- 加入 ValidateRange 屬性，如下列程式碼所示。 此範例指定參數的範圍為0到 5 `InputData` 。

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateRange 屬性聲明](./validaterange-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
