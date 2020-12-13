---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet 範例
description: Cmdlet 範例
ms.openlocfilehash: 6ee149f611e5af5c45a62363e19e66bf200c0c0a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668247"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="e6dfa-103">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="e6dfa-103">Cmdlet Samples</span></span>

<span data-ttu-id="e6dfa-104">此節描述 Windows PowerShell 2.0 SDK 中提供的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-104">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="e6dfa-105">您可以從此節的主題複製程式碼，或開啟隨 SDK 安裝的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-105">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="e6dfa-106">[Windows PowerShell 2.0 軟體開發工具組 (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) 提供每個範例的讀我檔案、原始程式檔與 Visual Studio 專案檔。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-106">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="e6dfa-107">安裝 SDK 之後，您可以在 `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` 資料夾底下找到範例。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-107">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e6dfa-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="e6dfa-108">In This Section</span></span>

<span data-ttu-id="e6dfa-109">[GetProcessSample01 範例](./getprocesssample01-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-109">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="e6dfa-110">[GetProcessSample02 範例](./getprocesssample02-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-110">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="e6dfa-111">其提供 Name 參數，可用來指定要擷取的處理序。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-111">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="e6dfa-112">[GetProcessSample03 範例](./getprocesssample03-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-112">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="e6dfa-113">其提供 Name 參數，此參數接受來自管線的物件，或屬性名稱與參數名稱相同之物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-113">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="e6dfa-114">[GetProcessSample04 範例](./getprocesssample04-sample.md) 此範例示範如何撰寫 Cmdlet 來擷取本機電腦上的處理序。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-114">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="e6dfa-115">如果其在擷取處理序時發生錯誤，會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-115">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="e6dfa-116">[GetProcessSample05 範例](./getprocesssample05-sample.md) 此範例會顯示完整版的 Get-Proc Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-116">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="e6dfa-117">[StopProcessSample01 範例](./stopprocesssample01-sample.md) 此範例示範如何撰寫 Cmdlet，以在嘗試停止處理序之前要求使用者提供意見反應，並示範如何實作 `PassThru` 參數以指出使用者想要 Cmdlet 傳回物件。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-117">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="e6dfa-118">[StopProcessSample02 範例](./stopprocesssample02-sample.md) 此範例示範如何撰寫 Cmdlet，以在停止本機電腦上的處理序時寫入偵錯、詳細與警告訊息。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-118">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="e6dfa-119">[StopProcessSample03 範例](./stopprocesssample03-sample.md) 此範例示範如何撰寫其參數具有別名且支援萬用字元的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-119">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="e6dfa-120">[StopProcessSample04 範例](./stopprocesssample04-sample.md) 此範例示範如何撰寫可宣告參數集、指定預設參數集且可接受輸入物件的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-120">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="e6dfa-121">[Events01 範例](./events01-sample.md) 此範例示範如何建立 Cmdlet，以讓使用者註冊 [Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher) 所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-121">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="e6dfa-122">例如，使用者可以使用此 Cmdlet 來註冊當特定目錄下有檔案建立時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-122">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="e6dfa-123">此範例衍生自 [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) 基底類別。</span><span class="sxs-lookup"><span data-stu-id="e6dfa-123">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6dfa-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6dfa-124">See Also</span></span>

[<span data-ttu-id="e6dfa-125">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e6dfa-125">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
