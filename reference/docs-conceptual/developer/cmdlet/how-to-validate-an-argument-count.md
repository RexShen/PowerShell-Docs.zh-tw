---
ms.date: 09/13/2016
ms.topic: reference
title: 如何驗證引數計數
description: 如何驗證引數計數
ms.openlocfilehash: 46a32d61138fb50bceea98171f76749c9d96734d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666938"
---
# <a name="how-to-validate-an-argument-count"></a>如何驗證引數計數

這個範例會示範如何指定 Windows PowerShell 執行時間可用來檢查在執行 Cmdlet 之前，參數所接受的引數數目 () 的驗證規則。 您可以藉由宣告 ValidateCount 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義這個屬性之類別的詳細資訊，請參閱 [Validatecountattribute](/dotnet/api/System.Management.Automation.ValidateCountAttribute)。

## <a name="to-validate-an-argument-count"></a>驗證引數計數

- 加入 Validate 屬性，如下列程式碼所示。 此範例會指定參數會接受一個引數，或最多三個引數。

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

如需如何宣告這個屬性的詳細資訊，請參閱 [ValidateCount 屬性聲明](./validatecount-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateCount 屬性宣告](./validatecount-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
