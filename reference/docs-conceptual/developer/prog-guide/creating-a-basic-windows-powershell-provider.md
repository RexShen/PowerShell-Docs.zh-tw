---
title: 建立基本的 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360517"
---
# <a name="creating-a-basic-windows-powershell-provider"></a><span data-ttu-id="72ff9-102">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-102">Creating a Basic Windows PowerShell Provider</span></span>

<span data-ttu-id="72ff9-103">本主題是學習如何建立 Windows PowerShell 提供者的起點。</span><span class="sxs-lookup"><span data-stu-id="72ff9-103">This topic is the starting point for learning how to create a Windows PowerShell provider.</span></span> <span data-ttu-id="72ff9-104">這裡所述的基本提供者提供啟動和停止提供者的方法，雖然此提供者並未提供存取資料存放區或取得或設定資料存放區中之資料的方式，但它確實提供了所需的基本功能所有提供者。</span><span class="sxs-lookup"><span data-stu-id="72ff9-104">The basic provider described here provides methods for starting and stopping the provider, and although this provider does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

<span data-ttu-id="72ff9-105">如先前所述，這裡所描述的基本提供者會執行啟動和停止提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-105">As mentioned previously, the basic provider described here implements methods for starting and stopping the provider.</span></span> <span data-ttu-id="72ff9-106">Windows PowerShell 執行時間會呼叫這些方法，以初始化並解除初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="72ff9-106">The Windows PowerShell runtime calls these methods to initialize and uninitialize the provider.</span></span>

> [!NOTE]
> <span data-ttu-id="72ff9-107">您可以在 Windows PowerShell 所提供的 AccessDBSampleProvider01.cs 檔案中找到此提供者的範例。</span><span class="sxs-lookup"><span data-stu-id="72ff9-107">You can find a sample of this provider in the AccessDBSampleProvider01.cs file provided by Windows PowerShell.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="72ff9-108">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="72ff9-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="72ff9-109">建立 Windows PowerShell 提供者的第一個步驟是定義它的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="72ff9-109">The first step in creating a Windows PowerShell provider is to define its .NET class.</span></span> <span data-ttu-id="72ff9-110">這個基本提供者會定義一個名為 `AccessDBProvider` 的類別，衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類。</span><span class="sxs-lookup"><span data-stu-id="72ff9-110">This basic provider defines a class called `AccessDBProvider` that derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class.</span></span>

<span data-ttu-id="72ff9-111">建議您將提供者類別放在 API 命名空間的 `Providers` 命名空間中，例如 xxx。PowerShell. 提供者。</span><span class="sxs-lookup"><span data-stu-id="72ff9-111">It is recommended that you place your provider classes in a `Providers` namespace of your API namespace, for example, xxx.PowerShell.Providers.</span></span> <span data-ttu-id="72ff9-112">此提供者會使用 `Microsoft.Samples.PowerShell.Provider` 命名空間，其中所有的 Windows PowerShell 提供者範例都會在其中執行。</span><span class="sxs-lookup"><span data-stu-id="72ff9-112">This provider uses the `Microsoft.Samples.PowerShell.Provider` namespace, in which all Windows PowerShell provider samples run.</span></span>

> [!NOTE]
> <span data-ttu-id="72ff9-113">Windows PowerShell 提供者的類別必須明確標示為公用。</span><span class="sxs-lookup"><span data-stu-id="72ff9-113">The class for a Windows PowerShell provider must be explicitly marked as public.</span></span> <span data-ttu-id="72ff9-114">未標示為公用的類別會預設為內部，且不會由 Windows PowerShell 執行時間找到。</span><span class="sxs-lookup"><span data-stu-id="72ff9-114">Classes not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="72ff9-115">以下是此基本提供者的類別定義：</span><span class="sxs-lookup"><span data-stu-id="72ff9-115">Here is the class definition for this basic provider:</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

