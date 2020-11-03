---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204091"
---
# <span data-ttu-id="5f2fe-103">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="5f2fe-103">Checkpoint-Computer</span></span>

## <span data-ttu-id="5f2fe-104">概要</span><span class="sxs-lookup"><span data-stu-id="5f2fe-104">SYNOPSIS</span></span>
<span data-ttu-id="5f2fe-105">在本機電腦上建立系統還原點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-105">Creates a system restore point on the local computer.</span></span>

## <span data-ttu-id="5f2fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f2fe-106">SYNTAX</span></span>

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## <span data-ttu-id="5f2fe-107">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="5f2fe-107">DESCRIPTION</span></span>

<span data-ttu-id="5f2fe-108">`Checkpoint-Computer`Cmdlet 會在本機電腦上建立系統還原點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-108">The `Checkpoint-Computer` cmdlet creates a system restore point on the local computer.</span></span>

<span data-ttu-id="5f2fe-109">`Checkpoint-Computer`只有用戶端作業系統（例如 Windows 8、windows 7、Windows Vista 和 WINDOWS XP）才支援系統還原點和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-109">System restore points and the `Checkpoint-Computer` cmdlet are supported only on client operating systems, such as Windows 8, Windows 7, Windows Vista, and Windows XP.</span></span>

<span data-ttu-id="5f2fe-110">從 Windows 8 開始， `Checkpoint-Computer` 每天不能建立一個以上的檢查點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-110">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one checkpoint each day.</span></span>

## <span data-ttu-id="5f2fe-111">範例</span><span class="sxs-lookup"><span data-stu-id="5f2fe-111">EXAMPLES</span></span>

### <span data-ttu-id="5f2fe-112">範例 1︰建立系統還原點</span><span class="sxs-lookup"><span data-stu-id="5f2fe-112">Example 1: Create a system restore point</span></span>

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

<span data-ttu-id="5f2fe-113">此命令建立名為 Install MyApp 的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-113">This command creates a system restore point called Install MyApp.</span></span>
<span data-ttu-id="5f2fe-114">它使用預設的 APPLICATION_INSTALL 還原點類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-114">It uses the default APPLICATION_INSTALL restore point type.</span></span>

### <span data-ttu-id="5f2fe-115">範例 2︰建立 MODIFY_SETTINGS 系統還原點</span><span class="sxs-lookup"><span data-stu-id="5f2fe-115">Example 2: Create a system MODIFY_SETTINGS restore point</span></span>

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

<span data-ttu-id="5f2fe-116">此命令建立名為 "ChangeNetSettings" 的 MODIFY_SETTINGS 系統還原點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-116">This command creates a MODIFY_SETTINGS system restore point called "ChangeNetSettings".</span></span>

## <span data-ttu-id="5f2fe-117">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5f2fe-117">PARAMETERS</span></span>

### <span data-ttu-id="5f2fe-118">-Description</span><span class="sxs-lookup"><span data-stu-id="5f2fe-118">-Description</span></span>

<span data-ttu-id="5f2fe-119">指定還原點的描述性名稱。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-119">Specifies a descriptive name for the restore point.</span></span>
<span data-ttu-id="5f2fe-120">這是必要參數。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-120">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f2fe-121">-RestorePointType</span><span class="sxs-lookup"><span data-stu-id="5f2fe-121">-RestorePointType</span></span>

<span data-ttu-id="5f2fe-122">指定還原點的類型。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-122">Specifies the type of restore point.</span></span>
<span data-ttu-id="5f2fe-123">預設為 APPLICATION_INSTALL。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-123">The default is APPLICATION_INSTALL.</span></span>

<span data-ttu-id="5f2fe-124">此參數可接受的值為：</span><span class="sxs-lookup"><span data-stu-id="5f2fe-124">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5f2fe-125">APPLICATION_INSTALL</span><span class="sxs-lookup"><span data-stu-id="5f2fe-125">APPLICATION_INSTALL</span></span>
- <span data-ttu-id="5f2fe-126">APPLICATION_UNINSTALL</span><span class="sxs-lookup"><span data-stu-id="5f2fe-126">APPLICATION_UNINSTALL</span></span>
- <span data-ttu-id="5f2fe-127">DEVICE_DRIVER_INSTALL</span><span class="sxs-lookup"><span data-stu-id="5f2fe-127">DEVICE_DRIVER_INSTALL</span></span>
- <span data-ttu-id="5f2fe-128">MODIFY_SETTINGS</span><span class="sxs-lookup"><span data-stu-id="5f2fe-128">MODIFY_SETTINGS</span></span>
- <span data-ttu-id="5f2fe-129">CANCELLED_OPERATION</span><span class="sxs-lookup"><span data-stu-id="5f2fe-129">CANCELLED_OPERATION</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5f2fe-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f2fe-130">CommonParameters</span></span>

<span data-ttu-id="5f2fe-131">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f2fe-132">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-132">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5f2fe-133">輸入</span><span class="sxs-lookup"><span data-stu-id="5f2fe-133">INPUTS</span></span>

### <span data-ttu-id="5f2fe-134">無</span><span class="sxs-lookup"><span data-stu-id="5f2fe-134">None</span></span>

<span data-ttu-id="5f2fe-135">您無法透過管道傳送物件至 `Checkpoint-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-135">You cannot pipe objects to `Checkpoint-Computer`.</span></span>

## <span data-ttu-id="5f2fe-136">輸出</span><span class="sxs-lookup"><span data-stu-id="5f2fe-136">OUTPUTS</span></span>

### <span data-ttu-id="5f2fe-137">無</span><span class="sxs-lookup"><span data-stu-id="5f2fe-137">None</span></span>

<span data-ttu-id="5f2fe-138">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-138">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5f2fe-139">注意</span><span class="sxs-lookup"><span data-stu-id="5f2fe-139">NOTES</span></span>

- <span data-ttu-id="5f2fe-140">此 Cmdlet 會使用 **SystemRestore** 類別的 **CreateRestorePoint** 方法搭配 **BEGIN_SYSTEM_CHANGE** 事件。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-140">This cmdlet uses the **CreateRestorePoint** method of the **SystemRestore** class with a **BEGIN_SYSTEM_CHANGE** event.</span></span>
- <span data-ttu-id="5f2fe-141">從 Windows 8 開始， `Checkpoint-Computer` 每天不能建立超過一個系統還原點。</span><span class="sxs-lookup"><span data-stu-id="5f2fe-141">Beginning in Windows 8, `Checkpoint-Computer` cannot create more than one system restore point each day.</span></span> <span data-ttu-id="5f2fe-142">如果您嘗試在 24 小時的期間內建立新的還原點，Windows PowerShell 會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="5f2fe-142">If you try to create a new restore point before the 24-hour period has elapsed, Windows PowerShell generates the following error:</span></span>

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## <span data-ttu-id="5f2fe-143">相關連結</span><span class="sxs-lookup"><span data-stu-id="5f2fe-143">RELATED LINKS</span></span>

[<span data-ttu-id="5f2fe-144">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5f2fe-144">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="5f2fe-145">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="5f2fe-145">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="5f2fe-146">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="5f2fe-146">Get-ComputerRestorePoint</span></span>](Get-ComputerRestorePoint.md)

[<span data-ttu-id="5f2fe-147">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="5f2fe-147">Restore-Computer</span></span>](Restore-Computer.md)
