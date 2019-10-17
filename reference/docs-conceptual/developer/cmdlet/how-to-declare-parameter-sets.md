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
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="d958e-102">如何宣告參數集合</span><span class="sxs-lookup"><span data-stu-id="d958e-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="d958e-103">這個範例示範當您宣告 Cmdlet 的參數時，如何定義兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="d958e-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="d958e-104">每個參數集都有唯一的參數，以及兩個參數集所使用的共用參數。</span><span class="sxs-lookup"><span data-stu-id="d958e-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="d958e-105">如需參數集的詳細資訊，包括如何指定預設參數集，請參閱[Cmdlet 參數集](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="d958e-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d958e-106">盡可能將參數集的唯一參數定義為必要參數。</span><span class="sxs-lookup"><span data-stu-id="d958e-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="d958e-107">不過，如果您想要在不指定任何參數的情況下執行 Cmdlet，則唯一參數可以是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="d958e-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="d958e-108">例如，`Get-Command` Cmdlet 的唯一參數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d958e-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="d958e-109">如何定義兩個參數集</span><span class="sxs-lookup"><span data-stu-id="d958e-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="d958e-110">針對第一個參數集的 unique 參數，將 `ParameterSet` 關鍵字新增至參數屬性。</span><span class="sxs-lookup"><span data-stu-id="d958e-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="d958e-111">針對第二個參數集的 unique 參數，將 `ParameterSet` 關鍵字新增至參數屬性。</span><span class="sxs-lookup"><span data-stu-id="d958e-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="d958e-112">對於同時屬於這兩個參數集的參數，請為每個參數集新增一個參數屬性，然後將 `ParameterSet` 關鍵字加入每個集合中。</span><span class="sxs-lookup"><span data-stu-id="d958e-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="d958e-113">在每個參數屬性中，您可以指定定義該參數的方式。</span><span class="sxs-lookup"><span data-stu-id="d958e-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="d958e-114">一個集合中的參數可以是選擇性的，另一個則是必要的。</span><span class="sxs-lookup"><span data-stu-id="d958e-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d958e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d958e-115">See Also</span></span>

[<span data-ttu-id="d958e-116">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="d958e-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="d958e-117">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d958e-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)