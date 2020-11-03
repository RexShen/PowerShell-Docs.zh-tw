---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/21/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-ciminstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimInstance
ms.openlocfilehash: 49838449bd2ffe949c4b2f1310c3f68c40867908
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205424"
---
# <span data-ttu-id="d8b5b-103">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8b5b-103">Get-CimInstance</span></span>

## <span data-ttu-id="d8b5b-104">概要</span><span class="sxs-lookup"><span data-stu-id="d8b5b-104">SYNOPSIS</span></span>
<span data-ttu-id="d8b5b-105">從 CIM 伺服器取得類別的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-105">Gets the CIM instances of a class from a CIM server.</span></span>

## <span data-ttu-id="d8b5b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8b5b-106">SYNTAX</span></span>

### <span data-ttu-id="d8b5b-107">ClassNameComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="d8b5b-107">ClassNameComputerSet (Default)</span></span>

```
Get-CimInstance [-ClassName] <String> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-108">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-108">ResourceUriSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> -ResourceUri <Uri> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-109">QuerySessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-110">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-110">ClassNameSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ClassName] <String> [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-QueryDialect <String>] [-Shallow] [-Filter <String>]
 [-Property <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-111">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-111">CimInstanceSessionSet</span></span>

```
Get-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-112">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-112">CimInstanceComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-113">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-113">ResourceUriComputerSet</span></span>

```
Get-CimInstance -ResourceUri <Uri> [-ComputerName <String[]>] [-KeyOnly] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-Shallow] [-Filter <String>] [-Property <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="d8b5b-114">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="d8b5b-114">QueryComputerSet</span></span>

```
Get-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] -Query <String> [-QueryDialect <String>] [-Shallow]
 [<CommonParameters>]
```

## <span data-ttu-id="d8b5b-115">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="d8b5b-115">DESCRIPTION</span></span>

<span data-ttu-id="d8b5b-116">`Get-CimInstance`Cmdlet 會從 cim 伺服器取得類別的 cim 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-116">The `Get-CimInstance` cmdlet gets the CIM instances of a class from a CIM server.</span></span> <span data-ttu-id="d8b5b-117">您可以為此 Cmdlet 指定類別名稱或查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-117">You can specify either the class name or a query for this cmdlet.</span></span> <span data-ttu-id="d8b5b-118">這個 Cmdlet 會傳回一或多個 CIM 實例物件，代表 CIM 伺服器上的 CIM 實例的快照。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-118">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances present on the CIM server.</span></span>

<span data-ttu-id="d8b5b-119">如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="d8b5b-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="d8b5b-120">如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="d8b5b-121">如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="d8b5b-122">如果指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="d8b5b-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="d8b5b-123">如果 **ComputerName** 參數和 **CimSession** 參數都未指定，則此 Cmdlet 會使用輸入物件中的 CIM 會話或電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="d8b5b-124">如果指定 **ComputerName** 參數或 **CimSession** 參數，則此 Cmdlet 會使用 CimSession 參數值或 **ComputerName** 參數值。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the CimSession parameter value or **ComputerName** parameter value.</span></span>

## <span data-ttu-id="d8b5b-125">範例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-125">EXAMPLES</span></span>

### <span data-ttu-id="d8b5b-126">範例1：取得指定類別的 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-126">Example 1: Get the CIM instances of a specified class</span></span>

<span data-ttu-id="d8b5b-127">此範例會抓取名為 **Win32_Process** 之類別的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-127">This example retrieves the CIM instances of a class named **Win32_Process** .</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process
```

### <span data-ttu-id="d8b5b-128">範例2：取得 WMI 伺服器的命名空間清單</span><span class="sxs-lookup"><span data-stu-id="d8b5b-128">Example 2: Get a list of namespaces from a WMI server</span></span>

<span data-ttu-id="d8b5b-129">此範例會在 WMI 伺服器的 **根** 命名空間下抓取命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-129">This example retrieves a list of namespaces under the **Root** namespace on a WMI server.</span></span>

```powershell
Get-CimInstance -Namespace root -ClassName __Namespace
```

### <span data-ttu-id="d8b5b-130">範例3：取得使用查詢篩選之類別的實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-130">Example 3: Get instances of a class filtered by using a query</span></span>

<span data-ttu-id="d8b5b-131">這個範例會使用 **查詢** 參數所指定的查詢，從名為 **Win32_Process** 之類別的字母 **P** 開始，抓取所有的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-131">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the query specified by a **Query** parameter.</span></span>

