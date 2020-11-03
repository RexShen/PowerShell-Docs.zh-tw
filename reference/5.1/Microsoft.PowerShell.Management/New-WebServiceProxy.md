---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-webserviceproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WebServiceProxy
ms.openlocfilehash: aea656bc8ad4416673a7abb7d32a58d45dd3cc4f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203587"
---
# <span data-ttu-id="f7b96-103">New-WebServiceProxy</span><span class="sxs-lookup"><span data-stu-id="f7b96-103">New-WebServiceProxy</span></span>

## <span data-ttu-id="f7b96-104">概要</span><span class="sxs-lookup"><span data-stu-id="f7b96-104">SYNOPSIS</span></span>
<span data-ttu-id="f7b96-105">建立 Web 服務 proxy 物件，可讓您使用和管理 PowerShell 中的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-105">Creates a Web service proxy object that lets you use and manage the Web service in PowerShell.</span></span>

## <span data-ttu-id="f7b96-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7b96-106">SYNTAX</span></span>

### <span data-ttu-id="f7b96-107">NoCredentials (預設值)</span><span class="sxs-lookup"><span data-stu-id="f7b96-107">NoCredentials (Default)</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [<CommonParameters>]
```

### <span data-ttu-id="f7b96-108">認證</span><span class="sxs-lookup"><span data-stu-id="f7b96-108">Credential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="f7b96-109">UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="f7b96-109">UseDefaultCredential</span></span>

```
New-WebServiceProxy [-Uri] <Uri> [[-Class] <String>] [[-Namespace] <String>] [-UseDefaultCredential]
 [<CommonParameters>]
```

## <span data-ttu-id="f7b96-110">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="f7b96-110">DESCRIPTION</span></span>

<span data-ttu-id="f7b96-111">此 `New-WebServiceProxy` Cmdlet 可讓您在 PowerShell 中使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-111">The `New-WebServiceProxy` cmdlet lets you use a Web service in PowerShell.</span></span> <span data-ttu-id="f7b96-112">此 Cmdlet 會連線到 Web 服務，並在 PowerShell 中建立 Web 服務 proxy 物件。</span><span class="sxs-lookup"><span data-stu-id="f7b96-112">The cmdlet connects to a Web service and creates a Web service proxy object in PowerShell.</span></span> <span data-ttu-id="f7b96-113">您可以使用 Proxy 物件來管理 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-113">You can use the proxy object to manage the Web service.</span></span>

<span data-ttu-id="f7b96-114">Web 服務是以 XML 為基礎的程式，可透過網路（尤其是透過網際網路）交換資料。</span><span class="sxs-lookup"><span data-stu-id="f7b96-114">A Web service is an XML-based program that exchanges data over a network, especially over the Internet.</span></span> <span data-ttu-id="f7b96-115">Microsoft .NET Framework 提供 Web 服務 Proxy 物件，這些物件會以 .NET Framework 物件代表 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-115">The Microsoft .NET Framework provides Web service proxy objects that represent the Web service as a .NET Framework object.</span></span>

## <span data-ttu-id="f7b96-116">範例</span><span class="sxs-lookup"><span data-stu-id="f7b96-116">EXAMPLES</span></span>

### <span data-ttu-id="f7b96-117">範例1：建立 Web 服務的 proxy</span><span class="sxs-lookup"><span data-stu-id="f7b96-117">Example 1: Create a proxy for a Web service</span></span>

<span data-ttu-id="f7b96-118">此範例會在 Windows PowerShell 中建立 .NET Framework 的計算機 Web 服務 proxy。</span><span class="sxs-lookup"><span data-stu-id="f7b96-118">This example creates a .NET Framework proxy of the calculator Web service in Windows PowerShell.</span></span>

```powershell
$calc = New-WebServiceProxy -Uri "http://www.dneonline.com/calculator.asmx?wsdl"
```

### <span data-ttu-id="f7b96-119">範例2：建立 Web 服務的 proxy 並指定命名空間和類別</span><span class="sxs-lookup"><span data-stu-id="f7b96-119">Example 2: Create a proxy for a Web service and specify namespace and class</span></span>

<span data-ttu-id="f7b96-120">這個範例會使用 `New-WebServiceProxy` Cmdlet 來建立 .NET Framework 的計算機 Web 服務 proxy。</span><span class="sxs-lookup"><span data-stu-id="f7b96-120">This example uses the `New-WebServiceProxy` cmdlet to create a .NET Framework proxy of the calculator Web service.</span></span>

```powershell
$URI = "http://www.dneonline.com/calculator.asmx?wsdl"
$calc = New-WebServiceProxy -Uri $URI -Namespace "WSProxy" -Class "Calculator"
```

<span data-ttu-id="f7b96-121">此命令會使用 **uri** 參數來指定 Uri 以及 **命名空間** 和 **類別** 參數，以指定物件的命名空間和類別。</span><span class="sxs-lookup"><span data-stu-id="f7b96-121">The command uses the **Uri** parameter to specify the URI and the **Namespace** and **Class** parameters to specify the namespace and class of the object.</span></span>

### <span data-ttu-id="f7b96-122">範例3：顯示 Web 服務 proxy 的方法</span><span class="sxs-lookup"><span data-stu-id="f7b96-122">Example 3: Display methods of a Web service proxy</span></span>

```powershell
$calc | Get-Member -MemberType method
```

```Output
   TypeName: WSProxy.Calculator

