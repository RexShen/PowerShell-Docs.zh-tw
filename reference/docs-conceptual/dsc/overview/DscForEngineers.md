---
ms.date: 10/13/2017
keywords: dsc,powershell,設定,安裝
title: 適合工程師的預期狀態設定概觀
ms.openlocfilehash: dbed274d5333c216970247b88d2a0956025e969d
ms.sourcegitcommit: a5e945e0889d0635b7af767d80d6a13bc5526269
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82584518"
---
# <a name="desired-state-configuration-overview-for-engineers"></a><span data-ttu-id="233df-103">適合工程師的預期狀態設定概觀</span><span class="sxs-lookup"><span data-stu-id="233df-103">Desired State Configuration Overview for Engineers</span></span>

<span data-ttu-id="233df-104">本文件適合開發人員及作業小組了解 PowerShell 預期狀態設定 (DSC) 的優勢。</span><span class="sxs-lookup"><span data-stu-id="233df-104">This document is intended for developer and operations teams to understand the benefits of PowerShell Desired State Configuration (DSC).</span></span> <span data-ttu-id="233df-105">如需 DSC 所提供價值的較高層級檢視，請參閱[適合決策者的預期狀態設定概觀](decisionMaker.md)</span><span class="sxs-lookup"><span data-stu-id="233df-105">For a higher level view of the value DSC provides, please see [Desired State Configuration Overview for Decision Makers](decisionMaker.md)</span></span>

## <a name="benefits-of-desired-state-configuration"></a><span data-ttu-id="233df-106">預期狀態設定的優勢</span><span class="sxs-lookup"><span data-stu-id="233df-106">Benefits of Desired State Configuration</span></span>

<span data-ttu-id="233df-107">DSC 是用來：</span><span class="sxs-lookup"><span data-stu-id="233df-107">DSC exists to:</span></span>

- <span data-ttu-id="233df-108">減少 Windows 中的指令碼複雜度</span><span class="sxs-lookup"><span data-stu-id="233df-108">Decrease the complexity of scripting in Windows</span></span>
- <span data-ttu-id="233df-109">提升反覆運算的速度</span><span class="sxs-lookup"><span data-stu-id="233df-109">Increase the speed of iteration</span></span>

<span data-ttu-id="233df-110">「持續部署」的概念越來越重要。</span><span class="sxs-lookup"><span data-stu-id="233df-110">The concept of "continuous deployment" is becoming more important.</span></span> <span data-ttu-id="233df-111">「持續部署」是指頻繁部署的能力，可以在一天內部署多次。</span><span class="sxs-lookup"><span data-stu-id="233df-111">Continuous deployment means the ability to deploy frequently, potentially many times per day.</span></span> <span data-ttu-id="233df-112">這些部署的目的並非修正某些項目，而是能快速發行某些項目。</span><span class="sxs-lookup"><span data-stu-id="233df-112">The purpose of these deployments are not to fix something but to get something published quickly.</span></span> <span data-ttu-id="233df-113">透過盡可能以順暢且可靠的方式讓新功能從開發進入作業，將可以減少新商務邏輯創造價值所需的時間。</span><span class="sxs-lookup"><span data-stu-id="233df-113">By getting new features through development into operation as smoothly and reliably as possible, you reduce time-to-value of new business logic.</span></span>

<span data-ttu-id="233df-114">移至雲端運算，代表需要能運用「宣告式」範本模型的部署解決方案，其中的結束狀態環境會宣告為文字，並發佈至部署引擎。</span><span class="sxs-lookup"><span data-stu-id="233df-114">The move towards cloud computing implies a deployment solution that utilizes a "declarative" template model, where an end state environment is declared as text and published to a deployment engine.</span></span> <span data-ttu-id="233df-115">此部署技術能大規模地做出快速變更，並具備針對失敗風險的恢復力，因為部署可隨時一致地重複以保證結束狀態。</span><span class="sxs-lookup"><span data-stu-id="233df-115">This deployment technique allows for rapid change, at scale, with resilience against threat of failure because at any time the deployment can be consistently repeated to guarantee an end state.</span></span> <span data-ttu-id="233df-116">透過自動化建立支援此作業模式的工具和服務，便是針對這些變更的回應。</span><span class="sxs-lookup"><span data-stu-id="233df-116">The creation of tools and services that support this style of operations through automation is a response to these changes.</span></span>

<span data-ttu-id="233df-117">DSC 是一個可提供宣告式且等冪 (可重複) 部署、設定和一致性的平台。</span><span class="sxs-lookup"><span data-stu-id="233df-117">DSC is a platform that provides declarative and idempotent (repeatable) deployment, configuration and conformance.</span></span> <span data-ttu-id="233df-118">DSC 平台可讓您確保資料中心的元件具有正確的設定，以避免錯誤並防止耗費成本的部署失敗。</span><span class="sxs-lookup"><span data-stu-id="233df-118">The DSC platform enables you to ensure that the components of your data center have the correct configuration, which avoids errors and prevents costly deployment failures.</span></span> <span data-ttu-id="233df-119">藉由將 DSC 設定當作應用程式程式碼的一部分，DSC 便能提供持續部署的可能性。</span><span class="sxs-lookup"><span data-stu-id="233df-119">By treating DSC configurations as part of application code, DSC enables continuous deployment.</span></span> <span data-ttu-id="233df-120">DSC 設定應該當作應用程式的一部分更新，以確保部署應用程式所需的知識永遠保持在最新狀態且隨時可用。</span><span class="sxs-lookup"><span data-stu-id="233df-120">The DSC configuration should be updated as a part of the application, ensuring that the knowledge needed to deploy the application is always up-to-date and ready to be used.</span></span>

