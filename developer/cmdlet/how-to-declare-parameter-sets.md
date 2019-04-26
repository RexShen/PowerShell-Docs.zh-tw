---
title: 如何宣告參數集 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067887"
---
# <a name="how-to-declare-parameter-sets"></a>如何宣告參數集合

此範例示範如何定義兩個參數集，當您宣告 cmdlet 的參數。 每個參數集同時具有唯一的參數和共用的參數，可由這兩個參數集。 如需有關參數集，包括如何指定預設參數集，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 可能的話，定義參數，為必要的參數設定的唯一參數。 不過，如果您想在不指定任何參數的情況下執行 cmdlet 時，唯一的參數可以是選擇性的參數。 例如，唯一的參數的`Get-Command`是選擇性的 cmdlet。

## <a name="how-to-define-two-parameter-sets"></a>如何定義兩個參數集

1. 新增`ParameterSet`的第一個參數集的唯一參數的參數屬性的關鍵字。

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. 新增`ParameterSet`關鍵字加入第二個參數集的唯一參數的參數屬性。

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. 參數屬於這兩個參數集，新增每個參數集的參數屬性，然後新增`ParameterSet`每一組關鍵字。 您可以在每個參數屬性，指定該參數的定義方式。 參數可以是在一組選擇性的而且在另一個強制。

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>另請參閱

[Cmdlet 參數集](./cmdlet-parameter-sets.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)
