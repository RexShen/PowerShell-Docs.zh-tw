---
title: Windows PowerShell 提供者的快速入門 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080878"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="32871-102">Windows PowerShell 提供者快速入門</span><span class="sxs-lookup"><span data-stu-id="32871-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="32871-103">本主題說明如何建立 Windows PowerShell 提供者已建立新的磁碟機的基本功能。</span><span class="sxs-lookup"><span data-stu-id="32871-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="32871-104">一般提供者的詳細資訊，請參閱[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="32871-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="32871-105">如需更完整的功能提供者的範例，請參閱[提供者範例](./provider-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="32871-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="32871-106">撰寫基本提供者</span><span class="sxs-lookup"><span data-stu-id="32871-106">Writing a basic provider</span></span>

<span data-ttu-id="32871-107">Windows PowerShell 提供者的最基本的功能是建立和移除磁碟機。</span><span class="sxs-lookup"><span data-stu-id="32871-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="32871-108">在此範例中，我們會實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)並[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="32871-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="32871-109">您也會看到如何宣告提供者類別。</span><span class="sxs-lookup"><span data-stu-id="32871-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="32871-110">當您撰寫的提供者時，您可以指定預設磁碟機磁碟機提供者可用時自動建立。</span><span class="sxs-lookup"><span data-stu-id="32871-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="32871-111">您也會定義方法，以建立新的磁碟機，使用該提供者。</span><span class="sxs-lookup"><span data-stu-id="32871-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="32871-112">本主題所提供的範例根據[AccessDBProviderSample02](./accessdbprovidersample02.md)範例中，這是完整的範例，表示為 Windows PowerShell 磁碟機的 Access 資料庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="32871-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="32871-113">設定專案</span><span class="sxs-lookup"><span data-stu-id="32871-113">Setting up the project</span></span>

<span data-ttu-id="32871-114">在 Visual Studio 中建立名為 AccessDBProviderSample 的類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="32871-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="32871-115">完成下列步驟來設定您的專案，因此將會啟動 Windows PowerShell，並提供者也會載入到工作階段，當您建置並啟動您的專案。</span><span class="sxs-lookup"><span data-stu-id="32871-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="32871-116">設定提供者專案</span><span class="sxs-lookup"><span data-stu-id="32871-116">Configure the provider project</span></span>

1. <span data-ttu-id="32871-117">為您的專案參考加入 System.Management.Automation 組件。</span><span class="sxs-lookup"><span data-stu-id="32871-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="32871-118">按一下 **專案 > AccessDBProviderSample 屬性 > 偵錯**。</span><span class="sxs-lookup"><span data-stu-id="32871-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="32871-119">在 **入門專案**，按一下**啟動外部程式**，並瀏覽至 Windows PowerShell 可執行檔 (通常 c:\Windows\System32\WindowsPowerShell\v1.0\\。 powershell.exe)。</span><span class="sxs-lookup"><span data-stu-id="32871-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="32871-120">底下**啟動選項**，輸入下列內容輸入**命令列引數**方塊： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="32871-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="32871-121">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="32871-121">Declaring the provider class</span></span>

<span data-ttu-id="32871-122">我們的提供者衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="32871-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="32871-123">大部分的提供者可提供真正的功能 （存取和操作項目、 瀏覽資料存放區，以及取得和設定項目內容的） 衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="32871-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="32871-124">除了指定的類別衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)，您必須將它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)範例所示。</span><span class="sxs-lookup"><span data-stu-id="32871-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="32871-125">實作 NewDrive</span><span class="sxs-lookup"><span data-stu-id="32871-125">Implementing NewDrive</span></span>

<span data-ttu-id="32871-126">[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)由 Windows PowerShell 引擎會呼叫方法，當使用者呼叫[Microsoft.PowerShell.Commands.New Persist](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet 並指定您的提供者的名稱。</span><span class="sxs-lookup"><span data-stu-id="32871-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="32871-127">PSDriveInfo 傳遞的參數是由 Windows PowerShell 引擎，且此方法傳回新的磁碟機至 Windows PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="32871-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="32871-128">這個方法必須宣告上面所建立的類別內。</span><span class="sxs-lookup"><span data-stu-id="32871-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="32871-129">方法會先檢查以確定磁碟機物件和傳遞的磁碟機根目錄都存在，傳回`null`如果其中任一不這樣做。</span><span class="sxs-lookup"><span data-stu-id="32871-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="32871-130">它會使用 AccessDBPSDriveInfo 的內部類別的建構函式來建立新的磁碟機和代表存取資料庫的磁碟機的連線。</span><span class="sxs-lookup"><span data-stu-id="32871-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="32871-131">以下是 AccessDBPSDriveInfo 內部類別包含用來建立新的磁碟機中，建構函式，其中包含磁碟機的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="32871-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="32871-132">實作 RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="32871-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="32871-133">[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)由 Windows PowerShell 引擎會呼叫方法，當使用者呼叫[Microsoft.PowerShell.Commands.Remove New-psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="32871-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="32871-134">此提供者中的方法關閉存取資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="32871-134">The method in this provider closes the connection to the Access database.</span></span>

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