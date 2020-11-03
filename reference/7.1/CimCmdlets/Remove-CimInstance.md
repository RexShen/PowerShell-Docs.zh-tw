---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/remove-ciminstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-CimInstance
ms.openlocfilehash: f236956b1da5f9632ff163cbf8a818bf190fd29a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205448"
---
# <span data-ttu-id="a418b-103">Remove-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a418b-103">Remove-CimInstance</span></span>

## <span data-ttu-id="a418b-104">概要</span><span class="sxs-lookup"><span data-stu-id="a418b-104">SYNOPSIS</span></span>
<span data-ttu-id="a418b-105">從電腦移除 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-105">Removes a CIM instance from a computer.</span></span>

## <span data-ttu-id="a418b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a418b-106">SYNTAX</span></span>

### <span data-ttu-id="a418b-107">CimInstanceComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="a418b-107">CimInstanceComputerSet (Default)</span></span>

```
Remove-CimInstance [-ResourceUri <Uri>] [-ComputerName <String[]>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a418b-108">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="a418b-108">CimInstanceSessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [-ResourceUri <Uri>] [-OperationTimeoutSec <UInt32>]
 [-InputObject] <CimInstance> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a418b-109">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="a418b-109">QuerySessionSet</span></span>

```
Remove-CimInstance -CimSession <CimSession[]> [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a418b-110">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="a418b-110">QueryComputerSet</span></span>

```
Remove-CimInstance [-ComputerName <String[]>] [[-Namespace] <String>]
 [-OperationTimeoutSec <UInt32>] [-Query] <String> [-QueryDialect <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a418b-111">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="a418b-111">DESCRIPTION</span></span>

<span data-ttu-id="a418b-112">此 Cmdlet 會從 CIM 伺服器移除 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-112">This cmdlet removes a CIM instance from a CIM server.</span></span> <span data-ttu-id="a418b-113">您可以使用 Cmdlet 所抓取的 CIM 實例物件 `Get-CimInstance` ，或指定查詢來指定要移除的 cim 實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-113">You can specify the CIM instance to remove by using either a CIM instance object retrieved by the `Get-CimInstance` cmdlet, or by specifying a query.</span></span>

<span data-ttu-id="a418b-114">如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="a418b-114">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="a418b-115">如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。</span><span class="sxs-lookup"><span data-stu-id="a418b-115">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="a418b-116">如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a418b-116">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

## <span data-ttu-id="a418b-117">範例</span><span class="sxs-lookup"><span data-stu-id="a418b-117">EXAMPLES</span></span>

### <span data-ttu-id="a418b-118">範例1：移除 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="a418b-118">Example 1: Remove the CIM instance</span></span>

<span data-ttu-id="a418b-119">這個範例會使用 **查詢** 參數，從名為 **Win32_Environment** 的類別中移除以字元字串 **testvar** 開頭的 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-119">This example use the **Query** parameter to remove CIM instances from the class named **Win32_Environment** that start with the character string **testvar** .</span></span>

```powershell
Remove-CimInstance -Query 'Select * from Win32_Environment where name LIKE "testvar%"'
```

### <span data-ttu-id="a418b-120">範例2：使用 CIM 實例物件移除 CIM 實例</span><span class="sxs-lookup"><span data-stu-id="a418b-120">Example 2: Remove the CIM instance using CIM instance object</span></span>

<span data-ttu-id="a418b-121">此範例會取出 **查詢** 參數所篩選的 CIM 實例物件，並將它們儲存在 `$var` 使用 Cmdlet 命名的變數中 `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="a418b-121">This example retrieves the CIM instance objects filtered by the **Query** parameter and stores them in variable named `$var` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="a418b-122">變數的內容接著會傳遞至 `Remove-CimInstance` Cmdlet，以移除 CIM 實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-122">The contents of the variable are then passed to the `Remove-CimInstance` cmdlet, which removes the CIM instances.</span></span>

```powershell
notepad.exe
$var = Get-CimInstance -Query 'Select * from Win32_Process where name LIKE "notepad%"'
Remove-CimInstance -InputObject $var
```

## <span data-ttu-id="a418b-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a418b-123">PARAMETERS</span></span>

### <span data-ttu-id="a418b-124">-CimSession</span><span class="sxs-lookup"><span data-stu-id="a418b-124">-CimSession</span></span>

<span data-ttu-id="a418b-125">使用指定的 CIM 會話來執行命令。</span><span class="sxs-lookup"><span data-stu-id="a418b-125">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="a418b-126">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a418b-126">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="a418b-127">如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="a418b-127">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimInstanceSessionSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a418b-128">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="a418b-128">-ComputerName</span></span>

<span data-ttu-id="a418b-129">指定要在其上執行 CIM 作業的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="a418b-129">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="a418b-130">您可以指定完整功能變數名稱 (FQDN) 或 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="a418b-130">You can specify a fully qualified domain name (FQDN) or a NetBIOS name.</span></span>

<span data-ttu-id="a418b-131">如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="a418b-131">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="a418b-132">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="a418b-132">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="a418b-133">如果在同一部電腦上執行多個作業，使用 CIM 會話進行連線可提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="a418b-133">If multiple operations are being performed on the same computer, connecting using a CIM session gives better performance.</span></span>

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

### <span data-ttu-id="a418b-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="a418b-134">-InputObject</span></span>

<span data-ttu-id="a418b-135">指定要從 CIM 伺服器移除的 CIM 實例物件。</span><span class="sxs-lookup"><span data-stu-id="a418b-135">Specifies a CIM instance object to be removed from the CIM server.</span></span> <span data-ttu-id="a418b-136">傳遞給 Cmdlet 的物件不會變更，只會移除 CIM 伺服器中的實例。</span><span class="sxs-lookup"><span data-stu-id="a418b-136">The object passed to the cmdlet is not changed, only the instance in the CIM server is removed.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimInstance
Parameter Sets: CimInstanceComputerSet, CimInstanceSessionSet
Aliases: CimInstance

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a418b-137">-Namespace</span><span class="sxs-lookup"><span data-stu-id="a418b-137">-Namespace</span></span>

<span data-ttu-id="a418b-138">指定 CIM 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a418b-138">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="a418b-139">預設命名空間為 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="a418b-139">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="a418b-140">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="a418b-140">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a418b-141">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="a418b-141">-OperationTimeoutSec</span></span>

<span data-ttu-id="a418b-142">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="a418b-142">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="a418b-143">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="a418b-143">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="a418b-144">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="a418b-144">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="a418b-145">-Query</span><span class="sxs-lookup"><span data-stu-id="a418b-145">-Query</span></span>

<span data-ttu-id="a418b-146">指定要在 CIM 伺服器上執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="a418b-146">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="a418b-147">您可以使用 **QueryDialect** 參數來指定查詢方言。</span><span class="sxs-lookup"><span data-stu-id="a418b-147">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="a418b-148">如果指定的值包含雙引號 (`"`) 、單引號 (`'`) 或反斜線 (`\`) ，則必須在字元前面加上反斜線 () 字元來將這些字元加上引號 `\` 。</span><span class="sxs-lookup"><span data-stu-id="a418b-148">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="a418b-149">如果指定的值使用 WQL LIKE 運算子，則必須以方括弧括住下列字元， (`[]`) ： percent (`%`) 、底線 (`_`) 或左方括弧 () `[` 。</span><span class="sxs-lookup"><span data-stu-id="a418b-149">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a418b-150">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="a418b-150">-QueryDialect</span></span>

<span data-ttu-id="a418b-151">指定用於查詢參數的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="a418b-151">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="a418b-152">此參數可接受的值為： **WQL** 或 **CQL** 。</span><span class="sxs-lookup"><span data-stu-id="a418b-152">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span> <span data-ttu-id="a418b-153">預設值為 **WQL** 。</span><span class="sxs-lookup"><span data-stu-id="a418b-153">The default value is **WQL** .</span></span>

```yaml
Type: System.String
Parameter Sets: QuerySessionSet, QueryComputerSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a418b-154">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="a418b-154">-ResourceUri</span></span>

<span data-ttu-id="a418b-155">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="a418b-155">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span> <span data-ttu-id="a418b-156">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="a418b-156">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="a418b-157">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="a418b-157">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="a418b-158">例如：</span><span class="sxs-lookup"><span data-stu-id="a418b-158">For example:</span></span>

- `http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`
- `http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="a418b-159">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="a418b-159">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="a418b-160">ResourceURI 只能搭配使用 WSMan 通訊協定所建立的 CIM 會話，或是在指定 ComputerName 參數時使用，後者會使用 WSMan 建立 CIM 會話。</span><span class="sxs-lookup"><span data-stu-id="a418b-160">ResourceURI can only be used with CIM sessions created using the WSMan protocol, or when specifying the ComputerName parameter, which creates a CIM session using WSMan.</span></span> <span data-ttu-id="a418b-161">如果您指定此參數但未指定 ComputerName 參數，或如果您指定使用 DCOM 通訊協定建立的 CIM 會話，則會收到錯誤，因為 DCOM 通訊協定不支援 ResourceURI 參數。</span><span class="sxs-lookup"><span data-stu-id="a418b-161">If you specify this parameter without specifying the ComputerName parameter, or if you specify a CIM session created using DCOM protocol, you get an error, because the DCOM protocol does not support the ResourceURI parameter.</span></span>

<span data-ttu-id="a418b-162">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="a418b-162">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

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

### <span data-ttu-id="a418b-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a418b-163">-Confirm</span></span>

<span data-ttu-id="a418b-164">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="a418b-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a418b-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a418b-165">-WhatIf</span></span>

<span data-ttu-id="a418b-166">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="a418b-166">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a418b-167">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="a418b-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a418b-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a418b-168">CommonParameters</span></span>

<span data-ttu-id="a418b-169">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="a418b-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a418b-170">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="a418b-170">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a418b-171">輸入</span><span class="sxs-lookup"><span data-stu-id="a418b-171">INPUTS</span></span>

### <span data-ttu-id="a418b-172">無</span><span class="sxs-lookup"><span data-stu-id="a418b-172">None</span></span>

<span data-ttu-id="a418b-173">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="a418b-173">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="a418b-174">輸出</span><span class="sxs-lookup"><span data-stu-id="a418b-174">OUTPUTS</span></span>

### <span data-ttu-id="a418b-175">無</span><span class="sxs-lookup"><span data-stu-id="a418b-175">None</span></span>

<span data-ttu-id="a418b-176">此 Cmdlet 不會產生任何輸出。</span><span class="sxs-lookup"><span data-stu-id="a418b-176">This cmdlet produces no outputs.</span></span>

## <span data-ttu-id="a418b-177">注意</span><span class="sxs-lookup"><span data-stu-id="a418b-177">NOTES</span></span>

## <span data-ttu-id="a418b-178">相關連結</span><span class="sxs-lookup"><span data-stu-id="a418b-178">RELATED LINKS</span></span>

[<span data-ttu-id="a418b-179">New-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a418b-179">New-CimInstance</span></span>](New-CimInstance.md)

[<span data-ttu-id="a418b-180">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a418b-180">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="a418b-181">Set-CimInstance</span><span class="sxs-lookup"><span data-stu-id="a418b-181">Set-CimInstance</span></span>](Set-CimInstance.md)

