---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: 附錄 1 相容性別名
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758494"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="2584e-103">附錄 1 - 相容性別名</span><span class="sxs-lookup"><span data-stu-id="2584e-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="2584e-104">PowerShell 有數個別名，可讓 **UNIX** 和 **cmd.exe** 使用者使用熟悉的命令。</span><span class="sxs-lookup"><span data-stu-id="2584e-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="2584e-105">下表顯示命令及其相關的 PowerShell Cmdlet 和 PowerShell 別名：</span><span class="sxs-lookup"><span data-stu-id="2584e-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="2584e-106">cmd.exe 命令</span><span class="sxs-lookup"><span data-stu-id="2584e-106">cmd.exe command</span></span>            | <span data-ttu-id="2584e-107">UNIX 命令</span><span class="sxs-lookup"><span data-stu-id="2584e-107">UNIX command</span></span> | <span data-ttu-id="2584e-108">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2584e-108">PowerShell cmdlet</span></span> | <span data-ttu-id="2584e-109">PowerShell 別名</span><span class="sxs-lookup"><span data-stu-id="2584e-109">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="2584e-110">**cd**、**chdir**</span><span class="sxs-lookup"><span data-stu-id="2584e-110">**cd**, **chdir**</span></span>                     | <span data-ttu-id="2584e-111">**cd**</span><span class="sxs-lookup"><span data-stu-id="2584e-111">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="2584e-112">**cls**</span><span class="sxs-lookup"><span data-stu-id="2584e-112">**cls**</span></span>                               | <span data-ttu-id="2584e-113">**清除**</span><span class="sxs-lookup"><span data-stu-id="2584e-113">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="2584e-114">**copy**</span><span class="sxs-lookup"><span data-stu-id="2584e-114">**copy**</span></span>                              | <span data-ttu-id="2584e-115">**cp**</span><span class="sxs-lookup"><span data-stu-id="2584e-115">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="2584e-116">**del**、**erase**、**rd**、**rmdir**</span><span class="sxs-lookup"><span data-stu-id="2584e-116">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="2584e-117">**rm**</span><span class="sxs-lookup"><span data-stu-id="2584e-117">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="2584e-118">**dir**</span><span class="sxs-lookup"><span data-stu-id="2584e-118">**dir**</span></span>                               | <span data-ttu-id="2584e-119">**ls**</span><span class="sxs-lookup"><span data-stu-id="2584e-119">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="2584e-120">**echo**</span><span class="sxs-lookup"><span data-stu-id="2584e-120">**echo**</span></span>                              | <span data-ttu-id="2584e-121">**echo**</span><span class="sxs-lookup"><span data-stu-id="2584e-121">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="2584e-122">**md**</span><span class="sxs-lookup"><span data-stu-id="2584e-122">**md**</span></span>                                | <span data-ttu-id="2584e-123">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="2584e-123">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="2584e-124">**move**</span><span class="sxs-lookup"><span data-stu-id="2584e-124">**move**</span></span>                              | <span data-ttu-id="2584e-125">**mv**</span><span class="sxs-lookup"><span data-stu-id="2584e-125">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="2584e-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="2584e-126">**popd**</span></span>                              | <span data-ttu-id="2584e-127">**popd**</span><span class="sxs-lookup"><span data-stu-id="2584e-127">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="2584e-128">**pushd**</span><span class="sxs-lookup"><span data-stu-id="2584e-128">**pushd**</span></span>                             | <span data-ttu-id="2584e-129">**pushd**</span><span class="sxs-lookup"><span data-stu-id="2584e-129">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="2584e-130">**ren**</span><span class="sxs-lookup"><span data-stu-id="2584e-130">**ren**</span></span>                               | <span data-ttu-id="2584e-131">**mv**</span><span class="sxs-lookup"><span data-stu-id="2584e-131">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="2584e-132">**type**</span><span class="sxs-lookup"><span data-stu-id="2584e-132">**type**</span></span>                              | <span data-ttu-id="2584e-133">**cat**</span><span class="sxs-lookup"><span data-stu-id="2584e-133">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="2584e-134">若要尋找 PowerShell 別名，請使用 [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="2584e-134">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="2584e-135">若要顯示 Cmdlet 的別名，請使用 **Definition** 參數並指定 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="2584e-135">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="2584e-136">或者，若要尋找別名的 Cmdlet 名稱，請使用 **Name** 參數並指定別名。</span><span class="sxs-lookup"><span data-stu-id="2584e-136">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
