---
description: 描述 WMI 查詢語言 (WQL)，這可用於取得 Windows PowerShell 中的 WMI 物件。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207880"
---
# <a name="about-wql"></a><span data-ttu-id="02057-104">關於 WQL</span><span class="sxs-lookup"><span data-stu-id="02057-104">About WQL</span></span>

## <a name="short-description"></a><span data-ttu-id="02057-105">簡短描述</span><span class="sxs-lookup"><span data-stu-id="02057-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="02057-106">描述 WMI 查詢語言 (WQL)，這可用於取得 Windows PowerShell 中的 WMI 物件。</span><span class="sxs-lookup"><span data-stu-id="02057-106">Describes WMI Query Language (WQL), which can be used to get WMI objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="02057-107">詳細描述</span><span class="sxs-lookup"><span data-stu-id="02057-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="02057-108">WQL 是 Windows Management Instrumentation (WMI) 查詢語言，這是用來從 WMI 取得資訊的語言。</span><span class="sxs-lookup"><span data-stu-id="02057-108">WQL is the Windows Management Instrumentation (WMI) query language, which is the language used to get information from WMI.</span></span>

<span data-ttu-id="02057-109">在 Windows PowerShell 中，您不需要使用 WQL 來執行 WMI 查詢。</span><span class="sxs-lookup"><span data-stu-id="02057-109">You are not required to use WQL to perform a WMI query in Windows PowerShell.</span></span>
<span data-ttu-id="02057-110">相反地，您可以使用 Get-WmiObject 或 Get-CimInstance Cmdlet 的參數。</span><span class="sxs-lookup"><span data-stu-id="02057-110">Instead, you can use the parameters of the Get-WmiObject or Get-CimInstance cmdlets.</span></span> <span data-ttu-id="02057-111">WQL 查詢的速度比標準 Get-WmiObject 命令還快，而且當命令在數百個系統上執行時，改善的效能也會明顯。</span><span class="sxs-lookup"><span data-stu-id="02057-111">WQL queries are somewhat faster than standard Get-WmiObject commands and the improved performance is evident when the commands run on hundreds of systems.</span></span> <span data-ttu-id="02057-112">不過，請確定您花費在撰寫成功 WQL 查詢的時間不會超過效能改進。</span><span class="sxs-lookup"><span data-stu-id="02057-112">However, be sure that the time you spend to write a successful WQL query doesn't outweigh the performance improvement.</span></span>

<span data-ttu-id="02057-113">您需要使用 WQL 的基本 WQL 語句包括 Select、Where 和 From。</span><span class="sxs-lookup"><span data-stu-id="02057-113">The basic WQL statements you need to use WQL are Select, Where, and From.</span></span>

## <a name="when-to-use-wql"></a><span data-ttu-id="02057-114">使用 WQL 的時機</span><span class="sxs-lookup"><span data-stu-id="02057-114">WHEN TO USE WQL</span></span>

<span data-ttu-id="02057-115">使用 WMI 時（尤其是 WQL），請別忘了您也會使用 Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="02057-115">When working with WMI, and especially with WQL, do not forget that you are also using Windows PowerShell.</span></span> <span data-ttu-id="02057-116">通常，如果 WQL 查詢未如預期般運作，則使用標準 Windows PowerShell 命令比偵測 WQL 查詢更容易。</span><span class="sxs-lookup"><span data-stu-id="02057-116">Often, if a WQL query does not work as expected, it's easier to use a standard Windows PowerShell command than to debug the WQL query.</span></span>

<span data-ttu-id="02057-117">除非您是從跨頻寬限制的遠端系統傳回大量資料，否則當有完全可接受的 Windows Cmdlet 來執行相同的工作時，很少需要花費數小時的時間來完成複雜且複雜的 WQL 查詢（如果有點緩慢）。</span><span class="sxs-lookup"><span data-stu-id="02057-117">Unless you are returning massive amounts of data from across bandwidth-constrained remote systems, it is rarely productive to spend hours trying to perfect a complicated and convoluted WQL query when there is a perfectly acceptable Windows cmdlet that does the same thing, if a bit more slowly.</span></span>

## <a name="using-the-select-statement"></a><span data-ttu-id="02057-118">使用 SELECT 語句</span><span class="sxs-lookup"><span data-stu-id="02057-118">USING THE SELECT STATEMENT</span></span>

<span data-ttu-id="02057-119">一般的 WMI 查詢是以 Select 語句開頭，該語句會取得 WMI 類別的所有屬性或特定屬性。</span><span class="sxs-lookup"><span data-stu-id="02057-119">A typical WMI query begins with a Select statement that gets all properties or particular properties of a WMI class.</span></span> <span data-ttu-id="02057-120">若要選取 WMI 類別的所有屬性，請使用星號 (\*) 。</span><span class="sxs-lookup"><span data-stu-id="02057-120">To select all properties of a WMI class, use an asterisk (\*).</span></span> <span data-ttu-id="02057-121">From 關鍵字會指定 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="02057-121">The From keyword specifies the WMI class.</span></span>

