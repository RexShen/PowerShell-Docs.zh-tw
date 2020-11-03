---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0f1173cbfab139438d55ff49272f9625579820dc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201960"
---
# <span data-ttu-id="b5e0f-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5e0f-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="b5e0f-104">概要</span><span class="sxs-lookup"><span data-stu-id="b5e0f-104">SYNOPSIS</span></span>
<span data-ttu-id="b5e0f-105">取消註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-105">Unregisters a repository.</span></span>

## <span data-ttu-id="b5e0f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b5e0f-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="b5e0f-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="b5e0f-107">DESCRIPTION</span></span>

<span data-ttu-id="b5e0f-108">`Unregister-PSRepository`Cmdlet 會為目前使用者取消註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="b5e0f-109">範例</span><span class="sxs-lookup"><span data-stu-id="b5e0f-109">EXAMPLES</span></span>

### <span data-ttu-id="b5e0f-110">範例1：取消註冊存放庫</span><span class="sxs-lookup"><span data-stu-id="b5e0f-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="b5e0f-111">此範例會將名為 myNuGetSource 的存放庫取消註冊。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="b5e0f-112">範例2：取消註冊所有存放庫</span><span class="sxs-lookup"><span data-stu-id="b5e0f-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="b5e0f-113">這個範例會使用 `Get-PSRepository` 來取得所有已註冊的存放庫，並使用管線運算子將它們傳遞給以 `Unregister-PSRepository` 取消註冊它們。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="b5e0f-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b5e0f-114">PARAMETERS</span></span>

### <span data-ttu-id="b5e0f-115">-Name</span><span class="sxs-lookup"><span data-stu-id="b5e0f-115">-Name</span></span>

<span data-ttu-id="b5e0f-116">指定要移除之存放庫的名稱陣列。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-116">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="b5e0f-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b5e0f-117">CommonParameters</span></span>

<span data-ttu-id="b5e0f-118">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b5e0f-119">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="b5e0f-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b5e0f-120">輸入</span><span class="sxs-lookup"><span data-stu-id="b5e0f-120">INPUTS</span></span>

### <span data-ttu-id="b5e0f-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="b5e0f-121">System.String[]</span></span>

## <span data-ttu-id="b5e0f-122">輸出</span><span class="sxs-lookup"><span data-stu-id="b5e0f-122">OUTPUTS</span></span>

### <span data-ttu-id="b5e0f-123">System.Object</span><span class="sxs-lookup"><span data-stu-id="b5e0f-123">System.Object</span></span>

## <span data-ttu-id="b5e0f-124">注意</span><span class="sxs-lookup"><span data-stu-id="b5e0f-124">NOTES</span></span>

## <span data-ttu-id="b5e0f-125">相關連結</span><span class="sxs-lookup"><span data-stu-id="b5e0f-125">RELATED LINKS</span></span>

[<span data-ttu-id="b5e0f-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5e0f-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="b5e0f-127">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5e0f-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="b5e0f-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="b5e0f-128">Set-PSRepository</span></span>](Set-PSRepository.md)
