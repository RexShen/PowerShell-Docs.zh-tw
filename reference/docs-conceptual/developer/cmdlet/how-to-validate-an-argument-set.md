---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數集
description: 如何驗證引數集
ms.openlocfilehash: 50ec0a48277893584d896e14ad6aa843682a28cc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650377"
---
# <a name="how-to-validate-an-argument-set"></a>如何驗證引數集

這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前用來檢查參數引數的驗證規則。 這項驗證規則會為參數引數提供一組有效值。

> [!NOTE]
> 如需定義這個屬性之類別的詳細資訊，請參閱 [Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。

## <a name="to-validate-an-argument-set"></a>驗證引數集

- 加入 ValidateSet 屬性，如下列程式碼所示。 此範例會為參數指定三個可能值的集合 `UserName` 。

    ```csharp
    [ValidateSet("Steve", "Mary", "Carl", IgnoreCase = true)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }

    private string userName;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateSet 屬性聲明](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[Validatesetattribute。](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