```powershell
Get-CimInstance -Query "SELECT * from Win32_Process WHERE name LIKE 'P%'"
```

### <span data-ttu-id="d8b5b-132">範例4：使用類別名稱和篩選運算式取得已篩選之類別的實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-132">Example 4: Get instances of a class filtered by using a class name and a filter expression</span></span>

<span data-ttu-id="d8b5b-133">此範例會使用篩選參數，從名稱為 **Win32_Process** 之類別的字母 **P** 開始，抓取所有的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-133">This example retrieves all the CIM instances that start with the letter **P** of a class named **Win32_Process** using the Filter parameter.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Process -Filter "Name like 'P%'"
```

### <span data-ttu-id="d8b5b-134">範例5：取得僅填入索引鍵屬性的 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-134">Example 5: Get the CIM instances with only key properties filled in</span></span>

<span data-ttu-id="d8b5b-135">此範例會使用索引鍵屬性，在記憶體中為名為 **Win32_Process** 的類別建立新的 CIM 實例 `@{ "Handle"=0 }` ，並將它儲存在名為的變數中 `$x` 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-135">This example creates a new CIM instance in memory for a class named **Win32_Process** with the key property `@{ "Handle"=0 }` and stores it in a variable named `$x`.</span></span> <span data-ttu-id="d8b5b-136">變數會以 CIM 實例的形式傳遞至 `Get-CimInstance` Cmdlet，以取得特定的實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-136">The variable is passed as a CIM instance to the `Get-CimInstance` cmdlet to get a particular instance.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Process -Namespace root\cimv2 -Property @{ "Handle"=0 } -Key Handle -ClientOnly
Get-CimInstance -CimInstance $x
```

### <span data-ttu-id="d8b5b-137">範例6：取出 CIM 實例並重複使用</span><span class="sxs-lookup"><span data-stu-id="d8b5b-137">Example 6: Retrieve CIM instances and reuse them</span></span>

<span data-ttu-id="d8b5b-138">這個範例會取得名為 **Win32_Process** 之類別的 CIM 實例，並將它們儲存在變數 `$x` 和中 `$y` 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-138">This example gets the CIM instances of a class named **Win32_Process** and stores them in the variables `$x` and `$y`.</span></span> <span data-ttu-id="d8b5b-139">然後，此變數 `$x` 會在僅包含 **Name** 和 **KernelModeTime** 屬性的資料表中格式化，並將資料表設定為自動 **調整** 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-139">The variable `$x` is then formatted in a table containing only the **Name** and **KernelModeTime** properties, the table set to **AutoSize** .</span></span>

```powershell
$x,$y = Get-CimInstance -ClassName Win32_Process
$x | Format-Table -Property Name,KernelModeTime -AutoSize
```

```Output
Name                 KernelModeTime
----                 --------------
System Idle Process 157238797968750
```

### <span data-ttu-id="d8b5b-140">範例7：從遠端電腦取得 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-140">Example 7: Get CIM instances from remote computer</span></span>

<span data-ttu-id="d8b5b-141">此範例會從名為 **Server01** 和 **Server02** 的遠端電腦，抓取名為 **Win32_ComputerSystem** 之類別的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-141">This example retrieves the CIM instances of a class named **Win32_ComputerSystem** from the remote computers named **Server01** and **Server02** .</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -ComputerName Server01,Server02
```

### <span data-ttu-id="d8b5b-142">範例8：只取得索引鍵屬性，而不是所有屬性</span><span class="sxs-lookup"><span data-stu-id="d8b5b-142">Example 8: Getting only the key properties, instead of all properties</span></span>

<span data-ttu-id="d8b5b-143">此範例只會抓取索引鍵屬性，以減少物件和網路流量的大小。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-143">This example retrieves only the key properties, which reduces the size of the object and network traffic.</span></span>

```powershell
$x = Get-CimInstance -Class Win32_Process -KeyOnly
$x | Invoke-CimMethod -MethodName GetOwner
```

### <span data-ttu-id="d8b5b-144">範例9：只取得屬性的子集，而不是所有屬性</span><span class="sxs-lookup"><span data-stu-id="d8b5b-144">Example 9: Getting only a subset of properties, instead of all properties</span></span>

<span data-ttu-id="d8b5b-145">此範例只會抓取屬性的子集，以減少物件和網路流量的大小。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-145">This example retrieves only a subset of properties, which reduces the size of the object and network traffic.</span></span>

```powershell
Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x = Get-CimInstance -Class Win32_Process -Property Name,KernelModeTime
$x | Invoke-CimMethod -MethodName GetOwner
```

<span data-ttu-id="d8b5b-146">使用 **Property** 參數取出的實例可以用來執行其他 CIM 作業，例如 `Set-CimInstance` 或 `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-146">The instance retrieved with the **Property** parameter can be used to perform other CIM operations, for example `Set-CimInstance` or `Invoke-CimMethod`.</span></span>

