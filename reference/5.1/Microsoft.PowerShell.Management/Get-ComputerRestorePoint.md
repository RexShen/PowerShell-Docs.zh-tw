---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/13/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerrestorepoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerRestorePoint
ms.openlocfilehash: 73819aafee9ed1911354daf9af23eedff0a3e14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204027"
---
# <span data-ttu-id="241f1-103">Get-ComputerRestorePoint</span><span class="sxs-lookup"><span data-stu-id="241f1-103">Get-ComputerRestorePoint</span></span>

## <span data-ttu-id="241f1-104">概要</span><span class="sxs-lookup"><span data-stu-id="241f1-104">SYNOPSIS</span></span>
<span data-ttu-id="241f1-105">在本機電腦上取得還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-105">Gets the restore points on the local computer.</span></span>

## <span data-ttu-id="241f1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="241f1-106">SYNTAX</span></span>

### <span data-ttu-id="241f1-107">ID (預設值)</span><span class="sxs-lookup"><span data-stu-id="241f1-107">ID (Default)</span></span>

```
Get-ComputerRestorePoint [[-RestorePoint] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="241f1-108">LastStatus</span><span class="sxs-lookup"><span data-stu-id="241f1-108">LastStatus</span></span>

```
Get-ComputerRestorePoint -LastStatus [<CommonParameters>]
```

## <span data-ttu-id="241f1-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="241f1-109">DESCRIPTION</span></span>

<span data-ttu-id="241f1-110">此 `Get-ComputerRestorePoint` Cmdlet 會取得本機電腦的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-110">The `Get-ComputerRestorePoint` cmdlet gets the local computer's system restore points.</span></span> <span data-ttu-id="241f1-111">而且，它可以顯示最近嘗試還原電腦的狀態。</span><span class="sxs-lookup"><span data-stu-id="241f1-111">And, it can display the status of the most recent attempt to restore the computer.</span></span>

<span data-ttu-id="241f1-112">您可以使用中的資訊 `Get-ComputerRestorePoint` 來選取還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-112">You can use the information from `Get-ComputerRestorePoint` to select a restore point.</span></span> <span data-ttu-id="241f1-113">例如，使用序號來識別 Cmdlet 的還原點 `Restore-Computer` 。</span><span class="sxs-lookup"><span data-stu-id="241f1-113">For example, use a sequence number to identify a restore point for the `Restore-Computer` cmdlet.</span></span>

<span data-ttu-id="241f1-114">`Get-ComputerRestorePoint`只有用戶端作業系統（例如 Windows 10、windows 7、Windows Vista 和 WINDOWS XP）才支援系統還原點和 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="241f1-114">System restore points and the `Get-ComputerRestorePoint` cmdlet are supported only on client operating systems such as Windows 10, Windows 7, Windows Vista, and Windows XP.</span></span>

## <span data-ttu-id="241f1-115">範例</span><span class="sxs-lookup"><span data-stu-id="241f1-115">EXAMPLES</span></span>

### <span data-ttu-id="241f1-116">範例1：取得所有系統還原點</span><span class="sxs-lookup"><span data-stu-id="241f1-116">Example 1: Get all system restore points</span></span>

<span data-ttu-id="241f1-117">在此範例中，會 `Get-ComputerRestorePoint` 取得所有本機電腦的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-117">In this example, `Get-ComputerRestorePoint` gets all the local computer's system restore points.</span></span>

```powershell
Get-ComputerRestorePoint
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
8/7/2019  12:56:45     Installed PowerShell 6-x64     6                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

### <span data-ttu-id="241f1-118">範例2：取得特定序號</span><span class="sxs-lookup"><span data-stu-id="241f1-118">Example 2: Get specific sequence numbers</span></span>

<span data-ttu-id="241f1-119">此範例會取得特定序號的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-119">This example gets system restore points for specific sequence numbers.</span></span>

```powershell
Get-ComputerRestorePoint -RestorePoint 4, 5
```

