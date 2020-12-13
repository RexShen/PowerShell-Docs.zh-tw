---
ms.date: 09/13/2016
ms.topic: reference
title: 建立 Windows PowerShell 磁碟機提供者
description: 建立 Windows PowerShell 磁碟機提供者
ms.openlocfilehash: 639518fce27d941b7529b091364c5905c91a5c0c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663041"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="43a18-103">建立 Windows PowerShell 磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="43a18-103">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="43a18-104">本主題說明如何建立 Windows PowerShell 磁片磁碟機提供者，以提供透過 Windows PowerShell 磁片磁碟機存取資料存放區的方式。</span><span class="sxs-lookup"><span data-stu-id="43a18-104">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="43a18-105">這種類型的提供者也稱為 Windows PowerShell 磁片磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="43a18-105">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="43a18-106">提供者使用的 Windows PowerShell 磁片磁碟機提供連接到資料存放區的方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-106">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="43a18-107">此處所述的 Windows PowerShell 磁片磁碟機提供者提供 Microsoft Access 資料庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="43a18-107">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span>
<span data-ttu-id="43a18-108">對於此提供者，Windows PowerShell 磁片磁碟機代表資料庫 (可以將任意數目的磁片磁碟機新增至磁片磁碟機提供者) 、磁片磁碟機的最上層容器代表資料庫中的資料表，而容器的專案則代表資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="43a18-108">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="43a18-109">定義 Windows PowerShell 提供者類別</span><span class="sxs-lookup"><span data-stu-id="43a18-109">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="43a18-110">您的磁片磁碟機提供者必須定義衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 基類的 .net 類別。</span><span class="sxs-lookup"><span data-stu-id="43a18-110">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="43a18-111">以下是此磁片磁碟機提供者的類別定義：</span><span class="sxs-lookup"><span data-stu-id="43a18-111">Here is the class definition for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

