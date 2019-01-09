---
ms.date: 12/12/2018
keywords: dsc,powershell,設定,安裝
title: 設定中的條件陳述式及迴圈
ms.openlocfilehash: 0073d94d28afbb45bb635442129a6cddde4c805a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 12/14/2018
ms.locfileid: "53400655"
---
# <a name="conditional-statements-and-loops-in-configurations"></a><span data-ttu-id="09586-103">設定中的條件陳述式及迴圈</span><span class="sxs-lookup"><span data-stu-id="09586-103">Conditional statements and loops in Configurations</span></span>

<span data-ttu-id="09586-104">您可以讓您[組態](configurations.md)更為動態使用 PowerShell 的流程控制關鍵字。</span><span class="sxs-lookup"><span data-stu-id="09586-104">You can make your [Configurations](configurations.md) more dynamic using PowerShell flow-control keywords.</span></span> <span data-ttu-id="09586-105">本文將說明如何使用條件陳述式和迴圈將您的設定更為動態。</span><span class="sxs-lookup"><span data-stu-id="09586-105">This article will show you how you can use conditional statements, and loops to make your Configurations more dynamic.</span></span> <span data-ttu-id="09586-106">結合條件和迴圈[參數](add-parameters-to-a-configuration.md)並[組態資料](configData.md)可讓您更多的彈性和控制編譯您的設定時。</span><span class="sxs-lookup"><span data-stu-id="09586-106">Combining conditional and loops with [parameters](add-parameters-to-a-configuration.md) and [Configuration Data](configData.md) allows you more flexibility and control when compiling your Configurations.</span></span>

<span data-ttu-id="09586-107">就像函式或指令碼區塊，您可以使用任何 PowerShell 語言設定中。</span><span class="sxs-lookup"><span data-stu-id="09586-107">Just like a Function or a Script Block, you can use any PowerShell language within a Configuration.</span></span> <span data-ttu-id="09586-108">當您呼叫您的組態來編譯 」.mof"檔案時，才會評估您所使用的陳述式。</span><span class="sxs-lookup"><span data-stu-id="09586-108">The statements you use will only be evaluated when you call your Configuration to compile a ".mof" file.</span></span> <span data-ttu-id="09586-109">下列範例示範簡單的案例來示範概念。</span><span class="sxs-lookup"><span data-stu-id="09586-109">The examples below show simple scenarios to demonstrate concepts.</span></span> <span data-ttu-id="09586-110">條件會使用參數和設定資料更常使用迴圈。</span><span class="sxs-lookup"><span data-stu-id="09586-110">Conditionals are loops are more often used with parameters and Configuration Data.</span></span>

<span data-ttu-id="09586-111">在此簡單範例中，**服務**資源區塊會擷取服務的目前狀態，在編譯時期產生 「.mof 」 檔案，以維護其目前的狀態。</span><span class="sxs-lookup"><span data-stu-id="09586-111">In this simple example, the **Service** resource block retrieves the current state of a service at compile time to generate a ".mof" file that maintains its current state.</span></span>

> [!NOTE]
> <span data-ttu-id="09586-112">使用動態資源區塊將會優先於 Intellisense 的效能。</span><span class="sxs-lookup"><span data-stu-id="09586-112">Using dynamic Resource blocks will preempt the effectiveness of Intellisense.</span></span> <span data-ttu-id="09586-113">PowerShell 剖析器無法判斷指定的值是否可接受之前編譯設定。</span><span class="sxs-lookup"><span data-stu-id="09586-113">The PowerShell parser cannot determine if the values specified are acceptable until the Configuration is compiled.</span></span>

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

<span data-ttu-id="09586-114">此外，您可以建立**服務**封鎖目前的電腦上的每個服務的資源使用`foreach`迴圈。</span><span class="sxs-lookup"><span data-stu-id="09586-114">Additionally, you could create a **Service** block resource for every service on the current machine, using a `foreach` loop.</span></span>

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

<span data-ttu-id="09586-115">您可以也只會建立都在線上，使用簡單的機器組態`if`陳述式。</span><span class="sxs-lookup"><span data-stu-id="09586-115">You could also only create configurations for machines that are online, by using a simple `if` statement.</span></span>

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
> <span data-ttu-id="09586-116">動態資源會封鎖在上面的範例參考目前的電腦。</span><span class="sxs-lookup"><span data-stu-id="09586-116">The dynamic resource blocks in the above examples reference the current machine.</span></span> <span data-ttu-id="09586-117">在這種情況是您要撰寫組態的機器，不是目標節點。</span><span class="sxs-lookup"><span data-stu-id="09586-117">In this instance, that would be the machine you are authoring the Configuration on, not the target Node.</span></span>

<!---
Mention Get-DSCConfigurationFromSystem
-->

## <a name="summary"></a><span data-ttu-id="09586-118">摘要</span><span class="sxs-lookup"><span data-stu-id="09586-118">Summary</span></span>

<span data-ttu-id="09586-119">在 [摘要] 中，您可以使用設定中的任何 PowerShell 語言。</span><span class="sxs-lookup"><span data-stu-id="09586-119">In summary, you can use any PowerShell language within a Configuration.</span></span>

<span data-ttu-id="09586-120">這包括像是：</span><span class="sxs-lookup"><span data-stu-id="09586-120">This includes things like:</span></span>

- <span data-ttu-id="09586-121">自訂物件</span><span class="sxs-lookup"><span data-stu-id="09586-121">Custom Objects</span></span>
- <span data-ttu-id="09586-122">雜湊表</span><span class="sxs-lookup"><span data-stu-id="09586-122">Hashtables</span></span>
- <span data-ttu-id="09586-123">字串操作</span><span class="sxs-lookup"><span data-stu-id="09586-123">String manipulation</span></span>
- <span data-ttu-id="09586-124">遠端</span><span class="sxs-lookup"><span data-stu-id="09586-124">Remoting</span></span>
- <span data-ttu-id="09586-125">WMI 和 CIM</span><span class="sxs-lookup"><span data-stu-id="09586-125">WMI and CIM</span></span>
- <span data-ttu-id="09586-126">Active Directory 物件</span><span class="sxs-lookup"><span data-stu-id="09586-126">ActiveDirectory objects</span></span>
- <span data-ttu-id="09586-127">及其他...</span><span class="sxs-lookup"><span data-stu-id="09586-127">and more...</span></span>

<span data-ttu-id="09586-128">在組態中定義任何 PowerShell 程式碼將會評估編譯時間，但您也可以將程式碼放在指令碼中包含您的組態。</span><span class="sxs-lookup"><span data-stu-id="09586-128">Any PowerShell code defined in a Configuration will be evaluated a compile time, but you can also place code in the script containing your Configuration.</span></span> <span data-ttu-id="09586-129">當您匯入您的設定，將會執行組態區塊之外的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="09586-129">Any code outside of the Configuration block will be executed when you import your Configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="09586-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09586-130">See also</span></span>

- [<span data-ttu-id="09586-131">將參數新增至設定</span><span class="sxs-lookup"><span data-stu-id="09586-131">Add parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
- [<span data-ttu-id="09586-132">從設定中分離設定資料</span><span class="sxs-lookup"><span data-stu-id="09586-132">Separate Configuration data from Configurations</span></span>](configData.md)
