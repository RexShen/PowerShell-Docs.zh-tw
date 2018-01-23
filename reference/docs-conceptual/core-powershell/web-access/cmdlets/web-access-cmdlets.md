---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Web 存取 Cmdlet"
ms.technology: powershell
ms.openlocfilehash: 54821c318b165461ec613678a39c4e3b500dfd0e
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="windows-powershell-web-access-cmdlets"></a><span data-ttu-id="488d3-103">Windows PowerShell Web 存取 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="488d3-103">Windows PowerShell Web Access Cmdlets</span></span>

<span data-ttu-id="488d3-104">本參考文件提供所有 Windows PowerShell® Web 存取特定 Cmdlet 的 Cmdlet 說明和語法。</span><span class="sxs-lookup"><span data-stu-id="488d3-104">This reference provides cmdlet descriptions and syntax for all Windows PowerShell® Web Access-specific cmdlets.</span></span> <span data-ttu-id="488d3-105">Cmdlet 清單以 Cmdlet 開頭動詞的字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="488d3-105">It lists the cmdlets in alphabetical order based on the verb at the beginning of the cmdlet.</span></span>

## <a name="add-pswaauthorizationruleadd-pswaauthorizationrulemd"></a>[<span data-ttu-id="488d3-106">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="488d3-106">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)

<span data-ttu-id="488d3-107">在 Windows PowerShell® Web 存取授權規則集中新增授權規則。</span><span class="sxs-lookup"><span data-stu-id="488d3-107">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="get-pswaauthorizationruleget-pswaauthorizationrulemd"></a>[<span data-ttu-id="488d3-108">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="488d3-108">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)

<span data-ttu-id="488d3-109">傳回一組 Windows PowerShell Web 存取授權規則。</span><span class="sxs-lookup"><span data-stu-id="488d3-109">Returns a set of the Windows PowerShell Web Access authorization rules.</span></span>

## <a name="install-pswawebapplicationinstall-pswawebapplicationmd"></a>[<span data-ttu-id="488d3-110">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="488d3-110">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)

<span data-ttu-id="488d3-111">在 IIS 中設定 Windows PowerShell Web 存取 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="488d3-111">Configures the Windows PowerShell Web Access web application in IIS.</span></span>

## <a name="remove-pswaauthorizationruleremove-pswaauthorizationrulemd"></a>[<span data-ttu-id="488d3-112">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="488d3-112">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)

<span data-ttu-id="488d3-113">從 Windows PowerShell Web 存取中移除指定的授權規則。</span><span class="sxs-lookup"><span data-stu-id="488d3-113">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="test-pswaauthorizationruletest-pswaauthorizationrulemd"></a>[<span data-ttu-id="488d3-114">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="488d3-114">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)

<span data-ttu-id="488d3-115">測試授權規則，以驗證特定使用者、電腦、端點存取要求是否已獲授權。</span><span class="sxs-lookup"><span data-stu-id="488d3-115">Tests authorization rules to validate that a particular user, computer, endpoint access request is authorized.</span></span>

## <a name="uninstall-pswawebapplicationuninstall-pswawebapplicationmd"></a>[<span data-ttu-id="488d3-116">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="488d3-116">Uninstall-PswaWebApplication</span></span>](uninstall-pswawebapplication.md)

<span data-ttu-id="488d3-117">從 IIS 解除安裝 Windows PowerShell Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="488d3-117">Uninstalls the Windows PowerShell web application from IIS.</span></span>

><span data-ttu-id="488d3-118">**注意**：</span><span class="sxs-lookup"><span data-stu-id="488d3-118">**Note**:</span></span>
>
><span data-ttu-id="488d3-119">若要列出可用的所有 Cmdlet，請使用：</span><span class="sxs-lookup"><span data-stu-id="488d3-119">To list all the cmdlets that are available, use the:</span></span>
>
> <span data-ttu-id="488d3-120">`Get-Command –Module PowerShellWebAccess` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="488d3-120">`Get-Command –Module PowerShellWebAccess` cmdlet.</span></span>

<span data-ttu-id="488d3-121">如需任何 Cmdlet 的詳細資訊或語法，請使用：</span><span class="sxs-lookup"><span data-stu-id="488d3-121">For more information about, or for the syntax of, any of the cmdlets, use:</span></span>  
<span data-ttu-id="488d3-122">`Get-Help `*&lt;Cmdlet 名稱&gt;*</span><span class="sxs-lookup"><span data-stu-id="488d3-122">`Get-Help `*&lt;cmdlet name&gt;*</span></span>  
<span data-ttu-id="488d3-123">其中 &lt;Cmdlet 名稱&gt; 是您要查詢的 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="488d3-123">where *&lt;cmdlet name&gt;* is the name of the cmdlet that you want to research.</span></span>

<span data-ttu-id="488d3-124">如需詳細資訊，您可以執行下列任一個 Cmdlet：</span><span class="sxs-lookup"><span data-stu-id="488d3-124">For more detailed information, you can run any of the following cmdlets:</span></span>

- <span data-ttu-id="488d3-125">`Get-Help `&lt;Cmdlet 名稱&gt;` -Detailed`</span><span class="sxs-lookup"><span data-stu-id="488d3-125">`Get-Help `*&lt;cmdlet name&gt;*` -Detailed`</span></span>
- <span data-ttu-id="488d3-126">`Get-Help `&lt;Cmdlet 名稱&gt;` -Examples`</span><span class="sxs-lookup"><span data-stu-id="488d3-126">`Get-Help `*&lt;cmdlet name&gt;*` -Examples`</span></span>
- <span data-ttu-id="488d3-127">`Get-Help `&lt;Cmdlet 名稱&gt;` -Full`</span><span class="sxs-lookup"><span data-stu-id="488d3-127">`Get-Help `*&lt;cmdlet name&gt;*` -Full`</span></span>

### <a name="more-information"></a><span data-ttu-id="488d3-128">更多資訊</span><span class="sxs-lookup"><span data-stu-id="488d3-128">More Information</span></span>

<span data-ttu-id="488d3-129">如需 PowerShell Web 存取的詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="488d3-129">For more information about PowerShell Web Access, see the following:</span></span>

- [<span data-ttu-id="488d3-130">安裝和使用 Windows PowerShell Web 存取</span><span class="sxs-lookup"><span data-stu-id="488d3-130">Install and Use Windows PowerShell Web Access</span></span>](../install-and-use-windows-powershell-web-access.md)

