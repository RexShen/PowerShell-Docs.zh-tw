---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 1922824a646e52238278612d3db5ce07624aae21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204955"
---
# <span data-ttu-id="8b0f0-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="8b0f0-102">Disable-PSTrace</span></span>

## <span data-ttu-id="8b0f0-103">概要</span><span class="sxs-lookup"><span data-stu-id="8b0f0-103">SYNOPSIS</span></span>
<span data-ttu-id="8b0f0-104">停用 Microsoft Windows PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="8b0f0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b0f0-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="8b0f0-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8b0f0-106">DESCRIPTION</span></span>

<span data-ttu-id="8b0f0-107">此 Cmdlet 會停用 Microsoft Windows-PowerShell 事件提供者的操作和分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="8b0f0-108">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="8b0f0-109">範例</span><span class="sxs-lookup"><span data-stu-id="8b0f0-109">EXAMPLES</span></span>

### <span data-ttu-id="8b0f0-110">範例1：停用 PowerShell 的分析事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="8b0f0-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="8b0f0-111">下列範例只會停用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="8b0f0-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8b0f0-112">PARAMETERS</span></span>

### <span data-ttu-id="8b0f0-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="8b0f0-113">-AnalyticOnly</span></span>

<span data-ttu-id="8b0f0-114">使用這個參數時，此 Cmdlet 會停用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="8b0f0-115">操作事件記錄檔不會變更。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="8b0f0-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b0f0-116">CommonParameters</span></span>
<span data-ttu-id="8b0f0-117">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b0f0-118">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b0f0-119">輸入</span><span class="sxs-lookup"><span data-stu-id="8b0f0-119">INPUTS</span></span>

### <span data-ttu-id="8b0f0-120">無</span><span class="sxs-lookup"><span data-stu-id="8b0f0-120">None</span></span>

## <span data-ttu-id="8b0f0-121">輸出</span><span class="sxs-lookup"><span data-stu-id="8b0f0-121">OUTPUTS</span></span>

### <span data-ttu-id="8b0f0-122">無</span><span class="sxs-lookup"><span data-stu-id="8b0f0-122">None</span></span>

## <span data-ttu-id="8b0f0-123">注意</span><span class="sxs-lookup"><span data-stu-id="8b0f0-123">NOTES</span></span>

<span data-ttu-id="8b0f0-124">此 Cmdlet 會使用 `Get-LogProperties` 和 `Set-LogProperties` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="8b0f0-125">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8b0f0-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="8b0f0-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="8b0f0-126">RELATED LINKS</span></span>

[<span data-ttu-id="8b0f0-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="8b0f0-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="8b0f0-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="8b0f0-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="8b0f0-129">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="8b0f0-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)

