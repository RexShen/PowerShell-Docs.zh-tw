---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/get-cimclass?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-CimClass
ms.openlocfilehash: 551ac39084ff7bf1729618d09cfa521cb6858242
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204351"
---
# <span data-ttu-id="cdc14-103">Get-CimClass</span><span class="sxs-lookup"><span data-stu-id="cdc14-103">Get-CimClass</span></span>

## <span data-ttu-id="cdc14-104">概要</span><span class="sxs-lookup"><span data-stu-id="cdc14-104">SYNOPSIS</span></span>
<span data-ttu-id="cdc14-105">取得特定命名空間中的 CIM 類別清單。</span><span class="sxs-lookup"><span data-stu-id="cdc14-105">Gets a list of CIM classes in a specific namespace.</span></span>

## <span data-ttu-id="cdc14-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cdc14-106">SYNTAX</span></span>

### <span data-ttu-id="cdc14-107">ComputerSet (預設) </span><span class="sxs-lookup"><span data-stu-id="cdc14-107">ComputerSet (Default)</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 [-ComputerName <String[]>] [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

### <span data-ttu-id="cdc14-108">SessionSet</span><span class="sxs-lookup"><span data-stu-id="cdc14-108">SessionSet</span></span>

```
Get-CimClass [[-ClassName] <String>] [[-Namespace] <String>] [-OperationTimeoutSec <UInt32>]
 -CimSession <CimSession[]> [-MethodName <String>] [-PropertyName <String>]
 [-QualifierName <String>] [<CommonParameters>]
```

## <span data-ttu-id="cdc14-109">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cdc14-109">DESCRIPTION</span></span>

<span data-ttu-id="cdc14-110">此 `Get-CimClass` Cmdlet 會抓取特定命名空間中的 CIM 類別清單。</span><span class="sxs-lookup"><span data-stu-id="cdc14-110">The `Get-CimClass` cmdlet retrieves a list of CIM classes in a specific namespace.</span></span> <span data-ttu-id="cdc14-111">如果未提供任何類別名稱，則 Cmdlet 會傳回命名空間中的所有類別。</span><span class="sxs-lookup"><span data-stu-id="cdc14-111">If there is no class name supplied, then the cmdlet returns all the classes in the namespace.</span></span> <span data-ttu-id="cdc14-112">與 CIM 實例不同的是，CIM 類別不包含從中抓取的 CIM 會話或電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="cdc14-112">Unlike a CIM instance, CIM classes do not contain the CIM session or computer name from which they are retrieved.</span></span>

## <span data-ttu-id="cdc14-113">範例</span><span class="sxs-lookup"><span data-stu-id="cdc14-113">EXAMPLES</span></span>

### <span data-ttu-id="cdc14-114">範例1：取得所有類別定義</span><span class="sxs-lookup"><span data-stu-id="cdc14-114">Example 1: Get all the class definitions</span></span>

<span data-ttu-id="cdc14-115">這個範例會取得命名空間 **根/cimv2** 下的所有類別定義。</span><span class="sxs-lookup"><span data-stu-id="cdc14-115">This example gets all the class definitions under the namespace **root/cimv2** .</span></span>

```powershell
Get-CimClass
```

### <span data-ttu-id="cdc14-116">範例2：取得具有特定名稱的類別</span><span class="sxs-lookup"><span data-stu-id="cdc14-116">Example 2: Get the classes with a specific name</span></span>

<span data-ttu-id="cdc14-117">此範例會取得在其名稱中包含文字 **磁片** 的類別。</span><span class="sxs-lookup"><span data-stu-id="cdc14-117">This example gets the classes that contain the word **disk** in their names.</span></span>

```powershell
Get-CimClass -ClassName *disk*
```

### <span data-ttu-id="cdc14-118">範例3：取得具有特定方法名稱的類別</span><span class="sxs-lookup"><span data-stu-id="cdc14-118">Example 3: Get the classes with a specific method name</span></span>

