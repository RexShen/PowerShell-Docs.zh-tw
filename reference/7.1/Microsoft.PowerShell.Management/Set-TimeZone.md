---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 4bade5a583533c3156fb923a5257ebb7a4453a2b
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347528"
---
# <span data-ttu-id="095e0-103">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="095e0-103">Set-TimeZone</span></span>

## <span data-ttu-id="095e0-104">概要</span><span class="sxs-lookup"><span data-stu-id="095e0-104">SYNOPSIS</span></span>
<span data-ttu-id="095e0-105">將系統時區設定為指定的時區。</span><span class="sxs-lookup"><span data-stu-id="095e0-105">Sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="095e0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="095e0-106">SYNTAX</span></span>

### <span data-ttu-id="095e0-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="095e0-107">Name (Default)</span></span>

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="095e0-108">Id</span><span class="sxs-lookup"><span data-stu-id="095e0-108">Id</span></span>

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="095e0-109">InputObject</span><span class="sxs-lookup"><span data-stu-id="095e0-109">InputObject</span></span>

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="095e0-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="095e0-110">DESCRIPTION</span></span>

<span data-ttu-id="095e0-111">`Set-TimeZone`Cmdlet 會將系統時區設定為指定的時區。</span><span class="sxs-lookup"><span data-stu-id="095e0-111">The `Set-TimeZone` cmdlet sets the system time zone to a specified time zone.</span></span>

## <span data-ttu-id="095e0-112">範例</span><span class="sxs-lookup"><span data-stu-id="095e0-112">EXAMPLES</span></span>

### <span data-ttu-id="095e0-113">範例1：依識別碼設定時區</span><span class="sxs-lookup"><span data-stu-id="095e0-113">Example 1: Set the time zone by Id</span></span>

<span data-ttu-id="095e0-114">此範例會將本機電腦上的時區設定為俄文標準時間。</span><span class="sxs-lookup"><span data-stu-id="095e0-114">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

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

### <span data-ttu-id="095e0-115">範例2：依名稱設定時區</span><span class="sxs-lookup"><span data-stu-id="095e0-115">Example 2: Set the time zone by name</span></span>

<span data-ttu-id="095e0-116">此範例會將本機電腦上的時區設定為俄文標準時間。</span><span class="sxs-lookup"><span data-stu-id="095e0-116">This example sets the time zone on the local computer to Russian Standard Time.</span></span>

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

<span data-ttu-id="095e0-117">如先前範例中所見，時區的 **識別碼** 和 **名稱** 不一定相符。</span><span class="sxs-lookup"><span data-stu-id="095e0-117">As we saw in the previous example, the **Id** and the **Name** of the Time Zone do not always match.</span></span>
<span data-ttu-id="095e0-118">**Name** 參數必須符合 **TimeZoneInfo** 物件的 **StandardName** 或 **DaylightName** 屬性。</span><span class="sxs-lookup"><span data-stu-id="095e0-118">The **Name** parameter must match the **StandardName** or **DaylightName** properties of the **TimeZoneInfo** object.</span></span>

## <span data-ttu-id="095e0-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="095e0-119">PARAMETERS</span></span>

### <span data-ttu-id="095e0-120">-Id</span><span class="sxs-lookup"><span data-stu-id="095e0-120">-Id</span></span>

<span data-ttu-id="095e0-121">指定此 Cmdlet 設定的時區識別碼。</span><span class="sxs-lookup"><span data-stu-id="095e0-121">Specifies the ID of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="095e0-122">您可以藉由執行下列命令來取得時區識別碼的完整清單： `Get-TimeZone -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="095e0-122">A full list of Time Zone IDs can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="095e0-123">-InputObject</span><span class="sxs-lookup"><span data-stu-id="095e0-123">-InputObject</span></span>

<span data-ttu-id="095e0-124">指定要做為輸入使用的 **TimeZoneInfo** 物件。</span><span class="sxs-lookup"><span data-stu-id="095e0-124">Specifies a **TimeZoneInfo** object to use as input.</span></span>

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

### <span data-ttu-id="095e0-125">-Name</span><span class="sxs-lookup"><span data-stu-id="095e0-125">-Name</span></span>

<span data-ttu-id="095e0-126">指定此 Cmdlet 設定的時區名稱。</span><span class="sxs-lookup"><span data-stu-id="095e0-126">Specifies the name of the time zone that this cmdlet sets.</span></span> <span data-ttu-id="095e0-127">您可以藉由執行下列命令來取得時區名稱的完整清單： `Get-TimeZone -ListAvailable` 。</span><span class="sxs-lookup"><span data-stu-id="095e0-127">A full list of Time Zone names can be obtained by running the following command: `Get-TimeZone -ListAvailable`.</span></span>

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

### <span data-ttu-id="095e0-128">-PassThru</span><span class="sxs-lookup"><span data-stu-id="095e0-128">-PassThru</span></span>

<span data-ttu-id="095e0-129">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="095e0-129">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="095e0-130">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="095e0-130">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="095e0-131">-Confirm</span><span class="sxs-lookup"><span data-stu-id="095e0-131">-Confirm</span></span>

<span data-ttu-id="095e0-132">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="095e0-132">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="095e0-133">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="095e0-133">-WhatIf</span></span>

<span data-ttu-id="095e0-134">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="095e0-134">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="095e0-135">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="095e0-135">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="095e0-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="095e0-136">CommonParameters</span></span>

<span data-ttu-id="095e0-137">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="095e0-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="095e0-138">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="095e0-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="095e0-139">輸入</span><span class="sxs-lookup"><span data-stu-id="095e0-139">INPUTS</span></span>

### <span data-ttu-id="095e0-140">System.string、TimeZoneInfo、System.string</span><span class="sxs-lookup"><span data-stu-id="095e0-140">System.String, System.TimeZoneInfo, System.String</span></span>

## <span data-ttu-id="095e0-141">輸出</span><span class="sxs-lookup"><span data-stu-id="095e0-141">OUTPUTS</span></span>

## <span data-ttu-id="095e0-142">注意</span><span class="sxs-lookup"><span data-stu-id="095e0-142">NOTES</span></span>

<span data-ttu-id="095e0-143">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="095e0-143">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="095e0-144">相關連結</span><span class="sxs-lookup"><span data-stu-id="095e0-144">RELATED LINKS</span></span>

[<span data-ttu-id="095e0-145">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="095e0-145">Get-TimeZone</span></span>](Get-TimeZone.md)
