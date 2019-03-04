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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859734"
---
# <a name="how-to-validate-an-argument-range"></a>如何驗證引數範圍

此範例示範如何指定驗證規則，Windows PowerShell 執行階段可以用來執行此指令程式之前，檢查參數引數的最小和最大值。 您可以設定這項驗證規則宣告 ValidateRange 屬性。

> [!NOTE]
> 如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validaterangeattribute](/dotnet/api/System.Management.Automation.ValidateRangeAttribute)。

### <a name="to-validate-an-argument-range"></a>若要驗證的引數範圍

- 下列程式碼所示，請新增 ValidateRange 屬性。 這個範例會指定 0 到 5 的各種`InputData`參數。

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

如需如何宣告這個屬性的詳細資訊，請參閱[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidateRange 屬性宣告](./validaterange-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
