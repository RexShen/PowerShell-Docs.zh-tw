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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365527"
---
# <a name="how-to-validate-an-argument-count"></a>如何驗證引數計數

這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間用來檢查參數在執行 Cmdlet 之前可接受的引數數目（計數）。 您可以藉由宣告 ValidateCount 屬性來設定此驗證規則。

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
