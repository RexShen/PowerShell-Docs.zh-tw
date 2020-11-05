---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定中的條件陳述式及迴圈
description: 此文章說明如何使用條件陳述式與迴圈，來讓您的設定更為動態。 將條件式陳述式與迴圈與參數和設定資料結合，可以在編譯您的設定時提供更多的彈性和控制。
ms.openlocfilehash: 7af8a360c17a0842fa2b95d1d1fb288323c327ef
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658460"
---
# <a name="conditional-statements-and-loops-in-a-configuration"></a><span data-ttu-id="1ca3c-105">設定中的條件陳述式及迴圈</span><span class="sxs-lookup"><span data-stu-id="1ca3c-105">Conditional statements and loops in a Configuration</span></span>

<span data-ttu-id="1ca3c-106">您可以使用 PowerShell 的流程控制關鍵字，讓[設定](configurations.md)更為動態。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-106">You can make your [Configuration](configurations.md) more dynamic by using PowerShell flow-control keywords.</span></span> <span data-ttu-id="1ca3c-107">此文章將說明如何使用條件陳述式與迴圈，來讓您的 `Configuration` 更為動態。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-107">This article shows you how you can use conditional statements and loops to make your `Configuration` more dynamic.</span></span> <span data-ttu-id="1ca3c-108">將條件式和迴圈與[參數](add-parameters-to-a-configuration.md)和[設定資料](configData.md)結合，可以在編譯您的`Configuration`時提供更多的彈性和控制。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-108">Combining conditional statements and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your `Configuration`.</span></span>

<span data-ttu-id="1ca3c-109">就像函式或指令碼區塊一樣，您可以在 `Configuration` 中使用任何 PowerShell 語言功能。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-109">Just like a function or a script block, you can use any PowerShell language feature within a `Configuration`.</span></span> <span data-ttu-id="1ca3c-110">只有在呼叫 `Configuration` 以編譯 `.mof` 檔案時，才會評估您所使用的陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-110">The statements you use will only be evaluated when you call your `Configuration` to compile a `.mof` file.</span></span> <span data-ttu-id="1ca3c-111">以下範例顯示了示範概念的案例。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-111">The examples below show scenarios to demonstrate concepts.</span></span> <span data-ttu-id="1ca3c-112">條件陳述式和迴圈通常與參數和設定資料一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-112">Conditional statements and loops are more often used with parameters and configuration Data.</span></span>

<span data-ttu-id="1ca3c-113">在此範例中， **服務** 資源區塊在編譯時間會擷取服務的目前狀態，以產生維護其目前的狀態的 `.mof` 檔案。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-113">In this  example, the **Service** resource block retrieves the current state of a service at compile time to generate a `.mof` file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="1ca3c-114">使用動態資源區塊將優先考慮 Intellisense 的有效性。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-114">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="1ca3c-115">在編譯 `Configuration` 之前，PowerShell 剖析器無法判斷指定的值是否可接受。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-115">The PowerShell parser cannot determine if the values specified are acceptable until the `Configuration` is compiled.</span></span>

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

<span data-ttu-id="1ca3c-116">此外，您可以使用 `foreach` 迴圈為目前電腦上的每個服務建立 **服務** 資源區塊。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-116">Additionally, you could create a **Service** resource block for every service on the current machine using a `foreach` loop.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration
    Node localhost
    {
        foreach ($service in $(Get-Service))
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

<span data-ttu-id="1ca3c-117">您也可以使用 `if` 陳述式，僅為線上電腦建立 `Configuration`。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-117">You could also create a `Configuration` only for machines that are online by using an `if` statement.</span></span>

```powershell
Configuration ServiceState
{
    # It is best practice to explicitly import any resources used in your Configurations.
    Import-DSCResource -Name Service -Module PSDesiredStateConfiguration

    foreach ($computer in @('Server01', 'Server02', 'Server03'))
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
> <span data-ttu-id="1ca3c-118">上述範例中的動態資源區塊會參考目前的電腦。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-118">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="1ca3c-119">在這種情況下，這將是您正在撰寫 `Configuration` 的電腦，而不是目標節點。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-119">In this instance, that would be the machine you are authoring the `Configuration` on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="1ca3c-120">總結</span><span class="sxs-lookup"><span data-stu-id="1ca3c-120">Summary</span></span>

<span data-ttu-id="1ca3c-121">總之，您可以在 `Configuration` 中使用任何 PowerShell 語言功能。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-121">In summary, you can use any PowerShell language feature within a `Configuration`.</span></span>

<span data-ttu-id="1ca3c-122">這包括像是：</span><span class="sxs-lookup"><span data-stu-id="1ca3c-122">This includes things like:</span></span>

- <span data-ttu-id="1ca3c-123">自訂物件</span><span class="sxs-lookup"><span data-stu-id="1ca3c-123">Custom Objects</span></span>
- <span data-ttu-id="1ca3c-124">雜湊表</span><span class="sxs-lookup"><span data-stu-id="1ca3c-124">Hashtables</span></span>
- <span data-ttu-id="1ca3c-125">字串操作</span><span class="sxs-lookup"><span data-stu-id="1ca3c-125">String manipulation</span></span>
- <span data-ttu-id="1ca3c-126">遠端</span><span class="sxs-lookup"><span data-stu-id="1ca3c-126">Remoting</span></span>
- <span data-ttu-id="1ca3c-127">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="1ca3c-127">WMI and CIM</span></span>
- <span data-ttu-id="1ca3c-128">ActiveDirectory 物件</span><span class="sxs-lookup"><span data-stu-id="1ca3c-128">ActiveDirectory objects</span></span>
- <span data-ttu-id="1ca3c-129">還有更多...</span><span class="sxs-lookup"><span data-stu-id="1ca3c-129">and more...</span></span>

<span data-ttu-id="1ca3c-130">`Configuration` 中定義的任何 PowerShell 程式碼都將在編譯時間進行評估，但您也可以在包含 `Configuration` 的指令碼中放置程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-130">Any PowerShell code defined in a `Configuration` is evaluated at compile time, but you can also place code in the script containing your `Configuration`.</span></span> <span data-ttu-id="1ca3c-131">當您匯入 `Configuration` 時，會執行 `Configuration` 區塊以外的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ca3c-131">Any code outside of the `Configuration` block is executed when you import your `Configuration`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ca3c-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ca3c-132">See also</span></span>

- [<span data-ttu-id="1ca3c-133">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="1ca3c-133">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="1ca3c-134">從設定中分離設定資料</span><span class="sxs-lookup"><span data-stu-id="1ca3c-134">Separate Configuration data from Configurations</span></span>](configData.md)
