---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: 3260b3d8333e8a79fdf603c372d1e3e50aa0dabc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205175"
---
# <span data-ttu-id="adfc9-102">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="adfc9-102">Disable-ExperimentalFeature</span></span>

## <span data-ttu-id="adfc9-103">概要</span><span class="sxs-lookup"><span data-stu-id="adfc9-103">SYNOPSIS</span></span>
<span data-ttu-id="adfc9-104">在啟動新的 PowerShell 實例時停用實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="adfc9-104">Disable an experimental feature on startup of new instance of PowerShell.</span></span>

## <span data-ttu-id="adfc9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="adfc9-105">SYNTAX</span></span>

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="adfc9-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="adfc9-106">DESCRIPTION</span></span>

<span data-ttu-id="adfc9-107">此 `Disable-ExperimentalFeature` Cmdlet 會從 `powershell.config.json` PowerShell 啟動時讀取的設定檔案中移除已命名的實驗性功能，以停用實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="adfc9-107">The `Disable-ExperimentalFeature` cmdlet disables experimental features by removing the named experimental features from the `powershell.config.json` settings file read on PowerShell startup.</span></span>

<span data-ttu-id="adfc9-108">此 Cmdlet 是在 PowerShell 6.2 中引進。</span><span class="sxs-lookup"><span data-stu-id="adfc9-108">This cmdlet was introduced in PowerShell 6.2.</span></span>

> [!NOTE]
> <span data-ttu-id="adfc9-109">實驗性功能狀態的任何變更只會在重新開機 PowerShell 時生效</span><span class="sxs-lookup"><span data-stu-id="adfc9-109">Any changes to experimental feature state only takes effect on restart of PowerShell</span></span>

## <span data-ttu-id="adfc9-110">範例</span><span class="sxs-lookup"><span data-stu-id="adfc9-110">EXAMPLES</span></span>

### <span data-ttu-id="adfc9-111">範例1：停用實驗性功能</span><span class="sxs-lookup"><span data-stu-id="adfc9-111">Example 1: Disable an experimental feature</span></span>

<span data-ttu-id="adfc9-112">在此範例中，如果先前已啟用此實驗性功能，則 `powershell.config.json` 會更新檔案，讓使用者在 PowerShell 重新開機後不啟用該功能。</span><span class="sxs-lookup"><span data-stu-id="adfc9-112">In this example, if this experimental feature was previously enabled, then the `powershell.config.json` file is updated for the user to not enable that feature once PowerShell is restarted.</span></span>
<span data-ttu-id="adfc9-113">成功時，不會對管線輸出任何內容，而且只會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="adfc9-113">Upon success nothing is output to the pipeline and only a warning message is displayed.</span></span>

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## <span data-ttu-id="adfc9-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="adfc9-114">PARAMETERS</span></span>

### <span data-ttu-id="adfc9-115">-Confirm</span><span class="sxs-lookup"><span data-stu-id="adfc9-115">-Confirm</span></span>

<span data-ttu-id="adfc9-116">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="adfc9-116">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="adfc9-117">-Name</span><span class="sxs-lookup"><span data-stu-id="adfc9-117">-Name</span></span>

<span data-ttu-id="adfc9-118">要停用之實驗性功能的名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="adfc9-118">The name or names of the experimental features to disable.</span></span>

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

### <span data-ttu-id="adfc9-119">-Scope</span><span class="sxs-lookup"><span data-stu-id="adfc9-119">-Scope</span></span>

<span data-ttu-id="adfc9-120">決定 `powershell.config.json` 是否要更新其是否會影響所有使用者，或只影響目前的使用者。</span><span class="sxs-lookup"><span data-stu-id="adfc9-120">Determines which `powershell.config.json` to update whether it affects all users or just the current user.</span></span>

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

### <span data-ttu-id="adfc9-121">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="adfc9-121">-WhatIf</span></span>

<span data-ttu-id="adfc9-122">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="adfc9-122">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="adfc9-123">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="adfc9-123">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="adfc9-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="adfc9-124">CommonParameters</span></span>

<span data-ttu-id="adfc9-125">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="adfc9-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="adfc9-126">如需詳細資訊，請參閱 [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="adfc9-126">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="adfc9-127">輸入</span><span class="sxs-lookup"><span data-stu-id="adfc9-127">INPUTS</span></span>

### <span data-ttu-id="adfc9-128">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="adfc9-128">ExperimentalFeature</span></span>

<span data-ttu-id="adfc9-129">將 ExperimentalFeature 的管道實例從 `Get-ExperimentalFeature` Cmdlet 傳送至停用。</span><span class="sxs-lookup"><span data-stu-id="adfc9-129">Pipe instances of ExperimentalFeature from `Get-ExperimentalFeature` cmdlet to disable.</span></span>

## <span data-ttu-id="adfc9-130">輸出</span><span class="sxs-lookup"><span data-stu-id="adfc9-130">OUTPUTS</span></span>

### <span data-ttu-id="adfc9-131">無</span><span class="sxs-lookup"><span data-stu-id="adfc9-131">None</span></span>

<span data-ttu-id="adfc9-132">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="adfc9-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="adfc9-133">注意</span><span class="sxs-lookup"><span data-stu-id="adfc9-133">NOTES</span></span>

<span data-ttu-id="adfc9-134">實驗性功能的狀態變更只會在重新開機 PowerShell 時生效。</span><span class="sxs-lookup"><span data-stu-id="adfc9-134">Changes to state of an experimental feature only take effect on restart of PowerShell.</span></span>

## <span data-ttu-id="adfc9-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="adfc9-135">RELATED LINKS</span></span>

[<span data-ttu-id="adfc9-136">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="adfc9-136">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

[<span data-ttu-id="adfc9-137">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="adfc9-137">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

