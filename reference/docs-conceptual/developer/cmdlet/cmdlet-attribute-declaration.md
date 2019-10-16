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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363537"
---
# <a name="cmdlet-attribute-declaration"></a><span data-ttu-id="5ac7f-102">Cmdlet 屬性宣告</span><span class="sxs-lookup"><span data-stu-id="5ac7f-102">Cmdlet Attribute Declaration</span></span>

<span data-ttu-id="5ac7f-103">Cmdlet 屬性會將 Microsoft .NET Framework 類別識別為 Cmdlet，並指定用來叫用 Cmdlet 的動詞和名詞。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-103">The Cmdlet attribute identifies a Microsoft .NET Framework class as a cmdlet and specifies the verb and noun used to invoke the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ac7f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ac7f-104">Syntax</span></span>

```csharp
[Cmdlet("verbName", "nounName")]
[Cmdlet("verbName", "nounName", Named Parameters...)]
```

#### <a name="parameters"></a><span data-ttu-id="5ac7f-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ac7f-105">Parameters</span></span>

<span data-ttu-id="5ac7f-106">需要 `VerbName` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-106">`VerbName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="5ac7f-107">指定 Cmdlet 動詞。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-107">Specifies the cmdlet verb.</span></span> <span data-ttu-id="5ac7f-108">這個動詞命令會指定 Cmdlet 所採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-108">This verb specifies the action taken by the cmdlet.</span></span> <span data-ttu-id="5ac7f-109">如需已核准 Cmdlet 動詞命令的詳細資訊，請參閱[Cmdlet 動詞名稱](./approved-verbs-for-windows-powershell-commands.md)和[必要的開發指導方針](./required-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md) and [Required Development Guidelines](./required-development-guidelines.md).</span></span>

<span data-ttu-id="5ac7f-110">需要 `NounName` （[system.string](/dotnet/api/System.String)）。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-110">`NounName` ([System.String](/dotnet/api/System.String)) Required.</span></span> <span data-ttu-id="5ac7f-111">指定 Cmdlet 名詞。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-111">Specifies the cmdlet noun.</span></span> <span data-ttu-id="5ac7f-112">此名詞會指定 Cmdlet 作用的資源。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-112">This noun specifies the resource that the cmdlet acts upon.</span></span> <span data-ttu-id="5ac7f-113">如需 Cmdlet 名詞的詳細資訊，請參閱[Cmdlet](./cmdlet-class-declaration.md)宣告和[強烈建議的開發指導方針](./strongly-encouraged-development-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-113">For more information about cmdlet nouns, see [Cmdlet Declaration](./cmdlet-class-declaration.md) and [Strongly Encouraged Development Guidelines](./strongly-encouraged-development-guidelines.md).</span></span>

<span data-ttu-id="5ac7f-114">`SupportsShouldProcess` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-114">`SupportsShouldProcess` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5ac7f-115">`True` 表示此 Cmdlet 支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的呼叫，它會提供 Cmdlet，讓您在執行變更系統的動作之前，先提示使用者。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-115">`True` indicates that the cmdlet supports calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method, which provides the cmdlet with a way to prompt the user before an action that changes the system is performed.</span></span> <span data-ttu-id="5ac7f-116">`False` （預設值）表示此 Cmdlet 不支援呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法的程式，。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-116">`False`, the default value, indicates that the cmdlet does not support calls to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="5ac7f-117">如需有關確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-117">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="5ac7f-118">`ConfirmImpact` （[Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-118">`ConfirmImpact` ([System.Management.Automation.Confirmimpact](/dotnet/api/System.Management.Automation.ConfirmImpact)) Optional named parameter.</span></span> <span data-ttu-id="5ac7f-119">指定在呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法時，應如何確認 Cmdlet 的動作。（& i）</span><span class="sxs-lookup"><span data-stu-id="5ac7f-119">Specifies when the action of the cmdlet should be confirmed by a call to the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="5ac7f-120">[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)只會在 Cmdlet 的 ConfirmImpact 值（根據預設為 Medium）等於或大於 @no__t 1 變數的值時呼叫，才會呼叫。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-120">[System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) will only be called when the ConfirmImpact value of the cmdlet (by default, Medium) is equal to or greater than the value of the `$ConfirmPreference` variable.</span></span> <span data-ttu-id="5ac7f-121">只有在指定了 `SupportsShouldProcess` 參數時，才應該指定這個參數。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-121">This parameter should be specified only when the `SupportsShouldProcess` parameter is specified.</span></span>

<span data-ttu-id="5ac7f-122">`DefaultParameterSetName` （[system.string](/dotnet/api/System.String)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-122">`DefaultParameterSetName` ([System.String](/dotnet/api/System.String)) Optional named parameter.</span></span> <span data-ttu-id="5ac7f-123">指定 Windows PowerShell 執行時間在無法判斷要使用哪個參數集時，所嘗試使用的預設參數集。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-123">Specifies the default parameter set that the Windows PowerShell runtime attempts to use when it cannot determine which parameter set to use.</span></span> <span data-ttu-id="5ac7f-124">請注意，您可以將每個參數的 unique 參數設定為強制參數，以消除這種情況。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-124">Notice that this situation can be eliminated by making the unique parameter of each parameter set a mandatory parameter.</span></span>

