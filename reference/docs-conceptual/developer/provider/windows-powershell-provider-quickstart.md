---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 提供者快速入門
description: Windows PowerShell 提供者快速入門
ms.openlocfilehash: f0fe0ad60e9d10efd505cda60af995c597226b92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664335"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="817fe-103">Windows PowerShell 提供者快速入門</span><span class="sxs-lookup"><span data-stu-id="817fe-103">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="817fe-104">本主題說明如何建立具有建立新磁片磁碟機基本功能的 Windows PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="817fe-104">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="817fe-105">如需提供者的一般資訊，請參閱 [Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="817fe-105">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="817fe-106">如需具有更完整功能的提供者範例，請參閱 [提供者範例](./provider-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="817fe-106">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="817fe-107">撰寫基本提供者</span><span class="sxs-lookup"><span data-stu-id="817fe-107">Writing a basic provider</span></span>

<span data-ttu-id="817fe-108">Windows PowerShell 提供者最基本的功能是建立和移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="817fe-108">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="817fe-109">在此範例中，我們會執行[DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和 DriveCmdletprovider.. [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的[.. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。」的範例如下。</span><span class="sxs-lookup"><span data-stu-id="817fe-109">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="817fe-110">您也將瞭解如何宣告提供者類別。</span><span class="sxs-lookup"><span data-stu-id="817fe-110">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="817fe-111">當您撰寫提供者時，可以指定提供者可供使用時自動建立的預設磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="817fe-111">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="817fe-112">您也會定義方法，以建立使用該提供者的新磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="817fe-112">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="817fe-113">本主題所提供的範例是以 [AccessDBProviderSample02](./accessdbprovidersample02.md) 範例為基礎，這是較大範例的一部分，表示 Access 資料庫做為 Windows PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="817fe-113">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="817fe-114">設定專案</span><span class="sxs-lookup"><span data-stu-id="817fe-114">Setting up the project</span></span>

<span data-ttu-id="817fe-115">在 Visual Studio 中，建立名為 AccessDBProviderSample 的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="817fe-115">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="817fe-116">請完成下列步驟來設定您的專案，以便 Windows PowerShell 將會啟動，並在您建立並啟動專案時，將提供者載入會話中。</span><span class="sxs-lookup"><span data-stu-id="817fe-116">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="817fe-117">設定提供者專案</span><span class="sxs-lookup"><span data-stu-id="817fe-117">Configure the provider project</span></span>

1. <span data-ttu-id="817fe-118">新增 System. Automation 元件做為您專案的參考。</span><span class="sxs-lookup"><span data-stu-id="817fe-118">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="817fe-119">按一下 [ **專案] > AccessDBProviderSample 屬性 > Debug**]。</span><span class="sxs-lookup"><span data-stu-id="817fe-119">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="817fe-120">在 [ **開始專案**] 中，按一下 [ **啟動外部程式**]，然後流覽至 Windows PowerShell 可執行檔 (通常會 c:\Windows\System32\WindowsPowerShell\v1.0 \\.powershell.exe) 。</span><span class="sxs-lookup"><span data-stu-id="817fe-120">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="817fe-121">在 [ **開始選項**] 下的 [ **命令列引數** ] 方塊中，輸入下列內容： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="817fe-121">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="817fe-122">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="817fe-122">Declaring the provider class</span></span>

<span data-ttu-id="817fe-123">我們的提供者衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別。</span><span class="sxs-lookup"><span data-stu-id="817fe-123">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="817fe-124">大部分提供真正功能的提供者 (存取和操作專案、流覽資料存放區，以及取得和設定專案的內容) 衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別。</span><span class="sxs-lookup"><span data-stu-id="817fe-124">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="817fe-125">除了指定類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)之外，您還必須使用 Cmdletproviderattribute 來裝飾它，如範例中所示的[](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)中所示。</span><span class="sxs-lookup"><span data-stu-id="817fe-125">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a><span data-ttu-id="817fe-126">執行 >newdrive</span><span class="sxs-lookup"><span data-stu-id="817fe-126">Implementing NewDrive</span></span>

<span data-ttu-id="817fe-127">當使用者呼叫[NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) Cmdlet 來指定提供者的名稱時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. >newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以指定您的提供者名稱。</span><span class="sxs-lookup"><span data-stu-id="817fe-127">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="817fe-128">PSDriveInfo 參數是由 Windows PowerShell 引擎傳遞，而方法會將新的磁片磁碟機傳回 Windows PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="817fe-128">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="817fe-129">您必須在上面建立的類別中宣告這個方法。</span><span class="sxs-lookup"><span data-stu-id="817fe-129">This method must be declared within the class created above.</span></span>

<span data-ttu-id="817fe-130">方法會先檢查以確定傳入的磁片磁碟機物件和磁片磁碟機根目錄都存在，如果其中一項沒有的話，就 `null` 會傳回。</span><span class="sxs-lookup"><span data-stu-id="817fe-130">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="817fe-131">接著，它會使用內部類別 AccessDBPSDriveInfo 的函式來建立新的磁片磁碟機，並連接到磁片磁碟機所代表的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="817fe-131">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

<span data-ttu-id="817fe-132">以下是 AccessDBPSDriveInfo 內部類別，其中包含用來建立新磁片磁碟機的函式，並包含磁片磁碟機的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="817fe-132">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a><span data-ttu-id="817fe-133">執行 >removedrive</span><span class="sxs-lookup"><span data-stu-id="817fe-133">Implementing RemoveDrive</span></span>

<span data-ttu-id="817fe-134">當使用者呼叫[RemovePSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand)程式時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. >removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，而此方法會呼叫 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="817fe-134">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="817fe-135">此提供者中的方法會關閉存取資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="817fe-135">The method in this provider closes the connection to the Access database.</span></span>

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```
