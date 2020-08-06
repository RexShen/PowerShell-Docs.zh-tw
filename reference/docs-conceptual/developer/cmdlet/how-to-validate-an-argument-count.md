---
title: 如何驗證引數計數 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateCount attribute, example
ms.openlocfilehash: e7c0eb364a6975cec089b984c2100d476631a12d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782118"
---
# <a name="how-to-validate-an-argument-count"></a>如何驗證引數計數

這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查引數數目的驗證規則， (在 Cmdlet 執行之前，參數所接受的計數) 。 您可以藉由宣告 ValidateCount 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。

## <a name="to-validate-an-argument-count"></a>驗證引數計數

- 加入 Validate 屬性，如下列程式碼所示。 這個範例會指定參數會接受一個引數，或最多三個引數。

    ```csharp
    [ValidateCount(1, 3)]
    [Parameter(Position = 0, Mandatory = true)]
    public string[] UserNames
    {
      get { return userNames; }
      set { userNames = value; }
    }

    private string[] userNames;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateCount 屬性](./validatecount-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
