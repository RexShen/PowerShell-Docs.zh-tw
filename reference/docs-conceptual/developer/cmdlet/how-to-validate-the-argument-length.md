---
title: 如何驗證引數長度 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateLength attribute, example
ms.assetid: d5ddaa6e-4904-46da-beb0-0295a8f38332
caps.latest.revision: 12
ms.openlocfilehash: 8a21675acd087df93f93c25952c78931255d60b3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365487"
---
# <a name="how-to-validate-the-argument-length"></a>如何驗證引數長度

這個範例示範如何指定驗證規則，讓 Windows PowerShell 執行時間可以在執行 Cmdlet 之前，用來檢查參數引數的字元數（長度）。 您可以藉由宣告 ValidateLength 屬性來設定此驗證規則。

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
