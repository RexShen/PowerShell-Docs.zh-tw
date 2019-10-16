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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365607"
---
# <a name="how-to-declare-parameter-sets"></a>如何宣告參數集合

這個範例示範當您宣告 Cmdlet 的參數時，如何定義兩個參數集。 每個參數集都有唯一的參數，以及兩個參數集所使用的共用參數。 如需參數集的詳細資訊，包括如何指定預設參數集，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 盡可能將參數集的唯一參數定義為必要參數。 不過，如果您想要在不指定任何參數的情況下執行 Cmdlet，則唯一參數可以是選擇性參數。 例如，`Get-Command` Cmdlet 的唯一參數是選擇性的。

## <a name="how-to-define-two-parameter-sets"></a>如何定義兩個參數集

1. 針對第一個參數集的 unique 參數，將 `ParameterSet` 關鍵字新增至參數屬性。

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

2. 針對第二個參數集的 unique 參數，將 `ParameterSet` 關鍵字新增至參數屬性。

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

3. 對於同時屬於這兩個參數集的參數，請為每個參數集新增一個參數屬性，然後將 `ParameterSet` 關鍵字加入每個集合中。 在每個參數屬性中，您可以指定定義該參數的方式。 一個集合中的參數可以是選擇性的，另一個則是必要的。

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
