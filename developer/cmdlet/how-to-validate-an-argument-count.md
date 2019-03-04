---
title: 如何驗證引數計數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateCount attribute, example
ms.assetid: 4e6b6ac4-1003-4e7e-9d4a-9f1cf74fc4af
caps.latest.revision: 8
ms.openlocfilehash: b6ddb8185f21a65b2e3142ebb640962047e11763
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859134"
---
# <a name="how-to-validate-an-argument-count"></a>如何驗證引數計數

此範例示範如何指定驗證規則，Windows PowerShell 執行階段可用來檢查參數可接受的引數 （計數） 的數目在執行此指令程式之前。 您可以設定這項驗證規則宣告 ValidateCount 屬性。

> [!NOTE]
> 如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。

## <a name="to-validate-an-argument-count"></a>若要驗證的引數計數

- 下列程式碼所示，請新增驗證屬性。 這個範例會指定此參數會接受一個引數或最多可達三個引數。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
