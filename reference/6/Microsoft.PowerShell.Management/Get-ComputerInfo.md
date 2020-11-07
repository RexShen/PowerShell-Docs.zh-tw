---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: d0bf17b4bdc169661cf4cde878739287d8be668b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343978"
---
# <span data-ttu-id="0b206-103">Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="0b206-103">Get-ComputerInfo</span></span>

## <span data-ttu-id="0b206-104">概要</span><span class="sxs-lookup"><span data-stu-id="0b206-104">SYNOPSIS</span></span>
<span data-ttu-id="0b206-105">取得系統和作業系統屬性的合併物件。</span><span class="sxs-lookup"><span data-stu-id="0b206-105">Gets a consolidated object of system and operating system properties.</span></span>

## <span data-ttu-id="0b206-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0b206-106">SYNTAX</span></span>

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0b206-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="0b206-107">DESCRIPTION</span></span>

<span data-ttu-id="0b206-108">`Get-ComputerInfo`Cmdlet 會取得系統和作業系統屬性的合併物件。</span><span class="sxs-lookup"><span data-stu-id="0b206-108">The `Get-ComputerInfo` cmdlet gets a consolidated object of system and operating system properties.</span></span>
<span data-ttu-id="0b206-109">此 Cmdlet 是在 Windows PowerShell 5.1 中引進。</span><span class="sxs-lookup"><span data-stu-id="0b206-109">This cmdlet was introduced in Windows PowerShell 5.1.</span></span>

## <span data-ttu-id="0b206-110">範例</span><span class="sxs-lookup"><span data-stu-id="0b206-110">EXAMPLES</span></span>

### <span data-ttu-id="0b206-111">範例1：取得所有電腦屬性</span><span class="sxs-lookup"><span data-stu-id="0b206-111">Example 1: Get all computer properties</span></span>

```powershell
Get-ComputerInfo
```

<span data-ttu-id="0b206-112">此命令會從電腦取得所有系統和作業系統屬性。</span><span class="sxs-lookup"><span data-stu-id="0b206-112">This command gets all system and operating system properties from the computer.</span></span>

### <span data-ttu-id="0b206-113">範例2：取得所有電腦作業系統屬性</span><span class="sxs-lookup"><span data-stu-id="0b206-113">Example 2: Get all computer operating system properties</span></span>

```powershell
Get-ComputerInfo -Property "os*"
```

<span data-ttu-id="0b206-114">此命令會從電腦取得所有的作業系統屬性。</span><span class="sxs-lookup"><span data-stu-id="0b206-114">This command gets all operating system properties from the computer.</span></span>

## <span data-ttu-id="0b206-115">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0b206-115">PARAMETERS</span></span>

### <span data-ttu-id="0b206-116">-Property</span><span class="sxs-lookup"><span data-stu-id="0b206-116">-Property</span></span>

<span data-ttu-id="0b206-117">以字串陣列指定此 Cmdlet 所顯示的電腦屬性。</span><span class="sxs-lookup"><span data-stu-id="0b206-117">Specifies, as a string array, the computer properties in which this cmdlet displays.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0b206-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b206-118">CommonParameters</span></span>

<span data-ttu-id="0b206-119">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="0b206-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b206-120">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="0b206-120">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0b206-121">輸入</span><span class="sxs-lookup"><span data-stu-id="0b206-121">INPUTS</span></span>

### <span data-ttu-id="0b206-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0b206-122">System.String[]</span></span>

## <span data-ttu-id="0b206-123">輸出</span><span class="sxs-lookup"><span data-stu-id="0b206-123">OUTPUTS</span></span>

### <span data-ttu-id="0b206-124">Get-computerinfo。</span><span class="sxs-lookup"><span data-stu-id="0b206-124">Microsoft.PowerShell.Management.ComputerInfo</span></span>

## <span data-ttu-id="0b206-125">注意</span><span class="sxs-lookup"><span data-stu-id="0b206-125">NOTES</span></span>

<span data-ttu-id="0b206-126">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="0b206-126">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="0b206-127">相關連結</span><span class="sxs-lookup"><span data-stu-id="0b206-127">RELATED LINKS</span></span>
