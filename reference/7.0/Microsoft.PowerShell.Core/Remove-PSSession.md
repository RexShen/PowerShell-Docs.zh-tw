---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSession
ms.openlocfilehash: aa6965b3a21c145ecccb284d43c6d0913bb31027
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2020
ms.locfileid: "93201227"
---
# <span data-ttu-id="a0f88-103">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-103">Remove-PSSession</span></span>

## <span data-ttu-id="a0f88-104">概要</span><span class="sxs-lookup"><span data-stu-id="a0f88-104">SYNOPSIS</span></span>
<span data-ttu-id="a0f88-105"> (Pssession) 關閉一或多個 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="a0f88-105">Closes one or more PowerShell sessions (PSSessions).</span></span>

## <span data-ttu-id="a0f88-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0f88-106">SYNTAX</span></span>

### <span data-ttu-id="a0f88-107">Id (預設值)</span><span class="sxs-lookup"><span data-stu-id="a0f88-107">Id (Default)</span></span>

```
Remove-PSSession [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-108">工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-108">Session</span></span>

```
Remove-PSSession [-Session] <PSSession[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-109">ContainerId</span><span class="sxs-lookup"><span data-stu-id="a0f88-109">ContainerId</span></span>

```
Remove-PSSession -ContainerId <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-110">VMId</span><span class="sxs-lookup"><span data-stu-id="a0f88-110">VMId</span></span>

```
Remove-PSSession -VMId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-111">VMName</span><span class="sxs-lookup"><span data-stu-id="a0f88-111">VMName</span></span>

```
Remove-PSSession -VMName <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-112">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a0f88-112">InstanceId</span></span>

```
Remove-PSSession -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-113">Name</span><span class="sxs-lookup"><span data-stu-id="a0f88-113">Name</span></span>

```
Remove-PSSession -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a0f88-114">ComputerName</span><span class="sxs-lookup"><span data-stu-id="a0f88-114">ComputerName</span></span>

```
Remove-PSSession [-ComputerName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a0f88-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a0f88-115">DESCRIPTION</span></span>

<span data-ttu-id="a0f88-116">**移除 PSSession** Cmdlet 會關閉目前會話中 ( **Pssession** ) 的 PowerShell 會話。</span><span class="sxs-lookup"><span data-stu-id="a0f88-116">The **Remove-PSSession** cmdlet closes PowerShell sessions ( **PSSessions** ) in the current session.</span></span>
<span data-ttu-id="a0f88-117">它會停止任何在 **PSSession** 中執行的命令、結束 **PSSession** ，並釋放 **PSSession** 使用的資源。</span><span class="sxs-lookup"><span data-stu-id="a0f88-117">It stops any commands that are running in the **PSSessions** , ends the **PSSession** , and releases the resources that the **PSSession** was using.</span></span>
<span data-ttu-id="a0f88-118">若 **PSSession** 連線到遠端電腦，此 Cmdlet 也會關閉本機和遠端電腦之間的連線。</span><span class="sxs-lookup"><span data-stu-id="a0f88-118">If the **PSSession** is connected to a remote computer, this cmdlet also closes the connection between the local and remote computers.</span></span>

<span data-ttu-id="a0f88-119">若要移除 **PSSession** ，請輸入工作階段的 *Name* 、 *ComputerName* 、 *ID* 或 *InstanceID* 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-119">To remove a **PSSession** , enter the *Name* , *ComputerName* , *ID* , or *InstanceID* of the session.</span></span>

<span data-ttu-id="a0f88-120">若您已將 *PSSession* 儲存在變數中，工作階段物件仍會維持在該變數中，但 *PSSession* 的狀態是「已關閉」。</span><span class="sxs-lookup"><span data-stu-id="a0f88-120">If you have saved the *PSSession* in a variable, the session object remains in the variable, but the state of the *PSSession* is Closed.</span></span>

## <span data-ttu-id="a0f88-121">範例</span><span class="sxs-lookup"><span data-stu-id="a0f88-121">EXAMPLES</span></span>

### <span data-ttu-id="a0f88-122">範例 1︰使用識別碼移除工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-122">Example 1: Remove sessions by using IDs</span></span>

```powershell
Remove-PSSession -Id 1, 2
```

<span data-ttu-id="a0f88-123">此命令會移除具有識別碼 1 和 2 的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-123">This command removes the **PSSessions** that have IDs 1 and 2.</span></span>

### <span data-ttu-id="a0f88-124">範例 2︰移除目前工作階段中的所有工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-124">Example 2: Remove all the sessions in the current session</span></span>

```powershell
Get-PSSession | Remove-PSSession
Remove-PSSession -Session (Get-PSSession)
$s = Get-PSSession
Remove-PSSession -Session $s
```

<span data-ttu-id="a0f88-125">這些命令會移除目前工作階段中的所有 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-125">These commands remove all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="a0f88-126">雖然這三個命令的格式看起來不同，但它們作用相同。</span><span class="sxs-lookup"><span data-stu-id="a0f88-126">Although the three command formats look different, they have the same effect.</span></span>

### <span data-ttu-id="a0f88-127">範例 3︰使用名稱關閉工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-127">Example 3: Close sessions by using names</span></span>

```powershell
$r = Get-PSSession -ComputerName Serv*
$r | Remove-PSSession
```

<span data-ttu-id="a0f88-128">這些命令會關閉連線到名稱開頭為 Serv 之電腦的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-128">These commands close the **PSSessions** that are connected to computers that have names that begin with Serv.</span></span>

### <span data-ttu-id="a0f88-129">範例 4︰關閉連線至連接埠的工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-129">Example 4: Close sessions connected to a port</span></span>

```powershell
Get-PSSession | where {$_.port -eq 90} | Remove-PSSession
```

<span data-ttu-id="a0f88-130">此命令會關閉連線至連接埠 90 的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-130">This command closes the **PSSessions** that are connected to port 90.</span></span>
<span data-ttu-id="a0f88-131">您可以使用此命令格式，以 *ComputerName* 、 *Name* 、 *InstanceID* 及 *ID* 之外的屬性來識別 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-131">You can use this command format to identify **PSSessions** by properties other than *ComputerName* , *Name* , *InstanceID* , and *ID* .</span></span>

### <span data-ttu-id="a0f88-132">範例 5︰根據執行個體識別碼關閉工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-132">Example 5: Close a session based on instance ID</span></span>

```powershell
Get-PSSession | Format-Table ComputerName, InstanceID  -AutoSize
```

```Output
ComputerName InstanceId
------------ ----------------
Server01     875d231b-2788-4f36-9f67-2e50d63bb82a
localhost    c065ffa0-02c4-406e-84a3-dacb0d677868
Server02     4699cdbc-61d5-4e0d-b916-84f82ebede1f
Server03     4e5a3245-4c63-43e4-88d0-a7798bfc2414
TX-TEST-01   fc4e9dfa-f246-452d-9fa3-1adbdd64ae85 PS C:\> Remove-PSSession -InstanceID fc4e9dfa-f246-452d-9fa3-1adbdd64ae85
```

<span data-ttu-id="a0f88-133">這些命令示範如何根據其執行個體識別碼或 **RemoteRunspaceID** 來關閉 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-133">These commands show how to close a **PSSession** based on its instance ID, or **RemoteRunspaceID** .</span></span>

<span data-ttu-id="a0f88-134">第一個命令會使用 **Get-PSsession** Cmdlet，來取得目前工作階段中的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-134">The first command uses the **Get-PSSession** cmdlet to get the **PSSessions** in the current session.</span></span>
<span data-ttu-id="a0f88-135">它使用管線運算子 (|) 將 **PSSession** 傳送至 Format-Table Cmdlet，以將它們的 **ComputerName** 和 **InstanceID** 屬性格式化為表格。</span><span class="sxs-lookup"><span data-stu-id="a0f88-135">It uses a pipeline operator (|) to send the **PSSessions** to the Format-Table cmdlet, which formats their **ComputerName** and **InstanceID** properties in a table.</span></span>
<span data-ttu-id="a0f88-136">*AutoSize* 參數會壓縮顯示的欄位。</span><span class="sxs-lookup"><span data-stu-id="a0f88-136">The *AutoSize* parameter compresses the columns for display.</span></span>

<span data-ttu-id="a0f88-137">您可以從顯示的結果中識別要關閉的 **PSSession** ，並複製該 **PSSession** 的 *InstanceID* ，然後在第二個命令中貼上。</span><span class="sxs-lookup"><span data-stu-id="a0f88-137">From the resulting display, you can identify the **PSSession** to be closed, and copy and paste the *InstanceID* of that **PSSession** into the second command.</span></span>

<span data-ttu-id="a0f88-138">第二個命令會使用 **Remove-PSSession** Cmdlet，來移除具有指定執行個體識別碼的 *PSSession* 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-138">The second command uses the **Remove-PSSession** cmdlet to remove the *PSSession* with the specified instance ID.</span></span>

### <span data-ttu-id="a0f88-139">範例 6︰建立函式以刪除目前工作階段中所有的工作階段</span><span class="sxs-lookup"><span data-stu-id="a0f88-139">Example 6: Create a function that deletes all sessions in the current session</span></span>

```powershell
Function EndPSS { Get-PSSession | Remove-PSSession }
```

<span data-ttu-id="a0f88-140">此函式會刪除目前工作階段中所有的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-140">This function deletes all of the **PSSessions** in the current session.</span></span>
<span data-ttu-id="a0f88-141">將此函式新增至您的 PowerShell 設定檔之後，若要刪除所有的會話，請輸入 `EndPSS` 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-141">After you add this function to your PowerShell profile, to delete all sessions, type `EndPSS`.</span></span>

## <span data-ttu-id="a0f88-142">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a0f88-142">PARAMETERS</span></span>

### <span data-ttu-id="a0f88-143">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a0f88-143">-ComputerName</span></span>

<span data-ttu-id="a0f88-144">指定電腦名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-144">Specifies an array of names of computers.</span></span>
<span data-ttu-id="a0f88-145">此 Cmdlet 會關閉連線到指定電腦的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-145">This cmdlet closes the **PSSessions** that are connected to the specified computers.</span></span>
<span data-ttu-id="a0f88-146">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a0f88-146">Wildcard characters are permitted.</span></span>

<span data-ttu-id="a0f88-147">輸入一或多部遠端電腦的 NetBIOS 名稱、IP 位址或完整網域名稱。</span><span class="sxs-lookup"><span data-stu-id="a0f88-147">Type the NetBIOS name, an IP address, or a fully qualified domain name of one or more remote computers.</span></span>
<span data-ttu-id="a0f88-148">若要指定本機電腦，請輸入電腦名稱、localhost 或句點 (.)。</span><span class="sxs-lookup"><span data-stu-id="a0f88-148">To specify the local computer, type the computer name, localhost, or a dot (.).</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a0f88-149">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="a0f88-149">-ContainerId</span></span>

<span data-ttu-id="a0f88-150">指定容器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-150">Specifies an array of IDs of containers.</span></span> <span data-ttu-id="a0f88-151">此 Cmdlet 會移除每個指定容器的會話。</span><span class="sxs-lookup"><span data-stu-id="a0f88-151">This cmdlet removes sessions for each of the specified containers.</span></span> <span data-ttu-id="a0f88-152">使用 `docker ps` 命令來取得容器識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="a0f88-152">Use the `docker ps` command to get a list of container IDs.</span></span> <span data-ttu-id="a0f88-153">如需詳細資訊，請參閱 [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) 命令的說明。</span><span class="sxs-lookup"><span data-stu-id="a0f88-153">For more information, see the help for the [docker ps](https://docs.docker.com/engine/reference/commandline/ps/) command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ContainerId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-154">-Id</span><span class="sxs-lookup"><span data-stu-id="a0f88-154">-Id</span></span>

<span data-ttu-id="a0f88-155">指定工作階段識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-155">Specifies an array of IDs of sessions.</span></span>
<span data-ttu-id="a0f88-156">此 Cmdlet 會關閉具有指定識別碼的 *PSSession* 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-156">This cmdlet closes the *PSSessions* with the specified IDs.</span></span>
<span data-ttu-id="a0f88-157">輸入一或多個識別碼 (以逗號分隔)，或使用範圍運算子 (..) 來指定某個範圍的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a0f88-157">Type one or more IDs, separated by commas, or use the range operator (..) to specify a range of IDs.</span></span>

<span data-ttu-id="a0f88-158">識別碼是整數，可唯一識別目前工作階段中的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-158">An ID is an integer that uniquely identifies the **PSSession** in the current session.</span></span>
<span data-ttu-id="a0f88-159">與 *InstanceId* 相比，它比較容易記住並輸入，但是它只有在目前工作階段內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a0f88-159">It is easier to remember and type than the *InstanceId* , but it is unique only in the current session.</span></span>
<span data-ttu-id="a0f88-160">若要尋找 **PSSession** 的識別碼，請執行 Get-PSSession 且不搭配任何參數。</span><span class="sxs-lookup"><span data-stu-id="a0f88-160">To find the ID of a **PSSession** , run the Get-PSSession cmdlet without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-161">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="a0f88-161">-InstanceId</span></span>

<span data-ttu-id="a0f88-162">指定執行階段識別碼的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-162">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="a0f88-163">此 Cmdlet 會關閉具有指定執行個體識別碼的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-163">This cmdlet closes the **PSSessions** that have the specified instance IDs.</span></span>

<span data-ttu-id="a0f88-164">執行個體識別碼是 GUID，可唯一識別目前工作階段中的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-164">The instance ID is a GUID that uniquely identifies a **PSSession** in the current session.</span></span>
<span data-ttu-id="a0f88-165">執行個體識別碼是唯一的，即使在同一部電腦上有多個正在執行的工作階段也一樣。</span><span class="sxs-lookup"><span data-stu-id="a0f88-165">The instance ID is unique, even when you have multiple sessions running on a single computer.</span></span>

<span data-ttu-id="a0f88-166">執行個體識別碼會儲存在代表 **PSSession** 之物件的 **InstanceID** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="a0f88-166">The instance ID is stored in the **InstanceID** property of the object that represents a **PSSession** .</span></span>
<span data-ttu-id="a0f88-167">若要在目前工作階段中尋找 **PSSessions** 的 **InstanceID** ，請輸入 `Get-PSSession | Format-Table Name, ComputerName, InstanceId`。</span><span class="sxs-lookup"><span data-stu-id="a0f88-167">To find the **InstanceID** of the **PSSessions** in the current session, type `Get-PSSession | Format-Table Name, ComputerName, InstanceId`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-168">-Name</span><span class="sxs-lookup"><span data-stu-id="a0f88-168">-Name</span></span>

<span data-ttu-id="a0f88-169">指定工作階段好記名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-169">Specifies an array of friendly names of sessions.</span></span>
<span data-ttu-id="a0f88-170">此 Cmdlet 會關閉具有指定好記名稱的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-170">This cmdlet closes the **PSSessions** that have the specified friendly names.</span></span>
<span data-ttu-id="a0f88-171">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="a0f88-171">Wildcard characters are permitted.</span></span>

<span data-ttu-id="a0f88-172">由於 **PSSession** 的好記名稱可能不是唯一的，因此在使用 *Name* 參數時，請考慮在 **Remove-PSSession** 命令中使用 *WhatIf* 或 *Confirm* 參數。</span><span class="sxs-lookup"><span data-stu-id="a0f88-172">Because the friendly name of a **PSSession** might not be unique, when you use the *Name* parameter, consider also using the *WhatIf* or *Confirm* parameter in the **Remove-PSSession** command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="a0f88-173">-Session</span><span class="sxs-lookup"><span data-stu-id="a0f88-173">-Session</span></span>

<span data-ttu-id="a0f88-174">指定要關閉的 **PSSession** 工作階段物件。</span><span class="sxs-lookup"><span data-stu-id="a0f88-174">Specifies the session objects of the **PSSessions** to close.</span></span>
<span data-ttu-id="a0f88-175">輸入包含 **PSSession** 的變數，或輸入會建立或取得 **PSSession** 的命令 (例如 New-PSSession 或 **Get-PSSession** 命令)。</span><span class="sxs-lookup"><span data-stu-id="a0f88-175">Enter a variable that contains the **PSSessions** or a command that creates or gets the **PSSessions** , such as a New-PSSession or **Get-PSSession** command.</span></span>
<span data-ttu-id="a0f88-176">您也可以使用管線將一或多個工作階段物件傳送至 **Remove-PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-176">You can also pipe one or more session objects to **Remove-PSSession** .</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-177">-VMId</span><span class="sxs-lookup"><span data-stu-id="a0f88-177">-VMId</span></span>

<span data-ttu-id="a0f88-178">指定虛擬機器的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-178">Specifies an array of ID of virtual machines.</span></span>
<span data-ttu-id="a0f88-179">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="a0f88-179">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="a0f88-180">若要查看可供您使用的虛擬機器，請使用下列命令：</span><span class="sxs-lookup"><span data-stu-id="a0f88-180">To see the virtual machines that are available to you, use the following command:</span></span>

`Get-VM | Select-Object -Property Name, ID`

```yaml
Type: System.Guid[]
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-181">-VMName</span><span class="sxs-lookup"><span data-stu-id="a0f88-181">-VMName</span></span>

<span data-ttu-id="a0f88-182">指定虛擬機器名稱的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0f88-182">Specifies an array of names of virtual machines.</span></span>
<span data-ttu-id="a0f88-183">此 Cmdlet 會在每個指定的虛擬機器之間啟動互動式會話。</span><span class="sxs-lookup"><span data-stu-id="a0f88-183">This cmdlet starts an interactive session with each of the specified virtual machines.</span></span>
<span data-ttu-id="a0f88-184">若要查看可供您使用的虛擬機器，請使用 **取得 VM** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0f88-184">To see the virtual machines that are available to you, use the **Get-VM** cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: VMName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a0f88-185">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a0f88-185">-Confirm</span></span>

<span data-ttu-id="a0f88-186">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a0f88-186">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a0f88-187">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a0f88-187">-WhatIf</span></span>

<span data-ttu-id="a0f88-188">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a0f88-188">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a0f88-189">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a0f88-189">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a0f88-190">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0f88-190">CommonParameters</span></span>

<span data-ttu-id="a0f88-191">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a0f88-191">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0f88-192">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a0f88-192">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0f88-193">輸入</span><span class="sxs-lookup"><span data-stu-id="a0f88-193">INPUTS</span></span>

### <span data-ttu-id="a0f88-194">System.Management.Automation.Runspaces.PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-194">System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="a0f88-195">您可以使用管線將工作階段物件傳送至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a0f88-195">You can pipe a session object to this cmdlet.</span></span>

## <span data-ttu-id="a0f88-196">輸出</span><span class="sxs-lookup"><span data-stu-id="a0f88-196">OUTPUTS</span></span>

### <span data-ttu-id="a0f88-197">無</span><span class="sxs-lookup"><span data-stu-id="a0f88-197">None</span></span>

<span data-ttu-id="a0f88-198">此 Cmdlet 不會傳回任何物件。</span><span class="sxs-lookup"><span data-stu-id="a0f88-198">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="a0f88-199">注意</span><span class="sxs-lookup"><span data-stu-id="a0f88-199">NOTES</span></span>

* <span data-ttu-id="a0f88-200">*Id* 參數是必要的。</span><span class="sxs-lookup"><span data-stu-id="a0f88-200">The *Id* parameter is mandatory.</span></span> <span data-ttu-id="a0f88-201">若要刪除目前工作階段中所有的 **PSSession** ，請輸入 `Get-PSSession | Remove-PSSession`。</span><span class="sxs-lookup"><span data-stu-id="a0f88-201">To delete all the **PSSessions** in the current session, type `Get-PSSession | Remove-PSSession`.</span></span>
* <span data-ttu-id="a0f88-202">**PSSession** 會使用遠端電腦的持續連線。</span><span class="sxs-lookup"><span data-stu-id="a0f88-202">A **PSSession** uses a persistent connection to a remote computer.</span></span> <span data-ttu-id="a0f88-203">建立 **PSSession** 來執行一系列共用資料的命令。</span><span class="sxs-lookup"><span data-stu-id="a0f88-203">Create a **PSSession** to run a series of commands that share data.</span></span> <span data-ttu-id="a0f88-204">如需詳細資訊，請鍵入 `Get-Help about_PSSessions`。</span><span class="sxs-lookup"><span data-stu-id="a0f88-204">For more information, type `Get-Help about_PSSessions`.</span></span>
* <span data-ttu-id="a0f88-205">**PSSession** 專屬於目前的工作階段。</span><span class="sxs-lookup"><span data-stu-id="a0f88-205">**PSSessions** are specific to the current session.</span></span> <span data-ttu-id="a0f88-206">當您結束工作階段時，即會強制關閉您在該工作階段中建立的 **PSSession** 。</span><span class="sxs-lookup"><span data-stu-id="a0f88-206">When you end a session, the **PSSessions** that you created in that session are forcibly closed.</span></span>

## <span data-ttu-id="a0f88-207">相關連結</span><span class="sxs-lookup"><span data-stu-id="a0f88-207">RELATED LINKS</span></span>

[<span data-ttu-id="a0f88-208">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-208">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="a0f88-209">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-209">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="a0f88-210">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-210">Enter-PSSession</span></span>](Enter-PSSession.md)

[<span data-ttu-id="a0f88-211">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-211">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="a0f88-212">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-212">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="a0f88-213">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a0f88-213">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="a0f88-214">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-214">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="a0f88-215">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="a0f88-215">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="a0f88-216">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a0f88-216">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="a0f88-217">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a0f88-217">about_Remote</span></span>](About/about_Remote.md)
