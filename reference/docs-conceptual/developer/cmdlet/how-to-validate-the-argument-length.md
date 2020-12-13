---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數長度
description: 如何驗證引數長度
ms.openlocfilehash: 460aedbe6847033f976cb7bf70b6c77ac5a3a3c9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652638"
---
# <a name="how-to-validate-the-argument-length"></a>如何驗證引數長度

這個範例示範如何指定 Windows PowerShell 執行時間可在執行 Cmdlet 之前，用來檢查參數引數) 長度 (字元數的驗證規則。 您可以藉由宣告 ValidateLength 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義這個屬性之類別的詳細資訊，請參閱 [Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。

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

如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateLength 屬性聲明](./validatelength-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