### <span data-ttu-id="d8b5b-147">範例10：使用 CIM 會話取得 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-147">Example 10: Get the CIM instance using CIM session</span></span>

<span data-ttu-id="d8b5b-148">此範例會使用 Cmdlet 在名為 **Server01** 的電腦上建立 CIM 會話 **，並將** `New-CimSession` 會話資訊儲存在名為的變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-148">This example creates a CIM session on the computers named **Server01** and **Server02** using the `New-CimSession` cmdlet and stores the session information in a variable named `$s`.</span></span> <span data-ttu-id="d8b5b-149">然後使用 CimSession 參數將變數的內容傳遞至 `Get-CimInstance` ，以 **CimSession** 取得名為 **WIN32_COMPUTERSYSTEM** 之類別的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-149">The contents of the variable are then passed to `Get-CimInstance` by using the **CimSession** parameter, to get the CIM instances of the class named **Win32_ComputerSystem** .</span></span>

```powershell
$s = New-CimSession -ComputerName Server01,Server02
Get-CimInstance -ClassName Win32_ComputerSystem -CimSession $s
```

## <span data-ttu-id="d8b5b-150">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d8b5b-150">PARAMETERS</span></span>

### <span data-ttu-id="d8b5b-151">-CimSession</span><span class="sxs-lookup"><span data-stu-id="d8b5b-151">-CimSession</span></span>

<span data-ttu-id="d8b5b-152">指定要用於此 Cmdlet 的 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-152">Specifies the CIM session to use for this cmdlet.</span></span> <span data-ttu-id="d8b5b-153">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-153">Enter a variable that contains the CIM session or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="d8b5b-154">如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-154">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-155">-ClassName</span><span class="sxs-lookup"><span data-stu-id="d8b5b-155">-ClassName</span></span>

<span data-ttu-id="d8b5b-156">指定要為其取得 CIM 實例的 CIM 類別名稱。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-156">Specifies the name of the CIM class for which to retrieve the CIM instances.</span></span> <span data-ttu-id="d8b5b-157">您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-157">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-158">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="d8b5b-158">-ComputerName</span></span>

<span data-ttu-id="d8b5b-159">指定您要執行 CIM 操作的電腦。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-159">Specifies computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="d8b5b-160">您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-160">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span> <span data-ttu-id="d8b5b-161">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-161">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="d8b5b-162">如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-162">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="d8b5b-163">如果在同一部電腦上執行多個作業，請使用 CIM 會話連線，以獲得更好的效能。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-163">If multiple operations are being performed on the same computer, connect using a CIM session for better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, CimInstanceComputerSet, ResourceUriComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="d8b5b-164">-Filter</span></span>

<span data-ttu-id="d8b5b-165">指定要做為篩選準則使用的 where 子句。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-165">Specifies a where clause to use as a filter.</span></span> <span data-ttu-id="d8b5b-166">請在 **WQL** 或 **CQL** 查詢語言中指定子句。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-166">Specify the clause in either the **WQL** or the **CQL** query language.</span></span> <span data-ttu-id="d8b5b-167">請勿 `WHERE` 在參數的值中包含關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-167">Do not include the `WHERE` keyword in the value of the parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-168">-InputObject</span><span class="sxs-lookup"><span data-stu-id="d8b5b-168">-InputObject</span></span>

<span data-ttu-id="d8b5b-169">指定要做為輸入使用的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-169">Specifies a CIM instance object to use as input.</span></span>

<span data-ttu-id="d8b5b-170">如果您已經在使用 CIM 實例物件，您可以使用此參數來傳遞 CIM 實例物件，以便從 CIM 伺服器取得最新的快照集。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-170">If you are already working with a CIM instance object, you can use this parameter to pass the CIM instance object in order to get the latest snapshot from the CIM server.</span></span> <span data-ttu-id="d8b5b-171">當您傳遞 CIM 實例物件做為輸入時，會 `Get-CimInstance` 使用取得 CIM 作業（而不是列舉或查詢作業）從伺服器傳回物件。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-171">When you pass a CIM instance object as an input, `Get-CimInstance` returns the object from server using a get CIM operation, instead of an enumerate or query operation.</span></span> <span data-ttu-id="d8b5b-172">使用「取得 CIM」作業會比取出所有實例，然後加以篩選更有效率。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-172">Using a get CIM operation is more efficient than retrieving all instances and then filtering them.</span></span>

