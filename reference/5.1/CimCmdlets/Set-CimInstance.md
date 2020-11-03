---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/set-ciminstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-CimInstance
ms.openlocfilehash: 7f44ddf52c2ad3ce68c5eccf0e8f952a0fa1873e
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205335"
---
# <span data-ttu-id="33372-103">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-103">Set-CimInstance</span></span>

## <span data-ttu-id="33372-104">概要</span><span class="sxs-lookup"><span data-stu-id="33372-104">SYNOPSIS</span></span>
<span data-ttu-id="33372-105">藉由呼叫 CIM 類別的 ModifyInstance 方法，修改 CIM 伺服器上的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="33372-105">Modifies a CIM instance on a CIM server by calling the ModifyInstance method of the CIM class.</span></span>

## <span data-ttu-id="33372-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33372-106">SYNTAX</span></span>

### <span data-ttu-id="33372-107">CimInstanceComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="33372-107">CimInstanceComputerSet (Default)</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="33372-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="33372-108">CimInstanceSessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-Property <IDictionary>] [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="33372-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="33372-109">QuerySessionSet</span></span>

```
Set-CimInstance -CimSession <CimSession[]> [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="33372-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="33372-110">QueryComputerSet</span></span>

```
Set-CimInstance [-ComputerName <String[]>] [-Namespace <String>] [-OperationTimeoutSec <UInt32>]
 [-Query] <String> [-QueryDialect <String>] -Property <IDictionary> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="33372-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="33372-111">DESCRIPTION</span></span>

<span data-ttu-id="33372-112">此 Cmdlet 會修改 CIM 伺服器上的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="33372-112">This cmdlet modifies a CIM instance on a CIM server.</span></span>

<span data-ttu-id="33372-113">如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="33372-113">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="33372-114">如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。</span><span class="sxs-lookup"><span data-stu-id="33372-114">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="33372-115">如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="33372-115">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="33372-116">如果指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="33372-116">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="33372-117">如果 **ComputerName** 參數和 **CimSession** 參數都未指定，則此 Cmdlet 會使用輸入物件中的 CIM 會話或電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="33372-117">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="33372-118">如果指定 **ComputerName** 參數或 **CimSession** 參數，則此 Cmdlet 會使用 **CimSession** 參數值或 **ComputerName** 參數值。</span><span class="sxs-lookup"><span data-stu-id="33372-118">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="33372-119">這並不常見。</span><span class="sxs-lookup"><span data-stu-id="33372-119">This is not very common.</span></span>

## <span data-ttu-id="33372-120">範例</span><span class="sxs-lookup"><span data-stu-id="33372-120">EXAMPLES</span></span>

### <span data-ttu-id="33372-121">範例1：設定 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="33372-121">Example 1: Set the CIM instance</span></span>

<span data-ttu-id="33372-122">這個範例會使用 **查詢** 參數，將 **VariableValue** 屬性的值設定為 **abcd** 。</span><span class="sxs-lookup"><span data-stu-id="33372-122">This example sets the value of the **VariableValue** property to **abcd** using the **Query** parameter.</span></span> <span data-ttu-id="33372-123">您可以修改符合 Windows Management Instrumentation 查詢語言 (WQL) 查詢的實例。</span><span class="sxs-lookup"><span data-stu-id="33372-123">You can modify instances matching a Windows Management Instrumentation Query Language (WQL) query.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="33372-124">範例2：使用管線設定 CIM 實例屬性</span><span class="sxs-lookup"><span data-stu-id="33372-124">Example 2: Set the CIM instance property using pipeline</span></span>

<span data-ttu-id="33372-125">此範例會使用 Cmdlet 來抓取 **查詢** 參數所篩選的 CIM 實例物件 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="33372-125">This example retrieves the CIM instance object filtered by the **Query** parameter using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="33372-126">此 `Set-CimInstance` Cmdlet 會將 **VariableValue** 屬性的值修改為 **abcd** 。</span><span class="sxs-lookup"><span data-stu-id="33372-126">The `Set-CimInstance` cmdlet modifies the value of **VariableValue** property to **abcd** .</span></span>

