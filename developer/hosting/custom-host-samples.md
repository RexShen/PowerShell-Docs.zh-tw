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
ms.openlocfilehash: 2d88847e17371c4c04b783569fbd983218b6791b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858614"
---
# <a name="custom-host-samples"></a><span data-ttu-id="a0c99-102">自訂主機範例</span><span class="sxs-lookup"><span data-stu-id="a0c99-102">Custom Host Samples</span></span>

<span data-ttu-id="a0c99-103">本節包含範例程式碼撰寫自訂主機。</span><span class="sxs-lookup"><span data-stu-id="a0c99-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="a0c99-104">您可以使用 Microsoft Visual Studio 來建立主控台應用程式，然後將從這一節的主題的程式碼複製到主應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c99-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a0c99-105">在本節中</span><span class="sxs-lookup"><span data-stu-id="a0c99-105">In This Section</span></span>

 <span data-ttu-id="a0c99-106">[Host01 範例](./host01-sample.md)這個範例示範如何實作使用基本的自訂主機的主機應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c99-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="a0c99-107">[Host02 範例](./host02-sample.md)這個範例示範如何撰寫使用 Windows PowerShell 執行階段，以及自訂主機實作的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c99-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="a0c99-108">主應用程式設定為德文、 執行的主控件的文化特性[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，並顯示結果，您會看到它們以德文使用 pwrsh.exe，然後列印目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a0c99-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>
<span data-ttu-id="a0c99-109">此範例示範如何撰寫使用 Windows PowerShell 執行階段，以及自訂主機實作的主應用程式。</span><span class="sxs-lookup"><span data-stu-id="a0c99-109">This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="a0c99-110">主應用程式設定為德文、 執行的主控件的文化特性[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet，並顯示結果，您會看到它們以德文使用 pwrsh.exe，然後列印目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a0c99-110">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="a0c99-111">[Host03 範例](./host03-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a0c99-111">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="a0c99-112">[Host04 範例](./host04-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a0c99-112">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a0c99-113">這個主應用程式也支援顯示允許使用者指定多個選項的提示。</span><span class="sxs-lookup"><span data-stu-id="a0c99-113">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="a0c99-114">[Host05 範例](./host05-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a0c99-114">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a0c99-115">這個主應用程式也支援呼叫遠端電腦使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)並[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet，此範例示範如何建置互動式主控台主機應用程式從命令列讀取命令、 執行命令，，然後在主控台中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a0c99-115">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a0c99-116">這個主應用程式也支援呼叫遠端電腦使用[Enter-pssession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession)並[Exit-pssession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlet</span><span class="sxs-lookup"><span data-stu-id="a0c99-116">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="a0c99-117">[Host06 範例](./host06-sample.md)這個範例示範如何建置互動式主控台主機應用程式，從命令列讀取命令、 執行命令，然後在主控台中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="a0c99-117">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="a0c99-118">此外，這個範例會使用權杖化工具 API 指定使用者所輸入的文字色彩。</span><span class="sxs-lookup"><span data-stu-id="a0c99-118">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0c99-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0c99-119">See Also</span></span>
