---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204903"
---
# <span data-ttu-id="26dd9-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="26dd9-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="26dd9-103">概要</span><span class="sxs-lookup"><span data-stu-id="26dd9-103">SYNOPSIS</span></span>
<span data-ttu-id="26dd9-104">取得實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="26dd9-104">Gets experimental features.</span></span>

## <span data-ttu-id="26dd9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26dd9-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="26dd9-106">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="26dd9-106">DESCRIPTION</span></span>

<span data-ttu-id="26dd9-107">Cmdlet 會傳回 `Get-ExperimentalFeature` PowerShell 探索到的所有實驗性功能。</span><span class="sxs-lookup"><span data-stu-id="26dd9-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="26dd9-108">實驗性功能可以來自模組或 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="26dd9-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="26dd9-109">實驗性功能可讓使用者安全地測試新功能，並提供意見反應 (通常會在設計被視為完成之前透過 GitHub) ，而且任何變更都可能會變成重大變更。</span><span class="sxs-lookup"><span data-stu-id="26dd9-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="26dd9-110">範例</span><span class="sxs-lookup"><span data-stu-id="26dd9-110">EXAMPLES</span></span>

### <span data-ttu-id="26dd9-111">範例 1</span><span class="sxs-lookup"><span data-stu-id="26dd9-111">Example 1</span></span>

<span data-ttu-id="26dd9-112">取得目前註冊的實驗性功能及其目前狀態的清單。</span><span class="sxs-lookup"><span data-stu-id="26dd9-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="26dd9-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="26dd9-113">PARAMETERS</span></span>

### <span data-ttu-id="26dd9-114">-Name</span><span class="sxs-lookup"><span data-stu-id="26dd9-114">-Name</span></span>

<span data-ttu-id="26dd9-115">要傳回之特定實驗性功能的名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="26dd9-115">Name or names of specific experimental features to return.</span></span>

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

### <span data-ttu-id="26dd9-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26dd9-116">CommonParameters</span></span>

<span data-ttu-id="26dd9-117">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="26dd9-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26dd9-118">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="26dd9-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26dd9-119">輸入</span><span class="sxs-lookup"><span data-stu-id="26dd9-119">INPUTS</span></span>

### <span data-ttu-id="26dd9-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="26dd9-120">System.String[]</span></span>

<span data-ttu-id="26dd9-121">要傳回的實驗性功能名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="26dd9-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="26dd9-122">輸出</span><span class="sxs-lookup"><span data-stu-id="26dd9-122">OUTPUTS</span></span>

### <span data-ttu-id="26dd9-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="26dd9-123">ExperimentalFeature</span></span>

<span data-ttu-id="26dd9-124">如果未指定名稱，則傳回符合所要求名稱或所有實驗性功能的實例。</span><span class="sxs-lookup"><span data-stu-id="26dd9-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="26dd9-125">注意</span><span class="sxs-lookup"><span data-stu-id="26dd9-125">NOTES</span></span>

## <span data-ttu-id="26dd9-126">相關連結</span><span class="sxs-lookup"><span data-stu-id="26dd9-126">RELATED LINKS</span></span>

[<span data-ttu-id="26dd9-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="26dd9-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="26dd9-128">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="26dd9-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
