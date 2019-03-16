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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058040"
---
# <a name="cmdlet-samples"></a><span data-ttu-id="6eebc-102">Cmdlet 範例</span><span class="sxs-lookup"><span data-stu-id="6eebc-102">Cmdlet Samples</span></span>

<span data-ttu-id="6eebc-103">本節描述 Windows PowerShell 2.0 SDK 中提供的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="6eebc-103">This section describes sample code that is provided in the Windows PowerShell 2.0 SDK.</span></span> <span data-ttu-id="6eebc-104">您可以在此區段中，主題從程式碼複製，或開啟與 SDK 一起安裝的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="6eebc-104">You can copy code from the topics in this section, or open the source files installed with the SDK.</span></span> <span data-ttu-id="6eebc-105">[Windows PowerShell 2.0 軟體開發套件 (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560)提供讀我檔案、 原始程式檔，以及每個範例的 Visual Studio 專案檔。</span><span class="sxs-lookup"><span data-stu-id="6eebc-105">The [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) provides ReadMe files, source files, and Visual Studio project files for each sample.</span></span> <span data-ttu-id="6eebc-106">已安裝 sdk，您可以找到下的範例`<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`資料夾。</span><span class="sxs-lookup"><span data-stu-id="6eebc-106">With the SDK installed, you can find the samples under the `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` folder.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6eebc-107">在本節中</span><span class="sxs-lookup"><span data-stu-id="6eebc-107">In This Section</span></span>

<span data-ttu-id="6eebc-108">[GetProcessSample01 範例](./getprocesssample01-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6eebc-108">[GetProcessSample01 Sample](./getprocesssample01-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span>

<span data-ttu-id="6eebc-109">[GetProcessSample02 範例](./getprocesssample02-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6eebc-109">[GetProcessSample02 Sample](./getprocesssample02-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6eebc-110">它會提供可用來指定要擷取的處理程序的 Name 參數。</span><span class="sxs-lookup"><span data-stu-id="6eebc-110">It provides a Name parameter that can be used to specify the processes to be retrieved.</span></span>

<span data-ttu-id="6eebc-111">[GetProcessSample03 範例](./getprocesssample03-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6eebc-111">[GetProcessSample03 Sample](./getprocesssample03-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6eebc-112">它提供可接受來自管線的物件或從屬性名稱是參數名稱與相同物件的屬性值的 Name 參數。</span><span class="sxs-lookup"><span data-stu-id="6eebc-112">It provides a Name parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span>

<span data-ttu-id="6eebc-113">[GetProcessSample04 範例](./getprocesssample04-sample.md)這個範例示範如何撰寫 cmdlet 來擷取本機電腦上的處理程序。</span><span class="sxs-lookup"><span data-stu-id="6eebc-113">[GetProcessSample04 Sample](./getprocesssample04-sample.md) This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="6eebc-114">如果在擷取處理序時發生錯誤，它會產生非終止錯誤。</span><span class="sxs-lookup"><span data-stu-id="6eebc-114">It generates a nonterminating error if an error occurs while retrieving a process.</span></span>

<span data-ttu-id="6eebc-115">[GetProcessSample05 範例](./getprocesssample05-sample.md)這個範例會示範 Get-proc cmdlet 的完整版本。</span><span class="sxs-lookup"><span data-stu-id="6eebc-115">[GetProcessSample05 Sample](./getprocesssample05-sample.md) This sample shows a complete version of the Get-Proc cmdlet.</span></span>

<span data-ttu-id="6eebc-116">[StopProcessSample01 範例](./stopprocesssample01-sample.md)這個範例示範如何撰寫的 cmdlet，向使用者要求意見反應之前它會嘗試停止處理程序，, 以及如何實作`PassThru`表示使用者想要傳回 cmdlet 的參數物件。</span><span class="sxs-lookup"><span data-stu-id="6eebc-116">[StopProcessSample01 Sample](./stopprocesssample01-sample.md) This sample shows how to write a cmdlet that requests feedback from the user before it attempts to stop a process, and how to implement a `PassThru` parameter that indicates that the user wants the cmdlet to return an object.</span></span>

<span data-ttu-id="6eebc-117">[StopProcessSample02 範例](./stopprocesssample02-sample.md)這個範例示範如何撰寫的 cmdlet，將寫入 verbose、 debug 和警告訊息，同時在本機電腦上停止處理程序。</span><span class="sxs-lookup"><span data-stu-id="6eebc-117">[StopProcessSample02 Sample](./stopprocesssample02-sample.md) This sample shows how to write a cmdlet that writes debug, verbose, and warning messages while stopping processes on the local computer.</span></span>

<span data-ttu-id="6eebc-118">[StopProcessSample03 範例](./stopprocesssample03-sample.md)這個範例示範如何撰寫的 cmdlet 的參數有別名，支援萬用字元。</span><span class="sxs-lookup"><span data-stu-id="6eebc-118">[StopProcessSample03 Sample](./stopprocesssample03-sample.md) This sample shows how to write a cmdlet whose parameters have aliases and that support wildcard characters.</span></span>

<span data-ttu-id="6eebc-119">[StopProcessSample04 範例](./stopprocesssample04-sample.md)這個範例示範如何撰寫 cmdlet 會宣告參數集，請指定預設參數設定，以及可接受輸入的物件。</span><span class="sxs-lookup"><span data-stu-id="6eebc-119">[StopProcessSample04 Sample](./stopprocesssample04-sample.md) This sample shows how to write a cmdlet that declares parameter sets, specifies the default parameter set, and can accept an input object.</span></span>

<span data-ttu-id="6eebc-120">[Events01 範例](./events01-sample.md)這個範例示範如何建立所引發的事件可讓使用者註冊的 cmdlet [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher)。</span><span class="sxs-lookup"><span data-stu-id="6eebc-120">[Events01 Sample](./events01-sample.md) This sample shows how to create a cmdlet that allows the user to register for events raised by [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span> <span data-ttu-id="6eebc-121">搭配這個指令程式使用者可以比方說，註冊特定的目錄下建立檔案時要執行的動作。</span><span class="sxs-lookup"><span data-stu-id="6eebc-121">With this cmdlet users can, for example, register an action to execute when a file is created under a specific directory.</span></span> <span data-ttu-id="6eebc-122">此範例衍生自[Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase)基底類別。</span><span class="sxs-lookup"><span data-stu-id="6eebc-122">This sample derives from the [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eebc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eebc-123">See Also</span></span>

[<span data-ttu-id="6eebc-124">撰寫 Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6eebc-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
