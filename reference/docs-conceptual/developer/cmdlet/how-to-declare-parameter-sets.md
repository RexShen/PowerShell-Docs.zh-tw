---
title: 如何宣告參數集 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e6d06a9a78356693fe7a338dc5c9207044b23441
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784158"
---
# <a name="how-to-declare-parameter-sets"></a>如何宣告參數集合

這個範例示範當您宣告 Cmdlet 的參數時，如何定義兩個參數集。 每個參數集都有唯一的參數，以及兩個參數集所使用的共用參數。 如需參數集的詳細資訊，包括如何指定預設參數集，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。

> [!IMPORTANT]
> 盡可能將參數集的唯一參數定義為必要參數。 不過，如果您想要在不指定任何參數的情況下執行 Cmdlet，則唯一參數可以是選擇性參數。 例如，Cmdlet 的唯一參數 `Get-Command` 是選擇性的。

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

2. `ParameterSet`針對第二個參數集的 unique 參數，將關鍵字加入至 Parameter 屬性。

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

3. 對於同時屬於這兩個參數集的參數，請為每個參數集新增一個參數屬性，然後在 `ParameterSet` 每個集合中新增關鍵字。 在每個參數屬性中，您可以指定定義該參數的方式。 一個集合中的參數可以是選擇性的，另一個則是必要的。

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
