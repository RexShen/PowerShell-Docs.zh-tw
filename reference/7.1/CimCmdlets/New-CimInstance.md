---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/new-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-CimInstance
ms.openlocfilehash: 7cd9d27eb291358fb4d2ee93d0a1e5ade3467249
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205455"
---
# <span data-ttu-id="bc333-103">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bc333-103">New-CimInstance</span></span>

## <span data-ttu-id="bc333-104">概要</span><span class="sxs-lookup"><span data-stu-id="bc333-104">SYNOPSIS</span></span>
<span data-ttu-id="bc333-105">建立 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-105">Creates a CIM instance.</span></span>

## <span data-ttu-id="bc333-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bc333-106">SYNTAX</span></span>

### <span data-ttu-id="bc333-107">ClassNameComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="bc333-107">ClassNameComputerSet (Default)</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bc333-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="bc333-108">ClassNameSessionSet</span></span>

```
New-CimInstance [-ClassName] <String> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-ClientOnly]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bc333-109">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="bc333-109">ResourceUriSessionSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] -CimSession <CimSession[]> [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bc333-110">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="bc333-110">ResourceUriComputerSet</span></span>

```
New-CimInstance -ResourceUri <Uri> [-Key <String[]>] [[-Property] <IDictionary>]
 [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-ComputerName <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bc333-111">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="bc333-111">CimClassSessionSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bc333-112">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="bc333-112">CimClassComputerSet</span></span>

```
New-CimInstance [-CimClass] <CimClass> [[-Property] <IDictionary>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-ClientOnly] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bc333-113">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="bc333-113">DESCRIPTION</span></span>

<span data-ttu-id="bc333-114">此 `New-CimInstance` Cmdlet 會根據本機電腦或遠端電腦上的類別定義，建立 CIM 類別的實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-114">The `New-CimInstance` cmdlet creates an instance of a CIM class based on the class definition on either the local computer or a remote computer.</span></span> <span data-ttu-id="bc333-115">根據預設，此 `New-CimInstance` Cmdlet 會在本機電腦上建立實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-115">By default, the `New-CimInstance` cmdlet creates an instance on the local computer.</span></span>

## <span data-ttu-id="bc333-116">範例</span><span class="sxs-lookup"><span data-stu-id="bc333-116">EXAMPLES</span></span>

### <span data-ttu-id="bc333-117">範例1：建立 CIM 類別的實例</span><span class="sxs-lookup"><span data-stu-id="bc333-117">Example 1: Create an instance of a CIM class</span></span>

<span data-ttu-id="bc333-118">此範例會在電腦的 root/cimv2 命名空間中建立名為 win32_environment 的 CIM 類別實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-118">This example creates an instance of a CIM Class named win32_environment in the root/cimv2 namespace on the computer.</span></span>

```powershell
New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";VariableValue="testvalue";UserName="domain\user"}
```

<span data-ttu-id="bc333-119">如果類別不存在、屬性錯誤或伺服器拒絕呼叫，就不會執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="bc333-119">No client side validation is performed if the class does not exist, the properties are wrong, or if the server rejects the call.</span></span> <span data-ttu-id="bc333-120">如果成功建立實例，此 Cmdlet 會輸出新建立的實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-120">If the instance is created successfully, the cmdlet outputs the newly created instance.</span></span>

### <span data-ttu-id="bc333-121">範例2：使用類別架構來建立 CIM 類別的實例</span><span class="sxs-lookup"><span data-stu-id="bc333-121">Example 2: Create an instance of a CIM class using a class schema</span></span>

<span data-ttu-id="bc333-122">此範例會抓取 CIM 類別物件，並將它儲存在名為的變數中 `$class` 。</span><span class="sxs-lookup"><span data-stu-id="bc333-122">This example retrieves a CIM class object and stores it in a variable named `$class`.</span></span> <span data-ttu-id="bc333-123">然後將變數的內容傳遞給 `New-CimInstance` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc333-123">The contents of the variable are then passed to the `New-CimInstance` cmdlet.</span></span>

```powershell
$class = Get-CimClass -ClassName Win32_Environment
New-CimInstance -CimClass $class -Property @{Name="testvar";VariableValue="testvalue";UserName="Contoso\User1"}
```

### <span data-ttu-id="bc333-124">範例3：在用戶端上建立動態實例</span><span class="sxs-lookup"><span data-stu-id="bc333-124">Example 3: Create a dynamic instance on the client</span></span>

<span data-ttu-id="bc333-125">此範例會在用戶端電腦上建立名為 **Win32_Process** 之 CIM 類別的動態實例，而不會從伺服器取得實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-125">This example creates a dynamic instance of a CIM class named **Win32_Process** on the client computer without getting the instance from the server.</span></span> <span data-ttu-id="bc333-126">新的實例會儲存在變數中 `$a` 。</span><span class="sxs-lookup"><span data-stu-id="bc333-126">The new instance is stored in the variable `$a`.</span></span> <span data-ttu-id="bc333-127">如果伺服器上有具有此索引鍵的實例，這個動態實例可以用來執行作業。</span><span class="sxs-lookup"><span data-stu-id="bc333-127">This dynamic instance can be used to perform operations if the instance with this key exists on the server.</span></span>

```powershell
$a = New-CimInstance -ClassName Win32_Process -Property @{Handle=0} -Key Handle -ClientOnly
Get-CimInstance -CimInstance $a
Invoke-CimMethod -CimInstance $a -MethodName GetOwner
```

```Output
ProcessId Name                HandleCount WorkingSetSize VirtualSize
--------- ----                ----------- -------------- -----------
0         System Idle Process 0           8192           8192

Domain         :
ReturnValue    : 2
User           :
PSComputerName :
```

<span data-ttu-id="bc333-128">然後，Cmdlet 會抓取 `Get-CimInstance` 特定的單一實例。</span><span class="sxs-lookup"><span data-stu-id="bc333-128">The `Get-CimInstance` cmdlet then retrieves a particular single instance.</span></span> <span data-ttu-id="bc333-129">Cmdlet 會在已抓取 `Invoke-CimMethod` 的實例上呼叫 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="bc333-129">The `Invoke-CimMethod` cmdlet calls the **GetOwner** method on the retrieved instance.</span></span>

### <span data-ttu-id="bc333-130">範例4：建立特定命名空間之 CIM 類別的實例</span><span class="sxs-lookup"><span data-stu-id="bc333-130">Example 4: Create an instance for a CIM class of a specific namespace</span></span>

<span data-ttu-id="bc333-131">這個範例會在命名空間 **根/位置** 取得名為 **MSFT_Something** 的 CIM 類別實例，並將它儲存在名為的變數中 `$class` 。</span><span class="sxs-lookup"><span data-stu-id="bc333-131">This example gets an instance of a CIM class named **MSFT_Something** in the namespace **root/somewhere** and stores it in a variable named `$class`.</span></span> <span data-ttu-id="bc333-132">變數會傳遞至 `New-CimInstance` Cmdlet 以建立新的 CIM 實例，並在新的實例上執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="bc333-132">The variable is passed to the `New-CimInstance` cmdlet to create a new CIM instance and perform client side validations on the new instance.</span></span>

```powershell
$class = Get-CimClass -ClassName MSFT_Something -Namespace root/somewhere
New-CimInstance -CimClass $class -Property @{"Prop1"=1;"Prop2"="value"} -ClientOnly
```

<span data-ttu-id="bc333-133">在此範例中，使用 **CimClass** 參數而非 **ClassName** 參數，會驗證 **Prop1** 和 **this.prop2** 確實存在，而且索引鍵的標記是否正確。</span><span class="sxs-lookup"><span data-stu-id="bc333-133">In this example, using the **CimClass** parameter instead of the **ClassName** parameter validates that **Prop1** and **Prop2** actually exist and that the keys are marked correctly.</span></span>

<span data-ttu-id="bc333-134">您無法使用 **ComputerName** 或 **CimSession** 參數搭配 **ClientOnly** 參數。</span><span class="sxs-lookup"><span data-stu-id="bc333-134">You cannot use the **ComputerName** or **CimSession** parameter with the **ClientOnly** parameter.</span></span>

## <span data-ttu-id="bc333-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bc333-135">PARAMETERS</span></span>

### <span data-ttu-id="bc333-136">-CimClass</span><span class="sxs-lookup"><span data-stu-id="bc333-136">-CimClass</span></span>

<span data-ttu-id="bc333-137">指定表示實例類型的 CIM 類別物件。</span><span class="sxs-lookup"><span data-stu-id="bc333-137">Specifies a CIM class object that represents the type of the instance.</span></span> <span data-ttu-id="bc333-138">使用 `Get-CimClass` Cmdlet 從電腦取出類別宣告。</span><span class="sxs-lookup"><span data-stu-id="bc333-138">Use the `Get-CimClass` cmdlet to retrieve the class declaration from a computer.</span></span> <span data-ttu-id="bc333-139">使用此參數會產生更佳的用戶端架構驗證。</span><span class="sxs-lookup"><span data-stu-id="bc333-139">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassSessionSet, CimClassComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-140">-CimSession</span><span class="sxs-lookup"><span data-stu-id="bc333-140">-CimSession</span></span>

<span data-ttu-id="bc333-141">使用指定的 CIM 會話來執行命令。</span><span class="sxs-lookup"><span data-stu-id="bc333-141">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="bc333-142">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="bc333-142">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="bc333-143">如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="bc333-143">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, ResourceUriSessionSet, CimClassSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-144">-ClassName</span><span class="sxs-lookup"><span data-stu-id="bc333-144">-ClassName</span></span>

<span data-ttu-id="bc333-145">指定作業建立實例之 CIM 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="bc333-145">Specifies the name of the CIM class of which the operation creates an instance.</span></span> <span data-ttu-id="bc333-146">注意：您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="bc333-146">NOTE: You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

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

### <span data-ttu-id="bc333-147">-ClientOnly</span><span class="sxs-lookup"><span data-stu-id="bc333-147">-ClientOnly</span></span>

<span data-ttu-id="bc333-148">表示實例只會在 PowerShell 中建立，而不會進入 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bc333-148">Indicates that the instance is only created in PowerShell without going to the CIM server.</span></span> <span data-ttu-id="bc333-149">您可以使用此參數來建立記憶體中的 CIM 實例，以用於後續的 PowerShell 作業。</span><span class="sxs-lookup"><span data-stu-id="bc333-149">You can use this parameter to create an in-memory CIM instance for use in subsequent PowerShell operations.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, CimClassSessionSet, CimClassComputerSet
Aliases: Local

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="bc333-150">-ComputerName</span></span>

<span data-ttu-id="bc333-151">指定要在其上執行 CIM 作業的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="bc333-151">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="bc333-152">您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="bc333-152">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="bc333-153">如果您指定這個參數，此 Cmdlet 會使用 WSMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="bc333-153">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WSMan protocol.</span></span>

<span data-ttu-id="bc333-154">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="bc333-154">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="bc333-155">如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="bc333-155">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-156">-Key</span><span class="sxs-lookup"><span data-stu-id="bc333-156">-Key</span></span>

<span data-ttu-id="bc333-157">指定用來做為索引鍵的屬性。</span><span class="sxs-lookup"><span data-stu-id="bc333-157">Specifies the properties that are used as keys.</span></span> <span data-ttu-id="bc333-158">指定索引 **鍵** 時，不能使用 **CimSession** 和 **ComputerName** 。</span><span class="sxs-lookup"><span data-stu-id="bc333-158">**CimSession** and **ComputerName** cannot be used when **Key** is specified.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-159">-Namespace</span><span class="sxs-lookup"><span data-stu-id="bc333-159">-Namespace</span></span>

<span data-ttu-id="bc333-160">為新的實例指定類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="bc333-160">Specifies the namespace of the class for the new instance.</span></span> <span data-ttu-id="bc333-161">預設命名空間為 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="bc333-161">The default namespace is **root/cimv2** .</span></span>
<span data-ttu-id="bc333-162">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="bc333-162">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-163">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="bc333-163">-OperationTimeoutSec</span></span>

<span data-ttu-id="bc333-164">指定 Cmdlet 等待 CIM 伺服器回應的時間量。</span><span class="sxs-lookup"><span data-stu-id="bc333-164">Specifies the amount of time that the cmdlet waits for a response from the CIM server.</span></span> <span data-ttu-id="bc333-165">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="bc333-165">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span> <span data-ttu-id="bc333-166">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="bc333-166">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="bc333-167">-Property</span><span class="sxs-lookup"><span data-stu-id="bc333-167">-Property</span></span>

<span data-ttu-id="bc333-168">使用雜湊表 (名稱/值組) ，指定 CIM 實例的屬性。</span><span class="sxs-lookup"><span data-stu-id="bc333-168">Specifies the properties of the CIM instance using a hash table (name-value pairs).</span></span>

<span data-ttu-id="bc333-169">如果您指定 **CimClass** 參數，則此 `New-CimInstance` Cmdlet 會在用戶端上執行屬性驗證，以確保指定的屬性與伺服器上的類別宣告一致。</span><span class="sxs-lookup"><span data-stu-id="bc333-169">If you specify the **CimClass** parameter, then the `New-CimInstance` cmdlet performs a property validation on the client to make sure that the properties specified are consistent with the class declaration on the server.</span></span> <span data-ttu-id="bc333-170">如果未指定 **CimClass** 參數，則會在伺服器上完成屬性驗證。</span><span class="sxs-lookup"><span data-stu-id="bc333-170">If the **CimClass** parameter is not specified, then the property validation is done on the server.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases: Arguments

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-171">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="bc333-171">-ResourceUri</span></span>

<span data-ttu-id="bc333-172">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="bc333-172">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="bc333-173">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="bc333-173">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="bc333-174">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="bc333-174">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="bc333-175">例如：</span><span class="sxs-lookup"><span data-stu-id="bc333-175">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="bc333-176">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="bc333-176">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="bc333-177">**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。</span><span class="sxs-lookup"><span data-stu-id="bc333-177">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="bc333-178">如果您指定此參數但未指定 **ComputerName** 參數，或如果您指定使用 dcom 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 dcom 通訊協定不支援 **ResourceURI** 參數。</span><span class="sxs-lookup"><span data-stu-id="bc333-178">If you specify this parameter without specifying the **ComputerName** parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="bc333-179">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="bc333-179">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bc333-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bc333-180">-Confirm</span></span>

<span data-ttu-id="bc333-181">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="bc333-181">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bc333-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bc333-182">-WhatIf</span></span>

<span data-ttu-id="bc333-183">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bc333-183">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bc333-184">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="bc333-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bc333-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bc333-185">CommonParameters</span></span>

<span data-ttu-id="bc333-186">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="bc333-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bc333-187">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="bc333-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bc333-188">輸入</span><span class="sxs-lookup"><span data-stu-id="bc333-188">INPUTS</span></span>

### <span data-ttu-id="bc333-189">無</span><span class="sxs-lookup"><span data-stu-id="bc333-189">None</span></span>

<span data-ttu-id="bc333-190">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="bc333-190">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="bc333-191">輸出</span><span class="sxs-lookup"><span data-stu-id="bc333-191">OUTPUTS</span></span>

### <span data-ttu-id="bc333-192">System.Object</span><span class="sxs-lookup"><span data-stu-id="bc333-192">System.Object</span></span>

<span data-ttu-id="bc333-193">此 Cmdlet 會傳回包含 CIM 實例資訊的物件。</span><span class="sxs-lookup"><span data-stu-id="bc333-193">This cmdlet returns an object that contains the CIM instance information.</span></span>

## <span data-ttu-id="bc333-194">注意</span><span class="sxs-lookup"><span data-stu-id="bc333-194">NOTES</span></span>

## <span data-ttu-id="bc333-195">相關連結</span><span class="sxs-lookup"><span data-stu-id="bc333-195">RELATED LINKS</span></span>

[<span data-ttu-id="bc333-196">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="bc333-196">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="bc333-197">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bc333-197">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="bc333-198">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bc333-198">Remove-CimInstance</span></span>](remove-ciminstance.md)

[<span data-ttu-id="bc333-199">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="bc333-199">Set-CimInstance</span></span>](Set-CimInstance.md)

