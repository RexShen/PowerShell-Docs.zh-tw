---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 9abc91086d42ec7b813695e241820947f7fb0acc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203059"
---
# <span data-ttu-id="e1eaa-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="e1eaa-102">Enable-PSTrace</span></span>

## <span data-ttu-id="e1eaa-103">概要</span><span class="sxs-lookup"><span data-stu-id="e1eaa-103">SYNOPSIS</span></span>
<span data-ttu-id="e1eaa-104">啟用 Microsoft Windows-PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="e1eaa-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1eaa-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="e1eaa-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e1eaa-106">DESCRIPTION</span></span>

<span data-ttu-id="e1eaa-107">此 Cmdlet 會啟用 Microsoft Windows-PowerShell 事件提供者的操作和分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="e1eaa-108">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e1eaa-109">範例</span><span class="sxs-lookup"><span data-stu-id="e1eaa-109">EXAMPLES</span></span>

### <span data-ttu-id="e1eaa-110">範例1：啟用 PowerShell 的分析事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="e1eaa-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="e1eaa-111">下列範例只會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="e1eaa-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e1eaa-112">PARAMETERS</span></span>

### <span data-ttu-id="e1eaa-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="e1eaa-113">-AnalyticOnly</span></span>

<span data-ttu-id="e1eaa-114">使用這個參數時，此 Cmdlet 會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="e1eaa-115">操作事件記錄檔不會變更。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-115">The Operational event log is not changed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e1eaa-116">-Force</span><span class="sxs-lookup"><span data-stu-id="e1eaa-116">-Force</span></span>

<span data-ttu-id="e1eaa-117">用來在不提示的情況下強制變更。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-117">Used to force the change without prompting.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## <span data-ttu-id="e1eaa-118">輸入</span><span class="sxs-lookup"><span data-stu-id="e1eaa-118">INPUTS</span></span>

### <span data-ttu-id="e1eaa-119">無</span><span class="sxs-lookup"><span data-stu-id="e1eaa-119">None</span></span>

## <span data-ttu-id="e1eaa-120">輸出</span><span class="sxs-lookup"><span data-stu-id="e1eaa-120">OUTPUTS</span></span>

### <span data-ttu-id="e1eaa-121">System.Object</span><span class="sxs-lookup"><span data-stu-id="e1eaa-121">System.Object</span></span>

## <span data-ttu-id="e1eaa-122">注意</span><span class="sxs-lookup"><span data-stu-id="e1eaa-122">NOTES</span></span>

<span data-ttu-id="e1eaa-123">此 Cmdlet 會使用 `Get-LogProperties` 和 `Set-LogProperties` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="e1eaa-124">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e1eaa-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="e1eaa-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="e1eaa-125">RELATED LINKS</span></span>

[<span data-ttu-id="e1eaa-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="e1eaa-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="e1eaa-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="e1eaa-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="e1eaa-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="e1eaa-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)
