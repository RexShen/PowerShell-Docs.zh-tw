---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: cc94d85e48849d47531ac0a83527f3c68c21377e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204952"
---
# <span data-ttu-id="95e78-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="95e78-102">Enable-PSTrace</span></span>

## <span data-ttu-id="95e78-103">概要</span><span class="sxs-lookup"><span data-stu-id="95e78-103">SYNOPSIS</span></span>
<span data-ttu-id="95e78-104">啟用 Microsoft Windows-PowerShell 事件提供者記錄檔。</span><span class="sxs-lookup"><span data-stu-id="95e78-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="95e78-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95e78-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="95e78-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="95e78-106">DESCRIPTION</span></span>

<span data-ttu-id="95e78-107">此 Cmdlet 會啟用 Microsoft Windows-PowerShell 事件提供者的操作和分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="95e78-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="95e78-108">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95e78-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="95e78-109">範例</span><span class="sxs-lookup"><span data-stu-id="95e78-109">EXAMPLES</span></span>

### <span data-ttu-id="95e78-110">範例1：啟用 PowerShell 的分析事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="95e78-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="95e78-111">下列範例只會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="95e78-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="95e78-112">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="95e78-112">PARAMETERS</span></span>

### <span data-ttu-id="95e78-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="95e78-113">-AnalyticOnly</span></span>

<span data-ttu-id="95e78-114">使用這個參數時，此 Cmdlet 會啟用 Microsoft Windows PowerShell 提供者的分析事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="95e78-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="95e78-115">操作事件記錄檔不會變更。</span><span class="sxs-lookup"><span data-stu-id="95e78-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="95e78-116">-Force</span><span class="sxs-lookup"><span data-stu-id="95e78-116">-Force</span></span>

<span data-ttu-id="95e78-117">用來在不提示的情況下強制變更。</span><span class="sxs-lookup"><span data-stu-id="95e78-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="95e78-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95e78-118">CommonParameters</span></span>
<span data-ttu-id="95e78-119">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="95e78-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95e78-120">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="95e78-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95e78-121">輸入</span><span class="sxs-lookup"><span data-stu-id="95e78-121">INPUTS</span></span>

### <span data-ttu-id="95e78-122">無</span><span class="sxs-lookup"><span data-stu-id="95e78-122">None</span></span>

## <span data-ttu-id="95e78-123">輸出</span><span class="sxs-lookup"><span data-stu-id="95e78-123">OUTPUTS</span></span>

### <span data-ttu-id="95e78-124">無</span><span class="sxs-lookup"><span data-stu-id="95e78-124">None</span></span>

## <span data-ttu-id="95e78-125">注意</span><span class="sxs-lookup"><span data-stu-id="95e78-125">NOTES</span></span>

<span data-ttu-id="95e78-126">此 Cmdlet 會使用 `Get-LogProperties` 和 `Set-LogProperties` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95e78-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="95e78-127">您必須從已提升許可權的 PowerShell 會話執行此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="95e78-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="95e78-128">相關連結</span><span class="sxs-lookup"><span data-stu-id="95e78-128">RELATED LINKS</span></span>

[<span data-ttu-id="95e78-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="95e78-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="95e78-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="95e78-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="95e78-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="95e78-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)

