---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: 1a107b2e4c7414250154d576d6dc9554cb9d800b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204395"
---
# <span data-ttu-id="36be0-103">Start-Sleep</span><span class="sxs-lookup"><span data-stu-id="36be0-103">Start-Sleep</span></span>

## <span data-ttu-id="36be0-104">概要</span><span class="sxs-lookup"><span data-stu-id="36be0-104">SYNOPSIS</span></span>
<span data-ttu-id="36be0-105">將指令碼或工作階段中的活動暫停一段指定的時間。</span><span class="sxs-lookup"><span data-stu-id="36be0-105">Suspends the activity in a script or session for the specified period of time.</span></span>

## <span data-ttu-id="36be0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36be0-106">SYNTAX</span></span>

### <span data-ttu-id="36be0-107">秒 (預設值)</span><span class="sxs-lookup"><span data-stu-id="36be0-107">Seconds (Default)</span></span>

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### <span data-ttu-id="36be0-108">毫秒</span><span class="sxs-lookup"><span data-stu-id="36be0-108">Milliseconds</span></span>

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## <span data-ttu-id="36be0-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="36be0-109">DESCRIPTION</span></span>

<span data-ttu-id="36be0-110">指令 `Start-Sleep` 程式會在指定的時間內暫停腳本或會話中的活動。</span><span class="sxs-lookup"><span data-stu-id="36be0-110">The `Start-Sleep` cmdlet suspends the activity in a script or session for the specified period of time.</span></span> <span data-ttu-id="36be0-111">您可以將它用於許多工作，例如等待操作完成，或先暫停再重複執行一項操作。</span><span class="sxs-lookup"><span data-stu-id="36be0-111">You can use it for many tasks, such as waiting for an operation to complete or pausing before repeating an operation.</span></span>

## <span data-ttu-id="36be0-112">範例</span><span class="sxs-lookup"><span data-stu-id="36be0-112">EXAMPLES</span></span>

### <span data-ttu-id="36be0-113">範例 1︰讓所有命令睡眠 15 秒</span><span class="sxs-lookup"><span data-stu-id="36be0-113">Example 1: Sleep all commands for 15 seconds</span></span>

```powershell
Start-Sleep -s 15
```

### <span data-ttu-id="36be0-114">範例2：睡眠所有命令1.5 秒</span><span class="sxs-lookup"><span data-stu-id="36be0-114">Example 2: Sleep all commands for 1.5 seconds</span></span>

<span data-ttu-id="36be0-115">此範例會讓會話中的所有命令睡眠一段時間，並將其放在一秒的一半內。</span><span class="sxs-lookup"><span data-stu-id="36be0-115">This example makes all the commands in the session sleep for one and one-half of a seconds.</span></span>

```powershell
Start-Sleep -Seconds 1.5
```

## <span data-ttu-id="36be0-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36be0-116">PARAMETERS</span></span>

### <span data-ttu-id="36be0-117">-Milliseconds</span><span class="sxs-lookup"><span data-stu-id="36be0-117">-Milliseconds</span></span>

<span data-ttu-id="36be0-118">指定資源的睡眠時間長度 (單位為毫秒)。</span><span class="sxs-lookup"><span data-stu-id="36be0-118">Specifies how long the resource sleeps in milliseconds.</span></span> <span data-ttu-id="36be0-119">參數可以縮寫為 **m** 。</span><span class="sxs-lookup"><span data-stu-id="36be0-119">The parameter can be abbreviated as **m** .</span></span>

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="36be0-120">-Seconds</span><span class="sxs-lookup"><span data-stu-id="36be0-120">-Seconds</span></span>

<span data-ttu-id="36be0-121">指定資源的睡眠時間長度 (單位為秒)。</span><span class="sxs-lookup"><span data-stu-id="36be0-121">Specifies how long the resource sleeps in seconds.</span></span> <span data-ttu-id="36be0-122">您可以省略參數名稱，也可以將它縮寫為 **s** 。</span><span class="sxs-lookup"><span data-stu-id="36be0-122">You can omit the parameter name or you can abbreviate it as **s** .</span></span> <span data-ttu-id="36be0-123">從 PowerShell 6.2.0 開始，此參數現在會接受小數值。</span><span class="sxs-lookup"><span data-stu-id="36be0-123">Beginning in PowerShell 6.2.0, this parameter now accepts fractional values.</span></span>

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36be0-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36be0-124">CommonParameters</span></span>

<span data-ttu-id="36be0-125">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="36be0-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36be0-126">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="36be0-126">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="36be0-127">輸入</span><span class="sxs-lookup"><span data-stu-id="36be0-127">INPUTS</span></span>

### <span data-ttu-id="36be0-128">System.Int32</span><span class="sxs-lookup"><span data-stu-id="36be0-128">System.Int32</span></span>

<span data-ttu-id="36be0-129">您可以用管線將秒數傳送至 `Start-Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="36be0-129">You can pipe the number of seconds to `Start-Sleep`.</span></span>

## <span data-ttu-id="36be0-130">輸出</span><span class="sxs-lookup"><span data-stu-id="36be0-130">OUTPUTS</span></span>

### <span data-ttu-id="36be0-131">無</span><span class="sxs-lookup"><span data-stu-id="36be0-131">None</span></span>

<span data-ttu-id="36be0-132">此 Cmdlet 不會傳回任何輸出。</span><span class="sxs-lookup"><span data-stu-id="36be0-132">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="36be0-133">注意</span><span class="sxs-lookup"><span data-stu-id="36be0-133">NOTES</span></span>

- <span data-ttu-id="36be0-134">您也可以 `Start-Sleep` 使用內建的別名來參考 `sleep` 。</span><span class="sxs-lookup"><span data-stu-id="36be0-134">You can also refer to `Start-Sleep` by its built-in alias, `sleep`.</span></span> <span data-ttu-id="36be0-135">如需詳細資訊，請參閱 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="36be0-135">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="36be0-136">`Ctrl+C` 中斷 `Start-Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="36be0-136">`Ctrl+C` breaks out of `Start-Sleep`.</span></span>
  - <span data-ttu-id="36be0-137">`Ctrl+C` 不會中斷 `[Threading.Thread]::Sleep` 。</span><span class="sxs-lookup"><span data-stu-id="36be0-137">`Ctrl+C` does not break out of `[Threading.Thread]::Sleep`.</span></span> <span data-ttu-id="36be0-138">如需詳細資訊，請參閱 [Sleep 方法](/dotnet/api/system.threading.thread.sleep)。</span><span class="sxs-lookup"><span data-stu-id="36be0-138">For more information, see [Thread.Sleep Method](/dotnet/api/system.threading.thread.sleep).</span></span>

## <span data-ttu-id="36be0-139">相關連結</span><span class="sxs-lookup"><span data-stu-id="36be0-139">RELATED LINKS</span></span>
