---
ms.date: 09/13/2016
ms.topic: reference
title: 在 Cmdlet 內叫用 Cmdlet 與指令碼
description: 在 Cmdlet 內叫用 Cmdlet 與指令碼
ms.openlocfilehash: 246c61661f2d290e7e7ac62a8ad303b05bdc7582
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652639"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="4a0a7-103">在 Cmdlet 內叫用 Cmdlet 與指令碼</span><span class="sxs-lookup"><span data-stu-id="4a0a7-103">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="4a0a7-104">Cmdlet 可以從 Cmdlet 的輸入處理方法中叫用其他 Cmdlet 和腳本。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-104">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="4a0a7-105">這可讓您將現有 Cmdlet 和腳本的功能新增至您的 Cmdlet，而不需要重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-105">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="4a0a7-106">Invoke 方法</span><span class="sxs-lookup"><span data-stu-id="4a0a7-106">The Invoke Method</span></span>

<span data-ttu-id="4a0a7-107">所有 Cmdlet 都可以呼叫 BeginProcessing 來叫用現有的 Cmdlet，方法是從 Cmdlet 所覆寫的輸入處理方法（例如， [ ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)）中叫[用方法。](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)</span><span class="sxs-lookup"><span data-stu-id="4a0a7-107">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="4a0a7-108">不過，您只能叫用直接衍生自 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-108">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="4a0a7-109">您無法叫用衍生自 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-109">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="4a0a7-110">System.servicemodel. [Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) 方法具有下列變體。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-110">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="4a0a7-111">（ [Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant）會叫用 Cmdlet 物件，並傳回 "T" 類型物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="4a0a7-112">Emumerator 叫[用此變異](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)會叫用 Cmdlet 物件，並傳回強型別的。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-112">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="4a0a7-113">此變數可讓使用者使用集合中的物件來執行自訂作業。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-113">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="4a0a7-114">範例</span><span class="sxs-lookup"><span data-stu-id="4a0a7-114">Examples</span></span>

|<span data-ttu-id="4a0a7-115">範例</span><span class="sxs-lookup"><span data-stu-id="4a0a7-115">Example</span></span>|<span data-ttu-id="4a0a7-116">描述</span><span class="sxs-lookup"><span data-stu-id="4a0a7-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4a0a7-117">在 Cmdlet 中叫用 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a0a7-117">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="4a0a7-118">此範例顯示如何從另一個 Cmdlet 中叫用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-118">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="4a0a7-119">在 Cmdlet 中叫用腳本</span><span class="sxs-lookup"><span data-stu-id="4a0a7-119">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="4a0a7-120">此範例示範如何從另一個 Cmdlet 中叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="4a0a7-120">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="4a0a7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a0a7-121">See Also</span></span>

[<span data-ttu-id="4a0a7-122">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4a0a7-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
