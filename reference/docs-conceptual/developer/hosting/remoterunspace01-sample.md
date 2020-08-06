---
title: RemoteRunspace01 範例 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f9ae846d70412858b32bfe32ba5bfbf2063d9eb1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783206"
---
# <a name="remoterunspace01-sample"></a>RemoteRunspace01 範例

這個範例會示範如何建立用來建立遠端連線的遠端執行時間。

## <a name="requirements"></a>需求

 此範例需要 Windows PowerShell 2.0。

## <a name="demonstrates"></a>示範

- 建立 Wsmanconnectioninfo 物件的的[元件](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)。

- 設定 system.servicemodel. [Runspaceconnectioninfo. Operationtimeout *](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout)和[Runspaceconnectioninfo. Opentimeout *](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout)物件的屬性（property），請將其設為.. 管理[元件](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)。

- 建立使用[Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)物件的遠端運行時，以建立遠端連線。

- 關閉遠端運行空間以釋放遠端連線。

## <a name="example"></a>範例

這個範例會定義遠端連線，然後使用該連接資訊來建立遠端連線。

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;             // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;   // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspace01
  {
    /// <summary>
    /// This sample shows how to use a WSManConnectionInfo object to set
    /// various timeouts and how to establish a remote connection.
    /// </summary>
    /// <param name="args">This parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property. The OperationTimeout is used to tell
      // Windows PowerShell how long to wait (in milliseconds) before timing out
      // for any operation. This includes sending input data to the remote computer,
      // receiving output data from the remote computer, and more. The user can
      // change this timeout depending on whether the connection is to a computer
      // in the data center or across a slow WAN.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.

      // Set the OpenTimeout property. OpenTimeout is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out while establishing a
      // remote connection. The user can change this timeout depending on whether the
      // connection is to a computer in the data center or across a slow WAN.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
        remoteRunspace.Open();

        // Add the code to run commands in the remote runspace here. The
        // OperationTimeout value set previously will play a role here because
        // running commands involves sending and receiving data.

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
