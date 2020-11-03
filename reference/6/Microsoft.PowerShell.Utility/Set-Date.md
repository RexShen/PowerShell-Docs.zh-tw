---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 4a7deaeb0570516c5d0cb1be704f0e1cb7bfe13c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204424"
---
# <span data-ttu-id="e54fe-103">Set-Date</span><span class="sxs-lookup"><span data-stu-id="e54fe-103">Set-Date</span></span>

## <span data-ttu-id="e54fe-104">概要</span><span class="sxs-lookup"><span data-stu-id="e54fe-104">SYNOPSIS</span></span>
<span data-ttu-id="e54fe-105">將電腦的系統時間變更為您指定的時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-105">Changes the system time on the computer to a time that you specify.</span></span>

## <span data-ttu-id="e54fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e54fe-106">SYNTAX</span></span>

### <span data-ttu-id="e54fe-107">Date (預設值)</span><span class="sxs-lookup"><span data-stu-id="e54fe-107">Date (Default)</span></span>

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e54fe-108">Adjust</span><span class="sxs-lookup"><span data-stu-id="e54fe-108">Adjust</span></span>

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e54fe-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e54fe-109">DESCRIPTION</span></span>

<span data-ttu-id="e54fe-110">此 `Set-Date` Cmdlet 會將電腦上的系統日期和時間變更為您指定的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-110">The `Set-Date` cmdlet changes the system date and time on the computer to a date and time that you specify.</span></span>
<span data-ttu-id="e54fe-111">您可以輸入字串或將 **DateTime** 或 **TimeSpan** 物件傳遞給，以指定新的日期和/或時間 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-111">You can specify a new date and/or time by typing a string or by passing a **DateTime** or **TimeSpan** object to `Set-Date`.</span></span> <span data-ttu-id="e54fe-112">若要指定新的日期或時間，請使用 **date** 參數。</span><span class="sxs-lookup"><span data-stu-id="e54fe-112">To specify a new date or time, use the **Date** parameter.</span></span>
<span data-ttu-id="e54fe-113">若要指定變更間隔，請使用 [ **調整** ] 參數。</span><span class="sxs-lookup"><span data-stu-id="e54fe-113">To specify a change interval, use the **Adjust** parameter.</span></span>

## <span data-ttu-id="e54fe-114">範例</span><span class="sxs-lookup"><span data-stu-id="e54fe-114">EXAMPLES</span></span>

### <span data-ttu-id="e54fe-115">範例1：將三天新增至系統日期</span><span class="sxs-lookup"><span data-stu-id="e54fe-115">Example 1: Add three days to the system date</span></span>

<span data-ttu-id="e54fe-116">此命令會將目前的系統日期增加 3 天。</span><span class="sxs-lookup"><span data-stu-id="e54fe-116">This command adds three days to the current system date.</span></span>
<span data-ttu-id="e54fe-117">它不會影響時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-117">It does not affect the time.</span></span>
<span data-ttu-id="e54fe-118">命令使用 **date** 參數指定日期。</span><span class="sxs-lookup"><span data-stu-id="e54fe-118">The command uses the **Date** parameter to specify the date.</span></span>

<span data-ttu-id="e54fe-119">Cmdlet 會傳回 `Get-Date` 目前的日期做為 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="e54fe-119">The `Get-Date` cmdlet returns the current date as a **DateTime** object.</span></span> <span data-ttu-id="e54fe-120">**Datetime** 物件的 **AddDays** 方法會將指定的天數 (3) 新增至目前的 **日期時間** 物件。</span><span class="sxs-lookup"><span data-stu-id="e54fe-120">The **DateTime** object's **AddDays** method adds a specified number of days (3) to the current **DateTime** object.</span></span>

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### <span data-ttu-id="e54fe-121">範例2：將系統時鐘設定回10分鐘</span><span class="sxs-lookup"><span data-stu-id="e54fe-121">Example 2: Set the system clock back 10 minutes</span></span>

<span data-ttu-id="e54fe-122">此範例會將目前的系統時間設定為10分鐘。</span><span class="sxs-lookup"><span data-stu-id="e54fe-122">This example sets the current system time back by 10 minutes.</span></span>

<span data-ttu-id="e54fe-123">[ **調整** ] 參數可讓您指定變更間隔 (減去十分鐘，以地區設定的標準時間格式) 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-123">The **Adjust** parameter allows you to specify an interval of change (minus ten minutes) in the standard time format for the locale.</span></span>

<span data-ttu-id="e54fe-124">**DisplayHint** 參數會指示 PowerShell 只顯示時間，但不會影響傳回的 **DateTime** 物件 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-124">The **DisplayHint** parameter tells PowerShell to display only the time, but it does not affect the **DateTime** object that `Set-Date` returns.</span></span>

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### <span data-ttu-id="e54fe-125">範例3：將日期和時間設定為變數值</span><span class="sxs-lookup"><span data-stu-id="e54fe-125">Example 3: Set the date and time to a variable value</span></span>

