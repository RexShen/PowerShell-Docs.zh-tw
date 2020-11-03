---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 01/21/2020
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-CimMethod
ms.openlocfilehash: a3636d485464aa66dce11d6a88431497ea45d6d0
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "93205552"
---
# <span data-ttu-id="3e327-103">Invoke-CimMethod</span><span class="sxs-lookup"><span data-stu-id="3e327-103">Invoke-CimMethod</span></span>

## <span data-ttu-id="3e327-104">概要</span><span class="sxs-lookup"><span data-stu-id="3e327-104">SYNOPSIS</span></span>
<span data-ttu-id="3e327-105">叫用 CIM 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-105">Invokes a method of a CIM class.</span></span>

## <span data-ttu-id="3e327-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e327-106">SYNTAX</span></span>

### <span data-ttu-id="3e327-107">ClassNameComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="3e327-107">ClassNameComputerSet (Default)</span></span>

```
Invoke-CimMethod [-ClassName] <String> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3e327-108">ClassNameSessionSet</span><span class="sxs-lookup"><span data-stu-id="3e327-108">ClassNameSessionSet</span></span>

```
Invoke-CimMethod [-ClassName] <String> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3e327-109">ResourceUriComputerSet</span><span class="sxs-lookup"><span data-stu-id="3e327-109">ResourceUriComputerSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3e327-110">CimInstanceSessionSet</span><span class="sxs-lookup"><span data-stu-id="3e327-110">CimInstanceSessionSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e327-111">CimInstanceComputerSet</span><span class="sxs-lookup"><span data-stu-id="3e327-111">CimInstanceComputerSet</span></span>

