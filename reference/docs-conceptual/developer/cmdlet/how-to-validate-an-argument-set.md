---
title: 如何驗證引數集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateSet attribute, example
ms.assetid: 55f0f664-d2ad-4501-a3dc-9f7a27c8ab11
caps.latest.revision: 8
ms.openlocfilehash: 6d8b189ed6311efd5a7348ab1e58934e9bff12a3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365507"
---
# <a name="how-to-validate-an-argument-set"></a>如何驗證引數集

這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的驗證規則，然後再執行 Cmdlet。 此驗證規則會為參數引數提供一組有效的值。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。

## <a name="to-validate-an-argument-set"></a>驗證引數集

- 新增 ValidateSet 屬性，如下列程式碼所示。 這個範例會為 `UserName` 參數指定三個可能值的集合。

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