<span data-ttu-id="e54fe-126">這些命令會將本機電腦上的系統日期和時間變更為儲存在變數中的日期和時間 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-126">These commands change the system date and time on local computer to the date and time saved in the variable `$T`.</span></span> <span data-ttu-id="e54fe-127">第一個命令會取得日期並將其儲存在中 `$T` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-127">The first command gets the date and stores it in `$T`.</span></span>

<span data-ttu-id="e54fe-128">第二個命令使用 **Date** 參數將 **DateTime** 物件傳送 `$T` 至 `Set-Date` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e54fe-128">The second command uses the **Date** parameter to pass the **DateTime** object in `$T` to the `Set-Date` cmdlet.</span></span>

```powershell
$T = Get-Date
Set-Date -Date $T
```

### <span data-ttu-id="e54fe-129">範例4：將90分鐘新增至系統時鐘</span><span class="sxs-lookup"><span data-stu-id="e54fe-129">Example 4: Add 90 minutes to the system clock</span></span>

<span data-ttu-id="e54fe-130">這些命令將本機電腦上的系統時間增加 90 分鐘。</span><span class="sxs-lookup"><span data-stu-id="e54fe-130">These commands advance the system time on the local computer by 90 minutes.</span></span>

<span data-ttu-id="e54fe-131">第一個命令會使用 `New-TimeSpan` Cmdlet 來建立具有90分鐘間隔的 **TimeSpan** 物件，並將它儲存在變數中 `$90mins` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-131">The first command uses the `New-TimeSpan` cmdlet to create a **TimeSpan** object with a 90-minute interval, and saves it in the `$90mins` variable.</span></span>

<span data-ttu-id="e54fe-132">第二個命令使用的 **調整** 參數 `Set-Date` ，將日期調整為變數中 **TimeSpan** 物件的值 `$90mins` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-132">The second command uses the **Adjust** parameter of `Set-Date` to adjust the date by the value of the **TimeSpan** object in the `$90mins` variable.</span></span>

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## <span data-ttu-id="e54fe-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e54fe-133">PARAMETERS</span></span>

### <span data-ttu-id="e54fe-134">-Adjust</span><span class="sxs-lookup"><span data-stu-id="e54fe-134">-Adjust</span></span>

<span data-ttu-id="e54fe-135">指定此 Cmdlet 會從目前的日期和時間加上或減去的值。</span><span class="sxs-lookup"><span data-stu-id="e54fe-135">Specifies the value for which this cmdlet adds or subtracts from the current date and time.</span></span>
<span data-ttu-id="e54fe-136">可以為您的地區設定輸入標準日期和時間格式的調整，或使用 [ **調整** ] 參數將 **TimeSpan** 物件從傳遞 `New-TimeSpan` 至 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-136">can type an adjustment in standard date and time format for your locale or use the **Adjust** parameter to pass a **TimeSpan** object from `New-TimeSpan` to `Set-Date`.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e54fe-137">-Date</span><span class="sxs-lookup"><span data-stu-id="e54fe-137">-Date</span></span>

<span data-ttu-id="e54fe-138">將日期和時間變更為指定值。</span><span class="sxs-lookup"><span data-stu-id="e54fe-138">Changes the date and time to the specified values.</span></span>
<span data-ttu-id="e54fe-139">您可以簡短的日期格式輸入新日期，並以您地區設定的標準時間格式輸入時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-139">You can type a new date in the short date format and a time in the standard time format for your locale.</span></span> <span data-ttu-id="e54fe-140">或者，您可以從傳遞 **DateTime** 物件 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-140">Or, you can pass a **DateTime** object from `Get-Date`.</span></span>

<span data-ttu-id="e54fe-141">如果您指定日期而非時間，則會將 `Set-Date` 時間變更為指定日期的午夜。</span><span class="sxs-lookup"><span data-stu-id="e54fe-141">If you specify a date, but not a time, `Set-Date` changes the time to midnight on the specified date.</span></span> <span data-ttu-id="e54fe-142">如果您只指定時間，則不會變更日期。</span><span class="sxs-lookup"><span data-stu-id="e54fe-142">If you specify only a time, it does not change the date.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e54fe-143">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="e54fe-143">-DisplayHint</span></span>

<span data-ttu-id="e54fe-144">指定要顯示日期和時間的哪些元素。此參數可接受的值包括：</span><span class="sxs-lookup"><span data-stu-id="e54fe-144">Specifies which elements of the date and time are displayed.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e54fe-145">日期。</span><span class="sxs-lookup"><span data-stu-id="e54fe-145">Date.</span></span>
  <span data-ttu-id="e54fe-146">只顯示日期。</span><span class="sxs-lookup"><span data-stu-id="e54fe-146">displays only the date.</span></span>