<span data-ttu-id="02057-122">Select 語句的格式如下：</span><span class="sxs-lookup"><span data-stu-id="02057-122">A Select statement has the following format:</span></span>

```
Select <property> from <WMI-class>
```

<span data-ttu-id="02057-123">例如，下列 Select 語句會從 Win32_Bios WMI 類別的實例中選取所有屬性 ( \* ) 。</span><span class="sxs-lookup"><span data-stu-id="02057-123">For example, the following Select statement selects all properties (\*) from the instances of the Win32_Bios WMI class.</span></span>

```
Select * from Win32_Bios
```

<span data-ttu-id="02057-124">若要選取 WMI 類別的特定屬性，請將屬性名稱放在 Select 和 From 關鍵字之間。</span><span class="sxs-lookup"><span data-stu-id="02057-124">To select a particular property of a WMI class, place the property name between the Select and From keywords.</span></span>

<span data-ttu-id="02057-125">下列查詢只會從 Win32_Bios WMI 類別選取 BIOS 的名稱。</span><span class="sxs-lookup"><span data-stu-id="02057-125">The following query selects only the name of the BIOS from the Win32_Bios WMI class.</span></span> <span data-ttu-id="02057-126">命令會將查詢儲存在 $queryName 變數中。</span><span class="sxs-lookup"><span data-stu-id="02057-126">The command saves the query in the $queryName variable.</span></span>

```
Select Name from Win32_Bios
```

<span data-ttu-id="02057-127">若要選取一個以上的屬性，請使用逗號來分隔屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="02057-127">To select more than one property, use commas to separate the property names.</span></span>
<span data-ttu-id="02057-128">下列 WMI 查詢會選取 Win32_Bios WMI 類別的名稱和版本。</span><span class="sxs-lookup"><span data-stu-id="02057-128">The following WMI query selects the name and the version of the Win32_Bios WMI class.</span></span> <span data-ttu-id="02057-129">命令會將查詢儲存在 $queryNameVersion 變數中。</span><span class="sxs-lookup"><span data-stu-id="02057-129">The command saves the query in the $queryNameVersion variable.</span></span>

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a><span data-ttu-id="02057-130">使用 WQL 查詢</span><span class="sxs-lookup"><span data-stu-id="02057-130">USING THE WQL QUERY</span></span>

<span data-ttu-id="02057-131">在 Windows PowerShell 命令中使用 WQL 查詢有三種方式。</span><span class="sxs-lookup"><span data-stu-id="02057-131">There are three ways to use WQL query in Windows PowerShell command.</span></span>

- <span data-ttu-id="02057-132">使用 Get-WmiObject Cmdlet</span><span class="sxs-lookup"><span data-stu-id="02057-132">Use the Get-WmiObject cmdlet</span></span>
- <span data-ttu-id="02057-133">使用 Get-CimInstance Cmdlet</span><span class="sxs-lookup"><span data-stu-id="02057-133">Use the Get-CimInstance cmdlet</span></span>
- <span data-ttu-id="02057-134">使用 [wmisearcher] 類型加速器。</span><span class="sxs-lookup"><span data-stu-id="02057-134">Use the [wmisearcher] type accelerator.</span></span>

## <a name="using-the-get-wmiobject-cmdlet"></a><span data-ttu-id="02057-135">使用 >GET-WMIOBJECT 指令 CMDLET</span><span class="sxs-lookup"><span data-stu-id="02057-135">USING THE GET-WMIOBJECT CMDLET</span></span>

<span data-ttu-id="02057-136">使用 WQL 查詢的最基本方式，就是將它括在引號 (作為字串) ，然後使用查詢字串做為 Get-WmiObject Cmdlet 的查詢參數值，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02057-136">The most basic way to use the WQL query is to enclose it in quotation marks (as a string) and then use the query string as the value of the Query parameter of the Get-WmiObject cmdlet, as shown in the following example.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="02057-137">您也可以將 WQL 語句儲存在變數中，然後使用該變數做為查詢參數的值，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="02057-137">You can also save the WQL statement in a variable and then use the variable as the value of the Query parameter, as shown in the following command.</span></span>

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

<span data-ttu-id="02057-138">您可以使用任一種格式搭配任何 WQL 語句。</span><span class="sxs-lookup"><span data-stu-id="02057-138">You can use either format with any WQL statement.</span></span> <span data-ttu-id="02057-139">下列命令會使用 $queryName 變數中的查詢，只取得系統 BIOS 的名稱和版本屬性。</span><span class="sxs-lookup"><span data-stu-id="02057-139">The following command uses the query in the $queryName variable to get only the name and version properties of the system BIOS.</span></span>

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