Name                      MemberType Definition
----                      ---------- ----------
Abort                     Method     void Abort()
Add                       Method     int Add(int intA, int intB)
AddAsync                  Method     void AddAsync(int intA, int intB), void AddAsync(int intA,
BeginAdd                  Method     System.IAsyncResult BeginAdd(int intA, int intB, System.Asy
BeginDivide               Method     System.IAsyncResult BeginDivide(int intA, int intB, System.
BeginMultiply             Method     System.IAsyncResult BeginMultiply(int intA, int intB, Syste
BeginSubtract             Method     System.IAsyncResult BeginSubtract(int intA, int intB, Syste
CancelAsync               Method     void CancelAsync(System.Object userState)
CreateObjRef              Method     System.Runtime.Remoting.ObjRef CreateObjRef(type requestedT
Discover                  Method     void Discover()
Dispose                   Method     void Dispose(), void IDisposable.Dispose()
Divide                    Method     int Divide(int intA, int intB)
DivideAsync               Method     void DivideAsync(int intA, int intB), void DivideAsync(int
EndAdd                    Method     int EndAdd(System.IAsyncResult asyncResult)
EndDivide                 Method     int EndDivide(System.IAsyncResult asyncResult)
EndMultiply               Method     int EndMultiply(System.IAsyncResult asyncResult)
EndSubtract               Method     int EndSubtract(System.IAsyncResult asyncResult)
Equals                    Method     bool Equals(System.Object obj)
GetHashCode               Method     int GetHashCode()
GetLifetimeService        Method     System.Object GetLifetimeService()
GetType                   Method     type GetType()
InitializeLifetimeService Method     System.Object InitializeLifetimeService()
Multiply                  Method     int Multiply(int intA, int intB)
MultiplyAsync             Method     void MultiplyAsync(int intA, int intB), void MultiplyAsync(
Subtract                  Method     int Subtract(int intA, int intB)
SubtractAsync             Method     void SubtractAsync(int intA, int intB), void SubtractAsync(
ToString                  Method     string ToString()
```

<span data-ttu-id="f7b96-123">此範例會使用 `Get-Member` Cmdlet 來顯示變數中 Web 服務 proxy 物件的方法 `$calc` 。</span><span class="sxs-lookup"><span data-stu-id="f7b96-123">This example uses the `Get-Member` cmdlet to display the methods of the Web service proxy object in the `$calc` variable.</span></span> <span data-ttu-id="f7b96-124">我們會在下列範例中使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="f7b96-124">We uses these methods in the following example.</span></span>

<span data-ttu-id="f7b96-125">請注意，proxy 物件的 **TypeName** （WebServiceProxy）會反映先前範例中所指定的命名空間和類別名稱。</span><span class="sxs-lookup"><span data-stu-id="f7b96-125">Notice that the **TypeName** of the proxy object, WebServiceProxy, reflects the namespace and class names that were specified in the previous example.</span></span>

### <span data-ttu-id="f7b96-126">範例4：使用 Web 服務 proxy</span><span class="sxs-lookup"><span data-stu-id="f7b96-126">Example 4: Use a Web service proxy</span></span>

```powershell
PS> $calc.Multiply(6,7)
42
```

<span data-ttu-id="f7b96-127">此範例會使用儲存在變數中的 Web 服務 proxy `$calc` 。</span><span class="sxs-lookup"><span data-stu-id="f7b96-127">This example uses the Web service proxy stored in the `$calc` variable.</span></span> <span data-ttu-id="f7b96-128">此命令會使用 proxy 的 **乘法** 方法。</span><span class="sxs-lookup"><span data-stu-id="f7b96-128">The command uses the **Multiply** method of the proxy.</span></span>

## <span data-ttu-id="f7b96-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f7b96-129">PARAMETERS</span></span>

### <span data-ttu-id="f7b96-130">-Class</span><span class="sxs-lookup"><span data-stu-id="f7b96-130">-Class</span></span>

<span data-ttu-id="f7b96-131">指定 Cmdlet 為 Web 服務建立之 Proxy 類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7b96-131">Specifies a name for the proxy class that the cmdlet creates for the Web service.</span></span> <span data-ttu-id="f7b96-132">此參數的值會與 **Namespace** 參數一起使用，以提供類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="f7b96-132">The value of this parameter is used together with the **Namespace** parameter to provide a fully qualified name for the class.</span></span> <span data-ttu-id="f7b96-133">預設值是從統一資源識別項 (URI) 產生。</span><span class="sxs-lookup"><span data-stu-id="f7b96-133">The default value is generated from the Uniform Resource Identifier (URI).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: FileName, FN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b96-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="f7b96-134">-Credential</span></span>

<span data-ttu-id="f7b96-135">指定具有執行此動作權限的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f7b96-135">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="f7b96-136">預設為目前使用者。</span><span class="sxs-lookup"><span data-stu-id="f7b96-136">The default is the current user.</span></span> <span data-ttu-id="f7b96-137">這可做為使用 **UseDefaultCredential** 參數的替代方案。</span><span class="sxs-lookup"><span data-stu-id="f7b96-137">This is an alternative to using the **UseDefaultCredential** parameter.</span></span>

<span data-ttu-id="f7b96-138">輸入使用者名稱（例如 User01 或 Domain01\User01），或輸入 **PSCredential** 物件，例如 Cmdlet 所產生的物件 `Get-Credential` 。</span><span class="sxs-lookup"><span data-stu-id="f7b96-138">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f7b96-139">如果您輸入使用者名稱，此 Cmdlet 會提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="f7b96-139">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Credential
Aliases: Cred

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b96-140">-Namespace</span><span class="sxs-lookup"><span data-stu-id="f7b96-140">-Namespace</span></span>

<span data-ttu-id="f7b96-141">指定新類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f7b96-141">Specifies a namespace for the new class.</span></span>

<span data-ttu-id="f7b96-142">這個參數的值會和 **class** 參數的值一起使用，以產生類別的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="f7b96-142">The value of this parameter is used together with the value of the **Class** parameter to generate a fully qualified name for the class.</span></span> <span data-ttu-id="f7b96-143">預設值為 **microsoft.powershell.commands.newwebserviceproxy.autogeneratedtypes. microsoft.powershell.commands.addtype.autogeneratedtypes** ，再加上從 URI 產生的類型。</span><span class="sxs-lookup"><span data-stu-id="f7b96-143">The default value is **Microsoft.PowerShell.Commands.NewWebserviceProxy.AutogeneratedTypes** plus a type that is generated from the URI.</span></span>

<span data-ttu-id="f7b96-144">您可以設定 **Namespace** 參數的值，讓您可以存取多個同名的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-144">You can set the value of the **Namespace** parameter so that you can access multiple Web services that have the same name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b96-145">-Uri</span><span class="sxs-lookup"><span data-stu-id="f7b96-145">-Uri</span></span>

<span data-ttu-id="f7b96-146">指定 Web 服務的 URI。</span><span class="sxs-lookup"><span data-stu-id="f7b96-146">Specifies the URI of the Web service.</span></span> <span data-ttu-id="f7b96-147">輸入 URI 或包含服務描述之檔案的路徑和檔案名。</span><span class="sxs-lookup"><span data-stu-id="f7b96-147">Enter a URI or the path and filename of a file that contains a service description.</span></span>

<span data-ttu-id="f7b96-148">URI 必須傳回 `.asmx` 頁面或傳回服務描述的頁面。</span><span class="sxs-lookup"><span data-stu-id="f7b96-148">The URI must return an `.asmx` page or to a page that returns a service description.</span></span> <span data-ttu-id="f7b96-149">若要傳回使用 ASP.NET 建立之 Web 服務的服務描述，請附加 "？WSDL」至 Web 服務的 URL (例如 `http://www.contoso.com/MyWebService.asmx?WSDL`) 。</span><span class="sxs-lookup"><span data-stu-id="f7b96-149">To return a service description of a Web service that was created using ASP.NET, append "?WSDL" to the URL of the Web service (for example, `http://www.contoso.com/MyWebService.asmx?WSDL`).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: WL, WSDL, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b96-150">-UseDefaultCredential</span><span class="sxs-lookup"><span data-stu-id="f7b96-150">-UseDefaultCredential</span></span>

<span data-ttu-id="f7b96-151">指出此 Cmdlet 會使用預設認證。</span><span class="sxs-lookup"><span data-stu-id="f7b96-151">Indicates that this cmdlet uses the default credential.</span></span> <span data-ttu-id="f7b96-152">此 Cmdlet 會將產生之 proxy 物件中的 **UseDefaultCredential** 屬性設定為 True。</span><span class="sxs-lookup"><span data-stu-id="f7b96-152">This cmdlet sets the **UseDefaultCredential** property in the resulting proxy object to True.</span></span> <span data-ttu-id="f7b96-153">這可做為使用 **Credential** 參數的替代方案。</span><span class="sxs-lookup"><span data-stu-id="f7b96-153">This is an alternative to using the **Credential** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseDefaultCredential
Aliases: UDC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f7b96-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7b96-154">CommonParameters</span></span>

<span data-ttu-id="f7b96-155">這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。</span><span class="sxs-lookup"><span data-stu-id="f7b96-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7b96-156">如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。</span><span class="sxs-lookup"><span data-stu-id="f7b96-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7b96-157">輸入</span><span class="sxs-lookup"><span data-stu-id="f7b96-157">INPUTS</span></span>

### <span data-ttu-id="f7b96-158">無</span><span class="sxs-lookup"><span data-stu-id="f7b96-158">None</span></span>

<span data-ttu-id="f7b96-159">您無法使用管線傳送輸入至此 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f7b96-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f7b96-160">輸出</span><span class="sxs-lookup"><span data-stu-id="f7b96-160">OUTPUTS</span></span>

### <span data-ttu-id="f7b96-161">Web 服務 Proxy 物件</span><span class="sxs-lookup"><span data-stu-id="f7b96-161">A Web service proxy object</span></span>

<span data-ttu-id="f7b96-162">此 Cmdlet 會傳回 Web 服務 proxy 物件。</span><span class="sxs-lookup"><span data-stu-id="f7b96-162">This cmdlet returns a Web service proxy object.</span></span> <span data-ttu-id="f7b96-163">物件的命名空間和類別取決於命令的參數。</span><span class="sxs-lookup"><span data-stu-id="f7b96-163">The namespace and class of the object are determined by the parameters of the command.</span></span> <span data-ttu-id="f7b96-164">預設值是從輸入 URI 產生的。</span><span class="sxs-lookup"><span data-stu-id="f7b96-164">The default is generated from the input URI.</span></span>

## <span data-ttu-id="f7b96-165">注意</span><span class="sxs-lookup"><span data-stu-id="f7b96-165">NOTES</span></span>

<span data-ttu-id="f7b96-166">`New-WebServiceProxy` 使用 **系統 .net. WebClient** 類別來載入指定的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="f7b96-166">`New-WebServiceProxy` uses the **System.Net.WebClient** class to load the specified Web service.</span></span>

## <span data-ttu-id="f7b96-167">相關連結</span><span class="sxs-lookup"><span data-stu-id="f7b96-167">RELATED LINKS</span></span>

[<span data-ttu-id="f7b96-168">New-Service</span><span class="sxs-lookup"><span data-stu-id="f7b96-168">New-Service</span></span>](New-Service.md)
