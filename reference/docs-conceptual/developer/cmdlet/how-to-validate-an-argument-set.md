---
title: 如何驗證引數集 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateSet attribute, example
ms.openlocfilehash: 6173f1380583f5b27e2b188990a5ea041f447c57
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781999"
---
# <a name="how-to-validate-an-argument-set"></a>如何驗證引數集

這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的驗證規則，然後再執行 Cmdlet。 此驗證規則會為參數引數提供一組有效的值。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。

## <a name="to-validate-an-argument-set"></a>驗證引數集

- 新增 ValidateSet 屬性，如下列程式碼所示。 這個範例會為參數指定三個可能值的集合 `UserName` 。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateSet 屬性](./validateset-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[Validatesetattribute。](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