<span data-ttu-id="5ac7f-125">有一種情況下，即使指定了預設參數集名稱，Windows PowerShell 也無法使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-125">There is one case where Windows PowerShell cannot use the default parameter set even if a default parameter set name is specified.</span></span> <span data-ttu-id="5ac7f-126">Windows PowerShell 執行時間無法根據物件類型來區分參數集。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-126">The Windows PowerShell runtime cannot distinguish between parameter sets based solely on object type.</span></span> <span data-ttu-id="5ac7f-127">例如，如果您有一個參數集採用字串做為檔案路徑，而另一組直接接受**FileInfo**物件，Windows PowerShell 就無法根據傳遞給 Cmdlet 的值來判斷要使用的參數集，也不會使用預設參數集。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-127">For example, if you have one parameter set that takes a string as the file path, and another set that takes a **FileInfo** object directly, Windows PowerShell cannot determine which parameter set to use based on the values passed to the cmdlet, nor does it use the default parameter set.</span></span> <span data-ttu-id="5ac7f-128">在此情況下，即使您指定預設參數集名稱，Windows PowerShell 還是會擲回不明確的參數集錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-128">In this case, even if you specify a default parameter set name, Windows PowerShell throws an ambiguous parameter set error message.</span></span>

<span data-ttu-id="5ac7f-129">`SupportsTransactions` （[布林值](/dotnet/api/System.Boolean)）選擇性的具名引數。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-129">`SupportsTransactions` ([System.Boolean](/dotnet/api/System.Boolean)) Optional named parameter.</span></span> <span data-ttu-id="5ac7f-130">`True` 表示可在交易內使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-130">`True` indicates that the cmdlet can be used within a transaction.</span></span> <span data-ttu-id="5ac7f-131">當指定 `True` 時，Windows PowerShell 執行時間會將 `UseTransaction` 參數新增至 Cmdlet 的參數清單。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-131">When `True` is specified, the Windows PowerShell runtime adds the `UseTransaction` parameter to the parameter list of the cmdlet.</span></span> <span data-ttu-id="5ac7f-132">`False`，預設值表示 Cmdlet 無法在交易內使用。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-132">`False`, the default value, indicates that the cmdlet cannot be used within a transaction.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ac7f-133">備註</span><span class="sxs-lookup"><span data-stu-id="5ac7f-133">Remarks</span></span>

- <span data-ttu-id="5ac7f-134">動詞和名詞一起用來識別您已註冊的 Cmdlet，並在腳本中叫用您的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-134">Together, the verb and noun are used to identify your registered cmdlet and to invoke your cmdlet within a script.</span></span>

- <span data-ttu-id="5ac7f-135">從 Windows PowerShell 主控台叫用 Cmdlet 時，命令會類似下列命令：</span><span class="sxs-lookup"><span data-stu-id="5ac7f-135">When the cmdlet is invoked from the Windows PowerShell console, the command resembles the following command:</span></span>

<span data-ttu-id="5ac7f-136">**VerbName-NounName**</span><span class="sxs-lookup"><span data-stu-id="5ac7f-136">**VerbName-NounName**</span></span>

- <span data-ttu-id="5ac7f-137">在 Windows PowerShell 外部變更資源的所有 Cmdlet，都應該在宣告 Cmdlet 屬性時包含 `SupportsShouldProcess` 關鍵字，這可讓 Cmdlet 呼叫[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)方法，然後再進行Cmdlet 會執行其動作。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-137">All cmdlets that change resources outside of Windows PowerShell should include the `SupportsShouldProcess` keyword when the Cmdlet attribute is declared, which allows the cmdlet to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method before the cmdlet performs its action.</span></span> <span data-ttu-id="5ac7f-138">如果[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫傳回 `false`，則不應採取此動作。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-138">If the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call returns `false`, the action should not be taken.</span></span> <span data-ttu-id="5ac7f-139">如需[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫所產生之確認要求的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-139">For more information about the confirmation requests generated by the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

<span data-ttu-id="5ac7f-140">@No__t-0 和 @no__t 1 Cmdlet 參數僅適用于支援[ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)呼叫的指令程式。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-140">The `Confirm` and `WhatIf` cmdlet parameters are available only for cmdlets that support [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) calls.</span></span>

## <a name="example"></a><span data-ttu-id="5ac7f-141">範例</span><span class="sxs-lookup"><span data-stu-id="5ac7f-141">Example</span></span>

<span data-ttu-id="5ac7f-142">下列類別定義會使用 Cmdlet 屬性來識別用來取得在本機電腦上執行之處理常式相關資訊的**Proc** Cmdlet 的 .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-142">The following class definition uses the Cmdlet attribute to identify the .NET Framework class for a **Get-Proc** cmdlet that retrieves information about the processes running on the local computer.</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="5ac7f-143">如需有關**Proc** Cmdlet 的詳細資訊，請參閱[GetProc 教學](./getproc-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="5ac7f-143">For more information about the **Get-Proc** cmdlet, see [GetProc Tutorial](./getproc-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ac7f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ac7f-144">See Also</span></span>

[<span data-ttu-id="5ac7f-145">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5ac7f-145">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
