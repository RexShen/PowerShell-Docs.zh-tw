---
title: 建立 Windows PowerShell 磁片磁碟機提供者 |Microsoft Docs
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
ms.openlocfilehash: 88be7cc6cc0ab54604bc9de71e0ae07c20457514
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978452"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="6e292-102">建立 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="6e292-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="6e292-103">本主題說明如何建立 Windows PowerShell 磁片磁碟機提供者，以提供透過 Windows PowerShell 磁片磁碟機存取資料存放區的方式。</span><span class="sxs-lookup"><span data-stu-id="6e292-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="6e292-104">這種類型的提供者也稱為 Windows PowerShell 磁片磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="6e292-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="6e292-105">提供者所使用的 Windows PowerShell 磁片磁碟機提供連接到資料存放區的方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="6e292-106">這裡所述的 Windows PowerShell 磁片磁碟機提供者可讓您存取 Microsoft Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="6e292-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span>
<span data-ttu-id="6e292-107">對於此提供者，Windows PowerShell 磁片磁碟機代表資料庫（可以將任意數目的磁片磁碟機新增至磁片磁碟機提供者）、磁片磁碟機的最上層容器代表資料庫中的資料表，而容器的專案則代表資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="6e292-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="6e292-108">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="6e292-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="6e292-109">您的磁片磁碟機提供者必須定義一個衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基類的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="6e292-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="6e292-110">以下是此磁片磁碟機提供者的類別定義：</span><span class="sxs-lookup"><span data-stu-id="6e292-110">Here is the class definition for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

<span data-ttu-id="6e292-111">請注意，在此範例中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性會指定提供者的使用者易記名稱，以及提供者在命令處理期間公開給 windows powershell 執行時間的 windows powershell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="6e292-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span>
<span data-ttu-id="6e292-112">提供者功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉所定義。</span><span class="sxs-lookup"><span data-stu-id="6e292-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="6e292-113">此磁片磁碟機提供者不支援任何這些功能。</span><span class="sxs-lookup"><span data-stu-id="6e292-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="6e292-114">定義基本功能</span><span class="sxs-lookup"><span data-stu-id="6e292-114">Defining Base Functionality</span></span>

