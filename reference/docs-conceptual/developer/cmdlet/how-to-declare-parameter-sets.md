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
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="c975c-103">如何宣告參數集合</span><span class="sxs-lookup"><span data-stu-id="c975c-103">How to Declare Parameter Sets</span></span>

<span data-ttu-id="c975c-104">此範例示範如何在宣告 Cmdlet 的參數時，定義兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="c975c-104">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="c975c-105">每個參數集都有唯一的參數，以及兩個參數集使用的共用參數。</span><span class="sxs-lookup"><span data-stu-id="c975c-105">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="c975c-106">如需參數集的詳細資訊，包括如何指定預設參數集，請參閱 [Cmdlet 參數集](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="c975c-106">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c975c-107">請盡可能將參數集的 unique 參數定義為必要參數。</span><span class="sxs-lookup"><span data-stu-id="c975c-107">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="c975c-108">但是，如果您想要在未指定任何參數的情況下執行 Cmdlet，則唯一參數可以是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c975c-108">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="c975c-109">例如，Cmdlet 的 unique 參數 `Get-Command` 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c975c-109">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="c975c-110">如何定義兩個參數集</span><span class="sxs-lookup"><span data-stu-id="c975c-110">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="c975c-111">`ParameterSet`針對第一個參數集的 unique 參數，將關鍵字加入至 parameter 屬性。</span><span class="sxs-lookup"><span data-stu-id="c975c-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="c975c-112">將 `ParameterSet` 關鍵字加入至第二個參數集之 unique 參數的 parameter 屬性。</span><span class="sxs-lookup"><span data-stu-id="c975c-112">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="c975c-113">針對屬於這兩個參數集的參數，加入每個參數集的參數屬性，然後將 `ParameterSet` 關鍵字加入至每個集合。</span><span class="sxs-lookup"><span data-stu-id="c975c-113">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="c975c-114">您可以在每個參數屬性中指定該參數的定義方式。</span><span class="sxs-lookup"><span data-stu-id="c975c-114">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="c975c-115">參數可以在一個集合中是選擇性的，並且在另一個集合中強制。</span><span class="sxs-lookup"><span data-stu-id="c975c-115">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c975c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c975c-116">See Also</span></span>

[<span data-ttu-id="c975c-117">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="c975c-117">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="c975c-118">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c975c-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
