---
title: 建立 Windows PowerShell 磁碟機提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 174d3a6860790295e1b73f32d9c1bad46b653917
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055643"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="05213-102">建立 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="05213-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="05213-103">本主題描述如何建立可用來存取資料存放區，透過 Windows PowerShell 磁碟機的 Windows PowerShell 磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="05213-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="05213-104">這種類型的提供者也稱為 Windows PowerShell 磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="05213-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="05213-105">提供者所使用的 Windows PowerShell 磁碟機提供方法來連線到資料存放區。</span><span class="sxs-lookup"><span data-stu-id="05213-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="05213-106">此處所述的 Windows PowerShell 磁碟機提供者會提供 Microsoft Access 資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="05213-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="05213-107">此提供者，Windows PowerShell 磁碟機代表資料庫 （您可將任意數目的磁碟機新增至磁碟機提供者），磁碟機的最上層容器代表在資料庫中，資料表和容器的項目代表的資料列資料表中。</span><span class="sxs-lookup"><span data-stu-id="05213-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="05213-108">以下是本主題中的區段清單。</span><span class="sxs-lookup"><span data-stu-id="05213-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="05213-109">如果您不熟悉如何撰寫 Windows PowerShell 磁碟機提供者，閱讀這些章節中出現的順序。</span><span class="sxs-lookup"><span data-stu-id="05213-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="05213-110">不過，如果您已熟悉撰寫磁碟機提供者，請直接前往您所需要的資訊。</span><span class="sxs-lookup"><span data-stu-id="05213-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="05213-111">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="05213-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="05213-112">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="05213-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="05213-113">建立磁碟機狀態資訊</span><span class="sxs-lookup"><span data-stu-id="05213-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="05213-114">建立磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="05213-115">將動態參數附加至 NewDrive</span><span class="sxs-lookup"><span data-stu-id="05213-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="05213-116">移除磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="05213-117">初始化的預設磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="05213-118">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="05213-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="05213-119">測試 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="05213-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="05213-120">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="05213-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="05213-121">您的磁碟機提供者必須定義衍生自.NET 類別[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。</span><span class="sxs-lookup"><span data-stu-id="05213-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="05213-122">以下是此磁碟機提供者的類別定義：</span><span class="sxs-lookup"><span data-stu-id="05213-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="05213-123">請注意，在此範例中， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性指定的提供者和 Windows PowerShell 的特定功能的使用者易記名稱，提供者命令處理期間，Windows PowerShell 執行階段會公開。</span><span class="sxs-lookup"><span data-stu-id="05213-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="05213-124">所定義的提供者功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="05213-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="05213-125">此磁碟機提供者不支援任何這些功能。</span><span class="sxs-lookup"><span data-stu-id="05213-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="05213-126">定義基底的功能</span><span class="sxs-lookup"><span data-stu-id="05213-126">Defining Base Functionality</span></span>