<span data-ttu-id="6e292-115">如[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)中所述， [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類，此類別定義了初始化和取消初始化提供者所需的方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="6e292-116">若要執行功能來新增會話特定的初始化資訊，以及釋放提供者所使用的資源，請參閱[建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6e292-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="6e292-117">不過，大部分的提供者（包括這裡所述的提供者）都可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="6e292-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="6e292-118">建立磁片磁碟機狀態資訊</span><span class="sxs-lookup"><span data-stu-id="6e292-118">Creating Drive State Information</span></span>

<span data-ttu-id="6e292-119">所有 Windows PowerShell 提供者都會被視為無狀態，這表示您的磁片磁碟機提供者需要在呼叫提供者時，建立 Windows PowerShell 執行時間所需的任何狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="6e292-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="6e292-120">對於此磁片磁碟機提供者，狀態資訊會包含與資料庫的連接，並保留為磁片磁碟機資訊的一部分。</span><span class="sxs-lookup"><span data-stu-id="6e292-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="6e292-121">以下程式碼顯示如何將這項資訊儲存在描述磁片磁碟機的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件中：</span><span class="sxs-lookup"><span data-stu-id="6e292-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a><span data-ttu-id="6e292-122">建立磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="6e292-122">Creating a Drive</span></span>

<span data-ttu-id="6e292-123">若要允許 Windows PowerShell 執行時間建立磁片磁碟機，磁片磁碟機提供者必須執行[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="6e292-124">下列程式碼顯示此磁片磁碟機提供者的[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法的執行：</span><span class="sxs-lookup"><span data-stu-id="6e292-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

<span data-ttu-id="6e292-125">您的此方法的覆寫應執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="6e292-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="6e292-126">確認[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo.Root)的成員存在，而且可以建立與資料存放區之間的連接。」</span><span class="sxs-lookup"><span data-stu-id="6e292-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>
- <span data-ttu-id="6e292-127">建立磁片磁碟機並填入連接成員，以支援 `New-PSDrive` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e292-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>
- <span data-ttu-id="6e292-128">驗證所提議磁片磁碟機的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件。</span><span class="sxs-lookup"><span data-stu-id="6e292-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>
- <span data-ttu-id="6e292-129">修改[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件，以描述具有任何必要效能或可靠性資訊的磁片磁碟機，或為使用磁片磁碟機的呼叫端提供額外的資料。</span><span class="sxs-lookup"><span data-stu-id="6e292-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>
- <span data-ttu-id="6e292-130">使用[Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError)方法來處理失敗，然後傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="6e292-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="6e292-131">這個方法會傳回傳遞給方法的磁片磁碟機資訊，或它的提供者特定版本。</span><span class="sxs-lookup"><span data-stu-id="6e292-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="6e292-132">將動態參數附加至 NewDrive</span><span class="sxs-lookup"><span data-stu-id="6e292-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="6e292-133">您的磁片磁碟機提供者所支援的 `New-PSDrive` Cmdlet 可能需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="6e292-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="6e292-134">若要將這些動態參數附加至 Cmdlet，提供者會執行[DriveCmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="6e292-135">這個方法會傳回物件，其中具有屬性和欄位，而且其具有類似于 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。</span><span class="sxs-lookup"><span data-stu-id="6e292-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="6e292-136">此磁片磁碟機提供者不會覆寫此方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-136">This drive provider does not override this method.</span></span> <span data-ttu-id="6e292-137">不過，下列程式碼會顯示此方法的預設執行：</span><span class="sxs-lookup"><span data-stu-id="6e292-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="6e292-138">移除磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="6e292-138">Removing a Drive</span></span>

<span data-ttu-id="6e292-139">若要關閉資料庫連接，磁片磁碟機提供者必須執行[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="6e292-140">這個方法會在清除任何提供者特定的資訊之後，關閉與磁片磁碟機的連接。</span><span class="sxs-lookup"><span data-stu-id="6e292-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="6e292-141">下列程式碼顯示此磁片磁碟機提供者的[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法的執行：</span><span class="sxs-lookup"><span data-stu-id="6e292-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

<span data-ttu-id="6e292-142">如果可以移除磁片磁碟機，方法應該會透過 `drive` 參數傳回傳遞給方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="6e292-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="6e292-143">如果無法移除磁片磁碟機，方法應該撰寫例外狀況，然後傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="6e292-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="6e292-144">如果您的提供者不會覆寫這個方法，這個方法的預設執行只會傳回傳遞做為輸入的磁片磁碟機資訊。</span><span class="sxs-lookup"><span data-stu-id="6e292-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="6e292-145">初始化預設磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="6e292-145">Initializing Default Drives</span></span>

<span data-ttu-id="6e292-146">您的磁片磁碟機提供者會執行[DriveCmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法來掛接磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="6e292-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="6e292-147">例如，如果電腦已加入網域，Active Directory 提供者可能會掛接預設命名內容的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="6e292-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="6e292-148">這個方法會傳回有關已初始化磁片磁碟機或空集合的磁片磁碟機資訊集合。</span><span class="sxs-lookup"><span data-stu-id="6e292-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="6e292-149">此方法的呼叫是在 Windows PowerShell 運行[時間呼叫 Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者之後進行。</span><span class="sxs-lookup"><span data-stu-id="6e292-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="6e292-150">此磁片磁碟機提供者不會覆寫[DriveCmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法。</span><span class="sxs-lookup"><span data-stu-id="6e292-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="6e292-151">不過，下列程式碼會顯示預設的實值，其會傳回空的磁片磁碟機集合：</span><span class="sxs-lookup"><span data-stu-id="6e292-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="6e292-152">執行 InitializeDefaultDrives 的相關事項</span><span class="sxs-lookup"><span data-stu-id="6e292-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="6e292-153">所有磁片磁碟機提供者都應該掛接根磁片磁碟機，以協助使用者進行發現。</span><span class="sxs-lookup"><span data-stu-id="6e292-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="6e292-154">根磁片磁碟機可能會列出作為其他已掛接磁片磁碟機之根目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="6e292-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="6e292-155">例如，Active Directory 提供者可能會建立一個磁片磁碟機，其中列出在根分散式系統內容（DSE）的 `namingContext` 屬性中找到的命名內容。</span><span class="sxs-lookup"><span data-stu-id="6e292-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="6e292-156">這可協助使用者探索其他磁片磁碟機的掛接點。</span><span class="sxs-lookup"><span data-stu-id="6e292-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6e292-157">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="6e292-157">Code Sample</span></span>

<span data-ttu-id="6e292-158">如需完整的範例程式碼，請參閱[AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="6e292-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="6e292-159">測試 Windows PowerShell 磁片磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="6e292-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="6e292-160">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的任何 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="6e292-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="6e292-161">讓我們來測試範例磁片磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="6e292-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="6e292-162">執行 `Get-PSProvider` Cmdlet 來抓取提供者清單，以確保 AccessDB 磁片磁碟機提供者存在：</span><span class="sxs-lookup"><span data-stu-id="6e292-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="6e292-163">**PS > `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="6e292-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="6e292-164">下列輸出隨即出現：</span><span class="sxs-lookup"><span data-stu-id="6e292-164">The following output appears:</span></span>

   ```Output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="6e292-165">藉由存取作業系統的系統**管理工具**的 [**資料來源**] 部分，確保資料庫有資料庫伺服器名稱（DSN）。</span><span class="sxs-lookup"><span data-stu-id="6e292-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="6e292-166">在 [**使用者 DSN** ] 資料表中，按兩下 [ **MS Access 資料庫**] 並新增磁片磁碟機路徑 `C:\ps\northwind.mdb`。</span><span class="sxs-lookup"><span data-stu-id="6e292-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path `C:\ps\northwind.mdb`.</span></span>

3. <span data-ttu-id="6e292-167">使用範例磁片磁碟機提供者建立新的磁片磁碟機：</span><span class="sxs-lookup"><span data-stu-id="6e292-167">Create a new drive using the sample drive provider:</span></span>

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   <span data-ttu-id="6e292-168">下列輸出隨即出現：</span><span class="sxs-lookup"><span data-stu-id="6e292-168">The following output appears:</span></span>

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="6e292-169">驗證連接。</span><span class="sxs-lookup"><span data-stu-id="6e292-169">Validate the connection.</span></span> <span data-ttu-id="6e292-170">因為連接是定義為磁片磁碟機的成員，所以您可以使用 PDDrive Cmdlet 來進行檢查。</span><span class="sxs-lookup"><span data-stu-id="6e292-170">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6e292-171">使用者還無法以磁片磁碟機的形式與提供者互動，因為提供者需要該互動的容器功能。</span><span class="sxs-lookup"><span data-stu-id="6e292-171">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="6e292-172">如需詳細資訊，請參閱[建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="6e292-172">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="6e292-173">**PS > （psdrive mydb）。連接**</span><span class="sxs-lookup"><span data-stu-id="6e292-173">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="6e292-174">下列輸出隨即出現：</span><span class="sxs-lookup"><span data-stu-id="6e292-174">The following output appears:</span></span>

   ```Output
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

5. <span data-ttu-id="6e292-175">移除磁片磁碟機並結束命令介面：</span><span class="sxs-lookup"><span data-stu-id="6e292-175">Remove the drive and exit the shell:</span></span>

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a><span data-ttu-id="6e292-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e292-176">See Also</span></span>

[<span data-ttu-id="6e292-177">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6e292-177">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="6e292-178">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6e292-178">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="6e292-179">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="6e292-179">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
