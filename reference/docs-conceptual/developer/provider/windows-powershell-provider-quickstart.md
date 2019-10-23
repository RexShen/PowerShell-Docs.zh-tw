---
title: Windows PowerShell 提供者快速入門 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359917"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="9f1d6-102">Windows PowerShell 提供者快速入門</span><span class="sxs-lookup"><span data-stu-id="9f1d6-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="9f1d6-103">本主題說明如何建立 Windows PowerShell 提供者，其具有建立新磁片磁碟機的基本功能。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="9f1d6-104">如需提供者的一般資訊，請參閱[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="9f1d6-105">如需具有更完整功能的提供者範例，請參閱[提供者範例](./provider-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="9f1d6-106">撰寫基本提供者</span><span class="sxs-lookup"><span data-stu-id="9f1d6-106">Writing a basic provider</span></span>

<span data-ttu-id="9f1d6-107">Windows PowerShell 提供者的最基本功能是建立和移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="9f1d6-108">在此範例中，我們會將[DriveCmdletprovider \* Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和的[DriveCmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法[提供給下列系統。DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的功能。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="9f1d6-109">您也會看到如何宣告提供者類別。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="9f1d6-110">當您撰寫提供者時，可以指定在提供者可用時自動建立的預設磁片磁碟機（磁片磁碟機）。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="9f1d6-111">您也會定義方法，以建立使用該提供者的新磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="9f1d6-112">本主題中提供的範例是以[AccessDBProviderSample02](./accessdbprovidersample02.md)範例為基礎，這是較大範例的一部分，其代表 Access 資料庫做為 Windows PowerShell 磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="9f1d6-113">設定專案</span><span class="sxs-lookup"><span data-stu-id="9f1d6-113">Setting up the project</span></span>

<span data-ttu-id="9f1d6-114">在 Visual Studio 中，建立名為 AccessDBProviderSample 的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="9f1d6-115">完成下列步驟來設定您的專案，以便在您建立和啟動專案時，將會啟動 Windows PowerShell，並將提供者載入會話。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="9f1d6-116">設定提供者專案</span><span class="sxs-lookup"><span data-stu-id="9f1d6-116">Configure the provider project</span></span>

1. <span data-ttu-id="9f1d6-117">將 System.webserver 元件新增為您專案的參考。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="9f1d6-118">按一下 **專案 > AccessDBProviderSample 屬性 > Debug**。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="9f1d6-119">在 [**起始專案**] 中，按一下 [**啟動外部程式**]，然後流覽至 Windows PowerShell 可執行檔（通常是 c:\Windows\System32\WindowsPowerShell\v1.0 \\）。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="9f1d6-120">在 [**起始選項**] 底下的 [**命令列引數**] 方塊中輸入下列內容： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="9f1d6-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="9f1d6-121">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="9f1d6-121">Declaring the provider class</span></span>

<span data-ttu-id="9f1d6-122">我們的提供者衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="9f1d6-123">大部分提供實際功能（存取和操作專案、流覽資料存放區，以及取得和設定專案內容）的提供者，都是衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="9f1d6-124">除了指定類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)，您也必須使用 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 來裝飾它，如範例中所示的，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="9f1d6-125">執行 NewDrive</span><span class="sxs-lookup"><span data-stu-id="9f1d6-125">Implementing NewDrive</span></span>

<span data-ttu-id="9f1d6-126">當使用者呼叫[NewPSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand)程式，並指定您的名稱時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，並指定您的那裡.</span><span class="sxs-lookup"><span data-stu-id="9f1d6-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="9f1d6-127">PSDriveInfo 參數是由 Windows PowerShell 引擎所傳遞，而方法會將新的磁片磁碟機傳回 Windows PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="9f1d6-128">這個方法必須在上面建立的類別中宣告。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="9f1d6-129">方法會先檢查並確定已傳入的磁片磁碟機物件和磁片磁碟機根目錄，如果其中之一不存在，則傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="9f1d6-130">然後，它會使用內部類別 AccessDBPSDriveInfo 的函式來建立新的磁片磁碟機，以及連接到磁片磁碟機所代表的 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="9f1d6-131">以下是 AccessDBPSDriveInfo 內部類別，其中包含用來建立新磁片磁碟機的程式，並包含磁片磁碟機的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="9f1d6-132">執行 RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="9f1d6-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="9f1d6-133">當使用者呼叫[RemovePSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand)程式時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. Removedrive \* 方法（System.](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .）。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="9f1d6-134">此提供者中的方法會關閉與 Access 資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="9f1d6-134">The method in this provider closes the connection to the Access database.</span></span>

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