```powershell
Get-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' |
  Set-CimInstance -Property @{VariableValue="abcd"}
```

### <span data-ttu-id="33372-127">範例3：使用輸入物件設定 CIM 實例屬性</span><span class="sxs-lookup"><span data-stu-id="33372-127">Example 3: Set the CIM instance property using input object</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where Name="testvar"'
Set-CimInstance -InputObject $x -Property @{VariableValue="somevalue"} -PassThru
```

<span data-ttu-id="33372-128">這個範例會使用，將中查詢參數篩選的 CIM 實例物件 `$x` `Get-CimInstance` ，然後將變數的內容傳遞給 `Set-CimInstance` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="33372-128">This example retrieves the CIM instance objects filtered by the Query parameter in to a variable `$x` using `Get-CimInstance`, and then passes the contents of the variable to the `Set-CimInstance` cmdlet.</span></span> <span data-ttu-id="33372-129">`Set-CimInstance` 然後，將 **VariableValue** 屬性修改為 **somevalue** 。</span><span class="sxs-lookup"><span data-stu-id="33372-129">`Set-CimInstance` then modifies the **VariableValue** property to **somevalue** .</span></span> <span data-ttu-id="33372-130">因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="33372-130">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

### <span data-ttu-id="33372-131">範例4：設定 CIM 實例屬性</span><span class="sxs-lookup"><span data-stu-id="33372-131">Example 4: Set the CIM instance property</span></span>

<span data-ttu-id="33372-132">此範例會使用 Cmdlet 將 **查詢** 參數中指定的 CIM 實例物件 `$x` ，變更為變數 `Get-CimInstance` ，並將物件的 **VariableValue** 屬性值變更為 change。</span><span class="sxs-lookup"><span data-stu-id="33372-132">This example retrieves the CIM instance object that is specified in the **Query** parameter into a variable `$x` using the `Get-CimInstance` cmdlet, and changes the **VariableValue** property value of the object to change.</span></span> <span data-ttu-id="33372-133">然後會使用 Cmdlet 來儲存 CIM 實例物件 `Set-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="33372-133">The CIM instance object is then saved using the `Set-CimInstance` cmdlet.</span></span>
<span data-ttu-id="33372-134">因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="33372-134">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Environment where name="testvar"'
$x.VariableValue = "Change"
Set-CimInstance -CimInstance $x -PassThru
```

### <span data-ttu-id="33372-135">範例5：顯示要使用 WhatIf 修改的 CIM 實例清單</span><span class="sxs-lookup"><span data-stu-id="33372-135">Example 5: Show the list of CIM instances to modify using WhatIf</span></span>

<span data-ttu-id="33372-136">此範例會使用一般參數 **WhatIf** 來指定不應執行修改，但是只會輸出完成時所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="33372-136">This example uses the common parameter **WhatIf** to specify that the modification should not be done, but only output what would happen if it were done.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -WhatIf
```

### <span data-ttu-id="33372-137">範例6：在使用者確認之後設定 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="33372-137">Example 6: Set the CIM instance after confirmation from the user</span></span>

<span data-ttu-id="33372-138">這個範例會使用一般參數 **Confirm** 來指定只在使用者確認之後才執行修改。</span><span class="sxs-lookup"><span data-stu-id="33372-138">This example uses the common parameter **Confirm** to specify that the modification should be done only after confirmation from the user.</span></span>

```powershell
Set-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"' -Property @{VariableValue="abcd"} -Confirm
```

### <span data-ttu-id="33372-139">範例7：設定已建立的 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="33372-139">Example 7: Set the created CIM instance</span></span>