## <a name="i-have-powershell-why-do-i-need-desired-state-configuration"></a><span data-ttu-id="233df-121">「我有 PowerShell，為什麼需要預期狀態設定？」</span><span class="sxs-lookup"><span data-stu-id="233df-121">"I have PowerShell, why do I need Desired State Configuration?"</span></span>

<span data-ttu-id="233df-122">DSC 設定可將意圖 (或「我要做什麼」) 從執行 (或「我要如何做」) 中分隔出來。</span><span class="sxs-lookup"><span data-stu-id="233df-122">DSC configurations separate intent, or "what I want to do", from execution, or "how I want to do it."</span></span> <span data-ttu-id="233df-123">這表示執行邏輯是包含在資源之內。</span><span class="sxs-lookup"><span data-stu-id="233df-123">This means the logic of execution is contained within the resources.</span></span> <span data-ttu-id="233df-124">當功能的 DSC 資源可用時，使用者並不需要了解實作或部署該功能的方式。</span><span class="sxs-lookup"><span data-stu-id="233df-124">Users do not have to know how to implement or deploy a feature when a DSC resource for that feature is available.</span></span> <span data-ttu-id="233df-125">這可讓使用者專注於他們的部署結構。</span><span class="sxs-lookup"><span data-stu-id="233df-125">This allows the user to focus on the structure of their deployment.</span></span>

<span data-ttu-id="233df-126">例如，PowerShell 指令碼看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="233df-126">As an example, PowerShell scripts should look like this:</span></span>

```powershell
# Create a share in Windows Server 8
New-SmbShare -Name MyShare -Path C:\Demo\Temp -FullAccess Alice -ReadAccess Bob
```

<span data-ttu-id="233df-127">這個指令碼簡單、易懂又直接。</span><span class="sxs-lookup"><span data-stu-id="233df-127">This script is simple, comprehensible, and straightforward.</span></span> <span data-ttu-id="233df-128">但是，如果您嘗試將該指令碼放入生產環境，您將會遇到幾個問題。</span><span class="sxs-lookup"><span data-stu-id="233df-128">However, if you try putting that script into production, you will run into several issues.</span></span> <span data-ttu-id="233df-129">如果該指令碼連續執行兩次，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="233df-129">What happens if that script is run twice in a row?</span></span> <span data-ttu-id="233df-130">如果 Bob 之前擁有該共用的完整存取權，會發生什麼事？</span><span class="sxs-lookup"><span data-stu-id="233df-130">What happens if Bob previously had Full Access to the share?</span></span>

<span data-ttu-id="233df-131">為了彌補這些問題，指令碼的「實際」版本看起來會更像這樣：</span><span class="sxs-lookup"><span data-stu-id="233df-131">To compensate for these issues, a "real" version of the script will look closer to something like:</span></span>

```powershell
# But actually creating a share in an idempotent way would be

$shareExists = $false
$smbShare = Get-SmbShare -Name $Name -ErrorAction SilentlyContinue
if($smbShare -ne $null)
{
    Write-Verbose -Message "Share with name $Name exists"
    $shareExists = $true
}

if ($shareExists -eq $false)
{
    Write-Verbose "Creating share $Name to ensure it is Present"
    New-SmbShare @PSBoundParameters
}
else
{
    # Need to call either Set-SmbShare or *ShareAccess cmdlets
    if ($PSBoundParameters.ContainsKey("ChangeAccess"))
    {
       #...etc, etc, etc
    }
}
```

<span data-ttu-id="233df-132">這個指令碼更複雜，含有大量的邏輯及錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="233df-132">This script is more complex, with plenty of logic and error handling.</span></span> <span data-ttu-id="233df-133">因為您已不再是指出要完成的動作，而是「要如何這麼做」  ，使得這個指令碼變得更加複雜。</span><span class="sxs-lookup"><span data-stu-id="233df-133">The script is more complex because you are no longer stating what you want done, but _how to do it_.</span></span>

<span data-ttu-id="233df-134">DSC 可讓您指定要完成的動作，並將基礎邏輯抽象化。</span><span class="sxs-lookup"><span data-stu-id="233df-134">DSC allows you to say what you want done, and the underlying logic is abstracted away.</span></span>

