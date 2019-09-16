---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: 附錄 1 相容性別名
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 00083f07b13c73b86936e7d7307397df27c63c04
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848175"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="965f0-103">附錄 1 - 相容性別名</span><span class="sxs-lookup"><span data-stu-id="965f0-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="965f0-104">PowerShell 有數個別名，可讓 **UNIX** 和 **cmd.exe** 使用者使用熟悉的命令。</span><span class="sxs-lookup"><span data-stu-id="965f0-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="965f0-105">下表顯示命令及其相關的 PowerShell Cmdlet 和 PowerShell 別名：</span><span class="sxs-lookup"><span data-stu-id="965f0-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="965f0-106">cmd.exe 命令</span><span class="sxs-lookup"><span data-stu-id="965f0-106">cmd.exe command</span></span>|<span data-ttu-id="965f0-107">UNIX 命令</span><span class="sxs-lookup"><span data-stu-id="965f0-107">UNIX command</span></span>|<span data-ttu-id="965f0-108">PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="965f0-108">PowerShell cmdlet</span></span>|<span data-ttu-id="965f0-109">PowerShell 別名</span><span class="sxs-lookup"><span data-stu-id="965f0-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="965f0-110">**cls**</span><span class="sxs-lookup"><span data-stu-id="965f0-110">**cls**</span></span>|<span data-ttu-id="965f0-111">**clear**</span><span class="sxs-lookup"><span data-stu-id="965f0-111">**clear**</span></span>|<span data-ttu-id="965f0-112">`Clear-Host` (函式)</span><span class="sxs-lookup"><span data-stu-id="965f0-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="965f0-113">**copy**</span><span class="sxs-lookup"><span data-stu-id="965f0-113">**copy**</span></span>|<span data-ttu-id="965f0-114">**cp**</span><span class="sxs-lookup"><span data-stu-id="965f0-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="965f0-115">**dir**</span><span class="sxs-lookup"><span data-stu-id="965f0-115">**dir**</span></span>|<span data-ttu-id="965f0-116">**ls**</span><span class="sxs-lookup"><span data-stu-id="965f0-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="965f0-117">**type**</span><span class="sxs-lookup"><span data-stu-id="965f0-117">**type**</span></span>|<span data-ttu-id="965f0-118">**cat**</span><span class="sxs-lookup"><span data-stu-id="965f0-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="965f0-119">**move**</span><span class="sxs-lookup"><span data-stu-id="965f0-119">**move**</span></span>|<span data-ttu-id="965f0-120">**mv**</span><span class="sxs-lookup"><span data-stu-id="965f0-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="965f0-121">**md**</span><span class="sxs-lookup"><span data-stu-id="965f0-121">**md**</span></span>|<span data-ttu-id="965f0-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="965f0-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="965f0-123">**pushd**</span><span class="sxs-lookup"><span data-stu-id="965f0-123">**pushd**</span></span>|<span data-ttu-id="965f0-124">**pushd**</span><span class="sxs-lookup"><span data-stu-id="965f0-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="965f0-125">**popd**</span><span class="sxs-lookup"><span data-stu-id="965f0-125">**popd**</span></span>|<span data-ttu-id="965f0-126">**popd**</span><span class="sxs-lookup"><span data-stu-id="965f0-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="965f0-127">**del**、**erase**、**rd**、**rmdir**</span><span class="sxs-lookup"><span data-stu-id="965f0-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="965f0-128">**rm**</span><span class="sxs-lookup"><span data-stu-id="965f0-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="965f0-129">**ren**</span><span class="sxs-lookup"><span data-stu-id="965f0-129">**ren**</span></span>|<span data-ttu-id="965f0-130">**mv**</span><span class="sxs-lookup"><span data-stu-id="965f0-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="965f0-131">**cd**、**chdir**</span><span class="sxs-lookup"><span data-stu-id="965f0-131">**cd**, **chdir**</span></span>|<span data-ttu-id="965f0-132">**cd**</span><span class="sxs-lookup"><span data-stu-id="965f0-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="965f0-133">若要尋找 PowerShell 別名，請使用 [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="965f0-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="965f0-134">若要顯示 Cmdlet 的別名，請使用 **Definition** 參數並指定 Cmdlet 名稱。</span><span class="sxs-lookup"><span data-stu-id="965f0-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="965f0-135">或者，若要尋找別名的 Cmdlet 名稱，請使用 **Name** 參數並指定別名。</span><span class="sxs-lookup"><span data-stu-id="965f0-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