```
Invoke-CimMethod [-ResourceUri <Uri>] [-InputObject] <CimInstance> [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e327-112">ResourceUriSessionSet</span><span class="sxs-lookup"><span data-stu-id="3e327-112">ResourceUriSessionSet</span></span>

```
Invoke-CimMethod -ResourceUri <Uri> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-Namespace <String>] [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3e327-113">CimClassComputerSet</span><span class="sxs-lookup"><span data-stu-id="3e327-113">CimClassComputerSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> [-ComputerName <String[]>] [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e327-114">CimClassSessionSet</span><span class="sxs-lookup"><span data-stu-id="3e327-114">CimClassSessionSet</span></span>

```
Invoke-CimMethod [-CimClass] <CimClass> -CimSession <CimSession[]> [[-Arguments] <IDictionary>]
 [-MethodName] <String> [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e327-115">QueryComputerSet</span><span class="sxs-lookup"><span data-stu-id="3e327-115">QueryComputerSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] [-ComputerName <String[]>]
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3e327-116">QuerySessionSet</span><span class="sxs-lookup"><span data-stu-id="3e327-116">QuerySessionSet</span></span>

```
Invoke-CimMethod -Query <String> [-QueryDialect <String>] -CimSession <CimSession[]>
 [[-Arguments] <IDictionary>] [-MethodName] <String> [-Namespace <String>]
 [-OperationTimeoutSec <UInt32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3e327-117">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3e327-117">DESCRIPTION</span></span>

<span data-ttu-id="3e327-118">此 `Invoke-CimMethod` Cmdlet 會使用 **引數** 參數所指定的名稱/值組，叫用 CIM 類別或 cim 實例的方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-118">The `Invoke-CimMethod` cmdlet invokes a method of a CIM class or CIM instance using the name-value pairs specified by the **Arguments** parameter.</span></span>

<span data-ttu-id="3e327-119">如果未指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="3e327-119">If the **InputObject** parameter is not specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="3e327-120">如果 **ComputerName** 參數或 **CimSession** 參數都未指定，則此 Cmdlet 會在本機 Windows Management Instrumentation (WMI) 使用元件物件模型 (COM) 會話。</span><span class="sxs-lookup"><span data-stu-id="3e327-120">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet works on local Windows Management Instrumentation (WMI) using a Component Object Model (COM) session.</span></span>
- <span data-ttu-id="3e327-121">如果指定 **computername** 參數或 **CimSession** 參數，則此 Cmdlet 適用于 **computername** 參數或 **CimSession** 參數所指定的 CIM 伺服器。</span><span class="sxs-lookup"><span data-stu-id="3e327-121">If either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet works against the CIM server specified by either the **ComputerName** parameter or the **CimSession** parameter.</span></span>

<span data-ttu-id="3e327-122">如果指定 **InputObject** 參數，Cmdlet 會以下列其中一種方式運作：</span><span class="sxs-lookup"><span data-stu-id="3e327-122">If the **InputObject** parameter is specified, the cmdlet works in one of the following ways:</span></span>

- <span data-ttu-id="3e327-123">如果 **ComputerName** 參數和 **CimSession** 參數都未指定，則此 Cmdlet 會使用輸入物件中的 CIM 會話或電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="3e327-123">If neither the **ComputerName** parameter nor the **CimSession** parameter is specified, then this cmdlet uses the CIM session or computer name from the input object.</span></span>
- <span data-ttu-id="3e327-124">如果指定 **ComputerName** 參數或 **CimSession** 參數，則此 Cmdlet 會使用 **CimSession** 參數值或 **ComputerName** 參數值。</span><span class="sxs-lookup"><span data-stu-id="3e327-124">If the either the **ComputerName** parameter or the **CimSession** parameter is specified, then this cmdlet uses the either the **CimSession** parameter value or **ComputerName** parameter value.</span></span> <span data-ttu-id="3e327-125">這不是常見的情況。</span><span class="sxs-lookup"><span data-stu-id="3e327-125">This is not a common scenario.</span></span>

## <span data-ttu-id="3e327-126">範例</span><span class="sxs-lookup"><span data-stu-id="3e327-126">EXAMPLES</span></span>

### <span data-ttu-id="3e327-127">範例1：叫用方法</span><span class="sxs-lookup"><span data-stu-id="3e327-127">Example 1: Invoke a method</span></span>

<span data-ttu-id="3e327-128">這個範例會叫用 **Win32_Process** 類別的 **Terminate** 方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-128">This example invokes the **Terminate** method of the **Win32_Process** class.</span></span>

```powershell
Invoke-CimMethod -Query 'select * from Win32_Process where name like "notepad%"' -MethodName "Terminate"
```

### <span data-ttu-id="3e327-129">範例2：使用 CIM 實例物件叫用方法</span><span class="sxs-lookup"><span data-stu-id="3e327-129">Example 2: Invoke a method using CIM instance object</span></span>

<span data-ttu-id="3e327-130">此範例會抓取 CIM 實例物件，並將它儲存在使用 Cmdlet 命名的變數中 `$x` `Get-CimInstance` 。</span><span class="sxs-lookup"><span data-stu-id="3e327-130">This example retrieves the CIM instance object and stores it in a variable named `$x` using the `Get-CimInstance` cmdlet.</span></span> <span data-ttu-id="3e327-131">變數的內容接著會用來做為 Cmdlet 的 **InputObject** `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="3e327-131">The contents of the variable are then used as the **InputObject** for the `Invoke-CimMethod` cmdlet.</span></span> <span data-ttu-id="3e327-132">針對 **CimInstance** 叫用 **GetOwner** 方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-132">The **GetOwner** method is invoked for the **CimInstance** .</span></span>

```powershell
$x = Get-CimInstance -Query 'Select * from Win32_Process where name like "notepad%"'
Invoke-CimMethod -InputObject $x -MethodName GetOwner
```

### <span data-ttu-id="3e327-133">範例3：使用引數叫用靜態方法</span><span class="sxs-lookup"><span data-stu-id="3e327-133">Example 3: Invoke a static method using arguments</span></span>

<span data-ttu-id="3e327-134">這個範例會叫用使用 **Arguments** 參數命名的 **Create** 方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-134">This example invokes the **Create** method named using the **Arguments** parameter.</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```

### <span data-ttu-id="3e327-135">範例4：用戶端驗證</span><span class="sxs-lookup"><span data-stu-id="3e327-135">Example 4: Client-side validation</span></span>

<span data-ttu-id="3e327-136">此範例會將 **CimClass** 物件傳遞給，以執行 **xyz** 方法的用戶端驗證 `Invoke-CimMethod` 。</span><span class="sxs-lookup"><span data-stu-id="3e327-136">This example performs client-side validation for the **xyz** method by passing a **CimClass** object to `Invoke-CimMethod`.</span></span>

```powershell
$c = Get-CimClass -ClassName Win32_Process
Invoke-CimMethod -CimClass $c -MethodName "xyz" -Arguments @{ CommandLine = 'notepad.exe' }
```

## <span data-ttu-id="3e327-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e327-137">PARAMETERS</span></span>

### <span data-ttu-id="3e327-138">-Arguments</span><span class="sxs-lookup"><span data-stu-id="3e327-138">-Arguments</span></span>

<span data-ttu-id="3e327-139">指定要傳送至呼叫之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-139">Specifies the parameters to pass to the called method.</span></span> <span data-ttu-id="3e327-140">將此參數的值指定為名稱/值組，並儲存在雜湊表中。</span><span class="sxs-lookup"><span data-stu-id="3e327-140">Specify the values for this parameter as name-value pairs, stored in a hash table.</span></span> <span data-ttu-id="3e327-141">輸入的值順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="3e327-141">The order of the values entered isn't important.</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-142">-CimClass</span><span class="sxs-lookup"><span data-stu-id="3e327-142">-CimClass</span></span>

<span data-ttu-id="3e327-143">指定表示伺服器上之 CIM 類別定義的 CIM 類別物件。</span><span class="sxs-lookup"><span data-stu-id="3e327-143">Specifies a CIM class object that represents a CIM class definition on the server.</span></span> <span data-ttu-id="3e327-144">叫用類別的靜態方法時，請使用此參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-144">Use this parameter when invoking a static method of a class.</span></span>

<span data-ttu-id="3e327-145">您可以使用 `Get-CimClass` Cmdlet 從伺服器取出類別定義。</span><span class="sxs-lookup"><span data-stu-id="3e327-145">You can use the `Get-CimClass` cmdlet to retrieve a class definition from the server.</span></span>

<span data-ttu-id="3e327-146">使用此參數會產生更佳的用戶端架構驗證。</span><span class="sxs-lookup"><span data-stu-id="3e327-146">Using this parameter results in better client side schema validations.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimClass
Parameter Sets: CimClassComputerSet, CimClassSessionSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-147">-CimSession</span><span class="sxs-lookup"><span data-stu-id="3e327-147">-CimSession</span></span>

<span data-ttu-id="3e327-148">使用指定的 CIM 會話來執行命令。</span><span class="sxs-lookup"><span data-stu-id="3e327-148">Runs the command using the specified CIM session.</span></span> <span data-ttu-id="3e327-149">輸入包含 CIM 會話的變數，或輸入可建立或取得 CIM 會話的命令，例如 `New-CimSession` 或 `Get-CimSession` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="3e327-149">Enter a variable that contains the CIM session, or a command that creates or gets the CIM session, such as the `New-CimSession` or `Get-CimSession` cmdlets.</span></span> <span data-ttu-id="3e327-150">如需詳細資訊，請參閱 [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md)。</span><span class="sxs-lookup"><span data-stu-id="3e327-150">For more information, see [about_CimSession](../Microsoft.PowerShell.Core/About/about_CimSession.md).</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: ClassNameSessionSet, CimInstanceSessionSet, CimClassSessionSet, QuerySessionSet, ResourceUriSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-151">-ClassName</span><span class="sxs-lookup"><span data-stu-id="3e327-151">-ClassName</span></span>

<span data-ttu-id="3e327-152">指定要執行作業之 CIM 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e327-152">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="3e327-153">這個參數只會用於靜態方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-153">This parameter is only used for static methods.</span></span> <span data-ttu-id="3e327-154">您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="3e327-154">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet
Aliases: Class

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-155">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3e327-155">-ComputerName</span></span>

<span data-ttu-id="3e327-156">指定要在其上執行 CIM 作業的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="3e327-156">Specifies the name of the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="3e327-157">您可以指定完整功能變數名稱 (FQDN) 、NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="3e327-157">You can specify a fully qualified domain name (FQDN), a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="3e327-158">使用這個參數時，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="3e327-158">When using this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span> <span data-ttu-id="3e327-159">否則，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="3e327-159">Otherwise, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="3e327-160">在同一部電腦上執行多個作業時，使用 CIM 會話連線以提升效能。</span><span class="sxs-lookup"><span data-stu-id="3e327-160">Connect using a CIM session for better performance when multiple operations are being performed on the same computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ClassNameComputerSet, ResourceUriComputerSet, CimClassComputerSet, CimInstanceComputerSet, QueryComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-161">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3e327-161">-InputObject</span></span>

<span data-ttu-id="3e327-162">指定要做為輸入的 CIM 實例物件，以叫用方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-162">Specifies a CIM instance object to use as input to invoke a method.</span></span> <span data-ttu-id="3e327-163">這個參數只能用來叫用實例方法。</span><span class="sxs-lookup"><span data-stu-id="3e327-163">This parameter can only be used to invoke instance methods.</span></span> <span data-ttu-id="3e327-164">若要叫用類別靜態方法，請使用 **類別** 參數或 **CimClass** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-164">To invoke class static methods, use the **Class** parameter or the **CimClass** parameter.</span></span>

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

### <span data-ttu-id="3e327-165">-方法名稱</span><span class="sxs-lookup"><span data-stu-id="3e327-165">-MethodName</span></span>

<span data-ttu-id="3e327-166">指定要叫用之 CIM 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="3e327-166">Specifies the name of the CIM method to invoke.</span></span> <span data-ttu-id="3e327-167">這是必要參數，不能是 null 或空白。</span><span class="sxs-lookup"><span data-stu-id="3e327-167">This parameter is mandatory and cannot be null or empty.</span></span> <span data-ttu-id="3e327-168">若要叫用 CIM 類別的靜態方法，請使用 **ClassName** 或 **CimClass** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-168">To invoke static method of a CIM class use the **ClassName** or the **CimClass** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Name

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-169">-Namespace</span><span class="sxs-lookup"><span data-stu-id="3e327-169">-Namespace</span></span>

<span data-ttu-id="3e327-170">指定 CIM 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3e327-170">Specifies the namespace for the CIM operation.</span></span> <span data-ttu-id="3e327-171">預設命名空間為 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="3e327-171">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="3e327-172">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="3e327-172">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

```yaml
Type: System.String
Parameter Sets: ClassNameComputerSet, ClassNameSessionSet, ResourceUriComputerSet, ResourceUriSessionSet, QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-173">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="3e327-173">-OperationTimeoutSec</span></span>

<span data-ttu-id="3e327-174">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="3e327-174">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="3e327-175">根據預設，此值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="3e327-175">By default, the value is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="3e327-176">如果 **OperationTimeoutSec** 參數設定為小於預設連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原。</span><span class="sxs-lookup"><span data-stu-id="3e327-176">If the **OperationTimeoutSec** parameter is set to a value less than the default connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable.</span></span>

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

### <span data-ttu-id="3e327-177">-Query</span><span class="sxs-lookup"><span data-stu-id="3e327-177">-Query</span></span>

<span data-ttu-id="3e327-178">指定要在 CIM 伺服器上執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="3e327-178">Specifies a query to run on the CIM server.</span></span> <span data-ttu-id="3e327-179">方法是在收到查詢結果的實例上叫用。</span><span class="sxs-lookup"><span data-stu-id="3e327-179">A method is invoked on the instances received as a result of the query.</span></span> <span data-ttu-id="3e327-180">您可以使用 **QueryDialect** 參數來指定查詢方言。</span><span class="sxs-lookup"><span data-stu-id="3e327-180">You can specify the query dialect using the **QueryDialect** parameter.</span></span>

<span data-ttu-id="3e327-181">如果指定的值包含雙引號 (`"`) 、單引號 (`'`) 或反斜線 (`\`) ，則必須在字元前面加上反斜線 () 字元來將這些字元加上引號 `\` 。</span><span class="sxs-lookup"><span data-stu-id="3e327-181">If the value specified contains double quotes (`"`), single quotes (`'`), or a backslash (`\`), you must escape those characters by prefixing them with the backslash (`\`) character.</span></span> <span data-ttu-id="3e327-182">如果指定的值使用 WQL LIKE 運算子，則必須以方括弧括住下列字元， (`[]`) ： percent (`%`) 、底線 (`_`) 或左方括弧 () `[` 。</span><span class="sxs-lookup"><span data-stu-id="3e327-182">If the value specified uses the WQL LIKE operator, then you must escape the following characters by enclosing them in square brackets (`[]`): percent (`%`), underscore (`_`), or opening square bracket (`[`).</span></span>

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-183">-QueryDialect</span><span class="sxs-lookup"><span data-stu-id="3e327-183">-QueryDialect</span></span>

<span data-ttu-id="3e327-184">指定用於查詢參數的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="3e327-184">Specifies the query language used for the Query parameter.</span></span> <span data-ttu-id="3e327-185">此參數可接受的值為： **WQL** 或 **CQL** 。</span><span class="sxs-lookup"><span data-stu-id="3e327-185">The acceptable values for this parameter are: **WQL** or **CQL** .</span></span>

<span data-ttu-id="3e327-186">預設值為 **WQL** 。</span><span class="sxs-lookup"><span data-stu-id="3e327-186">The default value is **WQL** .</span></span>

```yaml
Type: System.String
Parameter Sets: QueryComputerSet, QuerySessionSet
Aliases:

Required: False
Position: Named
Default value: WQL
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-187">-ResourceUri</span><span class="sxs-lookup"><span data-stu-id="3e327-187">-ResourceUri</span></span>

<span data-ttu-id="3e327-188">指定資源類別或實例 (URI) 的資源統一資源識別元。</span><span class="sxs-lookup"><span data-stu-id="3e327-188">Specifies the resource uniform resource identifier (URI) of the resource class or instance.</span></span>
<span data-ttu-id="3e327-189">URI 可用來識別電腦上的特定類型資源，例如磁碟或處理程序。</span><span class="sxs-lookup"><span data-stu-id="3e327-189">The URI is used to identify a specific type of resource, such as disks or processes, on a computer.</span></span>

<span data-ttu-id="3e327-190">URI 是由前置詞與資源路徑所組成。</span><span class="sxs-lookup"><span data-stu-id="3e327-190">A URI consists of a prefix and a path to a resource.</span></span> <span data-ttu-id="3e327-191">例如：</span><span class="sxs-lookup"><span data-stu-id="3e327-191">For example:</span></span>

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://intel.com/wbem/wscim/1/amt-schema/1/AMT_GeneralSettings`

<span data-ttu-id="3e327-192">根據預設，如果您未指定此參數，則會使用「DMTF 標準」資源 URI， `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` 並將類別名稱附加至該 URI。</span><span class="sxs-lookup"><span data-stu-id="3e327-192">By default, if you do not specify this parameter, the DMTF standard resource URI `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.</span></span>

<span data-ttu-id="3e327-193">**ResourceURI** 只能搭配使用 wsman 通訊協定所建立的 cim 會話，或是在指定 **ComputerName** 參數時使用，後者會使用 wsman 建立 cim 會話。</span><span class="sxs-lookup"><span data-stu-id="3e327-193">**ResourceURI** can only be used with CIM sessions created using the WSMan protocol, or when specifying the **ComputerName** parameter, which creates a CIM session using WSMan.</span></span>

<span data-ttu-id="3e327-194">當您指定這個參數但未指定 **ComputerName** 參數，或當您指定使用 DCOM 通訊協定所建立的 CIM 會話時，就會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="3e327-194">When you specify this parameter without specifying the **ComputerName** parameter, or when you specify a CIM session created using DCOM protocol, you get an error.</span></span> <span data-ttu-id="3e327-195">DCOM 通訊協定不支援 **ResourceURI** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-195">The DCOM protocol does not support the **ResourceURI** parameter.</span></span>

<span data-ttu-id="3e327-196">如果同時指定 **ResourceUri** 參數和 **篩選** 參數，則會忽略 **篩選** 參數。</span><span class="sxs-lookup"><span data-stu-id="3e327-196">If both the **ResourceUri** parameter and the **Filter** parameter are specified, the **Filter** parameter is ignored.</span></span>

```yaml
Type: System.Uri
Parameter Sets: ResourceUriSessionSet, ResourceUriComputerSet, CimInstanceSessionSet, CimInstanceComputerSet
Aliases:

Required: True (ResourceUriSessionSet, ResourceUriComputerSet), False (CimInstanceSessionSet, CimInstanceComputerSet)
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="3e327-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3e327-197">-Confirm</span></span>

<span data-ttu-id="3e327-198">在執行 Cmdlet 前提示您確認。</span><span class="sxs-lookup"><span data-stu-id="3e327-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3e327-199">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3e327-199">-WhatIf</span></span>

<span data-ttu-id="3e327-200">顯示執行 Cmdlet 後會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3e327-200">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3e327-201">Cmdlet 並不會執行。</span><span class="sxs-lookup"><span data-stu-id="3e327-201">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3e327-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e327-202">CommonParameters</span></span>

<span data-ttu-id="3e327-203">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="3e327-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e327-204">如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。</span><span class="sxs-lookup"><span data-stu-id="3e327-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3e327-205">輸入</span><span class="sxs-lookup"><span data-stu-id="3e327-205">INPUTS</span></span>

### <span data-ttu-id="3e327-206">CIM 類別</span><span class="sxs-lookup"><span data-stu-id="3e327-206">CIM class</span></span>

<span data-ttu-id="3e327-207">此 Cmdlet 會接受 CIM 類別做為輸入物件。</span><span class="sxs-lookup"><span data-stu-id="3e327-207">This cmdlet accepts a CIM class as an input object.</span></span>

### <span data-ttu-id="3e327-208">CIM 實例</span><span class="sxs-lookup"><span data-stu-id="3e327-208">CIM instance</span></span>

<span data-ttu-id="3e327-209">此 Cmdlet 會接受 CIM 實例作為輸入物件。</span><span class="sxs-lookup"><span data-stu-id="3e327-209">This cmdlet accepts a CIM instance as an input object.</span></span>

## <span data-ttu-id="3e327-210">輸出</span><span class="sxs-lookup"><span data-stu-id="3e327-210">OUTPUTS</span></span>

### <span data-ttu-id="3e327-211">System.Management.Automation.PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="3e327-211">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="3e327-212">此 Cmdlet 會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="3e327-212">This cmdlet returns an object.</span></span>

## <span data-ttu-id="3e327-213">注意</span><span class="sxs-lookup"><span data-stu-id="3e327-213">NOTES</span></span>

## <span data-ttu-id="3e327-214">相關連結</span><span class="sxs-lookup"><span data-stu-id="3e327-214">RELATED LINKS</span></span>

[<span data-ttu-id="3e327-215">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="3e327-215">Get-CimClass</span></span>](get-cimclass.md)

[<span data-ttu-id="3e327-216">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="3e327-216">Get-CimInstance</span></span>](get-ciminstance.md)

[<span data-ttu-id="3e327-217">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="3e327-217">Get-CimSession</span></span>](Get-CimSession.md)

[<span data-ttu-id="3e327-218">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="3e327-218">New-CimSession</span></span>](New-CimSession.md)
