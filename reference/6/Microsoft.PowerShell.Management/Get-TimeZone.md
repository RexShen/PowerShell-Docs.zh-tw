---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 0a2beb778001267beda0b23afaf1264b0440a5e5
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343954"
---
# <span data-ttu-id="d5436-103">Get-TimeZone</span><span class="sxs-lookup"><span data-stu-id="d5436-103">Get-TimeZone</span></span>

## <span data-ttu-id="d5436-104">概要</span><span class="sxs-lookup"><span data-stu-id="d5436-104">SYNOPSIS</span></span>
<span data-ttu-id="d5436-105">取得目前的時區或可用時區的清單。</span><span class="sxs-lookup"><span data-stu-id="d5436-105">Gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="d5436-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d5436-106">SYNTAX</span></span>

### <span data-ttu-id="d5436-107">Name (預設值)</span><span class="sxs-lookup"><span data-stu-id="d5436-107">Name (Default)</span></span>

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d5436-108">Id</span><span class="sxs-lookup"><span data-stu-id="d5436-108">Id</span></span>

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### <span data-ttu-id="d5436-109">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d5436-109">ListAvailable</span></span>

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="d5436-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d5436-110">DESCRIPTION</span></span>

<span data-ttu-id="d5436-111">**取得** 時區 Cmdlet 會取得目前的時區或可用時區的清單。</span><span class="sxs-lookup"><span data-stu-id="d5436-111">The **Get-TimeZone** cmdlet gets the current time zone or a list of available time zones.</span></span>

## <span data-ttu-id="d5436-112">範例</span><span class="sxs-lookup"><span data-stu-id="d5436-112">EXAMPLES</span></span>

### <span data-ttu-id="d5436-113">範例1：取得目前的時區</span><span class="sxs-lookup"><span data-stu-id="d5436-113">Example 1: Get the current time zone</span></span>

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

<span data-ttu-id="d5436-114">此命令會取得目前的時區。</span><span class="sxs-lookup"><span data-stu-id="d5436-114">This command gets the current time zone.</span></span>

### <span data-ttu-id="d5436-115">範例2：取得符合指定字串的時區</span><span class="sxs-lookup"><span data-stu-id="d5436-115">Example 2: Get time zones that match a specified string</span></span>

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

<span data-ttu-id="d5436-116">此命令會取得所有符合指定萬用字元的時區。</span><span class="sxs-lookup"><span data-stu-id="d5436-116">This command gets all time zones that match the specified wildcard.</span></span>

### <span data-ttu-id="d5436-117">範例3：取得所有可用時區</span><span class="sxs-lookup"><span data-stu-id="d5436-117">Example 3: Get all available time zones</span></span>

```
PS C:\> Get-TimeZone -ListAvailable
```

<span data-ttu-id="d5436-118">此命令會取得所有可用時區。</span><span class="sxs-lookup"><span data-stu-id="d5436-118">This command gets all available time zones.</span></span>

## <span data-ttu-id="d5436-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d5436-119">PARAMETERS</span></span>

### <span data-ttu-id="d5436-120">-Id</span><span class="sxs-lookup"><span data-stu-id="d5436-120">-Id</span></span>

<span data-ttu-id="d5436-121">以字串陣列指定此 Cmdlet 取得的時區識別碼或識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5436-121">Specifies, as a string array, the ID or IDs of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d5436-122">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="d5436-122">-ListAvailable</span></span>

<span data-ttu-id="d5436-123">指出此 Cmdlet 會取得所有可用時區。</span><span class="sxs-lookup"><span data-stu-id="d5436-123">Indicates that this cmdlet gets all available time zones.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d5436-124">-Name</span><span class="sxs-lookup"><span data-stu-id="d5436-124">-Name</span></span>

<span data-ttu-id="d5436-125">以字串陣列指定此 Cmdlet 取得的時區名稱或名稱。</span><span class="sxs-lookup"><span data-stu-id="d5436-125">Specifies, as a string array, the name or names of the time zones that this cmdlet gets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d5436-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d5436-126">CommonParameters</span></span>

<span data-ttu-id="d5436-127">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d5436-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d5436-128">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d5436-128">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d5436-129">輸入</span><span class="sxs-lookup"><span data-stu-id="d5436-129">INPUTS</span></span>

### <span data-ttu-id="d5436-130">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d5436-130">System.String[]</span></span>

## <span data-ttu-id="d5436-131">輸出</span><span class="sxs-lookup"><span data-stu-id="d5436-131">OUTPUTS</span></span>

### <span data-ttu-id="d5436-132">TimeZoneInfo []</span><span class="sxs-lookup"><span data-stu-id="d5436-132">System.TimeZoneInfo[]</span></span>

## <span data-ttu-id="d5436-133">注意</span><span class="sxs-lookup"><span data-stu-id="d5436-133">NOTES</span></span>

<span data-ttu-id="d5436-134">此 Cmdlet 僅適用于 Windows 平臺。</span><span class="sxs-lookup"><span data-stu-id="d5436-134">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="d5436-135">相關連結</span><span class="sxs-lookup"><span data-stu-id="d5436-135">RELATED LINKS</span></span>

[<span data-ttu-id="d5436-136">Set-TimeZone</span><span class="sxs-lookup"><span data-stu-id="d5436-136">Set-TimeZone</span></span>](Set-TimeZone.md)