<span data-ttu-id="43a18-112">請注意，在此範例中， [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 屬性會指定提供者的使用者易記名稱，以及提供者在命令處理期間公開給 Windows PowerShell 執行時間的 Windows PowerShell 特定功能。</span><span class="sxs-lookup"><span data-stu-id="43a18-112">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span>
<span data-ttu-id="43a18-113">提供者功能的可能值是由 [Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 列舉所定義。</span><span class="sxs-lookup"><span data-stu-id="43a18-113">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="43a18-114">此磁片磁碟機提供者不支援任何這些功能。</span><span class="sxs-lookup"><span data-stu-id="43a18-114">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="43a18-115">定義基底功能</span><span class="sxs-lookup"><span data-stu-id="43a18-115">Defining Base Functionality</span></span>

<span data-ttu-id="43a18-116">如 [設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)所述， [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 基類，該基類會定義初始化和取消初始化提供者所需的方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-116">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="43a18-117">若要執行新增會話特定初始化資訊，以及釋出提供者所使用之資源的功能，請參閱 [建立基本的 Windows PowerShell 提供者](./creating-a-basic-windows-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="43a18-117">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="43a18-118">不過，大部分的提供者 (包括此處所述的提供者) 可以使用 Windows PowerShell 所提供的這項功能的預設執行。</span><span class="sxs-lookup"><span data-stu-id="43a18-118">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="43a18-119">正在建立磁片磁碟機狀態資訊</span><span class="sxs-lookup"><span data-stu-id="43a18-119">Creating Drive State Information</span></span>

<span data-ttu-id="43a18-120">所有 Windows PowerShell 提供者均視為無狀態，這表示您的磁片磁碟機提供者必須在呼叫您的提供者時，建立 Windows PowerShell 執行時間所需的任何狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="43a18-120">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="43a18-121">在此磁片磁碟機提供者中，狀態資訊會包含保留為磁片磁碟機資訊一部分的資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="43a18-121">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="43a18-122">以下程式碼顯示如何將這項資訊儲存在描述磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件中：</span><span class="sxs-lookup"><span data-stu-id="43a18-122">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a><span data-ttu-id="43a18-123">建立磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="43a18-123">Creating a Drive</span></span>

<span data-ttu-id="43a18-124">若要允許 Windows PowerShell 執行時間建立磁片磁碟機，磁片磁碟機提供者必須執行 [DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-124">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="43a18-125">下列程式碼顯示此磁片磁碟機提供者的 [DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法的執行方式：</span><span class="sxs-lookup"><span data-stu-id="43a18-125">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

<span data-ttu-id="43a18-126">您對此方法的覆寫應該執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="43a18-126">Your override of this method should do the following:</span></span>

- <span data-ttu-id="43a18-127">確認 [System.Management.Automation.PSDriveinfo。根 \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) 成員存在，而且可以建立與資料存放區的連接。</span><span class="sxs-lookup"><span data-stu-id="43a18-127">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>
- <span data-ttu-id="43a18-128">建立磁片磁碟機，並填入連接成員，以支援 `New-PSDrive` Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43a18-128">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>
- <span data-ttu-id="43a18-129">驗證所建議磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件。</span><span class="sxs-lookup"><span data-stu-id="43a18-129">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>
- <span data-ttu-id="43a18-130">使用任何必要的效能或可靠性資訊修改描述磁片磁碟機的 [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) 物件，或為使用該磁片磁碟機的呼叫端提供額外的資料。</span><span class="sxs-lookup"><span data-stu-id="43a18-130">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>
- <span data-ttu-id="43a18-131">使用 [Cmdletprovider WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) 方法來處理失敗，然後再傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="43a18-131">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="43a18-132">這個方法會傳回傳遞給方法的磁片磁碟機資訊或它的提供者特定版本。</span><span class="sxs-lookup"><span data-stu-id="43a18-132">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="43a18-133">將動態參數附加至 >newdrive</span><span class="sxs-lookup"><span data-stu-id="43a18-133">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="43a18-134">`New-PSDrive`您的磁片磁碟機提供者所支援的 Cmdlet 可能需要額外的參數。</span><span class="sxs-lookup"><span data-stu-id="43a18-134">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="43a18-135">為了將這些動態參數附加至 Cmdlet，提供者會實 [DriveCmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) 方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-135">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="43a18-136">這個方法會傳回物件，該物件具有剖析屬性（attribute）與 Cmdlet 類別或 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 物件類似的屬性和欄位。</span><span class="sxs-lookup"><span data-stu-id="43a18-136">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="43a18-137">此磁片磁碟機提供者不會覆寫這個方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-137">This drive provider does not override this method.</span></span> <span data-ttu-id="43a18-138">但是，下列程式碼會顯示此方法的預設執行：</span><span class="sxs-lookup"><span data-stu-id="43a18-138">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="43a18-139">移除磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="43a18-139">Removing a Drive</span></span>

<span data-ttu-id="43a18-140">若要關閉資料庫連接，磁片磁碟機提供者必須執行 [DriveCmdletprovider. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-140">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="43a18-141">清除任何提供者特定的資訊之後，這個方法會關閉磁片磁碟機的連接。</span><span class="sxs-lookup"><span data-stu-id="43a18-141">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="43a18-142">下列程式碼顯示此磁片磁碟機提供者的 [DriveCmdletprovider. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法的執行方式：</span><span class="sxs-lookup"><span data-stu-id="43a18-142">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

<span data-ttu-id="43a18-143">如果可以移除磁片磁碟機，方法應該會透過參數傳回傳遞給方法的資訊 `drive` 。</span><span class="sxs-lookup"><span data-stu-id="43a18-143">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="43a18-144">如果無法移除磁片磁碟機，方法應寫入例外狀況，然後傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="43a18-144">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="43a18-145">如果您的提供者不會覆寫這個方法，這個方法的預設執行只會傳回傳遞做為輸入的磁片磁碟機資訊。</span><span class="sxs-lookup"><span data-stu-id="43a18-145">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="43a18-146">正在初始化預設磁片磁碟機</span><span class="sxs-lookup"><span data-stu-id="43a18-146">Initializing Default Drives</span></span>

<span data-ttu-id="43a18-147">您的磁片磁碟機提供者會執行 [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 方法來掛接磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="43a18-147">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="43a18-148">例如，如果電腦已加入網域，Active Directory 提供者可能會掛接預設命名內容的磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="43a18-148">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="43a18-149">這個方法會傳回有關已初始化磁片磁碟機的磁片磁碟機資訊集合，或空集合。</span><span class="sxs-lookup"><span data-stu-id="43a18-149">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="43a18-150">在 Windows PowerShell 執行時間呼叫 [Cmdletprovider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) 方法來初始化提供者之後，就會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-150">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="43a18-151">此磁片磁碟機提供者不會覆寫 [System.Management.Automation.Provider.Drivecmdletprovider.Ini的 tializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) 方法。</span><span class="sxs-lookup"><span data-stu-id="43a18-151">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="43a18-152">但是，下列程式碼會顯示預設的實作為，它會傳回空的磁片磁碟機集合：</span><span class="sxs-lookup"><span data-stu-id="43a18-152">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="43a18-153">執行 InitializeDefaultDrives 的注意事項</span><span class="sxs-lookup"><span data-stu-id="43a18-153">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="43a18-154">所有磁片磁碟機提供者都應該掛接根磁片磁碟機，以協助使用者進行可探索性。</span><span class="sxs-lookup"><span data-stu-id="43a18-154">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="43a18-155">根磁片磁碟機可能會列出作為其他載入的磁片磁碟機根目錄的位置。</span><span class="sxs-lookup"><span data-stu-id="43a18-155">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="43a18-156">例如，Active Directory 提供者可能會建立一個磁片磁碟機，以列出在根分散式系統內容的屬性中找到的命名內容 `namingContext` (DSE) 。</span><span class="sxs-lookup"><span data-stu-id="43a18-156">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="43a18-157">這可協助使用者探索其他磁片磁碟機的掛接點。</span><span class="sxs-lookup"><span data-stu-id="43a18-157">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="43a18-158">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="43a18-158">Code Sample</span></span>

<span data-ttu-id="43a18-159">如需完整的範例程式碼，請參閱 [AccessDbProviderSample02 程式碼範例](./accessdbprovidersample02-code-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="43a18-159">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="43a18-160">測試 Windows PowerShell 磁片磁碟機提供者</span><span class="sxs-lookup"><span data-stu-id="43a18-160">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="43a18-161">當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊時，您可以在命令列上執行支援的 Cmdlet 來進行測試，包括衍生所提供的任何 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="43a18-161">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="43a18-162">讓我們測試範例磁片磁碟機提供者。</span><span class="sxs-lookup"><span data-stu-id="43a18-162">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="43a18-163">執行 `Get-PSProvider` Cmdlet 以取得提供者清單，以確定 AccessDB 磁片磁碟機提供者存在：</span><span class="sxs-lookup"><span data-stu-id="43a18-163">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="43a18-164">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="43a18-164">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="43a18-165">下列輸出會出現：</span><span class="sxs-lookup"><span data-stu-id="43a18-165">The following output appears:</span></span>

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

2. <span data-ttu-id="43a18-166">存取作業系統的系統 **管理工具** 的 [**資料來源**] 部分，以確定資料庫的資料庫伺服器名稱 (DSN) 存在。</span><span class="sxs-lookup"><span data-stu-id="43a18-166">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="43a18-167">在 [ **使用者 DSN** ] 資料表中，按兩下 [ **MS Access 資料庫** ]，然後新增磁片磁碟機路徑 `C:\ps\northwind.mdb` 。</span><span class="sxs-lookup"><span data-stu-id="43a18-167">In the **User DSN** table, double-click **MS Access Database** and add the drive path `C:\ps\northwind.mdb`.</span></span>

3. <span data-ttu-id="43a18-168">使用範例磁片磁碟機提供者建立新的磁片磁碟機：</span><span class="sxs-lookup"><span data-stu-id="43a18-168">Create a new drive using the sample drive provider:</span></span>

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   <span data-ttu-id="43a18-169">下列輸出會出現：</span><span class="sxs-lookup"><span data-stu-id="43a18-169">The following output appears:</span></span>

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="43a18-170">驗證連接。</span><span class="sxs-lookup"><span data-stu-id="43a18-170">Validate the connection.</span></span> <span data-ttu-id="43a18-171">因為連接是定義為磁片磁碟機的成員，所以您可以使用 Get-PDDrive Cmdlet 來檢查它。</span><span class="sxs-lookup"><span data-stu-id="43a18-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="43a18-172">使用者還無法與提供者互動作為磁片磁碟機，因為提供者需要該互動的容器功能。</span><span class="sxs-lookup"><span data-stu-id="43a18-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="43a18-173">如需詳細資訊，請參閱 [建立 Windows PowerShell 容器提供者](./creating-a-windows-powershell-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="43a18-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="43a18-174">**PS> (new-psdrive mydb) 連接**</span><span class="sxs-lookup"><span data-stu-id="43a18-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="43a18-175">下列輸出會出現：</span><span class="sxs-lookup"><span data-stu-id="43a18-175">The following output appears:</span></span>

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

5. <span data-ttu-id="43a18-176">移除磁片磁碟機並結束 shell：</span><span class="sxs-lookup"><span data-stu-id="43a18-176">Remove the drive and exit the shell:</span></span>

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a><span data-ttu-id="43a18-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43a18-177">See Also</span></span>

[<span data-ttu-id="43a18-178">建立 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="43a18-178">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="43a18-179">設計您的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="43a18-179">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="43a18-180">建立基本的 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="43a18-180">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
