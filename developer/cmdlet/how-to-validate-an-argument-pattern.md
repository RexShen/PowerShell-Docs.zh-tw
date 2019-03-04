---
title: 如何驗證引數模式 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ValidatePattern attribute, example
ms.assetid: 7ff76d4c-443a-4887-9ff8-241225f0aeec
caps.latest.revision: 9
ms.openlocfilehash: 5efc1210328c76e57a31d93b9eb52de114816c3c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855064"
---
# <a name="how-to-validate-an-argument-pattern"></a>如何驗證引數模式

此範例示範如何指定 Windows PowerShell 執行階段可用來執行此指令程式之前，請檢查參數引數之字元模式的驗證規則。 您可以設定這項驗證規則宣告 ValidatePattern 屬性。

> [!NOTE]
> 如需有關定義這個屬性的類別的詳細資訊，請參閱[System.Management.Automation.Validatepatternattribute](/dotnet/api/System.Management.Automation.ValidatePatternAttribute)。

## <a name="to-validate-an-argument-pattern"></a>若要驗證的引數的模式

- 下列程式碼所示，請新增驗證屬性。 這個範例會指定四位數，其中每一個數字都有值為 0 到 9 的模式。

    ```csharp
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [Parameter(Position = 0, Mandatory = true)]
    public int InputData
    {
      get { return inputData; }
      set { inputData = value; }
    }

    private int inputData;
    ```

如需如何宣告這個屬性的詳細資訊，請參閱[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)。

## <a name="see-also"></a>另請參閱

[ValidatePattern 屬性宣告](./validatepattern-attribute-declaration.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