<span data-ttu-id="05213-127">中所述[設計您 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)，則[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別，定義所需的初始化和未初始化的提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="05213-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="05213-128">若要實作功能，說明如何加入工作階段特定的初始化資訊，以及用於釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="05213-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="05213-129">不過，大部分的提供者 （包括此處所述的提供者） 可以使用這項功能所提供的 Windows PowerShell 的預設實作。</span><span class="sxs-lookup"><span data-stu-id="05213-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="05213-130">建立磁碟機狀態資訊</span><span class="sxs-lookup"><span data-stu-id="05213-130">Creating Drive State Information</span></span>

<span data-ttu-id="05213-131">所有 Windows PowerShell 提供者會被都視為無狀態，這表示您的磁碟機提供者，必須建立呼叫您的提供者時，會將 Windows PowerShell 執行階段所需的任何狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="05213-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="05213-132">此磁碟機提供者、 狀態資訊會包含做為一部分的磁碟機資訊會保留資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="05213-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="05213-133">以下是示範如何將這項資訊儲存在程式碼[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)描述磁碟機的物件：</span><span class="sxs-lookup"><span data-stu-id="05213-133">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="05213-134">建立磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-134">Creating a Drive</span></span>

<span data-ttu-id="05213-135">若要讓 Windows PowerShell 執行階段建立的磁碟機，磁碟機提供者必須實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="05213-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="05213-136">下列程式碼示範實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)此磁碟機提供者的方法：</span><span class="sxs-lookup"><span data-stu-id="05213-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="05213-137">這個方法的覆寫應該執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="05213-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="05213-138">確認[System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)成員存在，而且可以建立連接到資料存放區。</span><span class="sxs-lookup"><span data-stu-id="05213-138">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="05213-139">建立磁碟機，並填入連接成員支援`New-PSDrive`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05213-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="05213-140">驗證[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)建議的磁碟機的物件。</span><span class="sxs-lookup"><span data-stu-id="05213-140">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="05213-141">修改[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件，描述與任何必要的效能或可靠性的詳細資訊，磁碟機，或呼叫端使用的磁碟機提供額外的資料。</span><span class="sxs-lookup"><span data-stu-id="05213-141">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="05213-142">處理使用的失敗[System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法，然後傳回`null`。</span><span class="sxs-lookup"><span data-stu-id="05213-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="05213-143">這個方法傳回的磁碟機資訊傳遞至方法或它的提供者特定版本。</span><span class="sxs-lookup"><span data-stu-id="05213-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="05213-144">將動態參數附加至 NewDrive</span><span class="sxs-lookup"><span data-stu-id="05213-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="05213-145">`New-PSDrive`您磁碟機提供者所支援的 cmdlet 可能會需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="05213-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="05213-146">若要將這些動態參數附加至 cmdlet，提供者會實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="05213-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="05213-147">這個方法會傳回具有屬性和欄位的剖析屬性類似於 cmdlet 類別的物件或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。</span><span class="sxs-lookup"><span data-stu-id="05213-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="05213-148">此磁碟機提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="05213-148">This drive provider does not override this method.</span></span> <span data-ttu-id="05213-149">不過，下列程式碼會顯示這個方法的預設實作：</span><span class="sxs-lookup"><span data-stu-id="05213-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="05213-150">移除磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-150">Removing a Drive</span></span>

<span data-ttu-id="05213-151">若要關閉資料庫連接，磁碟機提供者必須實作[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="05213-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="05213-152">這個方法會關閉磁碟機的連線之後清除任何提供者專屬資訊。</span><span class="sxs-lookup"><span data-stu-id="05213-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="05213-153">下列程式碼示範實作[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)此磁碟機提供者的方法：</span><span class="sxs-lookup"><span data-stu-id="05213-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="05213-154">如果可以移除磁碟機，這個方法應傳回的資訊傳遞給方法，透過`drive`參數。</span><span class="sxs-lookup"><span data-stu-id="05213-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="05213-155">如果無法移除磁碟機，方法應該撰寫例外狀況，並傳回`null`。</span><span class="sxs-lookup"><span data-stu-id="05213-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="05213-156">如果您的提供者不會覆寫這個方法，則這個方法的預設實作只會傳回做為輸入傳遞的磁碟機資訊。</span><span class="sxs-lookup"><span data-stu-id="05213-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="05213-157">初始化的預設磁碟機</span><span class="sxs-lookup"><span data-stu-id="05213-157">Initializing Default Drives</span></span>

<span data-ttu-id="05213-158">您的磁碟機提供者會實作[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法來掛接磁碟機。</span><span class="sxs-lookup"><span data-stu-id="05213-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="05213-159">例如，Active Directory 提供者可能會掛接磁碟機，預設命名內容，如果電腦已加入網域。</span><span class="sxs-lookup"><span data-stu-id="05213-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="05213-160">這個方法會傳回初始化的磁碟機的磁碟機資訊的集合則為空集合。</span><span class="sxs-lookup"><span data-stu-id="05213-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="05213-161">呼叫此方法會在 Windows PowerShell 執行階段會呼叫後[System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者。</span><span class="sxs-lookup"><span data-stu-id="05213-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="05213-162">此磁碟機提供者不會覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。</span><span class="sxs-lookup"><span data-stu-id="05213-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="05213-163">不過，下列程式碼會顯示預設的實作，它會傳回空的磁碟機的集合：</span><span class="sxs-lookup"><span data-stu-id="05213-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="05213-164">有關實作 InitializeDefaultDrives 的注意事項</span><span class="sxs-lookup"><span data-stu-id="05213-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="05213-165">所有的磁碟機提供者應該裝載的根磁碟機，以協助使用者使用可搜尋性。</span><span class="sxs-lookup"><span data-stu-id="05213-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="05213-166">根磁碟機可能會列出，做為其他已掛接的磁碟機的根位置。</span><span class="sxs-lookup"><span data-stu-id="05213-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="05213-167">例如，Active Directory 提供者可能會建立列出命名內容中找到的磁碟機`namingContext`根目錄分散式系統環境 (DSE) 上的屬性。</span><span class="sxs-lookup"><span data-stu-id="05213-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="05213-168">這可協助使用者探索的其他磁碟機的掛接點。</span><span class="sxs-lookup"><span data-stu-id="05213-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="05213-169">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="05213-169">Code Sample</span></span>

<span data-ttu-id="05213-170">完整的範例程式碼，請參閱[AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="05213-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="05213-171">測試 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="05213-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="05213-172">當您的 Windows PowerShell 提供者已向 Windows PowerShell 時，您可以在命令列，包括任何衍生所提供的指令程式上執行支援的 cmdlet 來進行測試。</span><span class="sxs-lookup"><span data-stu-id="05213-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="05213-173">我們來測試範例磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="05213-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="05213-174">執行`Get-PSProvider`cmdlet 來擷取確保 AccessDB 磁碟機提供者的提供者清單：</span><span class="sxs-lookup"><span data-stu-id="05213-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="05213-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="05213-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="05213-176">會出現下列輸出：</span><span class="sxs-lookup"><span data-stu-id="05213-176">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="05213-177">請確認資料庫伺服器名稱 (DSN) 資料庫中存在的存取**資料來源**一部分**系統管理工具**作業系統。</span><span class="sxs-lookup"><span data-stu-id="05213-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="05213-178">在 **使用者 DSN**資料表中，按兩下**MS Access 資料庫**，然後將磁碟機路徑 C:\ps\northwind.mdb。</span><span class="sxs-lookup"><span data-stu-id="05213-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="05213-179">建立新的磁碟機，使用範例磁碟機提供者：</span><span class="sxs-lookup"><span data-stu-id="05213-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="05213-180">**PS > 新 psdrive-名稱 mydb-根 c:\ps\northwind.mdb psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="05213-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="05213-181">會出現下列輸出：</span><span class="sxs-lookup"><span data-stu-id="05213-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="05213-182">驗證連線。</span><span class="sxs-lookup"><span data-stu-id="05213-182">Validate the connection.</span></span> <span data-ttu-id="05213-183">因為連接定義為磁碟機的成員，您可以檢查使用 Get PDDrive cmdlet。</span><span class="sxs-lookup"><span data-stu-id="05213-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="05213-184">因為提供者為該互動需要容器的功能，使用者無法還會與做為磁碟機中，提供者互動。</span><span class="sxs-lookup"><span data-stu-id="05213-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="05213-185">如需詳細資訊，請參閱 <<c0> [ 建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="05213-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="05213-186">**PS > (get psdrive mydb).connection**</span><span class="sxs-lookup"><span data-stu-id="05213-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="05213-187">會出現下列輸出：</span><span class="sxs-lookup"><span data-stu-id="05213-187">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="05213-188">移除磁碟機，並結束 shell:</span><span class="sxs-lookup"><span data-stu-id="05213-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="05213-189">**PS > 移除 psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="05213-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="05213-190">**PS > 結束**</span><span class="sxs-lookup"><span data-stu-id="05213-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="05213-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05213-191">See Also</span></span>

[<span data-ttu-id="05213-192">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="05213-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="05213-193">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="05213-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="05213-194">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="05213-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)