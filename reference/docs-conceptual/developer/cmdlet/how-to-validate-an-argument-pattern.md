---
title: 如何驗證引數模式 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidatePattern attribute, example
ms.openlocfilehash: 35104e786d4b809a711d97fea52ae0e348dd5ca3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782084"
---
# <a name="how-to-validate-an-argument-pattern"></a>如何驗證引數模式

這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間在執行 Cmdlet 之前，用來檢查參數引數的字元模式。 您可以藉由宣告 ValidatePattern 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。

## <a name="to-validate-an-argument-pattern"></a>驗證引數模式

- 加入 Validate 屬性，如下列程式碼所示。 這個範例會指定四位數的模式，其中每個數位的值為0到9。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidatePattern 屬性](./validatepattern-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