<span data-ttu-id="02057-140">請記住，您可以使用 Get-WmiObject Cmdlet 的參數來取得相同的結果。</span><span class="sxs-lookup"><span data-stu-id="02057-140">Remember that you can use the parameters of the Get-WmiObject cmdlet to get the same result.</span></span> <span data-ttu-id="02057-141">例如，下列命令也會取得 Win32_Bios WMI 類別之實例的 Name 和 Version 屬性值。</span><span class="sxs-lookup"><span data-stu-id="02057-141">For example, the following command also gets the values of the Name and Version properties of instances of the Win32_Bios WMI class.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a><span data-ttu-id="02057-142">使用 CIMINSTANCE 指令 CMDLET</span><span class="sxs-lookup"><span data-stu-id="02057-142">USING THE GET-CIMINSTANCE CMDLET</span></span>

<span data-ttu-id="02057-143">從 Windows PowerShell 3.0 開始，您可以使用 Get-CimInstance Cmdlet 來執行 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="02057-143">Beginning in Windows PowerShell 3.0, you can use the Get-CimInstance cmdlet to run WQL queries.</span></span>

<span data-ttu-id="02057-144">Get-CimInstance 取得 CIM 相容類別的實例，包括 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="02057-144">Get-CimInstance gets instances of CIM-compliant classes, including WMI classes.</span></span> <span data-ttu-id="02057-145">Windows PowerShell 3.0 引進的 CIM Cmdlet 會執行與 WMI Cmdlet 相同的工作。</span><span class="sxs-lookup"><span data-stu-id="02057-145">The CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="02057-146">CIM Cmdlet 符合 WS-Management (WSMan) 標準以及通用訊息模型 (CIM) 標準，可讓 Cmdlet 使用相同的技術來管理執行其他作業系統的 Windows 電腦和電腦。</span><span class="sxs-lookup"><span data-stu-id="02057-146">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and computers that are running other operating systems.</span></span>

<span data-ttu-id="02057-147">下列命令使用 Get-CimInstance Cmdlet 來執行 WQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="02057-147">The following command uses the Get-CimInstance cmdlet to run a WQL query.</span></span>

<span data-ttu-id="02057-148">任何可以搭配 Get-WmiObject 使用的 WQL 查詢，也可以搭配 CimInstance 使用。</span><span class="sxs-lookup"><span data-stu-id="02057-148">Any WQL query that can be used with Get-WmiObject can also be used with Get-CimInstance.</span></span>

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="02057-149">Get-CimInstance 會傳回 CimInstance 物件，而不是 Get-WmiObject 傳回的 System.management.managementobject，但物件相當類似。</span><span class="sxs-lookup"><span data-stu-id="02057-149">Get-CimInstance returns a CimInstance object, instead of the ManagementObject that Get-WmiObject returns, but the objects are quite similar.</span></span>

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a><span data-ttu-id="02057-150">使用 [wmisearcher] 類型加速器</span><span class="sxs-lookup"><span data-stu-id="02057-150">USING THE [wmisearcher] TYPE ACCELERATOR</span></span>

<span data-ttu-id="02057-151">[Wmisearcher] 類型加速器會從 WQL 語句字串建立 ManagementObjectSearcher 物件。</span><span class="sxs-lookup"><span data-stu-id="02057-151">The [wmisearcher] type accelerator creates a ManagementObjectSearcher object from a WQL statement string.</span></span> <span data-ttu-id="02057-152">ManagementObjectSearcher 物件有許多屬性和方法，但是最基本的方法是 Get 方法，它會叫用指定的 WMI 查詢並傳回產生的物件。</span><span class="sxs-lookup"><span data-stu-id="02057-152">The ManagementObjectSearcher object has many properties and methods, but the most basic method is the Get method, which invokes the specified WMI query and returns the resulting objects.</span></span>

<span data-ttu-id="02057-153">藉由使用 [wmisearcher]，您可以輕鬆地存取 ManagementObjectSearcher .NET Framework 類別。</span><span class="sxs-lookup"><span data-stu-id="02057-153">By using the [wmisearcher], you gain easy access to the ManagementObjectSearcher .NET Framework class.</span></span> <span data-ttu-id="02057-154">這可讓您查詢 WMI 並設定查詢的執行方式。</span><span class="sxs-lookup"><span data-stu-id="02057-154">This lets you query WMI and to configure the way the query is conducted.</span></span>

<span data-ttu-id="02057-155">若要使用 [wmisearcher] 類型加速器：</span><span class="sxs-lookup"><span data-stu-id="02057-155">To use the [wmisearcher] type accelerator:</span></span>

