---
ms.date: 09/13/2016
ms.topic: reference
title: 如何宣告參數集合
description: 如何宣告參數集合
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667057"
---
# <a name="how-to-declare-parameter-sets"></a>如何宣告參數集合

此範例示範如何在宣告 Cmdlet 的參數時，定義兩個參數集。 每個參數集都有唯一的參數，以及兩個參數集使用的共用參數。 如需參數集的詳細資訊，包括如何指定預設參數集，請參閱 [Cmdlet 參數集](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 請盡可能將參數集的 unique 參數定義為必要參數。 但是，如果您想要在未指定任何參數的情況下執行 Cmdlet，則唯一參數可以是選擇性參數。 例如，Cmdlet 的 unique 參數 `Get-Command` 是選擇性的。

## <a name="how-to-define-two-parameter-sets"></a>如何定義兩個參數集

1. `ParameterSet`針對第一個參數集的 unique 參數，將關鍵字加入至 parameter 屬性。

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

2. 將 `ParameterSet` 關鍵字加入至第二個參數集之 unique 參數的 parameter 屬性。

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

3. 針對屬於這兩個參數集的參數，加入每個參數集的參數屬性，然後將 `ParameterSet` 關鍵字加入至每個集合。 您可以在每個參數屬性中指定該參數的定義方式。 參數可以在一個集合中是選擇性的，並且在另一個集合中強制。

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