<span data-ttu-id="cdc14-119">這個範例會取得以名稱 **Win32** 開頭的類別，並具有以 **Term** 開頭的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="cdc14-119">This example gets the classes that start with the name **Win32** and have a method name that starts with **Term** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -MethodName Term*
```

### <span data-ttu-id="cdc14-120">範例4：取得具有特定屬性名稱的類別</span><span class="sxs-lookup"><span data-stu-id="cdc14-120">Example 4: Get the classes with a specific property name</span></span>

<span data-ttu-id="cdc14-121">這個範例會取得以名稱 **Win32** 開頭的類別，且具有名為 **Handle** 的屬性。</span><span class="sxs-lookup"><span data-stu-id="cdc14-121">This example gets the classes that start with the name **Win32** and have a property named **Handle** .</span></span>

```powershell
Get-CimClass -ClassName Win32* -PropertyName Handle
```

### <span data-ttu-id="cdc14-122">範例5：取得具有特定辨識符號名稱的類別</span><span class="sxs-lookup"><span data-stu-id="cdc14-122">Example 5: Get the classes with a specific qualifier name</span></span>

<span data-ttu-id="cdc14-123">此範例會取得以名稱 **Win32** 開頭的類別，並在其名稱中包含文字 **磁片** ，並且具有指定的限定詞 **關聯** 。</span><span class="sxs-lookup"><span data-stu-id="cdc14-123">This example gets the classes that start with the name **Win32** , contain the word **Disk** in their names and have the specified qualifier **Association** .</span></span>

```powershell
Get-CimClass -ClassName Win32*Disk* -QualifierName Association
```

### <span data-ttu-id="cdc14-124">範例6：從特定命名空間取得類別定義</span><span class="sxs-lookup"><span data-stu-id="cdc14-124">Example 6: Get the class definitions from a specific namespace</span></span>

<span data-ttu-id="cdc14-125">這個範例會從指定的命名空間 **根/standardCimv2** 取得名稱中包含文字 **Net** 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="cdc14-125">This example gets the class definitions that contain the word **Net** in their names from the specified namespace **root/standardCimv2** .</span></span>

```powershell
Get-CimClass -Namespace root/standardCimv2 -ClassName *Net*
```

### <span data-ttu-id="cdc14-126">範例7：從遠端伺服器取得類別定義</span><span class="sxs-lookup"><span data-stu-id="cdc14-126">Example 7: Get the class definitions from a remote server</span></span>

<span data-ttu-id="cdc14-127">這個範例會從指定的遠端伺服器 **Server01** 和 **Server02** 取得名稱中包含文字 **磁片** 的類別定義。</span><span class="sxs-lookup"><span data-stu-id="cdc14-127">This example gets the class definitions that contain the word **disk** in their names from the specified remote servers **Server01** and **Server02** .</span></span>

```powershell
Get-CimClass -ClassName *disk* -ComputerName Server01, Server02
```

### <span data-ttu-id="cdc14-128">範例8：使用 CIM 會話取得類別</span><span class="sxs-lookup"><span data-stu-id="cdc14-128">Example 8: Get the classes by using a CIM session</span></span>

```powershell
$s = New-CimSession -ComputerName Server01, Server02
Get-CimClass -ClassName *disk* -CimSession $s
```

<span data-ttu-id="cdc14-129">這組命令會建立具有多部電腦的會話，並使用指令程式將它儲存到變數 `$s` `New-CimSession` 中，然後使用 Cmdlet 取得類別 `Get-CimClass` 。</span><span class="sxs-lookup"><span data-stu-id="cdc14-129">This set of commands creates a session with multiple computers and stores it into a variable `$s` using the `New-CimSession` cmdlet, and then gets the classes using the `Get-CimClass` cmdlet.</span></span>

## <span data-ttu-id="cdc14-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="cdc14-130">PARAMETERS</span></span>

### <span data-ttu-id="cdc14-131">-CimSession</span><span class="sxs-lookup"><span data-stu-id="cdc14-131">-CimSession</span></span>

<span data-ttu-id="cdc14-132">在遠端工作階段或遠端電腦上執行 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cdc14-132">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="cdc14-133">輸入電腦名稱稱或會話物件，例如 `New-CimSession` 或 Cmdlet 的輸出 `Get-CimSession` 。</span><span class="sxs-lookup"><span data-stu-id="cdc14-133">Enter a computer name or a session object, such as the output of a `New-CimSession` or `Get-CimSession` cmdlet.</span></span> <span data-ttu-id="cdc14-134">預設為本機電腦上的目前工作階段。</span><span class="sxs-lookup"><span data-stu-id="cdc14-134">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="cdc14-135">-ClassName</span><span class="sxs-lookup"><span data-stu-id="cdc14-135">-ClassName</span></span>

<span data-ttu-id="cdc14-136">指定要執行作業之 CIM 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="cdc14-136">Specifies the name of the CIM class for which to perform the operation.</span></span> <span data-ttu-id="cdc14-137">您可以使用 tab 鍵自動完成來流覽類別清單，因為 PowerShell 會從本機 WMI 伺服器取得類別清單，以提供類別名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="cdc14-137">You can use tab completion to browse the list of classes, because PowerShell gets a list of classes from the local WMI server to provide a list of class names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cdc14-138">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="cdc14-138">-ComputerName</span></span>

<span data-ttu-id="cdc14-139">指定要在其上執行 CIM 操作的電腦。</span><span class="sxs-lookup"><span data-stu-id="cdc14-139">Specifies the computer on which you want to run the CIM operation.</span></span> <span data-ttu-id="cdc14-140">您可以指定完整功能變數名稱 (FQDN) NetBIOS 名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="cdc14-140">You can specify a fully qualified domain name (FQDN) a NetBIOS name, or an IP address.</span></span>

<span data-ttu-id="cdc14-141">如果您指定這個參數，此 Cmdlet 會使用 WsMan 通訊協定建立指定電腦的暫時會話。</span><span class="sxs-lookup"><span data-stu-id="cdc14-141">If you specify this parameter, the cmdlet creates a temporary session to the specified computer using the WsMan protocol.</span></span>

<span data-ttu-id="cdc14-142">如果您未指定這個參數，此 Cmdlet 會在本機電腦上使用元件物件模型 (COM) 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="cdc14-142">If you do not specify this parameter, the cmdlet performs the operation on the local computer using Component Object Model (COM).</span></span>

<span data-ttu-id="cdc14-143">如果在同一部電腦上執行多個作業，使用 CIM 會話可提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="cdc14-143">If multiple operations are being performed on the same computer, using a CIM session gives better performance.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerSet
Aliases: CN, ServerName

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="cdc14-144">-方法名稱</span><span class="sxs-lookup"><span data-stu-id="cdc14-144">-MethodName</span></span>

<span data-ttu-id="cdc14-145">尋找具有符合此名稱之方法的類別。</span><span class="sxs-lookup"><span data-stu-id="cdc14-145">Finds the classes that have a method matching this name.</span></span> <span data-ttu-id="cdc14-146">您可以使用萬用字元搭配此參數。</span><span class="sxs-lookup"><span data-stu-id="cdc14-146">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cdc14-147">-Namespace</span><span class="sxs-lookup"><span data-stu-id="cdc14-147">-Namespace</span></span>

<span data-ttu-id="cdc14-148">指定 CIM 作業的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cdc14-148">Specifies the namespace for CIM operation.</span></span> <span data-ttu-id="cdc14-149">預設命名空間為 **root/cimv2** 。</span><span class="sxs-lookup"><span data-stu-id="cdc14-149">The default namespace is **root/cimv2** .</span></span> <span data-ttu-id="cdc14-150">您可以使用 tab 鍵自動完成來流覽命名空間清單，因為 PowerShell 會取得本機 WMI 伺服器的命名空間清單，以提供命名空間清單。</span><span class="sxs-lookup"><span data-stu-id="cdc14-150">You can use tab completion to browse the list of namespaces, because PowerShell gets a list of namespaces from the local WMI server to provide the list of namespaces.</span></span>

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

### <span data-ttu-id="cdc14-151">-OperationTimeoutSec</span><span class="sxs-lookup"><span data-stu-id="cdc14-151">-OperationTimeoutSec</span></span>

<span data-ttu-id="cdc14-152">指定 Cmdlet 等候電腦回應的時間長度。</span><span class="sxs-lookup"><span data-stu-id="cdc14-152">Specifies the amount of time that the cmdlet waits for a response from the computer.</span></span> <span data-ttu-id="cdc14-153">根據預設，此參數的值為0，表示此 Cmdlet 會使用伺服器的預設超時值。</span><span class="sxs-lookup"><span data-stu-id="cdc14-153">By default, the value of this parameter is 0, which means that the cmdlet uses the default timeout value for the server.</span></span>

<span data-ttu-id="cdc14-154">如果 **OperationTimeoutSec** 參數設定為小於健全連接重試超時時間3分鐘的值，則超過 **OperationTimeoutSec** 參數值的網路失敗就無法復原，因為伺服器上的作業會在用戶端重新連線之前超時。</span><span class="sxs-lookup"><span data-stu-id="cdc14-154">If the **OperationTimeoutSec** parameter is set to a value less than the robust connection retry timeout of 3 minutes, network failures that last more than the value of the **OperationTimeoutSec** parameter are not recoverable, because the operation on the server times out before the client can reconnect.</span></span>

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

### <span data-ttu-id="cdc14-155">-PropertyName</span><span class="sxs-lookup"><span data-stu-id="cdc14-155">-PropertyName</span></span>

<span data-ttu-id="cdc14-156">尋找具有與此名稱相符之屬性的類別。</span><span class="sxs-lookup"><span data-stu-id="cdc14-156">Finds the classes which have a property matching this name.</span></span> <span data-ttu-id="cdc14-157">您可以使用萬用字元搭配此參數。</span><span class="sxs-lookup"><span data-stu-id="cdc14-157">You can use wildcard characters with this parameter.</span></span>

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

### <span data-ttu-id="cdc14-158">-QualifierName</span><span class="sxs-lookup"><span data-stu-id="cdc14-158">-QualifierName</span></span>

<span data-ttu-id="cdc14-159">依類別層級限定詞名稱篩選類別。</span><span class="sxs-lookup"><span data-stu-id="cdc14-159">Filters the classes by class level qualifier name.</span></span> <span data-ttu-id="cdc14-160">您可以使用萬用字元搭配此參數。</span><span class="sxs-lookup"><span data-stu-id="cdc14-160">You can use wildcard characters with this parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="cdc14-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cdc14-161">CommonParameters</span></span>

<span data-ttu-id="cdc14-162">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="cdc14-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cdc14-163">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="cdc14-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cdc14-164">輸入</span><span class="sxs-lookup"><span data-stu-id="cdc14-164">INPUTS</span></span>

### <span data-ttu-id="cdc14-165">無</span><span class="sxs-lookup"><span data-stu-id="cdc14-165">None</span></span>

<span data-ttu-id="cdc14-166">此 Cmdlet 不接受任何輸入物件。</span><span class="sxs-lookup"><span data-stu-id="cdc14-166">This cmdlet accepts no input objects.</span></span>

## <span data-ttu-id="cdc14-167">輸出</span><span class="sxs-lookup"><span data-stu-id="cdc14-167">OUTPUTS</span></span>

### <span data-ttu-id="cdc14-168">CimClass。</span><span class="sxs-lookup"><span data-stu-id="cdc14-168">Microsoft.Management.Infrastructure.CimClass</span></span>

<span data-ttu-id="cdc14-169">此 Cmdlet 會傳回 CIM 類別物件。</span><span class="sxs-lookup"><span data-stu-id="cdc14-169">This cmdlet returns a CIM class object.</span></span>

## <span data-ttu-id="cdc14-170">注意</span><span class="sxs-lookup"><span data-stu-id="cdc14-170">NOTES</span></span>

## <span data-ttu-id="cdc14-171">相關連結</span><span class="sxs-lookup"><span data-stu-id="cdc14-171">RELATED LINKS</span></span>

[<span data-ttu-id="cdc14-172">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="cdc14-172">New-CimSession</span></span>](New-CimSession.md)
