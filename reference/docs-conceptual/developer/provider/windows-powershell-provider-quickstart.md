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
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 提供者快速入門

本主題說明如何建立具有建立新磁片磁碟機基本功能的 Windows PowerShell 提供者。 如需提供者的一般資訊，請參閱 [Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。 如需具有更完整功能的提供者範例，請參閱 [提供者範例](./provider-samples.md)。

## <a name="writing-a-basic-provider"></a>撰寫基本提供者

Windows PowerShell 提供者最基本的功能是建立和移除磁片磁碟機。 在此範例中，我們會執行[DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和 DriveCmdletprovider.. [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的[.. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。」的範例如下。 您也將瞭解如何宣告提供者類別。

當您撰寫提供者時，可以指定提供者可供使用時自動建立的預設磁片磁碟機。 您也會定義方法，以建立使用該提供者的新磁片磁碟機。

本主題所提供的範例是以 [AccessDBProviderSample02](./accessdbprovidersample02.md) 範例為基礎，這是較大範例的一部分，表示 Access 資料庫做為 Windows PowerShell 磁片磁碟機。

### <a name="setting-up-the-project"></a>設定專案

在 Visual Studio 中，建立名為 AccessDBProviderSample 的類別庫專案。 請完成下列步驟來設定您的專案，以便 Windows PowerShell 將會啟動，並在您建立並啟動專案時，將提供者載入會話中。

##### <a name="configure-the-provider-project"></a>設定提供者專案

1. 新增 System. Automation 元件做為您專案的參考。

2. 按一下 [ **專案] > AccessDBProviderSample 屬性 > Debug**]。 在 [ **開始專案**] 中，按一下 [ **啟動外部程式**]，然後流覽至 Windows PowerShell 可執行檔 (通常會 c:\Windows\System32\WindowsPowerShell\v1.0 \\.powershell.exe) 。

3. 在 [ **開始選項**] 下的 [ **命令列引數** ] 方塊中，輸入下列內容： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>宣告提供者類別

我們的提供者衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別。 大部分提供真正功能的提供者 (存取和操作專案、流覽資料存放區，以及取得和設定專案的內容) 衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別。

除了指定類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)之外，您還必須使用 Cmdletproviderattribute 來裝飾它，如範例中所示的[](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)中所示。

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

### <a name="implementing-newdrive"></a>執行 >newdrive

當使用者呼叫[NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) Cmdlet 來指定提供者的名稱時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法，以指定您的提供者名稱。 PSDriveInfo 參數是由 Windows PowerShell 引擎傳遞，而方法會將新的磁片磁碟機傳回 Windows PowerShell 引擎。 您必須在上面建立的類別中宣告這個方法。

方法會先檢查以確定傳入的磁片磁碟機物件和磁片磁碟機根目錄都存在，如果其中一項沒有的話，就 `null` 會傳回。 接著，它會使用內部類別 AccessDBPSDriveInfo 的函式來建立新的磁片磁碟機，並連接到磁片磁碟機所代表的 Access 資料庫。

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

以下是 AccessDBPSDriveInfo 內部類別，其中包含用來建立新磁片磁碟機的函式，並包含磁片磁碟機的狀態資訊。

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

### <a name="implementing-removedrive"></a>執行 >removedrive

當使用者呼叫[RemovePSDriveCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand)程式時，Windows PowerShell 引擎會呼叫[DriveCmdletprovider. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，而此方法會呼叫 Cmdlet。 此提供者中的方法會關閉存取資料庫的連接。

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