<span data-ttu-id="d8b5b-173">如果 CIM 類別未執行 get 作業，則指定 **InputObject** 參數會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-173">If the CIM class does not implement the get operation, then specifying the **InputObject** parameter returns an error.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceSessionSet, CimInstanceComputerSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-174">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="d8b5b-174">-KeyOnly</span></span>

<span data-ttu-id="d8b5b-175">指出只會傳回已填入索引鍵屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-175">Indicates that only objects with key properties populated are returned.</span></span> <span data-ttu-id="d8b5b-176">指定 **KeyOnly** 參數可減少透過網路傳輸的資料量。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-176">Specifying the **KeyOnly** parameter reduces the amount of data transferred over the network.</span></span>

<span data-ttu-id="d8b5b-177">使用 **KeyOnly** 參數來只傳回物件的一小部分，這可用於其他作業，例如 `Set-CimInstance` 或 `Get-CimAssociatedInstance` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-177">Use the **KeyOnly** parameter to return only a small portion of the object, which can be used for other operations, such as the `Set-CimInstance` or `Get-CimAssociatedInstance` cmdlets.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-178">-Namespace</span><span class="sxs-lookup"><span data-stu-id="d8b5b-178">-Namespace</span></span>

<span data-ttu-id="d8b5b-179">指定 CIM 類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-179">Specifies the namespace of CIM class.</span></span>

<span data-ttu-id="d8b5b-180">預設命名空間為 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-180">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="d8b5b-181">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-181">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-182">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="d8b5b-182">-OperationTimeoutSec</span></span>

<span data-ttu-id="d8b5b-183">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-183">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="d8b5b-184">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-184">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="d8b5b-185">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-185">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-186">-Property</span><span class="sxs-lookup"><span data-stu-id="d8b5b-186">-Property</span></span>

<span data-ttu-id="d8b5b-187">指定要取出的實例屬性集。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-187">Specifies a set of instance properties to retrieve.</span></span> <span data-ttu-id="d8b5b-188">當您需要在記憶體中或透過網路來減少傳回的物件大小時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-188">Use this parameter when you need to reduce the size of the object returned, either in memory or over the network.</span></span> <span data-ttu-id="d8b5b-189">傳回的物件也會包含索引鍵屬性，即使您未使用 **Property** 參數列出它們也是一樣。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-189">The object returned also contains the key properties even if you have not listed them using the **Property** parameter.</span></span> <span data-ttu-id="d8b5b-190">類別的其他屬性存在，但不會填入。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-190">Other properties of the class are present but they are not populated.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, ClassNameSessionSet, ResourceUriComputerSet
Aliases: SelectProperties

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-191">-Query</span><span class="sxs-lookup"><span data-stu-id="d8b5b-191">-Query</span></span>

