---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 618f2ceca435e836a0c733f98533b62dfc86290b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93205219"
---
# <span data-ttu-id="fc7b9-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="fc7b9-103">Set-TimeZone</span></span>

## <span data-ttu-id="fc7b9-104">概要</span><span class="sxs-lookup"><span data-stu-id="fc7b9-104">SYNOPSIS</span></span>
<span data-ttu-id="fc7b9-105">將系統時區設定為指定的時區。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="fc7b9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc7b9-106">SYNTAX</span></span>

### <span data-ttu-id="fc7b9-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="fc7b9-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fc7b9-108">Id</span><span class="sxs-lookup"><span data-stu-id="fc7b9-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="fc7b9-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="fc7b9-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fc7b9-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="fc7b9-110">DESCRIPTION</span></span>

<span data-ttu-id="fc7b9-111">`Set-TimeZone`Cmdlet 會將系統時區設定為指定的時區。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="fc7b9-112">範例</span><span class="sxs-lookup"><span data-stu-id="fc7b9-112">EXAMPLES</span></span>

### <span data-ttu-id="fc7b9-113">範例1：依識別碼設定時區</span><span class="sxs-lookup"><span data-stu-id="fc7b9-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="fc7b9-114">此範例會將本機電腦上的時區設定為俄文標準時間。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### <span data-ttu-id="fc7b9-115">範例2：依名稱設定時區</span><span class="sxs-lookup"><span data-stu-id="fc7b9-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="fc7b9-116">此範例會將本機電腦上的時區設定為俄文標準時間。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="fc7b9-117">如先前範例中所見，時區的 **識別碼** 和 **名稱** 不一定相符。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="fc7b9-118">**Name** 參數必須符合 **TimeZoneInfo** 物件的 **StandardName** 或 **DaylightName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="fc7b9-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fc7b9-119">PARAMETERS</span></span>

### <span data-ttu-id="fc7b9-120">-Id</span><span class="sxs-lookup"><span data-stu-id="fc7b9-120">-Id</span></span>

<span data-ttu-id="fc7b9-121">指定此 Cmdlet 設定的時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="fc7b9-122">您可以藉由執行下列命令來取得時區識別碼的完整清單： `Get-TimeZone -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fc7b9-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="fc7b9-123">-InputObject</span></span>

<span data-ttu-id="fc7b9-124">指定要做為輸入使用的 **TimeZoneInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fc7b9-125">-Name</span><span class="sxs-lookup"><span data-stu-id="fc7b9-125">-Name</span></span>

<span data-ttu-id="fc7b9-126">指定此 Cmdlet 設定的時區名稱。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="fc7b9-127">您可以藉由執行下列命令來取得時區名稱的完整清單： `Get-TimeZone -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc7b9-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="fc7b9-128">-PassThru</span></span>

<span data-ttu-id="fc7b9-129">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="fc7b9-130">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-130">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="fc7b9-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fc7b9-131">-Confirm</span></span>

<span data-ttu-id="fc7b9-132">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-132">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc7b9-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fc7b9-133">-WhatIf</span></span>

<span data-ttu-id="fc7b9-134">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fc7b9-135">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-135">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fc7b9-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc7b9-136">CommonParameters</span></span>

<span data-ttu-id="fc7b9-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc7b9-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="fc7b9-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc7b9-139">輸入</span><span class="sxs-lookup"><span data-stu-id="fc7b9-139">INPUTS</span></span>

### <span data-ttu-id="fc7b9-140">System.string、TimeZoneInfo、System.string</span><span class="sxs-lookup"><span data-stu-id="fc7b9-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="fc7b9-141">輸出</span><span class="sxs-lookup"><span data-stu-id="fc7b9-141">OUTPUTS</span></span>

## <span data-ttu-id="fc7b9-142">注意</span><span class="sxs-lookup"><span data-stu-id="fc7b9-142">NOTES</span></span>

## <span data-ttu-id="fc7b9-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="fc7b9-143">RELATED LINKS</span></span>

[<span data-ttu-id="fc7b9-144">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="fc7b9-144">Get-TimeZone</span></span>](Get-TimeZone.md)