```Output
CreationTime           Description                    SequenceNumber    EventType         RestorePointType
------------           -----------                    --------------    ---------         ----------------
7/30/2019 09:17:24     Windows Update                 4                 BEGIN_SYSTEM_C... 17
8/5/2019  08:15:37     Installed PowerShell 7-prev... 5                 BEGIN_SYSTEM_C... APPLICATION_INSTALL
```

<span data-ttu-id="241f1-120">`Get-ComputerRestorePoint` 使用 **RestorePoint** 參數來指定以逗號分隔的序號陣列。</span><span class="sxs-lookup"><span data-stu-id="241f1-120">`Get-ComputerRestorePoint` uses the **RestorePoint** parameter to specify a comma-separated array of sequence numbers.</span></span>

### <span data-ttu-id="241f1-121">範例3：顯示系統還原的狀態</span><span class="sxs-lookup"><span data-stu-id="241f1-121">Example 3: Display the status of a system restore</span></span>

<span data-ttu-id="241f1-122">此範例會顯示本機電腦上最近系統還原的狀態。</span><span class="sxs-lookup"><span data-stu-id="241f1-122">This example displays the status of the most recent system restore on the local computer.</span></span>

```powershell
Get-ComputerRestorePoint -LastStatus
```

```Output
The last attempt to restore the computer failed.
```

<span data-ttu-id="241f1-123">`Get-ComputerRestorePoint` 使用 **LastStatus** 參數來顯示最近系統還原的結果。</span><span class="sxs-lookup"><span data-stu-id="241f1-123">`Get-ComputerRestorePoint` uses the **LastStatus** parameter to display the result of the most recent system restore.</span></span>

### <span data-ttu-id="241f1-124">範例4：使用運算式來轉換 CreationTime</span><span class="sxs-lookup"><span data-stu-id="241f1-124">Example 4: Use an expression to convert the CreationTime</span></span>

<span data-ttu-id="241f1-125">`Get-ComputerRestorePoint` 將 **CreationTime** 輸出為 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) 日期和時間字串。</span><span class="sxs-lookup"><span data-stu-id="241f1-125">`Get-ComputerRestorePoint` outputs the **CreationTime** as a Windows Management Instrumentation (WMI) date and time string.</span></span>

<span data-ttu-id="241f1-126">在此範例中，變數會儲存將 **CreationTime** 字串轉換成 **DateTime** 物件的運算式。</span><span class="sxs-lookup"><span data-stu-id="241f1-126">In this example, a variable stores an expression that converts the **CreationTime** string to a **DateTime** object.</span></span> <span data-ttu-id="241f1-127">若要在轉換之前先查看 **CreationTime** 字串，請使用類似的命令 `((Get-ComputerRestorePoint).CreationTime)` 。</span><span class="sxs-lookup"><span data-stu-id="241f1-127">To view **CreationTime** strings before they're converted, use a command such as `((Get-ComputerRestorePoint).CreationTime)`.</span></span> <span data-ttu-id="241f1-128">如需 WMI 日期和時間字串的詳細資訊，請參閱 [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime)。</span><span class="sxs-lookup"><span data-stu-id="241f1-128">For more information about the WMI date and time string, see [CIM_DATETIME](/windows/win32/wmisdk/cim-datetime).</span></span>

```powershell
$date = @{Label="Date"; Expression={$_.ConvertToDateTime($_.CreationTime)}}
Get-ComputerRestorePoint | Select-Object -Property SequenceNumber, $date, Description
```

```Output
SequenceNumber   Date                 Description
--------------   ----                 -----------
             4   7/30/2019 09:17:24   Windows Update
             5   8/5/2019  08:15:37   Installed PowerShell 7-preview-x64
             6   8/7/2019  12:56:45   Installed PowerShell 6-x64
```

<span data-ttu-id="241f1-129">`$date`變數會利用使用 **ConvertToDateTime** 方法的運算式來儲存雜湊表。</span><span class="sxs-lookup"><span data-stu-id="241f1-129">The `$date` variable stores a hash table with the expression that uses the **ConvertToDateTime** method.</span></span> <span data-ttu-id="241f1-130">運算式會將 **CreationTime** 屬性的值從 WMI 字串轉換成 **DateTime** 物件。</span><span class="sxs-lookup"><span data-stu-id="241f1-130">The expression converts the **CreationTime** property's value from a WMI string to a **DateTime** object.</span></span>