<span data-ttu-id="d8b5b-192">指定要在 CIM 伺服器上執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-192">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="d8b5b-193">如果指定的值包含雙引號 `"` 、單引號 `'` 或反斜線， `\` 您必須在前面加上反斜線字元，以將這些字元加上引號。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-193">If the value specified contains double quotes `"`, single quotes `'`, or a backslash `\`, you must escape those characters by prefixing them with the backslash character.</span></span> <span data-ttu-id="d8b5b-194">如果指定的值使用 WQL **LIKE** 運算子，您必須以方括弧括住下列字元 `[]` ：百分比 `%` 、底線 `_` 或左方括弧 `[` 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-194">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets `[]`: percent `%`, underscore `_`, or opening square bracket `[`.</span></span>

<span data-ttu-id="d8b5b-195">您無法使用中繼資料查詢來取出類別清單或事件查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-195">You cannot use a metadata query to retrieve a list of classes or an event query.</span></span> <span data-ttu-id="d8b5b-196">若要取出類別清單，請使用 `Get-CimClass` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-196">To retrieve a list of classes, use the `Get-CimClass` cmdlet.</span></span> <span data-ttu-id="d8b5b-197">若要取出事件查詢，請使用 `Register-CimIndicationEvent` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-197">To retrieve an event query, use the `Register-CimIndicationEvent` cmdlet.</span></span>

<span data-ttu-id="d8b5b-198">您可以使用 **QueryDialect** 參數來指定查詢方言。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-198">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-199">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="d8b5b-199">-QueryDialect</span></span>

<span data-ttu-id="d8b5b-200">指定用於查詢參數的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-200">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="d8b5b-201">此參數可接受的值為： **WQL** 或 **CQL** 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-201">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span> <span data-ttu-id="d8b5b-202">預設值為 **WQL** 。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-202">The default value is **WQL** .</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, QuerySessionSet, ClassNameSessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-203">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="d8b5b-203">-ResourceUri</span></span>

<span data-ttu-id="d8b5b-204">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-204">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="d8b5b-205">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-205">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="d8b5b-206">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-206">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="d8b5b-207">例如：</span><span class="sxs-lookup"><span data-stu-id="d8b5b-207">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="d8b5b-208">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-208">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="d8b5b-209">**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-209">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="d8b5b-210">如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-210">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="d8b5b-211">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-211">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (QuerySessionSet, QueryComputerSet, CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-212">-淺層</span><span class="sxs-lookup"><span data-stu-id="d8b5b-212">-Shallow</span></span>

<span data-ttu-id="d8b5b-213">表示傳回類別的實例，而不包含任何子類別的實例。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-213">Indicates that the instances of a class are returned without including the instances of any child classes.</span></span> <span data-ttu-id="d8b5b-214">根據預設，此 Cmdlet 會傳回類別的實例及其子類別。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-214">By default, the cmdlet returns the instances of a class and its child classes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ResourceUriSessionSet, QuerySessionSet, ClassNameSessionSet, ResourceUriComputerSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d8b5b-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8b5b-215">CommonParameters</span></span>

<span data-ttu-id="d8b5b-216">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8b5b-217">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8b5b-218">輸入</span><span class="sxs-lookup"><span data-stu-id="d8b5b-218">INPUTS</span></span>

### <span data-ttu-id="d8b5b-219">CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-219">CIM Instance</span></span>

<span data-ttu-id="d8b5b-220">此 Cmdlet 會接受以 InputObject 參數指定的輸入物件。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-220">This cmdlet accepts an input objects specified with the InputObject parameter.</span></span>

## <span data-ttu-id="d8b5b-221">輸出</span><span class="sxs-lookup"><span data-stu-id="d8b5b-221">OUTPUTS</span></span>

### <span data-ttu-id="d8b5b-222">CIM 實例</span><span class="sxs-lookup"><span data-stu-id="d8b5b-222">CIM Instance</span></span>

<span data-ttu-id="d8b5b-223">此 Cmdlet 會傳回一或多個 CIM 實例物件，代表 CIM 伺服器上 CIM 實例的快照集。</span><span class="sxs-lookup"><span data-stu-id="d8b5b-223">This cmdlet returns one or more CIM instance objects representing a snapshot of the CIM instances on the CIM server.</span></span>

## <span data-ttu-id="d8b5b-224">注意</span><span class="sxs-lookup"><span data-stu-id="d8b5b-224">NOTES</span></span>

## <span data-ttu-id="d8b5b-225">相關連結</span><span class="sxs-lookup"><span data-stu-id="d8b5b-225">RELATED LINKS</span></span>

[<span data-ttu-id="d8b5b-226">Format-Table</span><span class="sxs-lookup"><span data-stu-id="d8b5b-226">Format-Table</span></span>](../microsoft.powershell.utility/format-table.md)

[<span data-ttu-id="d8b5b-227">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="d8b5b-227">Get-CimAssociatedInstance</span></span>](Get-CimAssociatedInstance.md)

[<span data-ttu-id="d8b5b-228">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="d8b5b-228">Get-CimClass</span></span>](Get-CimClass.md)

[<span data-ttu-id="d8b5b-229">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="d8b5b-229">Invoke-CimMethod</span></span>](invoke-cimmethod.md)

[<span data-ttu-id="d8b5b-230">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8b5b-230">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="d8b5b-231">Register-CimIndicationEvent</span><span class="sxs-lookup"><span data-stu-id="d8b5b-231">Register-CimIndicationEvent</span></span>](Register-CimIndicationEvent.md)

[<span data-ttu-id="d8b5b-232">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8b5b-232">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="d8b5b-233">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="d8b5b-233">Set-CimInstance</span></span>](Set-CimInstance.md)
