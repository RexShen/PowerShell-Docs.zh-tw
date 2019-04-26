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
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 提供者快速入門

本主題說明如何建立 Windows PowerShell 提供者已建立新的磁碟機的基本功能。 一般提供者的詳細資訊，請參閱[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。 如需更完整的功能提供者的範例，請參閱[提供者範例](./provider-samples.md)。

## <a name="writing-a-basic-provider"></a>撰寫基本提供者

Windows PowerShell 提供者的最基本的功能是建立和移除磁碟機。 在此範例中，我們會實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)並[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。 您也會看到如何宣告提供者類別。

當您撰寫的提供者時，您可以指定預設磁碟機磁碟機提供者可用時自動建立。 您也會定義方法，以建立新的磁碟機，使用該提供者。

本主題所提供的範例根據[AccessDBProviderSample02](./accessdbprovidersample02.md)範例中，這是完整的範例，表示為 Windows PowerShell 磁碟機的 Access 資料庫的一部分。

### <a name="setting-up-the-project"></a>設定專案

在 Visual Studio 中建立名為 AccessDBProviderSample 的類別庫專案。 完成下列步驟來設定您的專案，因此將會啟動 Windows PowerShell，並提供者也會載入到工作階段，當您建置並啟動您的專案。

##### <a name="configure-the-provider-project"></a>設定提供者專案

1. 為您的專案參考加入 System.Management.Automation 組件。

2. 按一下 **專案 > AccessDBProviderSample 屬性 > 偵錯**。 在 **入門專案**，按一下**啟動外部程式**，並瀏覽至 Windows PowerShell 可執行檔 (通常 c:\Windows\System32\WindowsPowerShell\v1.0\\。 powershell.exe)。

3. 底下**啟動選項**，輸入下列內容輸入**命令列引數**方塊： `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>宣告提供者類別

我們的提供者衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。 大部分的提供者可提供真正的功能 （存取和操作項目、 瀏覽資料存放區，以及取得和設定項目內容的） 衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

除了指定的類別衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)，您必須將它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)範例所示。

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

### <a name="implementing-newdrive"></a>實作 NewDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)由 Windows PowerShell 引擎會呼叫方法，當使用者呼叫[Microsoft.PowerShell.Commands.New Persist](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)cmdlet 並指定您的提供者的名稱。 PSDriveInfo 傳遞的參數是由 Windows PowerShell 引擎，且此方法傳回新的磁碟機至 Windows PowerShell 引擎。 這個方法必須宣告上面所建立的類別內。

方法會先檢查以確定磁碟機物件和傳遞的磁碟機根目錄都存在，傳回`null`如果其中任一不這樣做。 它會使用 AccessDBPSDriveInfo 的內部類別的建構函式來建立新的磁碟機和代表存取資料庫的磁碟機的連線。

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

以下是 AccessDBPSDriveInfo 內部類別包含用來建立新的磁碟機中，建構函式，其中包含磁碟機的狀態資訊。

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

### <a name="implementing-removedrive"></a>實作 RemoveDrive

[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)由 Windows PowerShell 引擎會呼叫方法，當使用者呼叫[Microsoft.PowerShell.Commands.Remove New-psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet。 此提供者中的方法關閉存取資料庫的連接。

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