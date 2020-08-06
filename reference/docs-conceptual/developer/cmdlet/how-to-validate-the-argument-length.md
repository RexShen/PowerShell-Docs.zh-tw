---
title: 如何驗證引數長度 |Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- ValidateLength attribute, example
ms.openlocfilehash: aa0545def6d9628f6b41090a425f0c5af25f6ad7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784073"
---
# <a name="how-to-validate-the-argument-length"></a>如何驗證引數長度

這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查字元數的驗證規則， (在執行 Cmdlet 之前，參數引數的長度) 。 您可以藉由宣告 ValidateLength 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。

## <a name="to-validate-the-argument-length"></a>驗證引數長度

- 加入 Validate 屬性，如下列程式碼所示。 這個範例會指定引數長度的長度應為0到10個字元。

    ```csharp
    [ValidateLength(0, 10)]
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateLength 屬性](./validatelength-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
