---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 135b4441490bbee7d8c8e0088080f97a7128af53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204976"
---
# <span data-ttu-id="3d2bb-103">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3d2bb-103">New-TimeSpan</span></span>

## <span data-ttu-id="3d2bb-104">概要</span><span class="sxs-lookup"><span data-stu-id="3d2bb-104">SYNOPSIS</span></span>
<span data-ttu-id="3d2bb-105">建立 TimeSpan 物件。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-105">Creates a TimeSpan object.</span></span>

## <span data-ttu-id="3d2bb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d2bb-106">SYNTAX</span></span>

### <span data-ttu-id="3d2bb-107">Date (預設值)</span><span class="sxs-lookup"><span data-stu-id="3d2bb-107">Date (Default)</span></span>

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="3d2bb-108">時間</span><span class="sxs-lookup"><span data-stu-id="3d2bb-108">Time</span></span>

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3d2bb-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3d2bb-109">DESCRIPTION</span></span>

<span data-ttu-id="3d2bb-110">此 `New-TimeSpan` Cmdlet 會建立代表時間間隔的 **TimeSpan** 物件。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-110">The `New-TimeSpan` cmdlet creates a **TimeSpan** object that represents a time interval.</span></span>
<span data-ttu-id="3d2bb-111">您可以使用 **TimeSpan** 物件加上或減去 **DateTime** 物件的時間。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-111">You can use a **TimeSpan** object to add or subtract time from **DateTime** objects.</span></span>

<span data-ttu-id="3d2bb-112">如果沒有參數， `New-TimeSpan` 命令會傳回代表時間間隔為零的 **TimeSpan** 物件。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-112">Without parameters, a `New-TimeSpan` command returns a **TimeSpan** object that represents a time interval of zero.</span></span>

## <span data-ttu-id="3d2bb-113">範例</span><span class="sxs-lookup"><span data-stu-id="3d2bb-113">EXAMPLES</span></span>

### <span data-ttu-id="3d2bb-114">範例 1︰建立指定持續期間的 TimeSpan 物件</span><span class="sxs-lookup"><span data-stu-id="3d2bb-114">Example 1: Create a TimeSpan object for a specified duration</span></span>