1. <span data-ttu-id="02057-156">將 WQL 字串轉換成 ManagementObjectSearcher 物件。</span><span class="sxs-lookup"><span data-stu-id="02057-156">Cast the  WQL string into a ManagementObjectSearcher object.</span></span>
2. <span data-ttu-id="02057-157">呼叫 ManagementObjectSearcher 物件的 Get 方法。</span><span class="sxs-lookup"><span data-stu-id="02057-157">Call the Get method of the ManagementObjectSearcher object.</span></span>

<span data-ttu-id="02057-158">例如，下列命令會轉換「全選」查詢、將結果儲存在 $bios 變數中，然後在 $bios 變數中呼叫 ManagementObjectSearcher 物件的 Get 方法。</span><span class="sxs-lookup"><span data-stu-id="02057-158">For example, the following command casts the "select all" query, saves the result in the $bios variable, and then calls the Get method of the ManagementObjectSearcher object in the $bios variable.</span></span>

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="02057-159">注意：預設只會顯示選取的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="02057-159">NOTE: Only selected object properties are displayed by default.</span></span> <span data-ttu-id="02057-160">這些屬性是在 Types.ps1xml 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="02057-160">These properties are defined in the Types.ps1xml file.</span></span>

<span data-ttu-id="02057-161">您可以使用 [wmisearcher] 類型加速器來轉換查詢或變數。</span><span class="sxs-lookup"><span data-stu-id="02057-161">You can use the [wmisearcher] type accelerator to cast the query or the variable.</span></span> <span data-ttu-id="02057-162">在下列範例中，會使用 [wmisearcher] 類型加速器來轉換變數。</span><span class="sxs-lookup"><span data-stu-id="02057-162">In the following example, the [wmisearcher] type accelerator is used to cast the variable.</span></span> <span data-ttu-id="02057-163">結果會相同。</span><span class="sxs-lookup"><span data-stu-id="02057-163">The result is the same.</span></span>

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="02057-164">當您使用 [wmisearcher] 類型加速器時，它會將查詢字串變更為 ManagementObjectSearcher 物件，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="02057-164">When you use the [wmisearcher] type accelerator, it changes the query string into a ManagementObjectSearcher object, as shown in the following commands.</span></span>

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

<span data-ttu-id="02057-165">此命令格式適用于任何查詢。</span><span class="sxs-lookup"><span data-stu-id="02057-165">This command format works on any query.</span></span> <span data-ttu-id="02057-166">下列命令會取得 Win32_Bios WMI 類別之 Name 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="02057-166">The following command gets the value of the Name property of the Win32_Bios WMI class.</span></span>

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

<span data-ttu-id="02057-167">您可以使用單一命令來執行這項作業，雖然命令有點難以解讀。</span><span class="sxs-lookup"><span data-stu-id="02057-167">You can perform this operation in a single command, although the command is a bit more difficult to interpret.</span></span>

