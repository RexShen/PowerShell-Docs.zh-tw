---
title: 在 Cmdlet 內叫用 Cmdlet 和腳本 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364287"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="c8ca4-102">在 Cmdlet 內叫用 Cmdlet 與指令碼</span><span class="sxs-lookup"><span data-stu-id="c8ca4-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="c8ca4-103">Cmdlet 可以從 Cmdlet 的輸入處理方法中叫用其他 Cmdlet 和腳本。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="c8ca4-104">這可讓您將現有 Cmdlet 和腳本的功能新增至您的 Cmdlet，而不需要重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="c8ca4-105">Invoke 方法</span><span class="sxs-lookup"><span data-stu-id="c8ca4-105">The Invoke Method</span></span>

<span data-ttu-id="c8ca4-106">所有 Cmdlet 都可以叫用現有的 Cmdlet，方法是從輸入處理方法（例如[BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)）中的指令程式所覆寫的方法中，呼叫[。](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)</span><span class="sxs-lookup"><span data-stu-id="c8ca4-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="c8ca4-107">不過，您只能叫用直接衍生自[system.object](/dotnet/api/System.Management.Automation.Cmdlet)類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="c8ca4-108">您不能叫用衍生自[PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="c8ca4-109">[[調用] \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法具有下列變體。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="c8ca4-110">[。叫用此變](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)體會叫用 Cmdlet 物件，並傳回 "T" 類型物件的集合。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="c8ca4-111">[。叫用此變](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)體會叫用 Cmdlet 物件，並傳回強型別 emumerator。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="c8ca4-112">這個變異數可讓使用者使用集合中的物件來執行自訂作業。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="c8ca4-113">範例</span><span class="sxs-lookup"><span data-stu-id="c8ca4-113">Examples</span></span>

|<span data-ttu-id="c8ca4-114">範例</span><span class="sxs-lookup"><span data-stu-id="c8ca4-114">Example</span></span>|<span data-ttu-id="c8ca4-115">描述</span><span class="sxs-lookup"><span data-stu-id="c8ca4-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c8ca4-116">叫用 Cmdlet 中的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c8ca4-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="c8ca4-117">這個範例示範如何從另一個 Cmdlet 中叫用 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="c8ca4-118">在 Cmdlet 內叫用腳本</span><span class="sxs-lookup"><span data-stu-id="c8ca4-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="c8ca4-119">這個範例示範如何從另一個 Cmdlet 叫用提供給 Cmdlet 的腳本。</span><span class="sxs-lookup"><span data-stu-id="c8ca4-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c8ca4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8ca4-120">See Also</span></span>

[<span data-ttu-id="c8ca4-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c8ca4-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
