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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859694"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="ec3ce-102">如何宣告參數集合</span><span class="sxs-lookup"><span data-stu-id="ec3ce-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="ec3ce-103">此範例示範如何定義兩個參數集，當您宣告 cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="ec3ce-104">每個參數集同時具有唯一的參數和共用的參數，可由這兩個參數集。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="ec3ce-105">如需有關參數集，包括如何指定預設參數集，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec3ce-106">可能的話，定義參數，為必要的參數設定的唯一參數。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="ec3ce-107">不過，如果您想在不指定任何參數的情況下執行 cmdlet 時，唯一的參數可以是選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="ec3ce-108">例如，唯一的參數的`Get-Command`是選擇性的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="ec3ce-109">如何定義兩個參數集</span><span class="sxs-lookup"><span data-stu-id="ec3ce-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="ec3ce-110">新增`ParameterSet`的第一個參數集的唯一參數的參數屬性的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="ec3ce-111">新增`ParameterSet`關鍵字加入第二個參數集的唯一參數的參數屬性。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="ec3ce-112">參數屬於這兩個參數集，新增每個參數集的參數屬性，然後新增`ParameterSet`每一組關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="ec3ce-113">您可以在每個參數屬性，指定該參數的定義方式。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="ec3ce-114">參數可以是在一組選擇性的而且在另一個強制。</span><span class="sxs-lookup"><span data-stu-id="ec3ce-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec3ce-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec3ce-115">See Also</span></span>

[<span data-ttu-id="ec3ce-116">Cmdlet 參數集</span><span class="sxs-lookup"><span data-stu-id="ec3ce-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="ec3ce-117">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec3ce-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
