---
description: 列出專為搭配 PowerShell 提供者使用而設計的 Cmdlet。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 3391dce21cec5080020640be75e4c4df9da0c812
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93208079"
---
# <a name="about-core-commands"></a><span data-ttu-id="eb438-104">關於核心命令</span><span class="sxs-lookup"><span data-stu-id="eb438-104">About Core Commands</span></span>

## <a name="short-description"></a><span data-ttu-id="eb438-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="eb438-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="eb438-106">列出專為搭配 PowerShell 提供者使用而設計的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eb438-106">Lists the cmdlets that are designed for use with PowerShell providers.</span></span>

## <a name="long-description"></a><span data-ttu-id="eb438-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="eb438-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="eb438-108">PowerShell 包含一組 Cmdlet，專門設計來管理 Windows PowerShell 提供者所公開之資料存放區中的專案。</span><span class="sxs-lookup"><span data-stu-id="eb438-108">PowerShell includes a set of cmdlets that are specifically designed to manage the items in the data stores that are exposed by Windows PowerShell providers.</span></span>
<span data-ttu-id="eb438-109">您可以用相同的方式使用這些 Cmdlet 來管理提供者提供給您的所有不同資料類型。</span><span class="sxs-lookup"><span data-stu-id="eb438-109">You can use these cmdlets in the same ways to manage all the different types of data that the providers make available to you.</span></span> <span data-ttu-id="eb438-110">如需提供者的詳細資訊，請輸入 "get-help about_providers"。</span><span class="sxs-lookup"><span data-stu-id="eb438-110">For more information about providers, type "get-help about_providers".</span></span>

<span data-ttu-id="eb438-111">例如，您可以使用 Get-ChildItem Cmdlet 列出檔案系統目錄中的檔案、登錄機碼底下的機碼，或您撰寫或下載的提供者所公開的專案。</span><span class="sxs-lookup"><span data-stu-id="eb438-111">For example, you can use the Get-ChildItem cmdlet to list the files in a file system directory, the keys under a registry key, or the items that are exposed by a provider that you write or download.</span></span>

<span data-ttu-id="eb438-112">以下是專為與提供者搭配使用而設計的 PowerShell Cmdlet 清單：</span><span class="sxs-lookup"><span data-stu-id="eb438-112">The following is a list of the PowerShell cmdlets that are designed for use with providers:</span></span>

<span data-ttu-id="eb438-113">Get-childitem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-113">ChildItem cmdlets</span></span>

- <span data-ttu-id="eb438-114">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="eb438-114">Get-ChildItem</span></span>

<span data-ttu-id="eb438-115">Content Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-115">Content cmdlets</span></span>

- <span data-ttu-id="eb438-116">Add-Content</span><span class="sxs-lookup"><span data-stu-id="eb438-116">Add-Content</span></span>
- <span data-ttu-id="eb438-117">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="eb438-117">Clear-Content</span></span>
- <span data-ttu-id="eb438-118">Get-Content</span><span class="sxs-lookup"><span data-stu-id="eb438-118">Get-Content</span></span>
- <span data-ttu-id="eb438-119">Set-Content</span><span class="sxs-lookup"><span data-stu-id="eb438-119">Set-Content</span></span>

<span data-ttu-id="eb438-120">Item Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-120">Item cmdlets</span></span>

- <span data-ttu-id="eb438-121">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-121">Clear-Item</span></span>
- <span data-ttu-id="eb438-122">Copy-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-122">Copy-Item</span></span>
- <span data-ttu-id="eb438-123">Get-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-123">Get-Item</span></span>
- <span data-ttu-id="eb438-124">Invoke-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-124">Invoke-Item</span></span>
- <span data-ttu-id="eb438-125">Move-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-125">Move-Item</span></span>
- <span data-ttu-id="eb438-126">New-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-126">New-Item</span></span>
- <span data-ttu-id="eb438-127">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-127">Remove-Item</span></span>
- <span data-ttu-id="eb438-128">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-128">Rename-Item</span></span>
- <span data-ttu-id="eb438-129">Set-Item</span><span class="sxs-lookup"><span data-stu-id="eb438-129">Set-Item</span></span>

<span data-ttu-id="eb438-130">ItemProperty Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-130">ItemProperty cmdlets</span></span>

- <span data-ttu-id="eb438-131">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-131">Clear-ItemProperty</span></span>
- <span data-ttu-id="eb438-132">Copy-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-132">Copy-ItemProperty</span></span>
- <span data-ttu-id="eb438-133">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-133">Get-ItemProperty</span></span>
- <span data-ttu-id="eb438-134">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-134">Move-ItemProperty</span></span>
- <span data-ttu-id="eb438-135">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-135">New-ItemProperty</span></span>
- <span data-ttu-id="eb438-136">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-136">Remove-ItemProperty</span></span>
- <span data-ttu-id="eb438-137">Rename-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-137">Rename-ItemProperty</span></span>
- <span data-ttu-id="eb438-138">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="eb438-138">Set-ItemProperty</span></span>

<span data-ttu-id="eb438-139">Location Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-139">Location cmdlets</span></span>

- <span data-ttu-id="eb438-140">Get-Location</span><span class="sxs-lookup"><span data-stu-id="eb438-140">Get-Location</span></span>
- <span data-ttu-id="eb438-141">Pop-Location</span><span class="sxs-lookup"><span data-stu-id="eb438-141">Pop-Location</span></span>
- <span data-ttu-id="eb438-142">Push-Location</span><span class="sxs-lookup"><span data-stu-id="eb438-142">Push-Location</span></span>
- <span data-ttu-id="eb438-143">Set-Location</span><span class="sxs-lookup"><span data-stu-id="eb438-143">Set-Location</span></span>

<span data-ttu-id="eb438-144">路徑 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-144">Path cmdlets</span></span>

- <span data-ttu-id="eb438-145">Join-Path</span><span class="sxs-lookup"><span data-stu-id="eb438-145">Join-Path</span></span>
- <span data-ttu-id="eb438-146">Convert-Path</span><span class="sxs-lookup"><span data-stu-id="eb438-146">Convert-Path</span></span>
- <span data-ttu-id="eb438-147">Split-Path</span><span class="sxs-lookup"><span data-stu-id="eb438-147">Split-Path</span></span>
- <span data-ttu-id="eb438-148">Resolve-Path</span><span class="sxs-lookup"><span data-stu-id="eb438-148">Resolve-Path</span></span>
- <span data-ttu-id="eb438-149">Test-Path</span><span class="sxs-lookup"><span data-stu-id="eb438-149">Test-Path</span></span>

<span data-ttu-id="eb438-150">New-psdrive Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-150">PSDrive cmdlets</span></span>

- <span data-ttu-id="eb438-151">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb438-151">Get-PSDrive</span></span>
- <span data-ttu-id="eb438-152">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb438-152">New-PSDrive</span></span>
- <span data-ttu-id="eb438-153">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="eb438-153">Remove-PSDrive</span></span>

<span data-ttu-id="eb438-154">PSProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="eb438-154">PSProvider cmdlets</span></span>

- <span data-ttu-id="eb438-155">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="eb438-155">Get-PSProvider</span></span>

<span data-ttu-id="eb438-156">如需有關 Cmdlet 的詳細資訊，請輸入 `get-help <cmdlet-name>` 。</span><span class="sxs-lookup"><span data-stu-id="eb438-156">For more information about a cmdlet, type `get-help <cmdlet-name>`.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb438-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb438-157">SEE ALSO</span></span>

[<span data-ttu-id="eb438-158">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eb438-158">about_Providers</span></span>](about_Providers.md)
