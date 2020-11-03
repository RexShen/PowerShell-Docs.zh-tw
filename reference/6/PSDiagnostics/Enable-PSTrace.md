---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: d5008d5105b18b5a3d0423cab4282735e3d382d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202528"
---
# <span data-ttu-id="bafba-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="bafba-102">Enable-PSTrace</span></span>

## <span data-ttu-id="bafba-103">概要</span><span class="sxs-lookup"><span data-stu-id="bafba-103">SYNOPSIS</span></span>
<span data-ttu-id="bafba-104">啟用 Microsoft Windows-PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bafba-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="bafba-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bafba-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="bafba-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bafba-106">DESCRIPTION</span></span>

<span data-ttu-id="bafba-107">此 Cmdlet 會啟用 Microsoft Windows-PowerShell 事件提供者的操作和分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bafba-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="bafba-108">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bafba-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="bafba-109">範例</span><span class="sxs-lookup"><span data-stu-id="bafba-109">EXAMPLES</span></span>

### <span data-ttu-id="bafba-110">範例1：啟用 PowerShell 的分析事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="bafba-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="bafba-111">下列範例只會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bafba-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="bafba-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bafba-112">PARAMETERS</span></span>

### <span data-ttu-id="bafba-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="bafba-113">-AnalyticOnly</span></span>

<span data-ttu-id="bafba-114">使用這個參數時，此 Cmdlet 會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="bafba-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="bafba-115">操作事件記錄檔不會變更。</span><span class="sxs-lookup"><span data-stu-id="bafba-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="bafba-116">-Force</span><span class="sxs-lookup"><span data-stu-id="bafba-116">-Force</span></span>

<span data-ttu-id="bafba-117">用來在不提示的情況下強制變更。</span><span class="sxs-lookup"><span data-stu-id="bafba-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="bafba-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bafba-118">CommonParameters</span></span>
<span data-ttu-id="bafba-119">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bafba-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bafba-120">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="bafba-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bafba-121">輸入</span><span class="sxs-lookup"><span data-stu-id="bafba-121">INPUTS</span></span>

### <span data-ttu-id="bafba-122">無</span><span class="sxs-lookup"><span data-stu-id="bafba-122">None</span></span>

## <span data-ttu-id="bafba-123">輸出</span><span class="sxs-lookup"><span data-stu-id="bafba-123">OUTPUTS</span></span>

### <span data-ttu-id="bafba-124">無</span><span class="sxs-lookup"><span data-stu-id="bafba-124">None</span></span>

## <span data-ttu-id="bafba-125">注意</span><span class="sxs-lookup"><span data-stu-id="bafba-125">NOTES</span></span>

<span data-ttu-id="bafba-126">此 Cmdlet 會使用 `Get-LogProperties` 和 `Set-LogProperties` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bafba-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="bafba-127">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bafba-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="bafba-128">相關連結</span><span class="sxs-lookup"><span data-stu-id="bafba-128">RELATED LINKS</span></span>

[<span data-ttu-id="bafba-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="bafba-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="bafba-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="bafba-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="bafba-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="bafba-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