- <span data-ttu-id="e54fe-147">時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-147">Time.</span></span>
  <span data-ttu-id="e54fe-148">只顯示時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-148">displays only the time.</span></span>
- <span data-ttu-id="e54fe-149">日期時間：</span><span class="sxs-lookup"><span data-stu-id="e54fe-149">DateTime.</span></span>
  <span data-ttu-id="e54fe-150">顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e54fe-150">displays the date and time.</span></span>

<span data-ttu-id="e54fe-151">此參數只會影響顯示。</span><span class="sxs-lookup"><span data-stu-id="e54fe-151">This parameter affects only the display.</span></span>
<span data-ttu-id="e54fe-152">它不會影響抓取的 **DateTime** 物件 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-152">It does not affect the **DateTime** object that `Get-Date` retrieves.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e54fe-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e54fe-153">-Confirm</span></span>

<span data-ttu-id="e54fe-154">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="e54fe-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e54fe-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e54fe-155">-WhatIf</span></span>

<span data-ttu-id="e54fe-156">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e54fe-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e54fe-157">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="e54fe-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e54fe-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e54fe-158">CommonParameters</span></span>

<span data-ttu-id="e54fe-159">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="e54fe-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e54fe-160">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="e54fe-160">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e54fe-161">輸入</span><span class="sxs-lookup"><span data-stu-id="e54fe-161">INPUTS</span></span>

### <span data-ttu-id="e54fe-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e54fe-162">System.DateTime</span></span>

<span data-ttu-id="e54fe-163">您可以使用管線將日期傳送至 `Set-Date` 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-163">You can pipe a date to `Set-Date`.</span></span>

## <span data-ttu-id="e54fe-164">輸出</span><span class="sxs-lookup"><span data-stu-id="e54fe-164">OUTPUTS</span></span>

### <span data-ttu-id="e54fe-165">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="e54fe-165">System.DateTime</span></span>

<span data-ttu-id="e54fe-166">`Set-Date` 傳回物件，表示它所設定的日期。</span><span class="sxs-lookup"><span data-stu-id="e54fe-166">`Set-Date` returns an object that represents the date that it set.</span></span>

## <span data-ttu-id="e54fe-167">注意</span><span class="sxs-lookup"><span data-stu-id="e54fe-167">NOTES</span></span>

- <span data-ttu-id="e54fe-168">變更電腦上的日期和時間時，請小心使用此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e54fe-168">Use this cmdlet cautiously when changing the date and time on the computer.</span></span> <span data-ttu-id="e54fe-169">變更可能會導致電腦無法接收日期或時間觸發的全系統事件和更新。</span><span class="sxs-lookup"><span data-stu-id="e54fe-169">The change might prevent the computer from receiving system-wide events and updates that are triggered by a date or time.</span></span> <span data-ttu-id="e54fe-170">使用 **WhatIf** 並 **確認** 參數，以避免發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e54fe-170">Use the **WhatIf** and **Confirm** parameters to avoid errors.</span></span>
- <span data-ttu-id="e54fe-171">您可以使用標準的 .NET 方法搭配搭配使用的 **DateTime** 和 **TimeSpan** 物件 `Set-Date` ，例如 **AddDays** 、 **AddMonths** 和 **FromFileTime** 。</span><span class="sxs-lookup"><span data-stu-id="e54fe-171">You can use standard .NET methods with the **DateTime** and **TimeSpan** objects used with `Set-Date`, such as **AddDays** , **AddMonths** , and **FromFileTime** .</span></span> <span data-ttu-id="e54fe-172">如需詳細資訊，請參閱 [DateTime 方法](/dotnet/api/system.datetime) 和</span><span class="sxs-lookup"><span data-stu-id="e54fe-172">For more information, see [DateTime Methods](/dotnet/api/system.datetime) and</span></span>

  <span data-ttu-id="e54fe-173">MSDN library 中的[TimeSpan 方法](/dotnet/api/system.timespan)。</span><span class="sxs-lookup"><span data-stu-id="e54fe-173">[TimeSpan Methods](/dotnet/api/system.timespan) in the MSDN library.</span></span>

## <span data-ttu-id="e54fe-174">相關連結</span><span class="sxs-lookup"><span data-stu-id="e54fe-174">RELATED LINKS</span></span>

[<span data-ttu-id="e54fe-175">Get-Date</span><span class="sxs-lookup"><span data-stu-id="e54fe-175">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="e54fe-176">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="e54fe-176">New-TimeSpan</span></span>](New-TimeSpan.md)