<span data-ttu-id="72ff9-116">在類別定義之前，您必須使用語法 [CmdletProvider （）] 來宣告[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性（attribute）。</span><span class="sxs-lookup"><span data-stu-id="72ff9-116">Right before the class definition, you must declare the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute, with the syntax [CmdletProvider()].</span></span>

<span data-ttu-id="72ff9-117">您可以設定屬性關鍵字，以便在必要時進一步宣告類別。</span><span class="sxs-lookup"><span data-stu-id="72ff9-117">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="72ff9-118">請注意，此處所宣告的[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="72ff9-118">Notice that the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute declared here includes two parameters.</span></span> <span data-ttu-id="72ff9-119">第一個屬性參數會指定提供者的預設易記名稱，供使用者稍後修改。</span><span class="sxs-lookup"><span data-stu-id="72ff9-119">The first attribute parameter specifies the default-friendly name for the provider, which the user can modify later.</span></span> <span data-ttu-id="72ff9-120">第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 定義功能。</span><span class="sxs-lookup"><span data-stu-id="72ff9-120">The second parameter specifies the Windows PowerShell-defined capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="72ff9-121">提供者功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉所定義。</span><span class="sxs-lookup"><span data-stu-id="72ff9-121">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="72ff9-122">因為這是基底提供者，所以不支援任何功能。</span><span class="sxs-lookup"><span data-stu-id="72ff9-122">Because this is a base provider, it supports no capabilities.</span></span>

> [!NOTE]
> <span data-ttu-id="72ff9-123">Windows PowerShell 提供者的完整名稱包括在註冊提供者時，由 Windows PowerShell 決定的元件名稱和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="72ff9-123">The fully qualified name of the Windows PowerShell provider includes the assembly name and other attributes determined by Windows PowerShell upon registration of the provider.</span></span>

## <a name="defining-provider-specific-state-information"></a><span data-ttu-id="72ff9-124">定義提供者特定的狀態資訊</span><span class="sxs-lookup"><span data-stu-id="72ff9-124">Defining Provider-Specific State Information</span></span>

<span data-ttu-id="72ff9-125">[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類和所有衍生類別都會被視為無狀態，因為 Windows PowerShell 執行時間只會在必要時建立提供者實例。</span><span class="sxs-lookup"><span data-stu-id="72ff9-125">The [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class and all derived classes are considered stateless because the Windows PowerShell runtime creates provider instances only as required.</span></span> <span data-ttu-id="72ff9-126">因此，如果您的提供者需要提供者特定資料的完整控制和狀態維護，它必須從[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)類別衍生類別。</span><span class="sxs-lookup"><span data-stu-id="72ff9-126">Therefore, if your provider requires full control and state maintenance for provider-specific data, it must derive a class from the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) class.</span></span> <span data-ttu-id="72ff9-127">您的衍生類別應該定義維護狀態所需的成員，如此一來，當 Windows PowerShell 執行時間呼叫[Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者時，即可存取提供者特定的資料。</span><span class="sxs-lookup"><span data-stu-id="72ff9-127">Your derived class should define the members necessary to maintain the state so that the provider-specific data can be accessed when the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="72ff9-128">Windows PowerShell 提供者也可以維護以連接為基礎的狀態。</span><span class="sxs-lookup"><span data-stu-id="72ff9-128">A Windows PowerShell provider can also maintain connection-based state.</span></span> <span data-ttu-id="72ff9-129">如需維護線上狀態的詳細資訊，請參閱[建立 PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="72ff9-129">For more information about maintaining connection state, see [Creating a PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>

## <a name="initializing-the-provider"></a><span data-ttu-id="72ff9-130">初始化提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-130">Initializing the Provider</span></span>

<span data-ttu-id="72ff9-131">若要初始化提供者，當 Windows PowerShell 啟動時，Windows PowerShell 執行時間會呼叫[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-131">To initialize the provider, the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method when Windows PowerShell is started.</span></span> <span data-ttu-id="72ff9-132">在大部分的情況下，您的提供者可以使用這個方法的預設實值，這只會傳回描述提供者的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件。</span><span class="sxs-lookup"><span data-stu-id="72ff9-132">For the most part, your provider can use the default implementation of this method, which simply returns the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that describes your provider.</span></span> <span data-ttu-id="72ff9-133">不過，如果您想要加入額外的初始化資訊，則應該執行自己的[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回已修改的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件版本，並將其傳遞給您的提供者。</span><span class="sxs-lookup"><span data-stu-id="72ff9-133">However, in the case where you want to add additional initialization information, you should implement your own [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method that returns a modified version of the [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that is passed to your provider.</span></span> <span data-ttu-id="72ff9-134">一般來說，這個方法應該會傳回傳遞給它的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，或已修改的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，其中包含其他的初始化資訊。</span><span class="sxs-lookup"><span data-stu-id="72ff9-134">In general, this method should return the provided [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object passed to it or a modified [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) object that contains other initialization information.</span></span>

<span data-ttu-id="72ff9-135">這個基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-135">This basic provider does not override this method.</span></span> <span data-ttu-id="72ff9-136">不過，下列程式碼會顯示此方法的預設執行：</span><span class="sxs-lookup"><span data-stu-id="72ff9-136">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

<span data-ttu-id="72ff9-137">提供者可以維護提供者特定資訊的狀態，如[定義提供者特定的資料狀態](#defining-provider-specific-state-information)中所述。</span><span class="sxs-lookup"><span data-stu-id="72ff9-137">The provider can maintain the state of provider-specific information as described in [Defining Provider-specific Data State](#defining-provider-specific-state-information).</span></span> <span data-ttu-id="72ff9-138">在此情況下，您的執行必須覆寫[Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回衍生類別的實例。</span><span class="sxs-lookup"><span data-stu-id="72ff9-138">In this case, your implementation must override the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to return an instance of the derived class.</span></span>

## <a name="start-dynamic-parameters"></a><span data-ttu-id="72ff9-139">啟動動態參數</span><span class="sxs-lookup"><span data-stu-id="72ff9-139">Start Dynamic Parameters</span></span>

<span data-ttu-id="72ff9-140">您的提供者[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)可能需要額外的參數，才能執行。</span><span class="sxs-lookup"><span data-stu-id="72ff9-140">Your provider implementation of the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method might require additional parameters.</span></span> <span data-ttu-id="72ff9-141">在這種情況下，提供者應該覆寫[Cmdletprovider. Startdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法，並傳回具有屬性和欄位的物件，其具有類似 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="72ff9-141">In this case, the provider should override the [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) method and return an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="72ff9-142">這個基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-142">This basic provider does not override this method.</span></span> <span data-ttu-id="72ff9-143">不過，下列程式碼會顯示此方法的預設執行：</span><span class="sxs-lookup"><span data-stu-id="72ff9-143">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a><span data-ttu-id="72ff9-144">取消初始化提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-144">Uninitializing the Provider</span></span>

<span data-ttu-id="72ff9-145">為了釋放 Windows PowerShell 提供者所使用的資源，您的提供者應該執行自己的[Cmdletprovider \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-145">To free resources that the Windows PowerShell provider uses, your provider should implement its own [System.Management.Automation.Provider.Cmdletprovider.Stop\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) method.</span></span> <span data-ttu-id="72ff9-146">這個方法是由 Windows PowerShell 執行時間呼叫，以便在會話結束時將提供者解除初始化。</span><span class="sxs-lookup"><span data-stu-id="72ff9-146">This method is called by the Windows PowerShell runtime to uninitialize the provider at the close of a session.</span></span>

<span data-ttu-id="72ff9-147">這個基本提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="72ff9-147">This basic provider does not override this method.</span></span> <span data-ttu-id="72ff9-148">不過，下列程式碼會顯示此方法的預設執行：</span><span class="sxs-lookup"><span data-stu-id="72ff9-148">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a><span data-ttu-id="72ff9-149">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="72ff9-149">Code Sample</span></span>

<span data-ttu-id="72ff9-150">如需完整的範例程式碼，請參閱[AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="72ff9-150">For complete sample code, see [AccessDbProviderSample01 Code Sample](./accessdbprovidersample01-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-provider"></a><span data-ttu-id="72ff9-151">測試 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-151">Testing the Windows PowerShell Provider</span></span>

<span data-ttu-id="72ff9-152">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊之後，您可以在命令列上執行支援的 Cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="72ff9-152">Once your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line.</span></span> <span data-ttu-id="72ff9-153">針對此基本提供者，請執行新的 shell，並使用 `Get-PSProvider` Cmdlet 來抓取提供者清單，並確認 AccessDb 提供者存在。</span><span class="sxs-lookup"><span data-stu-id="72ff9-153">For this basic provider, run the new shell and use the `Get-PSProvider` cmdlet to retrieve the list of providers and ensure that the AccessDb provider is present.</span></span>

```powershell
Get-PSProvider
```

<span data-ttu-id="72ff9-154">會出現下列輸出：</span><span class="sxs-lookup"><span data-stu-id="72ff9-154">The following output appears:</span></span>

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a><span data-ttu-id="72ff9-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72ff9-155">See Also</span></span>

[<span data-ttu-id="72ff9-156">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-156">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="72ff9-157">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="72ff9-157">Designing Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)