<span data-ttu-id="33372-140">此範例會使用 Cmdlet 建立具有指定屬性的 CIM 實例 `New-CimInstance` ，並將其內容提取到變數中 `$x` 。</span><span class="sxs-lookup"><span data-stu-id="33372-140">This example creates a CIM instance with the specified properties using the `New-CimInstance` cmdlet, and retrieves its contents in to a variable `$x`.</span></span> <span data-ttu-id="33372-141">變數接著會傳遞至 `Set-CimInstance` Cmdlet，此 Cmdlet 會將 **VariableValue** 屬性的值修改為 **somevalue** 。</span><span class="sxs-lookup"><span data-stu-id="33372-141">The variable is then passed to the `Set-CimInstance` cmdlet, which modifies the value of **VariableValue** property to **somevalue** .</span></span>
<span data-ttu-id="33372-142">因為使用 **Passthru** 參數，所以此範例會傳回修改過的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="33372-142">Because the **Passthru** parameter is used, This example returns a modified CIM instance object.</span></span>

```powershell
$x = New-CimInstance -ClassName Win32_Environment -Property @{Name="testvar";UserName="domain\user"} -Keys Name,UserName -ClientOnly
Set-CimInstance -CimInstance $x -Property @{VariableValue="somevalue"} -PassThru
```

## <span data-ttu-id="33372-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="33372-143">PARAMETERS</span></span>

### <span data-ttu-id="33372-144">-CimSession</span><span class="sxs-lookup"><span data-stu-id="33372-144">-CimSession</span></span>

<span data-ttu-id="33372-145">在遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="33372-145">Runs the cmdlets on a remote computer.</span></span> <span data-ttu-id="33372-146">輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="33372-146">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: QuerySessionSet, CimInstanceSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-147">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="33372-147">-ComputerName</span></span>

<span data-ttu-id="33372-148">指定要在其上執行 CIM 作業的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="33372-148">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="33372-149">您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="33372-149">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="33372-150">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="33372-150">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="33372-151">如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="33372-151">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="33372-152">如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="33372-152">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="33372-153">-InputObject</span><span class="sxs-lookup"><span data-stu-id="33372-153">-InputObject</span></span>

<span data-ttu-id="33372-154">指定要做為輸入使用的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="33372-154">Specifies a CIM instance object to use as input.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-155">-Namespace</span><span class="sxs-lookup"><span data-stu-id="33372-155">-Namespace</span></span>

<span data-ttu-id="33372-156">指定 CIM 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="33372-156">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="33372-157">預設命名空間為 root/cimv2。</span><span class="sxs-lookup"><span data-stu-id="33372-157">The default namespace is root/cimv2.</span></span> <span data-ttu-id="33372-158">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="33372-158">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-159">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="33372-159">-OperationTimeoutSec</span></span>

<span data-ttu-id="33372-160">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="33372-160">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="33372-161">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="33372-161">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="33372-162">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="33372-162">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="33372-163">-PassThru</span><span class="sxs-lookup"><span data-stu-id="33372-163">-PassThru</span></span>

<span data-ttu-id="33372-164">傳回代表您正在使用之項目的物件。</span><span class="sxs-lookup"><span data-stu-id="33372-164">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="33372-165">根據預設，此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="33372-165">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="33372-166">-Property</span><span class="sxs-lookup"><span data-stu-id="33372-166">-Property</span></span>

