---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數模式
description: 如何驗證引數模式
ms.openlocfilehash: ab5777c918a53c0a3900f87c52e7f14f9cb9b726
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666904"
---
# <a name="how-to-validate-an-argument-pattern"></a>如何驗證引數模式

這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前用來檢查參數引數字元模式的驗證規則。 您可以藉由宣告 ValidatePattern 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義這個屬性之類別的詳細資訊，請參閱 [Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。

## <a name="to-validate-an-argument-pattern"></a>驗證引數模式

- 加入 Validate 屬性，如下列程式碼所示。 此範例會指定四位數的模式，其中每個數位的值為0到9。

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱 [ValidatePattern 屬性聲明](./validatepattern-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