<span data-ttu-id="02057-168">使用這種格式時，您可以使用 [wmisearcher] 類型加速器將 WQL 查詢字串轉換成 ManagementObjectSearcher，然後在該物件上呼叫 Get 方法，全都在單一命令中。</span><span class="sxs-lookup"><span data-stu-id="02057-168">In this format, you use the [wmisearcher] type accelerator to cast the WQL query string to a ManagementObjectSearcher, and then call the Get method on the object -- all in a single command.</span></span> <span data-ttu-id="02057-169">括弧 ( # A1，用來括住轉換字串直接 Windows PowerShell，以在呼叫方法之前轉換字串。</span><span class="sxs-lookup"><span data-stu-id="02057-169">The parentheses () that enclose the casted string direct Windows PowerShell to cast the string before calling the method.</span></span>

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a><span data-ttu-id="02057-170">使用基本 WQL WHERE 語句</span><span class="sxs-lookup"><span data-stu-id="02057-170">USING THE BASIC WQL WHERE STATEMENT</span></span>

<span data-ttu-id="02057-171">Where 語句會針對 Select 語句所傳回的資料，建立條件。</span><span class="sxs-lookup"><span data-stu-id="02057-171">A Where statement establishes conditions for the data that a Select statement returns.</span></span>

<span data-ttu-id="02057-172">Where 語句的格式如下：</span><span class="sxs-lookup"><span data-stu-id="02057-172">The Where statement has the following format:</span></span>

```
where <property> <operator> <value>
```

<span data-ttu-id="02057-173">例如：</span><span class="sxs-lookup"><span data-stu-id="02057-173">For example:</span></span>

```
where Name = 'Notepad.exe'
```

<span data-ttu-id="02057-174">Where 語句會搭配 Select 語句使用，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02057-174">The Where statement is used with the Select statement, as shown in the following example.</span></span>

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

<span data-ttu-id="02057-175">使用 Where 語句時，屬性名稱和值必須是正確的。</span><span class="sxs-lookup"><span data-stu-id="02057-175">When using the Where statement, the property name and value must be accurate.</span></span>

<span data-ttu-id="02057-176">例如，下列命令會取得本機電腦上的「記事本」處理常式。</span><span class="sxs-lookup"><span data-stu-id="02057-176">For example, the following command gets the Notepad processes on the local computer.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

<span data-ttu-id="02057-177">但是，下列命令會失敗，因為進程名稱包含 ".exe" 副檔名。</span><span class="sxs-lookup"><span data-stu-id="02057-177">However, the following command fails, because the process name includes the ".exe" file name extension.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a><span data-ttu-id="02057-178">WHERE 語句比較運算子</span><span class="sxs-lookup"><span data-stu-id="02057-178">WHERE STATEMENT COMPARISON OPERATORS</span></span>

<span data-ttu-id="02057-179">下列運算子在 WQL Where 語句中是有效的。</span><span class="sxs-lookup"><span data-stu-id="02057-179">The following operators are valid in a WQL Where statement.</span></span>

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

<span data-ttu-id="02057-180">還有其他運算子，但這些運算子是用來進行比較的運算子。</span><span class="sxs-lookup"><span data-stu-id="02057-180">There are other operators, but these are the ones used for making comparisons.</span></span>

<span data-ttu-id="02057-181">例如，下列查詢會從進程優先權大於或等於11的 Win32_Process 類別中的處理常式，選取名稱和優先權屬性。</span><span class="sxs-lookup"><span data-stu-id="02057-181">For example, the following query selects the Name and Priority properties from processes in the Win32_Process class where the process priority is greater than or equal to 11.</span></span> <span data-ttu-id="02057-182">Get-WmiObject Cmdlet 會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="02057-182">The Get-WmiObject cmdlet runs the query.</span></span>

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a><span data-ttu-id="02057-183">在篩選參數中使用 WQL 運算子</span><span class="sxs-lookup"><span data-stu-id="02057-183">USING THE WQL OPERATORS IN THE FILTER PARAMETER</span></span>

<span data-ttu-id="02057-184">WQL 運算子也可以用在 Get-WmiObject 或 Get-CimInstance Cmdlet 的 Filter 參數值中，也可以在這些 Cmdlet 的查詢參數值中使用。</span><span class="sxs-lookup"><span data-stu-id="02057-184">The WQL operators can also be used in the value of the Filter parameter of the Get-WmiObject or Get-CimInstance cmdlets, as well as in the value of the Query parameters of these cmdlets.</span></span>

<span data-ttu-id="02057-185">例如，下列命令會取得最後五個進程的名稱和 ProcessID 屬性，其 ProcessID 值大於1004。</span><span class="sxs-lookup"><span data-stu-id="02057-185">For example, the following command gets the Name and ProcessID properties of the last five processes that have ProcessID values greater than 1004.</span></span> <span data-ttu-id="02057-186">此命令會使用 Filter 參數來指定 ProcessID 條件。</span><span class="sxs-lookup"><span data-stu-id="02057-186">The command uses the Filter parameter to specify the ProcessID condition.</span></span>

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a><span data-ttu-id="02057-187">使用 LIKE 運算子</span><span class="sxs-lookup"><span data-stu-id="02057-187">USING THE LIKE OPERATOR</span></span>

<span data-ttu-id="02057-188">Like 運算子可讓您使用萬用字元來篩選 WQL 查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="02057-188">The Like operator lets you use wildcard characters to filter the results of a WQL query.</span></span>

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

<span data-ttu-id="02057-189">使用 Like 運算子時，如果沒有任何萬用字元或範圍運算子，其行為就像是相等運算子 (=) ，而且只有在與模式完全相符時，才會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="02057-189">When the Like operator is used without any wildcard characters or range operators, it behaves like the equality operator (=) and returns objects only when they are an exact match for the pattern.</span></span>

<span data-ttu-id="02057-190">您可以將範圍作業與百分比萬用字元結合，以建立簡單但功能強大的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="02057-190">You can combine the range operation with the percent wildcard character to create simple, yet powerful filters.</span></span>

### <a name="like-operator-examples"></a><span data-ttu-id="02057-191">LIKE 運算子範例</span><span class="sxs-lookup"><span data-stu-id="02057-191">LIKE OPERATOR EXAMPLES</span></span>

#### <a name="example-1-range"></a><span data-ttu-id="02057-192">範例1： [ \<range> ]</span><span class="sxs-lookup"><span data-stu-id="02057-192">EXAMPLE 1: [\<range>]</span></span>

<span data-ttu-id="02057-193">下列命令會啟動 [記事本]，然後搜尋 Win32_Process 類別的實例，該實例的名稱開頭為 "H" 和 "N" (不區分大小寫) 。</span><span class="sxs-lookup"><span data-stu-id="02057-193">The following commands start Notepad and then search for an instance of the Win32_Process class that has a name that starts with a letter between "H" and "N" (case-insensitive).</span></span>

<span data-ttu-id="02057-194">此查詢應該會透過 Notepad.exe 從 Hotpad.exe 傳回任何處理程式。</span><span class="sxs-lookup"><span data-stu-id="02057-194">The query should return any process from Hotpad.exe through Notepad.exe.</span></span>

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a><span data-ttu-id="02057-195">範例2： [ \<range> ] 和%</span><span class="sxs-lookup"><span data-stu-id="02057-195">EXAMPLE 2: [\<range>] and %</span></span>

<span data-ttu-id="02057-196">下列命令會選取名稱以 A 和 P 之間的字母為開頭的所有進程 (不區分大小寫) ，後面接著零或多個字母的任何組合。</span><span class="sxs-lookup"><span data-stu-id="02057-196">The following commands select all process that have a name that begins with a letter between A and P (case-insensitive) followed by zero or more letters in any combination.</span></span>

<span data-ttu-id="02057-197">Get-WmiObject Cmdlet 會執行查詢，Select-Object Cmdlet 會取得 Name 和 ProcessID 屬性，而 Sort-Object Cmdlet 會依名稱以字母順序排序結果。</span><span class="sxs-lookup"><span data-stu-id="02057-197">The Get-WmiObject cmdlet runs the query, the Select-Object cmdlet gets the Name and ProcessID properties, and the Sort-Object cmdlet sorts the results in alphabetical order by name.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a><span data-ttu-id="02057-198">範例3：不在範圍 (^) </span><span class="sxs-lookup"><span data-stu-id="02057-198">EXAMPLE 3: Not in Range (^)</span></span>

<span data-ttu-id="02057-199">下列命令會取得名稱不是以下列任何字母開頭的進程： A、S、W、P、R、C、U、N</span><span class="sxs-lookup"><span data-stu-id="02057-199">The following command gets processes whose names do not begin with any of the following letters: A, S, W, P, R, C, U, N</span></span>

<span data-ttu-id="02057-200">並遵循零或多個字母。</span><span class="sxs-lookup"><span data-stu-id="02057-200">and followed zero or more letters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a><span data-ttu-id="02057-201">範例4：任何字元--或無 (% ) </span><span class="sxs-lookup"><span data-stu-id="02057-201">EXAMPLE 4: Any characters -- or none (%)</span></span>

<span data-ttu-id="02057-202">下列命令會取得名稱開頭為 "calc" 的處理常式。</span><span class="sxs-lookup"><span data-stu-id="02057-202">The following commands get processes that have names that begin with "calc".</span></span>
<span data-ttu-id="02057-203">WQL 中的% 符號相當於 \* 正則運算式中的星號 () 符號。</span><span class="sxs-lookup"><span data-stu-id="02057-203">The % symbol in WQL is equivalent to the asterisk (\*) symbol in regular expressions.</span></span>

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a><span data-ttu-id="02057-204">範例5：一個字元 (_) </span><span class="sxs-lookup"><span data-stu-id="02057-204">EXAMPLE 5: One character (_)</span></span>

<span data-ttu-id="02057-205">下列命令會取得名稱具有下列模式的進程： "c_lc.exe"，其中底線字元代表任何一個字元。</span><span class="sxs-lookup"><span data-stu-id="02057-205">The following commands get processes that have names that have the following pattern, "c_lc.exe" where the underscore character represents any one character.</span></span> <span data-ttu-id="02057-206">此模式會透過 czlc.exe 或 c9lc.exe 來比對 calc.exe 中的任何名稱，但不會比對 "c" 和 "l" 以超過一個字元分隔的名稱。</span><span class="sxs-lookup"><span data-stu-id="02057-206">This pattern matches any name from calc.exe through czlc.exe, or c9lc.exe, but does not match names in which the "c" and "l" are separated by more than one character.</span></span>

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a><span data-ttu-id="02057-207">範例6：完全相符</span><span class="sxs-lookup"><span data-stu-id="02057-207">EXAMPLE 6: Exact match</span></span>

<span data-ttu-id="02057-208">下列命令會取得名為 WLIDSVC.exe 的進程。</span><span class="sxs-lookup"><span data-stu-id="02057-208">The following commands get processes named WLIDSVC.exe.</span></span> <span data-ttu-id="02057-209">即使查詢使用 Like 關鍵字，它還是需要完全相符，因為該值不包含任何萬用字元。</span><span class="sxs-lookup"><span data-stu-id="02057-209">Even though the query uses the Like keyword, it requires an exact match, because the value does not include any wildcard characters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a><span data-ttu-id="02057-210">使用 OR 運算子</span><span class="sxs-lookup"><span data-stu-id="02057-210">USING THE OR OPERATOR</span></span>

<span data-ttu-id="02057-211">若要指定多個獨立的條件，請使用或關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02057-211">To specify multiple independent conditions, use the Or keyword.</span></span> <span data-ttu-id="02057-212">Where 子句中會出現或關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02057-212">The Or keyword appears in the Where clause.</span></span> <span data-ttu-id="02057-213">它會在兩個 (或更多) 條件上執行內含 OR 運算，並傳回符合任何條件的專案。</span><span class="sxs-lookup"><span data-stu-id="02057-213">It performs an inclusive OR operation on two (or more) conditions and returns items that meet any of the conditions.</span></span>

<span data-ttu-id="02057-214">Or 運算子的格式如下：</span><span class="sxs-lookup"><span data-stu-id="02057-214">The Or operator has the following format:</span></span>

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

<span data-ttu-id="02057-215">例如，下列命令會取得 Win32_Process WMI 類別的所有實例，但只有在處理常式名稱是 winword.exe 或 excel.exe 時才會傳回它們。</span><span class="sxs-lookup"><span data-stu-id="02057-215">For example, the following commands get all instances of the Win32_Process WMI class but returns them only if the process name is winword.exe or excel.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

<span data-ttu-id="02057-216">或語句可以搭配兩個以上的條件使用。</span><span class="sxs-lookup"><span data-stu-id="02057-216">The Or statement can be used with more than two conditions.</span></span> <span data-ttu-id="02057-217">在下列查詢中，或語句會取得 Winword.exe、Excel.exe 或 Powershell.exe。</span><span class="sxs-lookup"><span data-stu-id="02057-217">In the following query, the Or statement gets Winword.exe, Excel.exe, or Powershell.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a><span data-ttu-id="02057-218">使用 AND 運算子</span><span class="sxs-lookup"><span data-stu-id="02057-218">USING THE AND OPERATOR</span></span>

<span data-ttu-id="02057-219">若要指定多個相關條件，請使用和關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02057-219">To specify multiple related conditions, use the And keyword.</span></span> <span data-ttu-id="02057-220">And 關鍵字會出現在 Where 子句中。</span><span class="sxs-lookup"><span data-stu-id="02057-220">The And keyword appears in the Where clause.</span></span> <span data-ttu-id="02057-221">它會傳回符合所有條件的專案。</span><span class="sxs-lookup"><span data-stu-id="02057-221">It returns items that meet all of the conditions.</span></span>

<span data-ttu-id="02057-222">And 運算子的格式如下：</span><span class="sxs-lookup"><span data-stu-id="02057-222">The And operator has the following format:</span></span>

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

<span data-ttu-id="02057-223">例如，下列命令會取得名稱為 "Winword.exe" 且處理序識別碼為6512的進程。</span><span class="sxs-lookup"><span data-stu-id="02057-223">For example, the following commands get processes that have a name of "Winword.exe" and the process ID of 6512.</span></span>

<span data-ttu-id="02057-224">請注意，命令使用 Get-CimInstance Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="02057-224">Note that the commands use the Get-CimInstance cmdlet.</span></span>

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

<span data-ttu-id="02057-225">所有運算子（包括 Like 運算子）都適用于 Or 和 And 運算子。</span><span class="sxs-lookup"><span data-stu-id="02057-225">All operators, including the Like operators are valid with the Or and And operators.</span></span> <span data-ttu-id="02057-226">而且，您可以將 Or 和 And 運算子結合在單一查詢中，並以括弧括住 Windows PowerShell 要先處理的子句。</span><span class="sxs-lookup"><span data-stu-id="02057-226">And, you can combine the Or and And operators in a single query with parentheses that tell Windows PowerShell which clauses to process first.</span></span>

<span data-ttu-id="02057-227">此命令會使用 Windows PowerShell 接續字元 (') 將命令分為兩行。</span><span class="sxs-lookup"><span data-stu-id="02057-227">This command uses the Windows PowerShell continuation character (\`) divide the command into two lines.</span></span>

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a><span data-ttu-id="02057-228">搜尋 Null 值</span><span class="sxs-lookup"><span data-stu-id="02057-228">SEARCHING FOR NULL VALUES</span></span>

<span data-ttu-id="02057-229">在 WMI 中搜尋 null 值是一項挑戰，因為這可能會導致無法預期的結果。</span><span class="sxs-lookup"><span data-stu-id="02057-229">Searching for null values in WMI is challenging, because it can lead to unpredictable results.</span></span> <span data-ttu-id="02057-230">Null 不是零，且不等於或為空字串。</span><span class="sxs-lookup"><span data-stu-id="02057-230">Null is not zero and it is not equivalent or to an empty string.</span></span> <span data-ttu-id="02057-231">某些 WMI 類別屬性已初始化，其他則不是，因此搜尋 null 對所有屬性都可能無法運作。</span><span class="sxs-lookup"><span data-stu-id="02057-231">Some WMI class properties are initialized and others are not, so a search for null might not work for all properties.</span></span>

<span data-ttu-id="02057-232">若要搜尋 null 值，請使用的是值為 "null" 的是運算子。</span><span class="sxs-lookup"><span data-stu-id="02057-232">To search for null values, use the Is operator with a value of "null".</span></span>

<span data-ttu-id="02057-233">例如，下列命令會取得 IntallDate 屬性有 null 值的處理常式。</span><span class="sxs-lookup"><span data-stu-id="02057-233">For example, the following commands get processes that have a null value for the IntallDate property.</span></span> <span data-ttu-id="02057-234">這些命令會傳回許多進程。</span><span class="sxs-lookup"><span data-stu-id="02057-234">The commands return many processes.</span></span>

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="02057-235">相反地，下列命令會取得具有 Description 屬性之 null 值的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="02057-235">In contrast, the following command, gets user accounts that have a null value for the Description property.</span></span> <span data-ttu-id="02057-236">此命令不會傳回任何使用者帳戶，即使大部分的使用者帳戶沒有 Description 屬性的任何值也一樣。</span><span class="sxs-lookup"><span data-stu-id="02057-236">This command does not return any user accounts, even though most user accounts do not have any value for the Description property.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="02057-237">若要尋找沒有 Description 屬性值的使用者帳戶，請使用等號比較運算子來取得空字串。</span><span class="sxs-lookup"><span data-stu-id="02057-237">To find the user accounts that have no value for the Description property, use the equality operator to get an empty string.</span></span> <span data-ttu-id="02057-238">若要表示空字串，請使用兩個連續的單引號。</span><span class="sxs-lookup"><span data-stu-id="02057-238">To represent the empty string, use two consecutive single quotation marks.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a><span data-ttu-id="02057-239">使用 TRUE 或 FALSE</span><span class="sxs-lookup"><span data-stu-id="02057-239">USING TRUE OR FALSE</span></span>

<span data-ttu-id="02057-240">若要在 WMI 物件的屬性中取得布林值，請使用 True 和 False。</span><span class="sxs-lookup"><span data-stu-id="02057-240">To get Boolean values in the properties of WMI objects, use True and False.</span></span>
<span data-ttu-id="02057-241">它們不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="02057-241">They are not case sensitive.</span></span>

<span data-ttu-id="02057-242">下列 WQL 查詢只會傳回已加入網域之電腦上的本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="02057-242">The following WQL query returns only local user accounts from a domain joined computer.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

<span data-ttu-id="02057-243">若要尋找網域帳戶，請使用值 False，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02057-243">To find domain accounts, use a value of False, as shown in the following example.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a><span data-ttu-id="02057-244">使用 ESCAPE 字元</span><span class="sxs-lookup"><span data-stu-id="02057-244">USING THE ESCAPE CHARACTER</span></span>

<span data-ttu-id="02057-245">WQL 使用反斜線 (\) 作為其 escape 字元。</span><span class="sxs-lookup"><span data-stu-id="02057-245">WQL uses the backslash (\) as its escape character.</span></span> <span data-ttu-id="02057-246">這不同于 Windows PowerShell，其使用倒引號字元 (') 。</span><span class="sxs-lookup"><span data-stu-id="02057-246">This is different from Windows PowerShell, which uses the backtick character (\`).</span></span>

<span data-ttu-id="02057-247">引號和用於引號的字元通常需要換成，如此就不會被誤解。</span><span class="sxs-lookup"><span data-stu-id="02057-247">Quotation marks, and the characters used for quotation marks, often need to be escaped so that they are not misinterpreted.</span></span>

<span data-ttu-id="02057-248">若要尋找名稱包含單引號的使用者，請使用反斜線來 escape 單引號，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="02057-248">To find a user whose name includes a single quotation mark, use a backslash to escape the single quotation mark, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

<span data-ttu-id="02057-249">在某些情況下，反斜線也需要進行轉義。</span><span class="sxs-lookup"><span data-stu-id="02057-249">In some case, the backslash also needs to be escaped.</span></span> <span data-ttu-id="02057-250">例如，下列命令會產生不正確查詢錯誤，因為標題值中有反斜線。</span><span class="sxs-lookup"><span data-stu-id="02057-250">For example, the following commands generate an Invalid Query error due to the backslash in the Caption value.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

<span data-ttu-id="02057-251">若要對反斜線進行 escape，請使用第二個反斜線字元，如下列命令所示。</span><span class="sxs-lookup"><span data-stu-id="02057-251">To escape the backslash, use a second backslash character, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a><span data-ttu-id="02057-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02057-252">SEE ALSO</span></span>

[<span data-ttu-id="02057-253">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="02057-253">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="02057-254">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="02057-254">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="02057-255">about_WMI</span><span class="sxs-lookup"><span data-stu-id="02057-255">about_WMI</span></span>](about_WMI.md)

[<span data-ttu-id="02057-256">about_WMI_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="02057-256">about_WMI_Cmdlets</span></span>](about_WMI_Cmdlets.md)
