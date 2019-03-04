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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861364"
---
# <a name="how-to-validate-an-argument-set"></a>如何驗證引數集

此範例示範如何指定 Windows PowerShell 執行階段可用來執行此指令程式之前，請檢查參數引數的驗證規則。 這項驗證規則參數引數提供一組有效的值。

> [!NOTE]
> 如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)。

## <a name="to-validate-an-argument-set"></a>若要驗證的引數設定

- 下列程式碼所示，請新增 ValidateSet 屬性。 這個範例會指定三個可能值的一組`UserName`參數。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Validatesetattribute](/dotnet/api/System.Management.Automation.ValidateSetAttribute)

[ValidateSet 屬性宣告](./validateset-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
