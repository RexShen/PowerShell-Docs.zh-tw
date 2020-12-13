---
ms.date: 09/13/2016
ms.topic: reference
title: 自訂主機範例
description: 自訂主機範例
ms.openlocfilehash: 939b9f5d6bbc3ccf1ac95343e897ecffef0a2f42
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649322"
---
# <a name="custom-host-samples"></a><span data-ttu-id="74baa-103">自訂主機範例</span><span class="sxs-lookup"><span data-stu-id="74baa-103">Custom Host Samples</span></span>

<span data-ttu-id="74baa-104">本節包含撰寫自訂主機的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="74baa-104">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="74baa-105">您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將本節中的主題的程式碼複製到您的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="74baa-105">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="74baa-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="74baa-106">In This Section</span></span>

 <span data-ttu-id="74baa-107">[Host01 範例](./host01-sample.md) 這個範例示範如何執行使用基本自訂主機的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="74baa-107">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="74baa-108">[Host02 範例](./host02-sample.md) 這個範例會示範如何撰寫使用 Windows PowerShell 執行時間以及自訂主機執行的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="74baa-108">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="74baa-109">主機應用程式會將主機文化特性設定為德文、執行 [取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet，並顯示您使用 pwrsh.exe 所看到的結果，然後以德文列印目前的資料和時間。</span><span class="sxs-lookup"><span data-stu-id="74baa-109">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="74baa-110">[Host03 範例](./host03-sample.md) 這個範例示範如何建立互動式主控台主機應用程式，以從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="74baa-110">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="74baa-111">[Host04 範例](./host04-sample.md) 這個範例示範如何建立互動式主控台主機應用程式，以從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="74baa-111">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="74baa-112">這個主應用程式也支援顯示允許使用者指定多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="74baa-112">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="74baa-113">[>host05 範例](./host05-sample.md) 這個範例示範如何建立互動式主控台主機應用程式，以從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="74baa-113">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="74baa-114">這個主應用程式也支援使用 [Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) 和 [Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 來呼叫遠端電腦</span><span class="sxs-lookup"><span data-stu-id="74baa-114">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="74baa-115">[Host06 範例](./host06-sample.md) 這個範例示範如何建立互動式主控台主機應用程式，以從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="74baa-115">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="74baa-116">此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="74baa-116">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="74baa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74baa-117">See Also</span></span>
