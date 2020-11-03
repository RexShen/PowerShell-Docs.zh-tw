---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 2a289500020f069231023fbabaa5401ee0759697
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "93200971"
---
# <span data-ttu-id="71e16-103">New-Guid</span><span class="sxs-lookup"><span data-stu-id="71e16-103">New-Guid</span></span>

## <span data-ttu-id="71e16-104">概要</span><span class="sxs-lookup"><span data-stu-id="71e16-104">SYNOPSIS</span></span>
<span data-ttu-id="71e16-105">建立 GUID。</span><span class="sxs-lookup"><span data-stu-id="71e16-105">Creates a GUID.</span></span>

## <span data-ttu-id="71e16-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="71e16-106">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="71e16-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="71e16-107">DESCRIPTION</span></span>

<span data-ttu-id="71e16-108">**New-Guid** Cmdlet 會建立一個隨機全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="71e16-108">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="71e16-109">如果您在指令碼中需要唯一識別碼，您可以視需要建立 GUID。</span><span class="sxs-lookup"><span data-stu-id="71e16-109">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="71e16-110">範例</span><span class="sxs-lookup"><span data-stu-id="71e16-110">EXAMPLES</span></span>

### <span data-ttu-id="71e16-111">範例 1︰建立 GUID</span><span class="sxs-lookup"><span data-stu-id="71e16-111">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="71e16-112">此命令會建立隨機的 GUID。</span><span class="sxs-lookup"><span data-stu-id="71e16-112">This command creates a random GUID.</span></span>
<span data-ttu-id="71e16-113">或者，您可以將此 Cmdlet 的輸出儲存於變數中，以在指令碼中的其他位置使用。</span><span class="sxs-lookup"><span data-stu-id="71e16-113">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="71e16-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="71e16-114">PARAMETERS</span></span>

### <span data-ttu-id="71e16-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="71e16-115">CommonParameters</span></span>

<span data-ttu-id="71e16-116">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="71e16-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="71e16-117">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="71e16-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="71e16-118">輸入</span><span class="sxs-lookup"><span data-stu-id="71e16-118">INPUTS</span></span>

## <span data-ttu-id="71e16-119">輸出</span><span class="sxs-lookup"><span data-stu-id="71e16-119">OUTPUTS</span></span>

### <span data-ttu-id="71e16-120">System.Guid</span><span class="sxs-lookup"><span data-stu-id="71e16-120">System.Guid</span></span>

<span data-ttu-id="71e16-121">這個 Cmdlet 會傳回 GUID。</span><span class="sxs-lookup"><span data-stu-id="71e16-121">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="71e16-122">注意</span><span class="sxs-lookup"><span data-stu-id="71e16-122">NOTES</span></span>

## <span data-ttu-id="71e16-123">相關連結</span><span class="sxs-lookup"><span data-stu-id="71e16-123">RELATED LINKS</span></span>

