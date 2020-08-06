---
title: 撰寫專案提供者 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1df30e7af1b534756f797b9b5d4e29b689cbc782
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786759"
---
# <a name="writing-an-item-provider"></a>撰寫項目提供者

本主題描述如何執行 Windows PowerShell 提供者的方法，以存取和運算元據存放區中的專案。 若要能夠存取專案，提供者必須衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別（provider）。

本主題的範例中的提供者會使用 Access 資料庫作為其資料存放區。 有數個 helper 方法和類別可用來與資料庫互動。 如需包含 helper 方法的完整範例，請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)

如需 Windows PowerShell 提供者的詳細資訊，請參閱[Windows Powershell 提供者總覽](./windows-powershell-provider-overview.md)。

## <a name="implementing-item-methods"></a>執行專案方法

[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會公開數個可用於存取和運算元據存放區中專案的方法。 如需這些方法的完整清單，請參閱[ItemCmdletProvider 方法](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods)。 在此範例中，我們將會執行這四種方法。 [ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)會取得指定路徑上的專案。 [ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)會設定指定之專案的值。 [ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會檢查項目是否存在於指定的路徑。 [ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)會檢查路徑，以查看它是否對應至資料存放區中的位置。

> [!NOTE]
> 本主題是以[Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)中的資訊為基礎。 本主題未涵蓋如何設定提供者專案的基本概念，或如何執行繼承自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的方法，以建立和移除磁片磁碟機。

### <a name="declaring-the-provider-class"></a>宣告提供者類別

宣告提供者，以衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別，並使用[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)來裝飾該服務的程式，並將其裝飾。

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>執行 GetItem

當使用者在您的提供者上呼叫[GetItemCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand)程式時，PowerShell 引擎會呼叫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ，而此介面會被呼叫。 方法會傳回指定路徑的專案。 在 Access 資料庫範例中，方法會檢查項目是否為磁片磁碟機本身、資料庫中的資料表，或資料庫中的資料列。 方法會藉由呼叫[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法，將專案傳送至 PowerShell 引擎。

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

### <a name="implementing-setitem"></a>執行 SetItem

當使用者呼叫[SetItemCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand)程式時，會呼叫[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法（由 PowerShell 引擎呼叫）來呼叫。 它會在指定的路徑設定專案的值。

在 Access 資料庫範例中，只有當專案是資料列時，才會設定專案的值，因此當專案不是資料列時，方法會擲回[NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) 。

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

### <a name="implementing-itemexists"></a>執行 ItemExists

當使用者呼叫[TestPathCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand)程式時，PowerShell 引擎會呼叫[ItemCmdletprovider. Itemexists * 方法（System.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) .）。 方法會判斷指定路徑上是否有專案。 如果專案存在，則方法會呼叫[Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)，將它傳回給 PowerShell 引擎。

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

### <a name="implementing-isvalidpath"></a>執行 IsValidPath

[ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法會檢查指定的路徑在語法上是否對目前的提供者有效。 它不會檢查項目是否存在於路徑。

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

## <a name="next-steps"></a>後續步驟

一般的真實世界提供者可以支援包含其他專案的專案，以及將專案從某個路徑移至磁片磁碟機中的另一個路徑。 如需支援容器的提供者範例，請參閱[撰寫容器提供者](./writing-a-container-provider.md)。 如需支援移動專案之提供者的範例，請參閱[撰寫導覽提供者](./writing-a-navigation-provider.md)。

## <a name="see-also"></a>另請參閱

[撰寫容器提供者](./writing-a-container-provider.md)

[撰寫瀏覽提供者](./writing-a-navigation-provider.md)

[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)
