---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 0c94d249bec36ecb71ab4322d2d65e63209ec032
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204344"
---
# <span data-ttu-id="f9e00-102">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="f9e00-102">Enable-ExperimentalFeature</span></span>

## <span data-ttu-id="f9e00-103">概要</span><span class="sxs-lookup"><span data-stu-id="f9e00-103">SYNOPSIS</span></span>
<span data-ttu-id="f9e00-104">啟用新的 PowerShell 實例啟動時的實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="f9e00-104">Enable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="f9e00-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9e00-105">SYNTAX</span></span>

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f9e00-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f9e00-106">DESCRIPTION</span></span>

<span data-ttu-id="f9e00-107">此 `Enable-ExperimentalFeature` Cmdlet 會將名為的實驗性功能新增至 `powershell.config.json` 在 PowerShell 啟動時讀取的設定檔，藉以啟用實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="f9e00-107">The `Enable-ExperimentalFeature` cmdlet enables experimental features by adding the named experimental features to the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="f9e00-108">此 Cmdlet 是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="f9e00-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="f9e00-109">實驗性功能狀態的任何變更只會在重新開機 PowerShell 時生效</span><span class="sxs-lookup"><span data-stu-id="f9e00-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="f9e00-110">範例</span><span class="sxs-lookup"><span data-stu-id="f9e00-110">EXAMPLES</span></span>

### <span data-ttu-id="f9e00-111">範例1：啟用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="f9e00-111">Example 1: Enable an experimental feature</span></span>

<span data-ttu-id="f9e00-112">在此範例中，如果先前已停用此實驗性功能，則 `powershell.config.json` 會更新檔案，讓使用者在 PowerShell 重新開機後啟用該功能。</span><span class="sxs-lookup"><span data-stu-id="f9e00-112">In this example, if this experimental feature was previously disabled, then the `powershell.config.json` file is updated for the user to enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="f9e00-113">成功時，不會對管線輸出任何內容，而且只會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="f9e00-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="f9e00-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f9e00-114">PARAMETERS</span></span>

### <span data-ttu-id="f9e00-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f9e00-115">-Confirm</span></span>

<span data-ttu-id="f9e00-116">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="f9e00-116">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9e00-117">-Name</span><span class="sxs-lookup"><span data-stu-id="f9e00-117">-Name</span></span>

<span data-ttu-id="f9e00-118">要啟用之實驗性功能的名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="f9e00-118">The name or names of the experimental features to enable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f9e00-119">-Scope</span><span class="sxs-lookup"><span data-stu-id="f9e00-119">-Scope</span></span>

<span data-ttu-id="f9e00-120">決定 `powershell.config.json` 是否要更新其是否會影響所有使用者，或只影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="f9e00-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9e00-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f9e00-121">-WhatIf</span></span>

<span data-ttu-id="f9e00-122">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="f9e00-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f9e00-123">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="f9e00-123">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9e00-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9e00-124">CommonParameters</span></span>

<span data-ttu-id="f9e00-125">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f9e00-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9e00-126">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f9e00-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9e00-127">輸入</span><span class="sxs-lookup"><span data-stu-id="f9e00-127">INPUTS</span></span>

### <span data-ttu-id="f9e00-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="f9e00-128">ExperimentalFeature</span></span>

<span data-ttu-id="f9e00-129">將 ExperimentalFeature 的管道實例從 `Get-ExperimentalFeature` Cmdlet 傳送至啟用。</span><span class="sxs-lookup"><span data-stu-id="f9e00-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to enable.</span></span>

## <span data-ttu-id="f9e00-130">輸出</span><span class="sxs-lookup"><span data-stu-id="f9e00-130">OUTPUTS</span></span>

### <span data-ttu-id="f9e00-131">無</span><span class="sxs-lookup"><span data-stu-id="f9e00-131">None</span></span>

<span data-ttu-id="f9e00-132">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="f9e00-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="f9e00-133">注意</span><span class="sxs-lookup"><span data-stu-id="f9e00-133">NOTES</span></span>

<span data-ttu-id="f9e00-134">實驗性功能的狀態變更只會在重新開機 PowerShell 時生效。</span><span class="sxs-lookup"><span data-stu-id="f9e00-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="f9e00-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="f9e00-135">RELATED LINKS</span></span>

[<span data-ttu-id="f9e00-136">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="f9e00-136">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="f9e00-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="f9e00-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)