<span data-ttu-id="33372-167">使用) 的名稱/值組，將 CIM 實例的屬性指定為雜湊表 (。</span><span class="sxs-lookup"><span data-stu-id="33372-167">Specifies the properties of the CIM instance as a hash table (using name-value pairs).</span></span> <span data-ttu-id="33372-168">只有使用此參數指定的屬性才會變更。</span><span class="sxs-lookup"><span data-stu-id="33372-168">Only the properties specified using this parameter are changed.</span></span> <span data-ttu-id="33372-169">其他 CIM 實例的屬性則不會變更。</span><span class="sxs-lookup"><span data-stu-id="33372-169">Other properties of the CIM instance are not changed.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet, QuerySessionSet, QueryComputerSet
Aliases: Arguments

Required: True (QuerySessionSet, QueryComputerSet), False (CimInstanceComputerSet, CimInstanceSessionSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-170">-Query</span><span class="sxs-lookup"><span data-stu-id="33372-170">-Query</span></span>

<span data-ttu-id="33372-171">指定要在 CIM 伺服器上執行的查詢，以抓取要執行 Cmdlet 的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="33372-171">Specifies a query to run on the CIM server to retrieve CIM instances on which to run the cmdlet.</span></span> <span data-ttu-id="33372-172">您可以使用 QueryDialect 參數來指定查詢方言。</span><span class="sxs-lookup"><span data-stu-id="33372-172">You can specify the query dialect using the QueryDialect parameter.</span></span>

<span data-ttu-id="33372-173">如果指定的值包含雙引號 (`"`) 、單引號 (`'`) 或反斜線 (`\`) ，則必須在字元前面加上反斜線 () 字元來將這些字元加上引號 `\` 。</span><span class="sxs-lookup"><span data-stu-id="33372-173">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="33372-174">如果指定的值使用 WQL **LIKE** 運算子，則必須以方括弧括住下列字元， (`[]`) ： percent (`%`) 、底線 (`_`) 或左方括弧 () `[` 。</span><span class="sxs-lookup"><span data-stu-id="33372-174">If the value specified uses the WQL **LIKE** operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-175">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="33372-175">-QueryDialect</span></span>

<span data-ttu-id="33372-176">指定用於查詢參數的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="33372-176">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="33372-177">此參數可接受的值為： **WQL** 或 **CQL** 。</span><span class="sxs-lookup"><span data-stu-id="33372-177">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span> <span data-ttu-id="33372-178">預設值為 **WQL** 。</span><span class="sxs-lookup"><span data-stu-id="33372-178">The default value is **WQL** .</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-179">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="33372-179">-ResourceUri</span></span>

<span data-ttu-id="33372-180">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="33372-180">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="33372-181">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="33372-181">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="33372-182">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="33372-182">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="33372-183">例如：</span><span class="sxs-lookup"><span data-stu-id="33372-183">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="33372-184">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="33372-184">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="33372-185">ResourceURI 只能搭配使用 WSMan 通訊協定所建立的 CIM 會話，或是在指定 ComputerName 參數時使用，後者會使用 WSMan 建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="33372-185">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="33372-186">如果您指定此參數但未指定 ComputerName 參數，或如果您指定使用 DCOM 通訊協定建立的 CIM 會話，您將會收到錯誤，因為 DCOM 通訊協定不支援 ResourceURI 參數。</span><span class="sxs-lookup"><span data-stu-id="33372-186">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you will get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="33372-187">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="33372-187">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="33372-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="33372-188">-Confirm</span></span>

<span data-ttu-id="33372-189">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="33372-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="33372-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="33372-190">-WhatIf</span></span>

<span data-ttu-id="33372-191">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="33372-191">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="33372-192">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="33372-192">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="33372-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33372-193">CommonParameters</span></span>

<span data-ttu-id="33372-194">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="33372-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33372-195">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="33372-195">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="33372-196">輸入</span><span class="sxs-lookup"><span data-stu-id="33372-196">INPUTS</span></span>

### <span data-ttu-id="33372-197">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-197">Microsoft.Management.Infrastructure.CimInstance</span></span>

## <span data-ttu-id="33372-198">輸出</span><span class="sxs-lookup"><span data-stu-id="33372-198">OUTPUTS</span></span>

### <span data-ttu-id="33372-199">Microsoft.Management.Infrastructure.CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-199">Microsoft.Management.Infrastructure.CimInstance</span></span>

<span data-ttu-id="33372-200">指定 **Passthru** 參數時，此 Cmdlet 會傳回修改過的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="33372-200">When the **Passthru** parameter is specified, this cmdlet returns a modified CIM instance object.</span></span>

## <span data-ttu-id="33372-201">注意</span><span class="sxs-lookup"><span data-stu-id="33372-201">NOTES</span></span>

## <span data-ttu-id="33372-202">相關連結</span><span class="sxs-lookup"><span data-stu-id="33372-202">RELATED LINKS</span></span>

[<span data-ttu-id="33372-203">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-203">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="33372-204">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-204">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="33372-205">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="33372-205">Remove-CimInstance</span></span>](remove-ciminstance.md)
