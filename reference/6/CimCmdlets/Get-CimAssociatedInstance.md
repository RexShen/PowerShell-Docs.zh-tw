---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimassociatedinstance?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimAssociatedInstance
ms.openlocfilehash: adf6c1ac6f6f9288233d530b7ea2101f4b7688e4
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205427"
---
# <span data-ttu-id="019ba-103">Get-CimAssociatedInstance</span><span class="sxs-lookup"><span data-stu-id="019ba-103">Get-CimAssociatedInstance</span></span>

## <span data-ttu-id="019ba-104">概要</span><span class="sxs-lookup"><span data-stu-id="019ba-104">SYNOPSIS</span></span>
<span data-ttu-id="019ba-105">抓取由關聯連接到特定 CIM 實例的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-105">Retrieves the CIM instances that are connected to a specific CIM instance by an association.</span></span>

## <span data-ttu-id="019ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="019ba-106">SYNTAX</span></span>

### <span data-ttu-id="019ba-107">ComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="019ba-107">ComputerSet (Default)</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] [-ComputerName <String[]>] [-KeyOnly] [<CommonParameters>]
```

### <span data-ttu-id="019ba-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="019ba-108">SessionSet</span></span>

```
Get-CimAssociatedInstance [[-Association] <String>] [-ResultClassName <String>]
 [-InputObject] <CimInstance> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-ResourceUri <Uri>] -CimSession <CimSession[]> [-KeyOnly] [<CommonParameters>]
```

## <span data-ttu-id="019ba-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="019ba-109">DESCRIPTION</span></span>

<span data-ttu-id="019ba-110">指令 `Get-CimAssociatedInstance` 程式可透過關聯，抓取連接到特定 cim 實例的 cim 實例，稱為來源實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-110">The `Get-CimAssociatedInstance` cmdlet retrieves the CIM instances connected to a specific CIM instance, called the source instance, by an association.</span></span>

<span data-ttu-id="019ba-111">在關聯中，每個 CIM 實例都有一個命名角色，而且相同的 CIM 實例可以參與不同角色的關聯。</span><span class="sxs-lookup"><span data-stu-id="019ba-111">In an association, each CIM instance has a named role and the same CIM instance can participate in an association in different roles.</span></span>

<span data-ttu-id="019ba-112">如果未指定 InputObject 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="019ba-112">If the InputObject parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="019ba-113">如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。</span><span class="sxs-lookup"><span data-stu-id="019ba-113">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="019ba-114">如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="019ba-114">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="019ba-115">範例</span><span class="sxs-lookup"><span data-stu-id="019ba-115">EXAMPLES</span></span>

### <span data-ttu-id="019ba-116">範例1：取得特定實例的所有相關聯實例</span><span class="sxs-lookup"><span data-stu-id="019ba-116">Example 1: Get all the associated instances of a specific instance</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1]
```

