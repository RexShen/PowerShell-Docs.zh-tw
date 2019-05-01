---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定中的條件陳述式及迴圈
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080130"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="4ba4d-103">設定中的條件陳述式及迴圈</span><span class="sxs-lookup"><span data-stu-id="4ba4d-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="4ba4d-104">您可以使用 PowerShell 的流程控制關鍵字，讓[設定](configurations.md)更為動態。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="4ba4d-105">本文將說明如何使用條件陳述式和迴圈，來讓您的設定更為動態。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="4ba4d-106">將條件式和迴圈與[參數](add-parameters-to-a-configuration.md)和[設定資料](configData.md)結合，可以在編譯您的設定時提供更多的彈性和控制。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="4ba4d-107">就像函式或指令碼區塊一樣，您可以在設定中使用任何 PowerShell 語言。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="4ba4d-108">只有在呼叫設定以編譯 ".mof" 檔案時，才會評估您所使用的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="4ba4d-109">以下範例顯示了示範概念的簡單案例。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="4ba4d-110">條件迴圈通常與參數和設定資料一起使用。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="4ba4d-111">在此簡單範例中，**服務**資源區塊在編譯時間會擷取服務的目前狀態，以產生維護其目前的狀態的 ".mof" 檔案。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="4ba4d-112">使用動態資源區塊將優先考慮 Intellisense 的有效性。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="4ba4d-113">在編譯設定之前，PowerShell 剖析器無法判斷指定的值是否可接受。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Service Spooler
        {
            Name = "Spooler"
            State = $(Get-Service -Name 'spooler').Status
            StartType = $(Get-Service -Name 'spooler').StartType
        }
    }
}
```

<span data-ttu-id="4ba4d-114">此外，您可以使用 `foreach` 迴圈為目前電腦上的每個服務建立**服務**區塊資源。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        Foreach ($service in $(Get-Service))
        {
            Service $service.Name
            {
                Name = $service.Name
                State = $service.Status
                StartType = $service.StartType
            }
        }
    }
}
```

<span data-ttu-id="4ba4d-115">您也可以使用簡單的 `if` 陳述式，為線上的電腦建立設定。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    Foreach ($computer in @('Server01', 'Server02', 'Server03'))
    {
        if (Test-Connection -ComputerName $computer)
        {
            Node $computer
            {
                Service "Spooler"
                {
                    Name = "Spooler"
                    State = "Started"
                }
            }
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="4ba4d-116">上述範例中的動態資源區塊會參考目前的電腦。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="4ba4d-117">在這種情況下，這將是您正在撰寫設定的電腦，而不是目標節點。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="4ba4d-118">摘要</span><span class="sxs-lookup"><span data-stu-id="4ba4d-118">Summary</span></span>

<span data-ttu-id="4ba4d-119">總之，您可以在設定中使用任何 PowerShell 語言。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="4ba4d-120">這包括像是：</span><span class="sxs-lookup"><span data-stu-id="4ba4d-120">This includes things like:</span></span>

- <span data-ttu-id="4ba4d-121">自訂物件</span><span class="sxs-lookup"><span data-stu-id="4ba4d-121">Custom Objects</span></span>
- <span data-ttu-id="4ba4d-122">雜湊表</span><span class="sxs-lookup"><span data-stu-id="4ba4d-122">Hashtables</span></span>
- <span data-ttu-id="4ba4d-123">字串操作</span><span class="sxs-lookup"><span data-stu-id="4ba4d-123">String manipulation</span></span>
- <span data-ttu-id="4ba4d-124">遠端</span><span class="sxs-lookup"><span data-stu-id="4ba4d-124">Remoting</span></span>
- <span data-ttu-id="4ba4d-125">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="4ba4d-125">WMI and CIM</span></span>
- <span data-ttu-id="4ba4d-126">ActiveDirectory 物件</span><span class="sxs-lookup"><span data-stu-id="4ba4d-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="4ba4d-127">及其他...</span><span class="sxs-lookup"><span data-stu-id="4ba4d-127">and more...</span></span>

<span data-ttu-id="4ba4d-128">設定中定義的任何 PowerShell 程式碼都將在編譯時間進行評估，但您也可以在包含設定的指令碼中放置程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="4ba4d-129">當您匯入您的設定時，將執行設定區塊之外的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ba4d-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba4d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ba4d-130">See also</span></span>

- [<span data-ttu-id="4ba4d-131">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="4ba4d-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="4ba4d-132">從設定中分離設定資料</span><span class="sxs-lookup"><span data-stu-id="4ba4d-132">Separate Configuration data from Configurations</span></span>](configData.md)
