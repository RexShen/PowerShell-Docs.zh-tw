---
title: 如何驗證引數範圍 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidateRange attribute, example
ms.assetid: 3cba3ab7-c3b6-4d17-aa17-88377496551b
caps.latest.revision: 9
ms.openlocfilehash: a39e34d1f1c333185f09b4a934819e1368d29a48
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365517"
---
# <a name="how-to-validate-an-argument-range"></a>如何驗證引數範圍

這個範例示範如何指定 Windows PowerShell 執行時間可用來檢查參數引數的最小和最大值，然後再執行 Cmdlet 的驗證規則。 您可以藉由宣告 ValidateRange 屬性來設定此驗證規則。

> [!NOTE]
> 如需定義此屬性之類別的詳細資訊，請參閱[Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。

### <a name="to-validate-an-argument-range"></a>驗證引數範圍

- 新增 ValidateRange 屬性，如下列程式碼所示。 這個範例會為 `InputData` 參數指定0到5的範圍。

    ```csharp
    [ValidateRange(0, 5)]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }
    private int inputData;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateRange 屬性](./validaterange-attribute-declaration.md)宣告。

## <a name="see-also"></a>另請參閱

[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
