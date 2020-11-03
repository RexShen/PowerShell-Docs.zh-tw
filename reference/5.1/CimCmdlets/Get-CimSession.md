---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimsession?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimSession
ms.openlocfilehash: 83425948e5fc4d7170a2e3a6e883f71df386fdb5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93202503"
---
# <span data-ttu-id="cf612-103">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="cf612-103">Get-CimSession</span></span>

## <span data-ttu-id="cf612-104">概要</span><span class="sxs-lookup"><span data-stu-id="cf612-104">SYNOPSIS</span></span>
<span data-ttu-id="cf612-105">從目前的會話取得 CIM 會話物件。</span><span class="sxs-lookup"><span data-stu-id="cf612-105">Gets the CIM session objects from the current session.</span></span>

## <span data-ttu-id="cf612-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cf612-106">SYNTAX</span></span>

### <span data-ttu-id="cf612-107">ComputerNameSet (預設值)</span><span class="sxs-lookup"><span data-stu-id="cf612-107">ComputerNameSet (Default)</span></span>

```
Get-CimSession [[-ComputerName] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="cf612-108">SessionIdSet</span><span class="sxs-lookup"><span data-stu-id="cf612-108">SessionIdSet</span></span>

```
Get-CimSession [-Id] <UInt32[]> [<CommonParameters>]
```

### <span data-ttu-id="cf612-109">InstanceIdSet</span><span class="sxs-lookup"><span data-stu-id="cf612-109">InstanceIdSet</span></span>

```
Get-CimSession -InstanceId <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="cf612-110">NameSet</span><span class="sxs-lookup"><span data-stu-id="cf612-110">NameSet</span></span>

```
Get-CimSession -Name <String[]> [<CommonParameters>]
```

## <span data-ttu-id="cf612-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cf612-111">DESCRIPTION</span></span>

<span data-ttu-id="cf612-112">根據預設，此 Cmdlet 會取得在目前 PowerShell 會話中建立的所有 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-112">By default, the cmdlet gets all of the CIM sessions created in the current PowerShell session.</span></span> <span data-ttu-id="cf612-113">您可以使用的參數 `Get-CimSession` 取得特定電腦的會話，也可以使用其名稱或其他識別碼來識別會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-113">You can use the parameters of `Get-CimSession` to get the sessions that are for particular computers, or you can identify sessions by their names or other identifiers.</span></span> <span data-ttu-id="cf612-114">`Get-CimSession` 不會取得在其他 PowerShell 會話中建立的 CIM 會話，或是在其他電腦上建立的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-114">`Get-CimSession` does not get CIM sessions that were created in other PowerShell sessions or that were created on other computers.</span></span>

<span data-ttu-id="cf612-115">如需 CIM 會話的詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="cf612-115">For more information about CIM sessions, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

## <span data-ttu-id="cf612-116">範例</span><span class="sxs-lookup"><span data-stu-id="cf612-116">EXAMPLES</span></span>

### <span data-ttu-id="cf612-117">範例1：從目前的 PowerShell 會話取得 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="cf612-117">Example 1: Get CIM sessions from the current PowerShell session</span></span>

<span data-ttu-id="cf612-118">此範例會使用 [CimSession](New-CimSession.md)建立 cim 會話，然後使用來取得 cim 會話 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="cf612-118">This example creates CIM sessions using [New-CimSession](New-CimSession.md), and then gets the CIM sessions using `Get-CimSession`.</span></span>

```powershell
New-CimSession -ComputerName Server01,Server02
Get-CimSession
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc3-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="cf612-119">範例2：取得特定電腦的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="cf612-119">Example 2: Get the CIM sessions to a specific computer</span></span>

<span data-ttu-id="cf612-120">這個範例會取得連接到名為 **Server02** 之電腦的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-120">This example gets the CIM sessions that are connected to the computer named **Server02** .</span></span>

```powershell
Get-CimSession -ComputerName Server02
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="cf612-121">範例3：取得 CIM 會話的清單，然後格式化清單</span><span class="sxs-lookup"><span data-stu-id="cf612-121">Example 3: Get a list of CIM sessions and then format the list</span></span>

<span data-ttu-id="cf612-122">此範例會取得目前 PowerShell 會話中的所有 CIM 會話，並顯示只包含 **ComputerName** 和 **InstanceID** 屬性的資料表。</span><span class="sxs-lookup"><span data-stu-id="cf612-122">This example gets all CIM sessions in the current PowerShell session and displays a table containing only the **ComputerName** and **InstanceID** properties.</span></span>

```powershell
Get-CimSession | Format-Table -Property ComputerName,InstanceId
```

```Output
ComputerName InstanceId
------------ ----------
Server01     d1413bc3-162a-4cb8-9aec-4d2c61253d59
Server02     c0095981-52c5-4e7f-a5bb-c4c680541710
```

### <span data-ttu-id="cf612-123">範例4：取得所有具有特定名稱的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="cf612-123">Example 4: Get all the CIM sessions that have specific names</span></span>

<span data-ttu-id="cf612-124">此範例會取得所有名稱開頭為 **serv** 的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-124">This example gets all CIM sessions that have names that begin with **serv** .</span></span>

```powershell
Get-CimSession -ComputerName Serv*
```