```powershell
# A configuration is a special kind of PowerShell function
Configuration Sample_Share
{
   Import-DscResource -Module xSmbShare
   # Nodes are the endpoint we wish to configure
   # A Configuration block can have zero or more Node blocks
   Node $NodeName
   {
      # Next, specify one or more resource blocks
      # Resources are simply PowerShell modules that
      # implement the logic of "how" to execute a task
      xSmbShare MySMBShare
      {
          Ensure      = "Present"
          Name        = "MyShare"
          Path        = "C:\Demo\Temp"
          ReadAccess  = "Bob"
          FullAccess  = "Alice"
          Description = "This is an updated description for this share"
      }
   }
}
#Run the function to compile the configuration
Sample_Share
#Pass the configuration to the nodes we defined and configure them
Start-DscConfiguration Sample_Share
```

<span data-ttu-id="233df-135">此指令碼的格式簡潔且容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="233df-135">This script is cleanly formatted and straightforward to read.</span></span>
<span data-ttu-id="233df-136">邏輯路徑和錯誤處理仍然存在於[資源](../resources/resources.md)的實作中，但指令碼作者看不到。</span><span class="sxs-lookup"><span data-stu-id="233df-136">The logic paths and error handling are still present in the [resource](../resources/resources.md) implementation, but invisible to the script author.</span></span>

## <a name="separating-environment-from-structure"></a><span data-ttu-id="233df-137">從結構分隔環境</span><span class="sxs-lookup"><span data-stu-id="233df-137">Separating Environment from Structure</span></span>

<span data-ttu-id="233df-138">DevOps 中其中一個常見的模式，是針對部署有多個環境。</span><span class="sxs-lookup"><span data-stu-id="233df-138">A common pattern in DevOps is to have multiple environments for deployment.</span></span> <span data-ttu-id="233df-139">例如，可能會有一個可用來快速開發新程式碼原型的「開發」環境。</span><span class="sxs-lookup"><span data-stu-id="233df-139">For example, there might be a "dev" environment used to quickly prototype new code.</span></span> <span data-ttu-id="233df-140">「開發」環境的程式碼接著會進入「測試」環境，讓其他人員可以確認新的功能。</span><span class="sxs-lookup"><span data-stu-id="233df-140">The code from the "dev" environment goes into a "test" environment, where other people verify the new functionality.</span></span> <span data-ttu-id="233df-141">最後，該程式碼會進入「生產」，也就是即時網站生產環境。</span><span class="sxs-lookup"><span data-stu-id="233df-141">Finally, the code goes into "prod", or the live site production environment.</span></span>

<span data-ttu-id="233df-142">DSC 設定透過使用[設定資料](../configurations/configData.md)來容納這個開發-測試-生產的管線。</span><span class="sxs-lookup"><span data-stu-id="233df-142">DSC configurations accommodate this dev-test-prod pipeline through the use of [configuration data](../configurations/configData.md).</span></span>
<span data-ttu-id="233df-143">這會進一步將設定結構與受管理節點之間的差異抽象化。</span><span class="sxs-lookup"><span data-stu-id="233df-143">This further abstracts the difference between the structure of the configuration from the nodes that are managed.</span></span> <span data-ttu-id="233df-144">例如，您可以定義一個需要 SQL 伺服器、IIS 伺服器以及中介層伺服器的設定。</span><span class="sxs-lookup"><span data-stu-id="233df-144">For example, you can define a configuration that requires a SQL server, an IIS server, and a middle-tier server.</span></span> <span data-ttu-id="233df-145">無論何種節點接收此設定的何種部分，這三個元素將總是會存在。</span><span class="sxs-lookup"><span data-stu-id="233df-145">Regardless of what nodes receive the different pieces of this configuration, those three elements will always be present.</span></span> <span data-ttu-id="233df-146">您可以使用設定資料將所有三個元素指向開發環境的同一部電腦，然後將三個元素分別指向測試環境的三台不同的電腦，並於最後將三個元素指向生產環境的所有生產伺服器。</span><span class="sxs-lookup"><span data-stu-id="233df-146">You can use configuration data to point all three elements towards the same machine for a dev environment, separate out the three elements to three different machines for a test environment, and finally towards all your production servers for the prod environment.</span></span> <span data-ttu-id="233df-147">若要部署至不同環境，您可以叫用 `Start-DscConfiguration` 並搭配您目標環境的正確設定資料。</span><span class="sxs-lookup"><span data-stu-id="233df-147">To deploy to the different environments, you can invoke `Start-DscConfiguration` with the correct configuration data for the environment you want to target.</span></span>

## <a name="see-also"></a><span data-ttu-id="233df-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="233df-148">See Also</span></span>

[<span data-ttu-id="233df-149">組態</span><span class="sxs-lookup"><span data-stu-id="233df-149">Configurations</span></span>](../configurations/configurations.md)

[<span data-ttu-id="233df-150">設定資料</span><span class="sxs-lookup"><span data-stu-id="233df-150">Configuration Data</span></span>](../configurations/configData.md)

[<span data-ttu-id="233df-151">資源</span><span class="sxs-lookup"><span data-stu-id="233df-151">Resources</span></span>](../resources/resources.md)