<span data-ttu-id="3d2bb-115">此命令會建立持續時間為1小時和25分鐘的 **TimeSpan** 物件，並將它儲存在名為的變數中 `$TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-115">This command creates a **TimeSpan** object with a duration of 1 hour and 25 minutes and stores it in a variable named `$TimeSpan`.</span></span> <span data-ttu-id="3d2bb-116">它會顯示 **TimeSpan** 物件的表示法。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-116">It displays a representation of the **TimeSpan** object.</span></span>

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### <span data-ttu-id="3d2bb-117">範例 2︰建立某時間間隔的 TimeSpan 物件</span><span class="sxs-lookup"><span data-stu-id="3d2bb-117">Example 2: Create a TimeSpan object for a time interval</span></span>

<span data-ttu-id="3d2bb-118">此範例建立一個新的 **TimeSpan** 物件，代表命令執行時間和 2010 年 1 月 1 日之間的間隔。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-118">This example creates a new **TimeSpan** object that represents the interval between the time that the command is run and January 1, 2010.</span></span>

<span data-ttu-id="3d2bb-119">此命令不需要 **Start** 參數，因為 **Start** 參數的預設值是目前的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-119">This command does not require the **Start** parameter, because the default value of the **Start** parameter is the current date and time.</span></span>

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### <span data-ttu-id="3d2bb-120">範例 3︰取得距離目前日期 90 天的日期</span><span class="sxs-lookup"><span data-stu-id="3d2bb-120">Example 3: Get the date 90 days from the current date</span></span>

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

<span data-ttu-id="3d2bb-121">這些命令傳回目前日期後 90 天的日期。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-121">These commands return the date that is 90 days after the current date.</span></span>

### <span data-ttu-id="3d2bb-122">範例 4︰探索自檔案更新後的 TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3d2bb-122">Example 4: Discover the TimeSpan since a file was updated</span></span>

<span data-ttu-id="3d2bb-123">此命令會告訴您，自從上一次更新 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 說明檔以來有多長時間。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-123">This command tells you how long it has been since the [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) help file was last updated.</span></span>
<span data-ttu-id="3d2bb-124">您可以在任何檔案或具有 **LastWriteTime** 屬性的任何其他物件上使用此命令格式。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-124">You can use this command format on any file, or any other object that has a **LastWriteTime** property.</span></span>

<span data-ttu-id="3d2bb-125">此命令的運作方式是因為的 **啟動** 參數 `New-TimeSpan` 具有 **LastWriteTime** 的別名。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-125">This command works because the **Start** parameter of `New-TimeSpan` has an alias of **LastWriteTime** .</span></span> <span data-ttu-id="3d2bb-126">當您使用管線將具有 **LastWriteTime** 屬性的物件傳送至時 `New-TimeSpan` ，PowerShell 會使用 **LastWriteTime** 屬性的值作為 **Start** 參數的值。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-126">When you pipe an object that has a **LastWriteTime** property to `New-TimeSpan`, PowerShell uses the value of the **LastWriteTime** property as the value of the **Start** parameter.</span></span>

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## <span data-ttu-id="3d2bb-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3d2bb-127">PARAMETERS</span></span>

### <span data-ttu-id="3d2bb-128">-Days</span><span class="sxs-lookup"><span data-stu-id="3d2bb-128">-Days</span></span>

<span data-ttu-id="3d2bb-129">指定時間範圍中的天數。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-129">Specifies the days in the time span.</span></span>
<span data-ttu-id="3d2bb-130">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-130">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-131">-End</span><span class="sxs-lookup"><span data-stu-id="3d2bb-131">-End</span></span>

<span data-ttu-id="3d2bb-132">指定時間範圍的結束。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-132">Specifies the end of a time span.</span></span>
<span data-ttu-id="3d2bb-133">預設值為目前日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-133">The default value is the current date and time.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-134">-Hours</span><span class="sxs-lookup"><span data-stu-id="3d2bb-134">-Hours</span></span>

<span data-ttu-id="3d2bb-135">指定時間範圍中的小時數。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-135">Specifies the hours in the time span.</span></span>
<span data-ttu-id="3d2bb-136">預設值為零。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-136">The default value is zero.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-137">-Minutes</span><span class="sxs-lookup"><span data-stu-id="3d2bb-137">-Minutes</span></span>

<span data-ttu-id="3d2bb-138">指定時間範圍中的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-138">Specifies the minutes in the time span.</span></span>
<span data-ttu-id="3d2bb-139">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-139">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-140">-Seconds</span><span class="sxs-lookup"><span data-stu-id="3d2bb-140">-Seconds</span></span>

<span data-ttu-id="3d2bb-141">指定時間範圍的長度 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-141">Specifies the length of the time span in seconds.</span></span>
<span data-ttu-id="3d2bb-142">預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-142">The default value is 0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-143">-Start</span><span class="sxs-lookup"><span data-stu-id="3d2bb-143">-Start</span></span>

<span data-ttu-id="3d2bb-144">指定時間範圍的開始。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-144">Specifies the start of a time span.</span></span>
<span data-ttu-id="3d2bb-145">輸入代表日期和時間的字串，例如 "3/15/09" 或 **DateTime** 物件，例如來自命令的日期和時間 `Get-Date` 。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-145">Enter a string that represents the date and time, such as "3/15/09" or a **DateTime** object, such as one from a `Get-Date` command.</span></span> <span data-ttu-id="3d2bb-146">預設值為目前日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-146">The default value is the current date and time.</span></span>

<span data-ttu-id="3d2bb-147">您可以使用 **Start** 或其別名 **LastWriteTime** 。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-147">You can use **Start** or its alias, **LastWriteTime** .</span></span>
<span data-ttu-id="3d2bb-148">**LastWriteTime** 別名可讓您使用管線將具有 **LastWriteTime** 屬性的物件（例如檔案系統中的檔案 `[System.Io.FileIO]` ）傳送至 **的 Start** 參數 `New-TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-148">The **LastWriteTime** alias lets you pipe objects that have a **LastWriteTime** property, such as files in the file system `[System.Io.FileIO]`, to the **Start** parameter of `New-TimeSpan`.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3d2bb-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d2bb-149">CommonParameters</span></span>

<span data-ttu-id="3d2bb-150">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d2bb-151">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3d2bb-152">輸入</span><span class="sxs-lookup"><span data-stu-id="3d2bb-152">INPUTS</span></span>

### <span data-ttu-id="3d2bb-153">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="3d2bb-153">System.DateTime</span></span>

<span data-ttu-id="3d2bb-154">您可以使用管線將代表該開始時間的 **DateTime** 物件傳送至 `New-TimeSpan` 。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-154">You can pipe a **DateTime** object that represents that start time to `New-TimeSpan`.</span></span>

## <span data-ttu-id="3d2bb-155">輸出</span><span class="sxs-lookup"><span data-stu-id="3d2bb-155">OUTPUTS</span></span>

### <span data-ttu-id="3d2bb-156">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="3d2bb-156">System.TimeSpan</span></span>

<span data-ttu-id="3d2bb-157">`New-TimeSpan` 傳回代表時間範圍的物件。</span><span class="sxs-lookup"><span data-stu-id="3d2bb-157">`New-TimeSpan` returns an object that represents the time span.</span></span>

## <span data-ttu-id="3d2bb-158">注意</span><span class="sxs-lookup"><span data-stu-id="3d2bb-158">NOTES</span></span>

## <span data-ttu-id="3d2bb-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="3d2bb-159">RELATED LINKS</span></span>

[<span data-ttu-id="3d2bb-160">Get-Date</span><span class="sxs-lookup"><span data-stu-id="3d2bb-160">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="3d2bb-161">Set-Date</span><span class="sxs-lookup"><span data-stu-id="3d2bb-161">Set-Date</span></span>](Set-Date.md)