```Output
Id           : 1
Name         : CimSession1
InstanceId   : d1413bc-162a-4cb8-9aec-4d2c61253d59
ComputerName : Server01
Protocol     : WSMAN

Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

### <span data-ttu-id="cf612-125">範例5：取得特定的 CIM 會話</span><span class="sxs-lookup"><span data-stu-id="cf612-125">Example 5: Get a specific CIM session</span></span>

<span data-ttu-id="cf612-126">此範例會取得 **識別碼** 為2的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-126">This example gets the CIM session that has an **Id** of 2.</span></span>

```powershell
Get-CimSession -ID 2
```

```Output
Id           : 2
Name         : CimSession2
InstanceId   : c0095981-52c5-4e7f-a5bb-c4c680541710
ComputerName : Server02
Protocol     : WSMAN
```

## <span data-ttu-id="cf612-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cf612-127">PARAMETERS</span></span>

### <span data-ttu-id="cf612-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cf612-128">-ComputerName</span></span>

<span data-ttu-id="cf612-129">指定要取得連接之 CIM 會話的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="cf612-129">Specifies the name of the computer to get CIM sessions connected to.</span></span> <span data-ttu-id="cf612-130">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf612-130">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cf612-131">-Id</span><span class="sxs-lookup"><span data-stu-id="cf612-131">-Id</span></span>

<span data-ttu-id="cf612-132">指定要取得之 CIM 會話的識別碼。</span><span class="sxs-lookup"><span data-stu-id="cf612-132">Specifies the identifier of the CIM session to get.</span></span> <span data-ttu-id="cf612-133">若為多個識別符，請使用逗號來分隔識別碼，或使用範圍運算子 (`..`) 來指定識別碼的範圍。</span><span class="sxs-lookup"><span data-stu-id="cf612-133">For multiple IDs, use commas to separate the IDs or use the range operator (`..`) to specify a range of IDs.</span></span> <span data-ttu-id="cf612-134">**識別碼** 是一個整數，可唯一識別目前 PowerShell 會話內的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-134">An **Id** is an integer that uniquely identifies the CIM session within the current PowerShell session.</span></span>

<span data-ttu-id="cf612-135">如需範圍運算子的詳細資訊，請參閱 [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md)。</span><span class="sxs-lookup"><span data-stu-id="cf612-135">For more information about the range operator, see [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md).</span></span>

```yaml
Type: System.UInt32[]
Parameter Sets: SessionIdSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cf612-136">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="cf612-136">-InstanceId</span></span>

<span data-ttu-id="cf612-137">指定要取得之 CIM 會話的實例識別碼。</span><span class="sxs-lookup"><span data-stu-id="cf612-137">Specifies the instance IDs of the CIM session to get.</span></span>

<span data-ttu-id="cf612-138">**InstanceId** 是全域唯一識別碼 (GUID) ，可唯一識別 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-138">**InstanceId** is a globally-unique identifier (GUID) that uniquely identifies a CIM session.</span></span> <span data-ttu-id="cf612-139">**InstanceId** 是唯一的，即使您有多個會話在 PowerShell 中執行也是一樣。</span><span class="sxs-lookup"><span data-stu-id="cf612-139">The **InstanceId** is unique, even when you have multiple sessions running in PowerShell.</span></span>

<span data-ttu-id="cf612-140">**Instanceid** 儲存在代表 CIM 會話之物件的 **instanceid** 屬性中。</span><span class="sxs-lookup"><span data-stu-id="cf612-140">The **InstanceId** is stored in the **InstanceId** property of the object that represents a CIM session.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cf612-141">-Name</span><span class="sxs-lookup"><span data-stu-id="cf612-141">-Name</span></span>

<span data-ttu-id="cf612-142">取得一或多個包含指定易記名稱的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="cf612-142">Gets one or more CIM sessions which contain the specified friendly names.</span></span> <span data-ttu-id="cf612-143">允許使用萬用字元。</span><span class="sxs-lookup"><span data-stu-id="cf612-143">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cf612-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cf612-144">CommonParameters</span></span>
<span data-ttu-id="cf612-145">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cf612-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cf612-146">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cf612-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cf612-147">輸入</span><span class="sxs-lookup"><span data-stu-id="cf612-147">INPUTS</span></span>

### <span data-ttu-id="cf612-148">無</span><span class="sxs-lookup"><span data-stu-id="cf612-148">None</span></span>

## <span data-ttu-id="cf612-149">輸出</span><span class="sxs-lookup"><span data-stu-id="cf612-149">OUTPUTS</span></span>

### <span data-ttu-id="cf612-150">Microsoft.Management.Infrastructure.CimSession</span><span class="sxs-lookup"><span data-stu-id="cf612-150">Microsoft.Management.Infrastructure.CimSession</span></span>

## <span data-ttu-id="cf612-151">注意</span><span class="sxs-lookup"><span data-stu-id="cf612-151">NOTES</span></span>

## <span data-ttu-id="cf612-152">相關連結</span><span class="sxs-lookup"><span data-stu-id="cf612-152">RELATED LINKS</span></span>

[<span data-ttu-id="cf612-153">Format-Table</span><span class="sxs-lookup"><span data-stu-id="cf612-153">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="cf612-154">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="cf612-154">New-CimSession</span></span>](New-CimSession.md)

[<span data-ttu-id="cf612-155">Remove-CimSession</span><span class="sxs-lookup"><span data-stu-id="cf612-155">Remove-CimSession</span></span>](remove-cimsession.md)

[<span data-ttu-id="cf612-156">about_CimSession</span><span class="sxs-lookup"><span data-stu-id="cf612-156">about_CimSession</span></span>](../Microsoft.PowerShell.Core/About/about_CimSession.md)
