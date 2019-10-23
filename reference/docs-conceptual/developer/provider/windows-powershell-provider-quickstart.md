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
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 提供者快速入門

本主題說明如何建立 Windows PowerShell 提供者，其具有建立新磁片磁碟機的基本功能。 如需提供者的一般資訊，請參閱[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。 如需具有更完整功能的提供者範例，請參閱[提供者範例](./provider-samples.md)。

## <a name="writing-a-basic-provider"></a>撰寫基本提供者

Windows PowerShell 提供者的最基本功能是建立和移除磁片磁碟機。 在此範例中，我們會將[DriveCmdletprovider * Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和的[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法[提供給下列系統。DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的功能。 您也會看到如何宣告提供者類別。

當您撰寫提供者時，可以指定在提供者可用時自動建立的預設磁片磁碟機（磁片磁碟機）。 您也會定義方法，以建立使用該提供者的新磁片磁碟機。

本主題中提供的範例是以[AccessDBProviderSample02](./accessdbprovidersample02.md)範例為基礎，這是較大範例的一部分，其代表 Access 資料庫做為 Windows PowerShell 磁片磁碟機。

### <a name="setting-up-the-project"></a>設定專案

在 Visual Studio 中，建立名為 AccessDBProviderSample 的類別庫專案。 完成下列步驟來設定您的專案，以便在您建立和啟動專案時，將會啟動 Windows PowerShell，並將提供者載入會話。

##### <a name="configure-the-provider-project"></a>設定提供者專案

1. 將 System.webserver 元件新增為您專案的參考。

2. 按一下 **專案 > AccessDBProviderSample 屬性 > Debug**。 在 [**起始專案**] 中，按一下 [**啟動外部程式**]，然後流覽至 Windows PowerShell 可執行檔（通常是 c:\Windows\System32\WindowsPowerShell\v1.0 \\）。

3. 在 [**起始選項**] 底下的 [**命令列引數**] 方塊中輸入下列內容： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>宣告提供者類別

我們的提供者衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。 大部分提供實際功能（存取和操作專案、流覽資料存放區，以及取得和設定專案內容）的提供者，都是衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

除了指定類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)，您也必須使用 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 來裝飾它，如範例中所示的，如下所示。

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

### <a name="implementing-newdrive"></a>執行 NewDrive

當使用者呼叫[NewPSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand)程式，並指定您的名稱時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，並指定您的那裡. PSDriveInfo 參數是由 Windows PowerShell 引擎所傳遞，而方法會將新的磁片磁碟機傳回 Windows PowerShell 引擎。 這個方法必須在上面建立的類別中宣告。

方法會先檢查並確定已傳入的磁片磁碟機物件和磁片磁碟機根目錄，如果其中之一不存在，則傳回 `null`。 然後，它會使用內部類別 AccessDBPSDriveInfo 的函式來建立新的磁片磁碟機，以及連接到磁片磁碟機所代表的 Access 資料庫。

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

以下是 AccessDBPSDriveInfo 內部類別，其中包含用來建立新磁片磁碟機的程式，並包含磁片磁碟機的狀態資訊。

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

### <a name="implementing-removedrive"></a>執行 RemoveDrive

當使用者呼叫[RemovePSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand)程式時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. Removedrive * 方法（System.](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .）。 此提供者中的方法會關閉與 Access 資料庫的連接。

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