---
title: 叫用 Cmdlet 與 Cmdlet 中的指令碼 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855184"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="3384b-102">在 Cmdlet 內叫用 Cmdlet 與指令碼</span><span class="sxs-lookup"><span data-stu-id="3384b-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="3384b-103">其他的 cmdlet 和指令碼的位置內的輸入處理方法的 cmdlet，可以叫用 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3384b-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="3384b-104">這可讓您將現有的 cmdlet 與指令碼的功能新增至 cmdlet，而不必重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="3384b-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="3384b-105">叫用方法</span><span class="sxs-lookup"><span data-stu-id="3384b-105">The Invoke Method</span></span>

<span data-ttu-id="3384b-106">所有的指令程式可以藉由呼叫項目叫用現有的 cmdlet [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法內的輸入處理方法，例如[System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)，也就是覆寫 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3384b-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="3384b-107">不過，您可以叫用直接衍生自這些指令程式[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="3384b-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="3384b-108">您無法叫用的 cmdlet，衍生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。</span><span class="sxs-lookup"><span data-stu-id="3384b-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="3384b-109">[System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)方法有下列的變化。</span><span class="sxs-lookup"><span data-stu-id="3384b-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="3384b-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此變異會叫用 cmdlet 物件，並傳回"T"type 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="3384b-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="3384b-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke)此變異會叫用 cmdlet 物件，並傳回強型別的 emumerator。</span><span class="sxs-lookup"><span data-stu-id="3384b-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="3384b-112">此變數可讓使用者使用集合中的物件，來執行自訂的作業。</span><span class="sxs-lookup"><span data-stu-id="3384b-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="3384b-113">範例</span><span class="sxs-lookup"><span data-stu-id="3384b-113">Examples</span></span>

|<span data-ttu-id="3384b-114">範例</span><span class="sxs-lookup"><span data-stu-id="3384b-114">Example</span></span>|<span data-ttu-id="3384b-115">描述</span><span class="sxs-lookup"><span data-stu-id="3384b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3384b-116">叫用 Cmdlet 中的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3384b-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="3384b-117">此範例示範如何叫用另一個 cmdlet 中的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3384b-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="3384b-118">叫用的指令碼中的 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3384b-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="3384b-119">此範例示範如何叫用的指令碼，提供給從中另一個 cmdlet 的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3384b-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="3384b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3384b-120">See Also</span></span>

[<span data-ttu-id="3384b-121">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3384b-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
