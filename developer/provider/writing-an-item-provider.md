---
title: 撰寫項目提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: e3289e9336b863b5e0998a2beb29353c82a31f79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856704"
---
# <a name="writing-an-item-provider"></a>撰寫項目提供者

本主題描述如何實作 Windows PowerShell 提供者的方法，以存取和管理資料存放區中的項目。 若要能夠存取的項目，提供者必須衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。

本主題中的範例中的提供者會使用 Access 資料庫作為其資料存放區。 有幾個 helper 方法和類別，用來與資料庫互動。 完整的範例，其中包含協助程式方法，請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)

如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 < [Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。

## <a name="implementing-item-methods"></a>實作的項目方法

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會公開數種方法，可用來存取和操作資料存放區中的項目。 如需這些方法的完整清單，請參閱 < [ItemCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)。 在此範例中，我們會實作四種方法。 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)取得位於指定路徑的項目。 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)設定所指定項目的值。 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會檢查在指定的路徑是否存在的項目。 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)會檢查以查看它對應到資料存放區中的位置路徑。

> [!NOTE]
> 本主題中的資訊是根據[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)。 本主題並未涵蓋如何設定提供者專案的基本概念，或如何實作方法繼承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，建立和移除磁碟機。

### <a name="declaring-the-provider-class"></a>宣告提供者類別

宣告提供者衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別，而且它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>實作 GetItem

[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)當使用者呼叫 PowerShell 引擎會呼叫[Microsoft.Powershell.Commands.Get 項目](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item)cmdlet 您提供者。 方法會傳回位於指定路徑的項目。 在存取資料庫範例中，方法會檢查項目是否在磁碟機本身，在資料庫或資料庫中的資料列的資料表。 方法會將傳送之項目的 PowerShell 引擎藉由呼叫[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>實作 SetItem

[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)當使用者呼叫，方法由 PowerShell 引擎會呼叫呼叫[Microsoft.Powershell.Commands.Set 項目](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item)cmdlet. 在指定的路徑，它就會設定項目的值。

在存取資料庫範例中，合理的設定項目的值，只有當該項目是資料列，因此這個方法會擲回[NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx)當項目不是一個資料列。

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>實作 ItemExists

[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)當使用者呼叫 PowerShell 引擎便會呼叫方法[Microsoft.Powershell.Commands.Test 路徑](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path)cmdlet。 方法會判斷是否有項目在指定的路徑。 如果項目不存在，此方法將它傳遞給 PowerShell 引擎藉由呼叫[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)。

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>實作 IsValidPath

[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法會檢查指定的路徑是否語法有效，目前提供者。 它不會檢查路徑是否存在的項目。

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>接下來的步驟

典型的實際提供者都能支援包含其他項目，項目，並將項目從某個路徑移到另一個磁碟機中的項目。 如需支援容器的提供者的範例，請參閱 <<c0> [ 撰寫容器提供者](./writing-a-container-provider.md)。 如需支援移動的項目提供者的範例，請參閱 <<c0> [ 撰寫瀏覽提供者](./writing-a-navigation-provider.md)。

## <a name="see-also"></a>另請參閱

[撰寫容器提供者](./writing-a-container-provider.md)

[撰寫瀏覽提供者](./writing-a-navigation-provider.md)

[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)