<span data-ttu-id="019ba-117">這組命令會抓取名為 Win32_LogicalDisk 之類別的實例，並將資訊儲存在使用 Cmdlet 命名的變數中 `$disk` `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="019ba-117">This set of commands retrieves the instances of the class named Win32_LogicalDisk and stores the information in a variable named `$disk` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="019ba-118">變數中的第一個邏輯磁片實例接著會用來做為 Cmdlet 的輸入物件， `Get-CimAssociatedInstance` 以取得指定之 cim 實例的所有相關聯 cim 實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-118">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated CIM instances of the specified CIM instance.</span></span>

### <span data-ttu-id="019ba-119">範例2：取得特定類型的所有相關聯實例</span><span class="sxs-lookup"><span data-stu-id="019ba-119">Example 2: Get all the associated instances of a specific type</span></span>

```powershell
$disk = Get-CimInstance -ClassName Win32_LogicalDisk -KeyOnly
Get-CimAssociatedInstance -InputObject $disk[1] -ResultClass Win32_DiskPartition
```

<span data-ttu-id="019ba-120">這組命令會抓取 **Win32_LogicalDisk** 類別的所有實例，並將其儲存在名為的變數中 `$disk` 。</span><span class="sxs-lookup"><span data-stu-id="019ba-120">This set of commands retrieves all the instances of the **Win32_LogicalDisk** class and stores them in a variable named `$disk`.</span></span> <span data-ttu-id="019ba-121">變數中的第一個邏輯磁片實例接著會用來做為 Cmdlet 的輸入物件， `Get-CimAssociatedInstance` 以取得透過指定的關聯類別 **Win32_DiskPartition** 建立關聯的所有相關聯實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-121">The first logical disk instance in the variable is then used as the input object for the `Get-CimAssociatedInstance` cmdlet to get all the associated instances that are associated through the specified association class **Win32_DiskPartition** .</span></span>

### <span data-ttu-id="019ba-122">範例3：透過特定類別的辨識符號取得所有相關聯的實例</span><span class="sxs-lookup"><span data-stu-id="019ba-122">Example 3: Get all the associated instances through qualifier of a specific class</span></span>

```powershell
$s = Get-CimInstance -Query "Select * from Win32_Service where name like 'Winmgmt'"
Get-CimClass -ClassName *Service* -Qualifier "Association"
$c.CimClasName
```

```Output
Win32_LoadOrderGroupServiceDependencies
Win32_DependentService
Win32_SystemServices
Win32_LoadOrderGroupServiceMembers
Win32_ServiceSpecificationService
```

```powershell
Get-CimAssociatedInstance -InputObject $s -Association Win32_DependentService
```

<span data-ttu-id="019ba-123">這組命令會抓取相依于 WMI 服務的服務，並將其儲存在名為的變數中 `$s` 。</span><span class="sxs-lookup"><span data-stu-id="019ba-123">This set of commands retrieves the services that depend on WMI service and stores them in a variable named `$s`.</span></span> <span data-ttu-id="019ba-124">使用 Cmdlet 來抓取 **Win32_DependentService** 的關聯類別名稱， `Get-CimClass` 方法是指定 **association** 做為辨識符號，然後使用 $s 傳遞至 Cmdlet， `Get-CimAssociatedInstance` 以取得已抓取之關聯類別的所有相關聯實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-124">The association class name for the **Win32_DependentService** is retrieved using the `Get-CimClass` cmdlet by specifying **Association** as the qualifier and is then passed with $s to the `Get-CimAssociatedInstance` cmdlet to get all the associated instances of the retrieved association class.</span></span>

## <span data-ttu-id="019ba-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="019ba-125">PARAMETERS</span></span>

### <span data-ttu-id="019ba-126">-關聯</span><span class="sxs-lookup"><span data-stu-id="019ba-126">-Association</span></span>

<span data-ttu-id="019ba-127">指定關聯類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="019ba-127">Specifies the name of the association class.</span></span> <span data-ttu-id="019ba-128">如果您未指定此參數，Cmdlet 會傳回任何類型的所有現有關聯物件。</span><span class="sxs-lookup"><span data-stu-id="019ba-128">If you do not specify this parameter, the cmdlet returns all existing association objects of any type.</span></span>

<span data-ttu-id="019ba-129">例如，如果類別 A 透過兩個關聯（AB1 和 AB2）與類別 B 相關聯，則這個參數可以用來指定關聯的類型，也就是 AB1 或 AB2。</span><span class="sxs-lookup"><span data-stu-id="019ba-129">For example, if class A is associated with class B through two associations, AB1 and AB2, then this parameter can be used to specify the type of association, either AB1 or AB2.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-130">-CimSession</span><span class="sxs-lookup"><span data-stu-id="019ba-130">-CimSession</span></span>

<span data-ttu-id="019ba-131">使用指定的 CIM 會話來執行命令。</span><span class="sxs-lookup"><span data-stu-id="019ba-131">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="019ba-132">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="019ba-132">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as `New-CimSession` or `Get-CimSession`.</span></span> <span data-ttu-id="019ba-133">如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="019ba-133">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: SessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-134">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="019ba-134">-ComputerName</span></span>

<span data-ttu-id="019ba-135">指定要在其上執行 CIM 作業的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="019ba-135">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="019ba-136">您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="019ba-136">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="019ba-137">如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="019ba-137">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="019ba-138">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="019ba-138">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="019ba-139">如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="019ba-139">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="019ba-140">-InputObject</span></span>

<span data-ttu-id="019ba-141">指定此 Cmdlet 的輸入。</span><span class="sxs-lookup"><span data-stu-id="019ba-141">Specifies the input to this cmdlet.</span></span> <span data-ttu-id="019ba-142">您可以使用這個參數，或者您可以透過管線將輸入傳送到此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="019ba-142">You can use this parameter, or you can pipe the input to this cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: (All)
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-143">-KeyOnly</span><span class="sxs-lookup"><span data-stu-id="019ba-143">-KeyOnly</span></span>

<span data-ttu-id="019ba-144">傳回只填入索引鍵屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="019ba-144">Returns objects with only key properties populated.</span></span> <span data-ttu-id="019ba-145">這會減少透過網路傳輸的資料量。</span><span class="sxs-lookup"><span data-stu-id="019ba-145">This reduces the amount of data that is transferred over the network.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-146">-Namespace</span><span class="sxs-lookup"><span data-stu-id="019ba-146">-Namespace</span></span>

<span data-ttu-id="019ba-147">指定 CIM 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="019ba-147">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="019ba-148">預設命名空間為 root/cimv2。</span><span class="sxs-lookup"><span data-stu-id="019ba-148">The default namespace is root/cimv2.</span></span>

> [!NOTE]
> <span data-ttu-id="019ba-149">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="019ba-149">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-150">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="019ba-150">-OperationTimeoutSec</span></span>

<span data-ttu-id="019ba-151">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="019ba-151">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="019ba-152">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="019ba-152">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="019ba-153">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="019ba-153">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases: OT

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="019ba-154">-ResourceUri</span></span>

<span data-ttu-id="019ba-155">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="019ba-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="019ba-156">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="019ba-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="019ba-157">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="019ba-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="019ba-158">例如：</span><span class="sxs-lookup"><span data-stu-id="019ba-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="019ba-159">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="019ba-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="019ba-160">**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。</span><span class="sxs-lookup"><span data-stu-id="019ba-160">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="019ba-161">如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，則會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。</span><span class="sxs-lookup"><span data-stu-id="019ba-161">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="019ba-162">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="019ba-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-163">-ResultClassName</span><span class="sxs-lookup"><span data-stu-id="019ba-163">-ResultClassName</span></span>

<span data-ttu-id="019ba-164">指定相關聯實例的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="019ba-164">Specifies the class name of the associated instances.</span></span> <span data-ttu-id="019ba-165">CIM 實例可以與一或多個 CIM 實例相關聯。</span><span class="sxs-lookup"><span data-stu-id="019ba-165">A CIM instance can be associated with one or more CIM instances.</span></span> <span data-ttu-id="019ba-166">如果您未指定結果類別名稱，則會傳回所有相關聯的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-166">All associated CIM instances are returned if you do not specify the result class name.</span></span>

<span data-ttu-id="019ba-167">根據預設，此參數的值為 null，而且會傳回所有相關聯的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="019ba-167">By default, the value of this parameter is null, and all associated CIM instances are returned.</span></span>

<span data-ttu-id="019ba-168">您可以篩選關聯結果，使其符合特定的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="019ba-168">You can filter the association results to match a specific class name.</span></span> <span data-ttu-id="019ba-169">篩選會在伺服器上進行。</span><span class="sxs-lookup"><span data-stu-id="019ba-169">Filtering happens on the server.</span></span> <span data-ttu-id="019ba-170">如果未指定此參數，則會傳回 `Get-CIMAssociatedInstance` 所有現有的關聯。</span><span class="sxs-lookup"><span data-stu-id="019ba-170">If this parameter is not specified, `Get-CIMAssociatedInstance` returns all existing associations.</span></span> <span data-ttu-id="019ba-171">例如，如果類別 A 與類別 B、C 和 D 相關聯，則這個參數可以用來將輸出限制為特定類型， (B、C 或 D) 。</span><span class="sxs-lookup"><span data-stu-id="019ba-171">For example, if class A is associated with classes B, C and D, then this parameter can be used to restrict the output to a specific type (B, C or D).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="019ba-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="019ba-172">CommonParameters</span></span>

<span data-ttu-id="019ba-173">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="019ba-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="019ba-174">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="019ba-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="019ba-175">輸入</span><span class="sxs-lookup"><span data-stu-id="019ba-175">INPUTS</span></span>

### <span data-ttu-id="019ba-176">無</span><span class="sxs-lookup"><span data-stu-id="019ba-176">None</span></span>

<span data-ttu-id="019ba-177">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="019ba-177">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="019ba-178">輸出</span><span class="sxs-lookup"><span data-stu-id="019ba-178">OUTPUTS</span></span>

### <span data-ttu-id="019ba-179">System.Object</span><span class="sxs-lookup"><span data-stu-id="019ba-179">System.Object</span></span>

<span data-ttu-id="019ba-180">此 Cmdlet 會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="019ba-180">This cmdlet returns an object.</span></span>

## <span data-ttu-id="019ba-181">注意</span><span class="sxs-lookup"><span data-stu-id="019ba-181">NOTES</span></span>

## <span data-ttu-id="019ba-182">相關連結</span><span class="sxs-lookup"><span data-stu-id="019ba-182">RELATED LINKS</span></span>

[<span data-ttu-id="019ba-183">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="019ba-183">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="019ba-184">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="019ba-184">Get-CimInstance</span></span>](get-ciminstance.md)
