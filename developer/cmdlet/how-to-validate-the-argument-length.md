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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067703"
---
# <a name="how-to-validate-the-argument-length"></a>如何驗證引數長度

此範例示範如何指定驗證規則，Windows PowerShell 執行階段可用來執行此指令程式之前檢查的字元 （長度） 的參數引數數目。 您可以設定這項驗證規則宣告 ValidateLength 屬性。

> [!NOTE]
> 如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatelengthattribute](/dotnet/api/System.Management.Automation.ValidateLengthAttribute)。

## <a name="to-validate-the-argument-length"></a>若要驗證的引數長度

- 下列程式碼所示，請新增驗證屬性。 此範例中指定的引數的長度應該有 0 到 10 個字元的長度。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateLength 屬性宣告](./validatelength-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
