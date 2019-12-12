---
title: 自訂主機範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367507"
---
# <a name="custom-host-samples"></a><span data-ttu-id="1c170-102">自訂主機範例</span><span class="sxs-lookup"><span data-stu-id="1c170-102">Custom Host Samples</span></span>

<span data-ttu-id="1c170-103">本節包含用來撰寫自訂主機的範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="1c170-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="1c170-104">您可以使用 Microsoft Visual Studio 建立主控台應用程式，然後將此區段中的主題中的程式碼複製到您的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c170-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1c170-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="1c170-105">In This Section</span></span>

 <span data-ttu-id="1c170-106">[Host01 範例](./host01-sample.md)這個範例示範如何執行使用基本自訂主機的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c170-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="1c170-107">[Host02 範例](./host02-sample.md)這個範例示範如何撰寫使用 Windows PowerShell 執行時間以及自訂主機執行的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c170-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="1c170-108">主應用程式會將主機文化特性設定為德文、執行[取得程式](/powershell/module/Microsoft.PowerShell.Management/Get-Process)Cmdlet 並顯示結果，就像您使用 pwrsh 所看到的一樣，然後以德文印出目前的資料和時間。</span><span class="sxs-lookup"><span data-stu-id="1c170-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="1c170-109">[Host03 範例](./host03-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="1c170-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="1c170-110">[Host04 範例](./host04-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="1c170-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="1c170-111">這個主應用程式也支援顯示允許使用者指定多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="1c170-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="1c170-112">[Host05 範例](./host05-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="1c170-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="1c170-113">此主機應用程式也支援使用[輸入-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)和[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) Cmdlet 呼叫遠端電腦</span><span class="sxs-lookup"><span data-stu-id="1c170-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="1c170-114">[Host06 範例](./host06-sample.md)這個範例示範如何建立互動式主控台主機應用程式，從命令列讀取命令、執行命令，然後將結果顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="1c170-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="1c170-115">此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="1c170-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c170-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c170-116">See Also</span></span>
