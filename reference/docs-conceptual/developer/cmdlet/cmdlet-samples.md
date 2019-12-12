---
title: Cmdlet 範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365877"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="b51ac-102">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="b51ac-102">Cmdlet Samples</span></span>

<span data-ttu-id="b51ac-103">本節說明 Windows PowerShell 2.0 SDK 中提供的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="b51ac-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="b51ac-104">您可以從本節的主題複製程式碼，或開啟隨 SDK 安裝的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="b51ac-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="b51ac-105">[Windows PowerShell 2.0 軟體發展工具組（SDK）](https://www.microsoft.com/en-us/download/details.aspx?id=2560)會提供每個範例的讀我檔案、原始程式檔和 Visual Studio 專案檔案。</span><span class="sxs-lookup"><span data-stu-id="b51ac-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="b51ac-106">安裝 SDK 之後，您可以在 [`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`] 資料夾底下找到範例。</span><span class="sxs-lookup"><span data-stu-id="b51ac-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b51ac-107">在本節中</span><span class="sxs-lookup"><span data-stu-id="b51ac-107">In This Section</span></span>

<span data-ttu-id="b51ac-108">[GetProcessSample01 範例](./getprocesssample01-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b51ac-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="b51ac-109">[GetProcessSample02 範例](./getprocesssample02-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b51ac-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="b51ac-110">它會提供名稱參數，可用來指定要抓取的進程。</span><span class="sxs-lookup"><span data-stu-id="b51ac-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="b51ac-111">[GetProcessSample03 範例](./getprocesssample03-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b51ac-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="b51ac-112">它所提供的 Name 參數可以接受來自管線的物件，或是從屬性名稱與參數名稱相同的物件屬性值。</span><span class="sxs-lookup"><span data-stu-id="b51ac-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="b51ac-113">[GetProcessSample04 範例](./getprocesssample04-sample.md)這個範例會示範如何撰寫 Cmdlet 來抓取本機電腦上的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b51ac-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="b51ac-114">如果在抓取進程時發生錯誤，就會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="b51ac-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="b51ac-115">[GetProcessSample05 範例](./getprocesssample05-sample.md)這個範例會顯示完整版的 Get Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b51ac-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="b51ac-116">[StopProcessSample01 範例](./stopprocesssample01-sample.md)這個範例會示範如何撰寫 Cmdlet，以在嘗試停止進程之前要求使用者提供意見反應，以及如何執行 `PassThru` 參數，表示使用者想要 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="b51ac-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="b51ac-117">[StopProcessSample02 範例](./stopprocesssample02-sample.md)這個範例示範如何撰寫 Cmdlet，以在停止本機電腦上的處理常式時寫入 debug、verbose 和警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b51ac-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="b51ac-118">[StopProcessSample03 範例](./stopprocesssample03-sample.md)這個範例示範如何撰寫 Cmdlet，其參數具有可支援萬用字元的別名和。</span><span class="sxs-lookup"><span data-stu-id="b51ac-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="b51ac-119">[StopProcessSample04 範例](./stopprocesssample04-sample.md)這個範例會示範如何撰寫宣告參數集的 Cmdlet、指定預設參數集，以及接受輸入物件。</span><span class="sxs-lookup"><span data-stu-id="b51ac-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="b51ac-120">[Events01 範例](./events01-sample.md)這個範例示範如何建立 Cmdlet，讓使用者註冊[Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="b51ac-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="b51ac-121">例如，使用此 Cmdlet 時，使用者可以在特定目錄下建立檔案時，註冊要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="b51ac-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="b51ac-122">這個範例是衍生自[自 objecteventregistrationbase Cmdlet](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基類。</span><span class="sxs-lookup"><span data-stu-id="b51ac-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="b51ac-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b51ac-123">See Also</span></span>

[<span data-ttu-id="b51ac-124">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b51ac-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
