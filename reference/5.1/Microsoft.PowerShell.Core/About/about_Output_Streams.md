---
description: 說明 PowerShell 中輸出資料流程的可用性和用途。
keywords: PowerShell，Cmdlet
Locale: en-US
ms.date: 10/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_output_streams?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Output_Streams
ms.openlocfilehash: 2f63c468f6b0d82559fca354a8ce5c1343eb2084
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "93208448"
---
# <a name="about-output-streams"></a><span data-ttu-id="44a3c-104">關於輸出資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-104">About output streams</span></span>

## <a name="short-description"></a><span data-ttu-id="44a3c-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="44a3c-105">Short description</span></span>
<span data-ttu-id="44a3c-106">說明 PowerShell 中輸出資料流程的可用性和用途。</span><span class="sxs-lookup"><span data-stu-id="44a3c-106">Explains the availability and purpose of output streams in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="44a3c-107">完整描述</span><span class="sxs-lookup"><span data-stu-id="44a3c-107">Long description</span></span>

<span data-ttu-id="44a3c-108">PowerShell 提供多個輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-108">PowerShell provides multiple output streams.</span></span> <span data-ttu-id="44a3c-109">資料流程會針對不同類型的訊息提供通道。</span><span class="sxs-lookup"><span data-stu-id="44a3c-109">The streams provide channels for different types of messages.</span></span> <span data-ttu-id="44a3c-110">您可以使用相關聯的 Cmdlet 或重新導向來寫入這些資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-110">You can write to these streams using the associated cmdlet or redirection.</span></span> <span data-ttu-id="44a3c-111">如需詳細資訊，請參閱 [about_Redirection](about_Redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="44a3c-111">For more information, see [about_Redirection](about_Redirection.md).</span></span>

<span data-ttu-id="44a3c-112">PowerShell 支援下列輸出資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-112">PowerShell supports the following output streams.</span></span>

| <span data-ttu-id="44a3c-113">流#</span><span class="sxs-lookup"><span data-stu-id="44a3c-113">Stream #</span></span> |      <span data-ttu-id="44a3c-114">Description</span><span class="sxs-lookup"><span data-stu-id="44a3c-114">Description</span></span>       | <span data-ttu-id="44a3c-115">引進于</span><span class="sxs-lookup"><span data-stu-id="44a3c-115">Introduced in</span></span>  |    <span data-ttu-id="44a3c-116">Write Cmdlet</span><span class="sxs-lookup"><span data-stu-id="44a3c-116">Write Cmdlet</span></span>     |
| -------- | ---------------------- | -------------- | ------------------- |
| <span data-ttu-id="44a3c-117">1</span><span class="sxs-lookup"><span data-stu-id="44a3c-117">1</span></span>        | <span data-ttu-id="44a3c-118">**成功** 串流</span><span class="sxs-lookup"><span data-stu-id="44a3c-118">**Success** stream</span></span>     | <span data-ttu-id="44a3c-119">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-119">PowerShell 2.0</span></span> | `Write-Output`      |
| <span data-ttu-id="44a3c-120">2</span><span class="sxs-lookup"><span data-stu-id="44a3c-120">2</span></span>        | <span data-ttu-id="44a3c-121">**錯誤** 資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-121">**Error** stream</span></span>       | <span data-ttu-id="44a3c-122">PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-122">PowerShell 2.0</span></span> | `Write-Error`       |
| <span data-ttu-id="44a3c-123">3</span><span class="sxs-lookup"><span data-stu-id="44a3c-123">3</span></span>        | <span data-ttu-id="44a3c-124">**警告** 資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-124">**Warning** stream</span></span>     | <span data-ttu-id="44a3c-125">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-125">PowerShell 3.0</span></span> | `Write-Warning`     |
| <span data-ttu-id="44a3c-126">4</span><span class="sxs-lookup"><span data-stu-id="44a3c-126">4</span></span>        | <span data-ttu-id="44a3c-127">**詳細** 資訊串流</span><span class="sxs-lookup"><span data-stu-id="44a3c-127">**Verbose** stream</span></span>     | <span data-ttu-id="44a3c-128">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-128">PowerShell 3.0</span></span> | `Write-Verbose`     |
| <span data-ttu-id="44a3c-129">5</span><span class="sxs-lookup"><span data-stu-id="44a3c-129">5</span></span>        | <span data-ttu-id="44a3c-130">**Debug** 資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-130">**Debug** stream</span></span>       | <span data-ttu-id="44a3c-131">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-131">PowerShell 3.0</span></span> | `Write-Debug`       |
| <span data-ttu-id="44a3c-132">6</span><span class="sxs-lookup"><span data-stu-id="44a3c-132">6</span></span>        | <span data-ttu-id="44a3c-133">**資訊** 資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-133">**Information** stream</span></span> | <span data-ttu-id="44a3c-134">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-134">PowerShell 5.0</span></span> | `Write-Information` |
| <span data-ttu-id="44a3c-135">n/a</span><span class="sxs-lookup"><span data-stu-id="44a3c-135">n/a</span></span>      | <span data-ttu-id="44a3c-136">**進度** 資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-136">**Progress** stream</span></span>    | <span data-ttu-id="44a3c-137">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="44a3c-137">PowerShell 3.0</span></span> | `Write-Progress`    |

> [!NOTE]
> <span data-ttu-id="44a3c-138">**進度** 資料流程不支援重新導向。</span><span class="sxs-lookup"><span data-stu-id="44a3c-138">The **Progress** stream does not support redirection.</span></span>

## <a name="success-stream"></a><span data-ttu-id="44a3c-139">成功串流</span><span class="sxs-lookup"><span data-stu-id="44a3c-139">Success stream</span></span>

<span data-ttu-id="44a3c-140">**成功** 資料流程是正常成功結果的預設資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-140">The **Success** stream is the default stream for normal, successful results.</span></span>
<span data-ttu-id="44a3c-141">使用 `Write-Output` Cmdlet 明確地將物件寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-141">Use the `Write-Output` cmdlet to explicitly write objects to this stream.</span></span> <span data-ttu-id="44a3c-142">此資料流程用於透過 PowerShell 管線傳遞物件。</span><span class="sxs-lookup"><span data-stu-id="44a3c-142">This stream is used for passing objects through the PowerShell pipeline.</span></span> <span data-ttu-id="44a3c-143">**成功** 資料流程會連接到原生應用程式的 **stdout** 資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-143">The **Success** stream is connected to the **stdout** stream for native applications.</span></span>

## <a name="error-stream"></a><span data-ttu-id="44a3c-144">錯誤資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-144">Error stream</span></span>

<span data-ttu-id="44a3c-145">**錯誤** 資料流程是錯誤結果的預設資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-145">The **Error** stream is the default stream for error results.</span></span> <span data-ttu-id="44a3c-146">使用 `Write-Error` Cmdlet 明確寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-146">Use the `Write-Error` cmdlet to explicitly write to this stream.</span></span> <span data-ttu-id="44a3c-147">**錯誤** 資料流程會連接到原生應用程式的 **stderr** 資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-147">The **Error** stream is connected to the **stderr** stream for native applications.</span></span> <span data-ttu-id="44a3c-148">在大部分的情況下，這些錯誤可能會終止執行管線。</span><span class="sxs-lookup"><span data-stu-id="44a3c-148">Under most conditions, these errors can terminate the execution pipeline.</span></span> <span data-ttu-id="44a3c-149">寫入此資料流程的錯誤也會新增至 `$Error` 自動變數。</span><span class="sxs-lookup"><span data-stu-id="44a3c-149">Errors written to this stream are also added the the `$Error` automatic variable.</span></span> <span data-ttu-id="44a3c-150">如需詳細資訊，請參閱 [about_Automatic_Variables](about_Automatic_Variables.md)。</span><span class="sxs-lookup"><span data-stu-id="44a3c-150">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

## <a name="warning-stream"></a><span data-ttu-id="44a3c-151">警告資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-151">Warning stream</span></span>

<span data-ttu-id="44a3c-152">**警告** 資料流程適用于比寫入 **錯誤** 資料流程的錯誤更不嚴重的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="44a3c-152">The **Warning** stream is intended for error conditions that are less severe than errors written to the **Error** stream.</span></span> <span data-ttu-id="44a3c-153">在正常情況下，這些警告不會終止執行。</span><span class="sxs-lookup"><span data-stu-id="44a3c-153">Under normal conditions, these warnings do not terminate execution.</span></span> <span data-ttu-id="44a3c-154">警告不會寫入 `$Error` 自動變數中。</span><span class="sxs-lookup"><span data-stu-id="44a3c-154">Warnings are not written to the `$Error` automatic variable.</span></span> <span data-ttu-id="44a3c-155">使用 `Write-Warning` Cmdlet 明確寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-155">Use the `Write-Warning` cmdlet to explicitly write to this stream.</span></span>

## <a name="verbose-stream"></a><span data-ttu-id="44a3c-156">詳細資訊資料流</span><span class="sxs-lookup"><span data-stu-id="44a3c-156">Verbose stream</span></span>

<span data-ttu-id="44a3c-157">**詳細** 資訊資料流程適用于協助使用者以互動方式執行命令或從腳本執行命令的訊息。</span><span class="sxs-lookup"><span data-stu-id="44a3c-157">The **Verbose** stream is intended for messages that help users troubleshoot commands as they are run interactively or from a script.</span></span> <span data-ttu-id="44a3c-158">使用 `Write-Verbose` Cmdlet 明確地將訊息寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-158">Use the `Write-Verbose` cmdlet to explicitly write messages to this stream.</span></span> <span data-ttu-id="44a3c-159">許多 Cmdlet 都提供詳細資訊輸出，有助於瞭解 Cmdlet 的內部運作方式。</span><span class="sxs-lookup"><span data-stu-id="44a3c-159">Many cmdlets provide verbose output that is useful for understanding the internal workings of the cmdlet.</span></span> <span data-ttu-id="44a3c-160">只有當您使用一般參數時，才會輸出詳細資訊訊息 `-Verbose` 。</span><span class="sxs-lookup"><span data-stu-id="44a3c-160">The verbose messages are output only when you use the `-Verbose` common parameter.</span></span> <span data-ttu-id="44a3c-161">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="44a3c-161">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="debug-stream"></a><span data-ttu-id="44a3c-162">偵錯資料流</span><span class="sxs-lookup"><span data-stu-id="44a3c-162">Debug stream</span></span>

<span data-ttu-id="44a3c-163">**調試** 程式資料流程用於協助腳本設計師瞭解其程式碼失敗原因的訊息。</span><span class="sxs-lookup"><span data-stu-id="44a3c-163">The **Debug** stream is used for messages that help scripters understand why their code is failing.</span></span> <span data-ttu-id="44a3c-164">使用 `Write-Debug` Cmdlet 明確寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-164">Use the `Write-Debug` cmdlet to explicitly write to this stream.</span></span> <span data-ttu-id="44a3c-165">只有當您使用一般參數時，才會輸出 debug 訊息 `-Debug` 。</span><span class="sxs-lookup"><span data-stu-id="44a3c-165">The debug messages are output only when you use the `-Debug` common parameter.</span></span> <span data-ttu-id="44a3c-166">如需詳細資訊，請參閱 [about_CommonParameters](about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="44a3c-166">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="44a3c-167">Debug 訊息適用于比一般使用者更多的腳本和 Cmdlet 開發人員。</span><span class="sxs-lookup"><span data-stu-id="44a3c-167">Debug messages are intended for script and cmdlet developers more than end users.</span></span> <span data-ttu-id="44a3c-168">這些偵錯工具訊息可能包含深度疑難排解所需的內部詳細資料。</span><span class="sxs-lookup"><span data-stu-id="44a3c-168">These debug messages can contain internal details necessary for deep troubleshooting.</span></span>

## <a name="information-stream"></a><span data-ttu-id="44a3c-169">資訊資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-169">Information stream</span></span>

<span data-ttu-id="44a3c-170">**資訊** 資料流程旨在提供訊息，協助使用者瞭解腳本的作用。</span><span class="sxs-lookup"><span data-stu-id="44a3c-170">The **Information** stream is intended to provide message that help a user understand what a script is doing.</span></span> <span data-ttu-id="44a3c-171">開發人員也可以使用它當做額外的資料流程，用來透過 PowerShell 傳遞資訊。</span><span class="sxs-lookup"><span data-stu-id="44a3c-171">It can also be used by developers as an additional stream used to pass information through PowerShell.</span></span> <span data-ttu-id="44a3c-172">開發人員可以標記串流資料，並具有該資料流程的特定處理。</span><span class="sxs-lookup"><span data-stu-id="44a3c-172">The developer can tag stream data and have specific handling for that stream.</span></span> <span data-ttu-id="44a3c-173">使用 `Write-Information` Cmdlet 明確寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-173">Use the `Write-Information` cmdlet to explicitly write to this stream.</span></span>

## <a name="progress-stream"></a><span data-ttu-id="44a3c-174">進度資料流程</span><span class="sxs-lookup"><span data-stu-id="44a3c-174">Progress stream</span></span>

<span data-ttu-id="44a3c-175">**進度** 資料流程是用於傳達長時間執行命令和腳本之進度的訊息。</span><span class="sxs-lookup"><span data-stu-id="44a3c-175">The **Progress** stream is used for messages that communicate progress in longer running commands and scripts.</span></span> <span data-ttu-id="44a3c-176">使用 `Write-Progress` Cmdlet 明確地將訊息寫入此資料流程。</span><span class="sxs-lookup"><span data-stu-id="44a3c-176">Use the `Write-Progress` cmdlet to explicitly write messages to this stream.</span></span> <span data-ttu-id="44a3c-177">**進度** 資料流程不支援重新導向。</span><span class="sxs-lookup"><span data-stu-id="44a3c-177">The **Progress** stream does not support redirection.</span></span>

## <a name="see-also"></a><span data-ttu-id="44a3c-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44a3c-178">See also</span></span>

- [<span data-ttu-id="44a3c-179">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="44a3c-179">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="44a3c-180">Write-Error</span><span class="sxs-lookup"><span data-stu-id="44a3c-180">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)
- [<span data-ttu-id="44a3c-181">Write-Host</span><span class="sxs-lookup"><span data-stu-id="44a3c-181">Write-Host</span></span>](xref:Microsoft.PowerShell.Utility.Write-Host)
- [<span data-ttu-id="44a3c-182">Write-Information</span><span class="sxs-lookup"><span data-stu-id="44a3c-182">Write-Information</span></span>](xref:Microsoft.PowerShell.Utility.Write-Information)
- [<span data-ttu-id="44a3c-183">Write-Output</span><span class="sxs-lookup"><span data-stu-id="44a3c-183">Write-Output</span></span>](xref:Microsoft.PowerShell.Utility.Write-Output)
- [<span data-ttu-id="44a3c-184">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="44a3c-184">Write-Progress</span></span>](xref:Microsoft.PowerShell.Utility.Write-Progress)
- [<span data-ttu-id="44a3c-185">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="44a3c-185">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
- [<span data-ttu-id="44a3c-186">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="44a3c-186">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)
- [<span data-ttu-id="44a3c-187">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44a3c-187">about_CommonParameters</span></span>](about_CommonParameters.md)
- [<span data-ttu-id="44a3c-188">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="44a3c-188">about_Redirection</span></span>](about_Redirection.md)
