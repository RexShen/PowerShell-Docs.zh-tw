---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: d06dbc66d9674b59df4d75f8ae333d4fe24aa7eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202795"
---
# <span data-ttu-id="9f07f-102">Get-Uptime</span><span class="sxs-lookup"><span data-stu-id="9f07f-102">Get-Uptime</span></span>

## <span data-ttu-id="9f07f-103">概要</span><span class="sxs-lookup"><span data-stu-id="9f07f-103">SYNOPSIS</span></span>
<span data-ttu-id="9f07f-104">取得自上一次開機之後的 **TimeSpan** 。</span><span class="sxs-lookup"><span data-stu-id="9f07f-104">Get the **TimeSpan** since last boot.</span></span>

## <span data-ttu-id="9f07f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9f07f-105">SYNTAX</span></span>

### <span data-ttu-id="9f07f-106">Timespan (預設) </span><span class="sxs-lookup"><span data-stu-id="9f07f-106">Timespan (Default)</span></span>

```
Get-Uptime [<CommonParameters>]
```

### <span data-ttu-id="9f07f-107">因為</span><span class="sxs-lookup"><span data-stu-id="9f07f-107">Since</span></span>

```
Get-Uptime [-Since] [<CommonParameters>]
```

## <span data-ttu-id="9f07f-108">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="9f07f-108">DESCRIPTION</span></span>

<span data-ttu-id="9f07f-109">此 Cmdlet 會傳回自上次開機作業系統之後經過的時間。</span><span class="sxs-lookup"><span data-stu-id="9f07f-109">This cmdlet returns the time elapsed since the last boot of the operating system.</span></span>

<span data-ttu-id="9f07f-110">`Get-Uptime`Cmdlet 是在 PowerShell 6.0 中引進。</span><span class="sxs-lookup"><span data-stu-id="9f07f-110">The `Get-Uptime` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="9f07f-111">範例</span><span class="sxs-lookup"><span data-stu-id="9f07f-111">EXAMPLES</span></span>

### <span data-ttu-id="9f07f-112">範例 1-顯示自上次開機後的時間</span><span class="sxs-lookup"><span data-stu-id="9f07f-112">Example 1 - Show time since last boot</span></span>

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### <span data-ttu-id="9f07f-113">範例 2-顯示上次開機的時間</span><span class="sxs-lookup"><span data-stu-id="9f07f-113">Example 2 - Show the time of the last boot</span></span>

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## <span data-ttu-id="9f07f-114">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9f07f-114">PARAMETERS</span></span>

### <span data-ttu-id="9f07f-115">-自</span><span class="sxs-lookup"><span data-stu-id="9f07f-115">-Since</span></span>

<span data-ttu-id="9f07f-116">讓指令程式傳回代表作業系統上次開機時間的 **日期時間** 物件。</span><span class="sxs-lookup"><span data-stu-id="9f07f-116">Cause the cmdlet to return a **DateTime** object representing the last time that the operating system was booted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9f07f-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9f07f-117">CommonParameters</span></span>

<span data-ttu-id="9f07f-118">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="9f07f-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9f07f-119">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="9f07f-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9f07f-120">輸入</span><span class="sxs-lookup"><span data-stu-id="9f07f-120">INPUTS</span></span>

### <span data-ttu-id="9f07f-121">無</span><span class="sxs-lookup"><span data-stu-id="9f07f-121">None</span></span>

## <span data-ttu-id="9f07f-122">輸出</span><span class="sxs-lookup"><span data-stu-id="9f07f-122">OUTPUTS</span></span>

### <span data-ttu-id="9f07f-123">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="9f07f-123">System.TimeSpan</span></span>

<span data-ttu-id="9f07f-124">如果未使用任何參數，這就是預設的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9f07f-124">This is the default return type when no parameters are used.</span></span>

### <span data-ttu-id="9f07f-125">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="9f07f-125">System.DateTime</span></span>

<span data-ttu-id="9f07f-126">使用 **自** 參數時，會傳回此類型。</span><span class="sxs-lookup"><span data-stu-id="9f07f-126">This type is returned when using the **Since** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="9f07f-127">如果啟用 [Windows 快速啟動]，Windows 不會更新儲存在 **LastBootUpTime** 中的值。</span><span class="sxs-lookup"><span data-stu-id="9f07f-127">If Windows fast startup is enabled, Windows does not update the value stored in **LastBootUpTime** .</span></span> <span data-ttu-id="9f07f-128">若要停用快速啟動，請執行下列命令： `Powercfg -h off` 。</span><span class="sxs-lookup"><span data-stu-id="9f07f-128">To disable fast startup, run the following command: `Powercfg -h off`.</span></span>
>
> <span data-ttu-id="9f07f-129">如需有關 Windows 快速啟動的詳細資訊，請參閱 [從休眠喚醒開始區分快速啟動](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)。</span><span class="sxs-lookup"><span data-stu-id="9f07f-129">For more information about Windows fast startup, see [Distinguishing Fast Startup from Wake-from-Hibernation](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation).</span></span>

## <span data-ttu-id="9f07f-130">注意</span><span class="sxs-lookup"><span data-stu-id="9f07f-130">NOTES</span></span>

<span data-ttu-id="9f07f-131">在 Windows 上，傳回的值與 WMI 中 **Win32_OperatingSystem** 類別的 **LastBootUpTime** 屬性相同。</span><span class="sxs-lookup"><span data-stu-id="9f07f-131">On Windows, the value returned is the same as the **LastBootUpTime** property of the **Win32_OperatingSystem** class in WMI.</span></span>

## <span data-ttu-id="9f07f-132">相關連結</span><span class="sxs-lookup"><span data-stu-id="9f07f-132">RELATED LINKS</span></span>

[<span data-ttu-id="9f07f-133">Win32_OperatingSystem</span><span class="sxs-lookup"><span data-stu-id="9f07f-133">Win32_OperatingSystem</span></span>](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