<span data-ttu-id="241f1-131">`Get-ComputerRestorePoint` 將系統還原點物件沿著管線向下傳送。</span><span class="sxs-lookup"><span data-stu-id="241f1-131">`Get-ComputerRestorePoint` sends the system restore point objects down the pipeline.</span></span> <span data-ttu-id="241f1-132">`Select-Object` 使用 **Property** 參數來指定要顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="241f1-132">`Select-Object` uses the **Property** parameter to specify the properties to display.</span></span> <span data-ttu-id="241f1-133">針對管線中的每個物件，中的運算式會 `$date` 轉換 **CreationTime** ，並在 **Date** 屬性中輸出結果。</span><span class="sxs-lookup"><span data-stu-id="241f1-133">For each object in the pipeline, the expression in `$date` converts the **CreationTime** and outputs the result in the **Date** property.</span></span>

### <span data-ttu-id="241f1-134">範例5：使用屬性取得序號</span><span class="sxs-lookup"><span data-stu-id="241f1-134">Example 5: Use a property to get a sequence number</span></span>

<span data-ttu-id="241f1-135">此範例會使用 **SequenceNumber** 屬性和陣列索引來取得序號。</span><span class="sxs-lookup"><span data-stu-id="241f1-135">This example gets a sequence number by using the **SequenceNumber** property and an array index.</span></span> <span data-ttu-id="241f1-136">輸出只包含序號。</span><span class="sxs-lookup"><span data-stu-id="241f1-136">The output only contains the sequence number.</span></span>

```powershell
((Get-ComputerRestorePoint).SequenceNumber)[-1]
```

```Output
6
```

<span data-ttu-id="241f1-137">`Get-ComputerRestorePoint` 使用 **SequenceNumber** 屬性搭配陣列索引。</span><span class="sxs-lookup"><span data-stu-id="241f1-137">`Get-ComputerRestorePoint` uses the **SequenceNumber** property with an array index.</span></span> <span data-ttu-id="241f1-138">的陣列索引會 `-1` 取得陣列中最近的序號。</span><span class="sxs-lookup"><span data-stu-id="241f1-138">The array index of `-1` gets the most recent sequence number in the array.</span></span>

## <span data-ttu-id="241f1-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="241f1-139">PARAMETERS</span></span>

### <span data-ttu-id="241f1-140">-LastStatus</span><span class="sxs-lookup"><span data-stu-id="241f1-140">-LastStatus</span></span>

<span data-ttu-id="241f1-141">表示 `Get-ComputerRestorePoint` 取得最新系統還原作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="241f1-141">Indicates that `Get-ComputerRestorePoint` gets the status of the most recent system restore operation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LastStatus
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f1-142">-RestorePoint</span><span class="sxs-lookup"><span data-stu-id="241f1-142">-RestorePoint</span></span>

<span data-ttu-id="241f1-143">指定系統還原點的序號。</span><span class="sxs-lookup"><span data-stu-id="241f1-143">Specifies the sequence numbers of the system restore points.</span></span> <span data-ttu-id="241f1-144">您可以指定單一序號或序號的逗號分隔陣列。</span><span class="sxs-lookup"><span data-stu-id="241f1-144">You can specify either a single sequence number or a comma-separated array of sequence numbers.</span></span>

<span data-ttu-id="241f1-145">如果未指定 **RestorePoint** 參數，則會傳回 `Get-ComputerRestorePoint` 所有本機電腦的系統還原點。</span><span class="sxs-lookup"><span data-stu-id="241f1-145">If the **RestorePoint** parameter isn't specified, `Get-ComputerRestorePoint` returns all the local computer's system restore points.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: ID
Aliases:

Required: False
Position: 0
Default value: All restore points
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="241f1-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="241f1-146">CommonParameters</span></span>

