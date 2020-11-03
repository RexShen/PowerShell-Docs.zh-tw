---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 18a7163a2f67c22013fb607c3b90f3c350a0d797
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204372"
---
# <span data-ttu-id="b2888-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b2888-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="b2888-103">概要</span><span class="sxs-lookup"><span data-stu-id="b2888-103">SYNOPSIS</span></span>
<span data-ttu-id="b2888-104">取得實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="b2888-104">Gets experimental features.</span></span>

## <span data-ttu-id="b2888-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2888-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="b2888-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b2888-106">DESCRIPTION</span></span>

<span data-ttu-id="b2888-107">Cmdlet 會傳回 `Get-ExperimentalFeature` PowerShell 探索到的所有實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="b2888-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="b2888-108">實驗性功能可以來自模組或 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="b2888-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="b2888-109">實驗性功能可讓使用者安全地測試新功能，並提供意見反應 (通常會在設計被視為完成之前透過 GitHub) ，而且任何變更都可能會變成重大變更。</span><span class="sxs-lookup"><span data-stu-id="b2888-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="b2888-110">範例</span><span class="sxs-lookup"><span data-stu-id="b2888-110">EXAMPLES</span></span>

### <span data-ttu-id="b2888-111">範例 1</span><span class="sxs-lookup"><span data-stu-id="b2888-111">Example 1</span></span>

<span data-ttu-id="b2888-112">取得目前註冊的實驗性功能及其目前狀態的清單。</span><span class="sxs-lookup"><span data-stu-id="b2888-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="b2888-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2888-113">PARAMETERS</span></span>

### <span data-ttu-id="b2888-114">-Name</span><span class="sxs-lookup"><span data-stu-id="b2888-114">-Name</span></span>

<span data-ttu-id="b2888-115">要傳回之特定實驗性功能的名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="b2888-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2888-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2888-116">CommonParameters</span></span>

<span data-ttu-id="b2888-117">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b2888-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2888-118">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b2888-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2888-119">輸入</span><span class="sxs-lookup"><span data-stu-id="b2888-119">INPUTS</span></span>

### <span data-ttu-id="b2888-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b2888-120">System.String[]</span></span>

<span data-ttu-id="b2888-121">要傳回的實驗性功能名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="b2888-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="b2888-122">輸出</span><span class="sxs-lookup"><span data-stu-id="b2888-122">OUTPUTS</span></span>

### <span data-ttu-id="b2888-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b2888-123">ExperimentalFeature</span></span>

<span data-ttu-id="b2888-124">如果未指定名稱，則傳回符合所要求名稱或所有實驗性功能的實例。</span><span class="sxs-lookup"><span data-stu-id="b2888-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="b2888-125">注意</span><span class="sxs-lookup"><span data-stu-id="b2888-125">NOTES</span></span>

## <span data-ttu-id="b2888-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="b2888-126">RELATED LINKS</span></span>

[<span data-ttu-id="b2888-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b2888-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="b2888-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="b2888-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
