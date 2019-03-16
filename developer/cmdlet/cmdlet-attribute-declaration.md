---
title: Cmdlet 屬性宣告 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlet attribute, described
- attributes, Cmdlet
- Cmdlet attribute
ms.assetid: 1d323332-f773-4c0e-8a69-2aada765afb2
caps.latest.revision: 12
ms.openlocfilehash: 6887467ad5ccafe6edf8f03f531b4750133aa9e9
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058023"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="ae067-102">Cmdlet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="ae067-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="ae067-103">Cmdlet 屬性識別為 cmdlet 的 Microsoft.NET Framework 類別，並指定用來叫用 cmdlet 的名詞與動詞命令。</span><span class="sxs-lookup"><span data-stu-id="ae067-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae067-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae067-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="ae067-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae067-105">Parameters</span></span>

<span data-ttu-id="ae067-106">`VerbName` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="ae067-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="ae067-107">指定 cmdlet 動詞命令。</span><span class="sxs-lookup"><span data-stu-id="ae067-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="ae067-108">此動詞命令會指定此 cmdlet 所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ae067-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="ae067-109">如需已核准的 cmdlet 動詞命令的詳細資訊，請參閱[動詞的 Cmdlet 名稱](./approved-verbs-for-windows-powershell-commands.md)並[所需的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="ae067-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="ae067-110">`NounName` ([System.String](/dotnet/api/System.String)) 所需。</span><span class="sxs-lookup"><span data-stu-id="ae067-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="ae067-111">指定 cmdlet 名詞。</span><span class="sxs-lookup"><span data-stu-id="ae067-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="ae067-112">這個名詞會指定此 cmdlet 作用的資源。</span><span class="sxs-lookup"><span data-stu-id="ae067-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="ae067-113">如需有關 cmdlet 名詞的詳細資訊，請參閱[Cmdlet 宣告](./cmdlet-class-declaration.md)並[強烈鼓勵開發指導方針](./strongly-encouraged-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="ae067-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="ae067-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="ae067-115">`True` 指出此 cmdlet 支援對[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，可提供此 cmdlet 以變更系統的動作執行之前，提示使用者的方式。</span><span class="sxs-lookup"><span data-stu-id="ae067-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="ae067-116">`False`預設值，指出此 cmdlet 不支援呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="ae067-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="ae067-117">如需確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="ae067-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="ae067-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="ae067-119">指定 cmdlet 的動作時應該呼叫確認[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法。</span><span class="sxs-lookup"><span data-stu-id="ae067-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="ae067-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)將只在等於或大於的值 （根據預設，媒體） cmdlet 的 ConfirmImpact 值時才呼叫`$ConfirmPreference`變數。</span><span class="sxs-lookup"><span data-stu-id="ae067-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="ae067-121">應該指定這個參數時，才`SupportsShouldProcess`指定參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="ae067-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="ae067-123">指定預設參數可讓您設定 Windows PowerShell 執行階段嘗試時無法判斷哪一個參數設定為使用所要使用的。</span><span class="sxs-lookup"><span data-stu-id="ae067-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="ae067-124">請注意，這種情況下要消除，可以藉由每個參數的唯一參數，設定必要的參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="ae067-125">沒有 Windows PowerShell 不能使用的預設參數集，即使未指定預設參數集名稱的其中一種情況。</span><span class="sxs-lookup"><span data-stu-id="ae067-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="ae067-126">Windows PowerShell 執行階段無法區分僅根據物件類型的參數集。</span><span class="sxs-lookup"><span data-stu-id="ae067-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="ae067-127">例如，如果您有另一組檔案路徑，以及採用字串的一個參數集花**FileInfo**物件直接，Windows PowerShell 無法判斷哪一個參數設定為使用根據傳遞給的值指令程式，也不會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="ae067-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="ae067-128">在此情況下，即使您指定預設參數集名稱，Windows PowerShell 會擲回模稜兩可的參數設定錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="ae067-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="ae067-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) 選擇性具名參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="ae067-130">`True` 指出此 cmdlet，可以使用在交易內。</span><span class="sxs-lookup"><span data-stu-id="ae067-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="ae067-131">當`True`未指定，Windows PowerShell 執行階段加入`UseTransaction`cmdlet 的參數清單的參數。</span><span class="sxs-lookup"><span data-stu-id="ae067-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="ae067-132">`False`預設值，指出此 cmdlet 不可用於交易。</span><span class="sxs-lookup"><span data-stu-id="ae067-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae067-133">備註</span><span class="sxs-lookup"><span data-stu-id="ae067-133">Remarks</span></span>

- <span data-ttu-id="ae067-134">在一起，動詞和名詞用來識別您已註冊的 cmdlet，並叫用您在指令碼內的 cmdlet。</span><span class="sxs-lookup"><span data-stu-id="ae067-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="ae067-135">從 Windows PowerShell 主控台中，叫用 cmdlet 時，命令就會類似下列的命令：</span><span class="sxs-lookup"><span data-stu-id="ae067-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="ae067-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="ae067-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="ae067-137">變更 Windows PowerShell 以外之資源的所有 cmdlet 應該都包含`SupportsShouldProcess`關鍵字宣告 Cmdlet 屬性時，它可讓 cmdlet 呼叫[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法之前，此 cmdlet 會執行其動作。</span><span class="sxs-lookup"><span data-stu-id="ae067-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="ae067-138">如果[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫傳回`false`，不應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="ae067-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="ae067-139">如需詳細資訊，所產生之確認要求的相關[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="ae067-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="ae067-140">`Confirm`並`WhatIf`只會針對支援的 cmdlet 的 cmdlet 參數可[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae067-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="ae067-141">範例</span><span class="sxs-lookup"><span data-stu-id="ae067-141">Example</span></span>

<span data-ttu-id="ae067-142">下列類別定義使用 Cmdlet 屬性來識別的.NET Framework 類別**Get-proc** cmdlet，擷取本機電腦上執行的處理程序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ae067-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="ae067-143">如需詳細資訊**Get-proc** cmdlet，請參閱[GetProc 教學課程](./getproc-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="ae067-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae067-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae067-144">See Also</span></span>

[<span data-ttu-id="ae067-145">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ae067-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