<span data-ttu-id="241f1-147">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="241f1-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="241f1-148">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="241f1-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="241f1-149">輸入</span><span class="sxs-lookup"><span data-stu-id="241f1-149">INPUTS</span></span>

### <span data-ttu-id="241f1-150">無</span><span class="sxs-lookup"><span data-stu-id="241f1-150">None</span></span>

<span data-ttu-id="241f1-151">您無法將物件沿著管線向下傳送至 `Get-ComputerRestorePoint` 。</span><span class="sxs-lookup"><span data-stu-id="241f1-151">You can't send objects down the pipeline to `Get-ComputerRestorePoint`.</span></span>

## <span data-ttu-id="241f1-152">輸出</span><span class="sxs-lookup"><span data-stu-id="241f1-152">OUTPUTS</span></span>

### <span data-ttu-id="241f1-153">System.management.managementobject # root\default\SystemRestore 或 String</span><span class="sxs-lookup"><span data-stu-id="241f1-153">System.Management.ManagementObject#root\default\SystemRestore or String</span></span>

<span data-ttu-id="241f1-154">`Get-ComputerRestorePoint` 傳回 **SystemRestore** 物件，這是 WINDOWS MANAGEMENT INSTRUMENTATION (WMI) **SystemRestore** 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="241f1-154">`Get-ComputerRestorePoint` returns a **SystemRestore** object, which is an instance of the Windows Management Instrumentation (WMI) **SystemRestore** class.</span></span>

<span data-ttu-id="241f1-155">當您使用 **LastStatus** 參數時，會傳回 `Get-ComputerRestorePoint` 字串。</span><span class="sxs-lookup"><span data-stu-id="241f1-155">When you use the **LastStatus** parameter, `Get-ComputerRestorePoint` returns a string.</span></span>

## <span data-ttu-id="241f1-156">注意</span><span class="sxs-lookup"><span data-stu-id="241f1-156">NOTES</span></span>

<span data-ttu-id="241f1-157">若要 `Get-ComputerRestorePoint` 在 Windows Vista 和更新版本的 windows 上執行命令，請使用 [以 **系統管理員身分執行** ] 選項開啟 PowerShell。</span><span class="sxs-lookup"><span data-stu-id="241f1-157">To run a `Get-ComputerRestorePoint` command on Windows Vista and later versions of Windows, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="241f1-158">`Get-ComputerRestorePoint` 使用 WMI **SystemRestore** 類別。</span><span class="sxs-lookup"><span data-stu-id="241f1-158">`Get-ComputerRestorePoint` uses the WMI **SystemRestore** class.</span></span>

## <span data-ttu-id="241f1-159">相關連結</span><span class="sxs-lookup"><span data-stu-id="241f1-159">RELATED LINKS</span></span>

[<span data-ttu-id="241f1-160">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="241f1-160">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="241f1-161">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="241f1-161">about_Arrays</span></span>](../Microsoft.PowerShell.Core/About/about_Arrays.md)

[<span data-ttu-id="241f1-162">Checkpoint-Computer</span><span class="sxs-lookup"><span data-stu-id="241f1-162">Checkpoint-Computer</span></span>](Checkpoint-Computer.md)

[<span data-ttu-id="241f1-163">Disable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="241f1-163">Disable-ComputerRestore</span></span>](Disable-ComputerRestore.md)

[<span data-ttu-id="241f1-164">Enable-ComputerRestore</span><span class="sxs-lookup"><span data-stu-id="241f1-164">Enable-ComputerRestore</span></span>](Enable-ComputerRestore.md)

[<span data-ttu-id="241f1-165">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="241f1-165">Restart-Computer</span></span>](Restart-Computer.md)

[<span data-ttu-id="241f1-166">Restore-Computer</span><span class="sxs-lookup"><span data-stu-id="241f1-166">Restore-Computer</span></span>](Restore-Computer.md)

[<span data-ttu-id="241f1-167">SystemRestore</span><span class="sxs-lookup"><span data-stu-id="241f1-167">SystemRestore</span></span>](/windows/win32/sr/systemrestore)
