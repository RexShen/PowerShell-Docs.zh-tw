---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 附錄 1 相容性別名
description: PowerShell 有數個別名，可讓 UNIX 和 cmd.exe 使用者使用熟悉的命令。
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500737"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="09f7c-104">附錄 1 - 相容性別名</span><span class="sxs-lookup"><span data-stu-id="09f7c-104">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="09f7c-105">PowerShell 有數個別名，可讓 **UNIX** 和 **cmd.exe** 使用者使用熟悉的命令。</span><span class="sxs-lookup"><span data-stu-id="09f7c-105">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="09f7c-106">下表顯示命令及其相關的 PowerShell Cmdlet 和 PowerShell 別名：</span><span class="sxs-lookup"><span data-stu-id="09f7c-106">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="09f7c-107">cmd.exe 命令</span><span class="sxs-lookup"><span data-stu-id="09f7c-107">cmd.exe command</span></span>            | <span data-ttu-id="09f7c-108">UNIX 命令</span><span class="sxs-lookup"><span data-stu-id="09f7c-108">UNIX command</span></span> | <span data-ttu-id="09f7c-109">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="09f7c-109">PowerShell cmdlet</span></span> | <span data-ttu-id="09f7c-110">PowerShell 別名</span><span class="sxs-lookup"><span data-stu-id="09f7c-110">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="09f7c-111">**cd** 、 **chdir**</span><span class="sxs-lookup"><span data-stu-id="09f7c-111">**cd** , **chdir**</span></span>                     | <span data-ttu-id="09f7c-112">**cd**</span><span class="sxs-lookup"><span data-stu-id="09f7c-112">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="09f7c-113">**cls**</span><span class="sxs-lookup"><span data-stu-id="09f7c-113">**cls**</span></span>                               | <span data-ttu-id="09f7c-114">**清除**</span><span class="sxs-lookup"><span data-stu-id="09f7c-114">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="09f7c-115">**copy**</span><span class="sxs-lookup"><span data-stu-id="09f7c-115">**copy**</span></span>                              | <span data-ttu-id="09f7c-116">**cp**</span><span class="sxs-lookup"><span data-stu-id="09f7c-116">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="09f7c-117">**del** 、 **erase** 、 **rd** 、 **rmdir**</span><span class="sxs-lookup"><span data-stu-id="09f7c-117">**del** , **erase** , **rd** , **rmdir**</span></span> | <span data-ttu-id="09f7c-118">**rm**</span><span class="sxs-lookup"><span data-stu-id="09f7c-118">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="09f7c-119">**dir**</span><span class="sxs-lookup"><span data-stu-id="09f7c-119">**dir**</span></span>                               | <span data-ttu-id="09f7c-120">**ls**</span><span class="sxs-lookup"><span data-stu-id="09f7c-120">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="09f7c-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="09f7c-121">**echo**</span></span>                              | <span data-ttu-id="09f7c-122">**echo**</span><span class="sxs-lookup"><span data-stu-id="09f7c-122">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="09f7c-123">**md**</span><span class="sxs-lookup"><span data-stu-id="09f7c-123">**md**</span></span>                                | <span data-ttu-id="09f7c-124">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="09f7c-124">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="09f7c-125">**move**</span><span class="sxs-lookup"><span data-stu-id="09f7c-125">**move**</span></span>                              | <span data-ttu-id="09f7c-126">**mv**</span><span class="sxs-lookup"><span data-stu-id="09f7c-126">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="09f7c-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="09f7c-127">**popd**</span></span>                              | <span data-ttu-id="09f7c-128">**popd**</span><span class="sxs-lookup"><span data-stu-id="09f7c-128">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="09f7c-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="09f7c-129">**pushd**</span></span>                             | <span data-ttu-id="09f7c-130">**pushd**</span><span class="sxs-lookup"><span data-stu-id="09f7c-130">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="09f7c-131">**ren**</span><span class="sxs-lookup"><span data-stu-id="09f7c-131">**ren**</span></span>                               | <span data-ttu-id="09f7c-132">**mv**</span><span class="sxs-lookup"><span data-stu-id="09f7c-132">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="09f7c-133">**type**</span><span class="sxs-lookup"><span data-stu-id="09f7c-133">**type**</span></span>                              | <span data-ttu-id="09f7c-134">**cat**</span><span class="sxs-lookup"><span data-stu-id="09f7c-134">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="09f7c-135">若要尋找 PowerShell 別名，請使用 [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="09f7c-135">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="09f7c-136">若要顯示 Cmdlet 的別名，請使用 **Definition** 參數並指定 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="09f7c-136">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="09f7c-137">或者，若要尋找別名的 Cmdlet 名稱，請使用 **Name** 參數並指定別名。</span><span class="sxs-lookup"><span data-stu-id="09f7c-137">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
