---
title: 撰寫容器提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 524fd900-c0fe-4d13-87f2-14903a8fd5a4
caps.latest.revision: 5
ms.openlocfilehash: bf0a73267b3cad1f50d983ebed53318ec98180e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056459"
---
# <a name="writing-a-container-provider"></a><span data-ttu-id="b9e2c-102">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="b9e2c-102">Writing a container provider</span></span>

<span data-ttu-id="b9e2c-103">本主題描述如何實作方法的 Windows PowerShell 提供者支援包含其他項目，例如檔案系統提供者中的資料夾項目。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-103">This topic describes how to implement the methods of a Windows PowerShell provider that support items that contain other items, such as folders in the file system provider.</span></span> <span data-ttu-id="b9e2c-104">若要能夠支援容器項目，提供者必須衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-104">To be able to support containers, a provider must derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

<span data-ttu-id="b9e2c-105">本主題中的範例中的提供者會使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="b9e2c-106">有幾個 helper 方法和類別，用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="b9e2c-107">完整的範例，其中包含協助程式方法，請參閱 < [AccessDBProviderSample04](./accessdbprovidersample04.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>

<span data-ttu-id="b9e2c-108">如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 < [Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-container-methods"></a><span data-ttu-id="b9e2c-109">實作容器方法</span><span class="sxs-lookup"><span data-stu-id="b9e2c-109">Implementing container methods</span></span>

<span data-ttu-id="b9e2c-110">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別會實作支援容器，以及建立、 複製和移除項目方法。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-110">The [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class implements methods that support containers, and create, copy, and remove items.</span></span> <span data-ttu-id="b9e2c-111">如需這些方法的完整清單，請參閱 < [ContainerCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.containercmdletprovider_methods\(v=vs.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-111">For a complete list of these methods, see [ContainerCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.containercmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="b9e2c-112">本主題中的資訊是根據[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="b9e2c-113">本主題並未涵蓋如何設定提供者專案的基本概念，或如何實作方法繼承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，建立和移除磁碟機。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="b9e2c-114">本主題也不會說明如何實作所公開的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b9e2c-115">如需示範如何實作 item cmdlet 的範例，請參閱 <<c0> [ 撰寫項目提供者](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="b9e2c-116">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="b9e2c-116">Declaring the provider class</span></span>

<span data-ttu-id="b9e2c-117">宣告提供者衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別，而且它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="b9e2c-117">Declare the provider to derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a><span data-ttu-id="b9e2c-118">實作 GetChildItems</span><span class="sxs-lookup"><span data-stu-id="b9e2c-118">Implementing GetChildItems</span></span>

<span data-ttu-id="b9e2c-119">PowerShell 引擎會呼叫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，當使用者呼叫[Microsoft.PowerShell.Commands.Get Get-childitem](/dotnet/api/Microsoft.PowerShell.Commands.Get-ChildItem)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-119">The PowerShell engine calls the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method when a user calls the [Microsoft.PowerShell.Commands.Get-Childitem](/dotnet/api/Microsoft.PowerShell.Commands.Get-ChildItem) cmdlet.</span></span> <span data-ttu-id="b9e2c-120">這個方法會取得位於指定路徑的項目子系的項目。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-120">This method gets the items that are the children of the item at the specified path.</span></span>

<span data-ttu-id="b9e2c-121">在存取資料庫範例中，行為[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法取決於所指定項目的類型。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-121">In the Access database example, the behavior of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method depends on the type of the specified item.</span></span> <span data-ttu-id="b9e2c-122">如果項目是磁碟機，然後子系資料表，方法會傳回一組資料表從資料庫。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-122">If the item is the drive, then the children are tables, and the method returns the set of tables from the database.</span></span> <span data-ttu-id="b9e2c-123">如果指定的項目是資料表，子系就會是該資料表的資料列。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-123">If the specified item is a table, then the children are the rows of that table.</span></span> <span data-ttu-id="b9e2c-124">如果項目資料列，然後它沒有子系，而且方法會傳回只在該資料列。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-124">If the item is a row, then it  has no children, and the method returns that row only.</span></span> <span data-ttu-id="b9e2c-125">所有子項目會都傳送給 PowerShell 引擎所[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-125">All child items are sent back to the PowerShell engine by the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

```csharp
protected override void GetChildItems(string path, bool recurse)
       {
           // If path represented is a drive then the children in the path are
           // tables. Hence all tables in the drive represented will have to be
           // returned
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table, path, true);

                   // if the specified item exists and recurse has been set then
                   // all child items within it have to be obtained as well
                   if (ItemExists(path) && recurse)
                   {
                       GetChildItems(path + pathSeparator + table.Name, recurse);
                   }
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get the table name, row number and type of path from the
               // path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Obtain all the rows within the table
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);
                   WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
               }
               else
               {
                   // In this case, the path specified is not valid
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-getchildnames"></a><span data-ttu-id="b9e2c-126">實作 GetChildNames</span><span class="sxs-lookup"><span data-stu-id="b9e2c-126">Implementing GetChildNames</span></span>

<span data-ttu-id="b9e2c-127">[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方式類似於[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法，但是它會傳回名稱屬性的項目，並沒有項目本身。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-127">The [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method is similar to the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method, except that it returns only the name property of the items, and not the items themselves.</span></span>

```csharp
protected override void GetChildNames(string path,
                                     ReturnContainers returnContainers)
       {
           // If the path represented is a drive, then the child items are
           // tables. get the names of all the tables in the drive.
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table.Name, path, true);
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get type, table name and row number from path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Get all the rows in the table and then write out the
                   // row numbers.
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row.RowNumber, path, false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);

                   WriteItemObject(row.RowNumber, path, false);
               }
               else
               {
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-newitem"></a><span data-ttu-id="b9e2c-128">實作 NewItem</span><span class="sxs-lookup"><span data-stu-id="b9e2c-128">Implementing NewItem</span></span>

<span data-ttu-id="b9e2c-129">[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法會在指定的路徑建立指定型別的新項目。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-129">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method creates a new item of the specified type at the specified path.</span></span> <span data-ttu-id="b9e2c-130">PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.PowerShell.Commands.New 項目](/dotnet/api/Microsoft.PowerShell.Commands.New-Item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-130">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.New-Item](/dotnet/api/Microsoft.PowerShell.Commands.New-Item) cmdlet.</span></span>

<span data-ttu-id="b9e2c-131">在此範例中，該方法會實作邏輯來判斷型別與路徑比對。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-131">In this example, the method implements logic to determine that the path and type match.</span></span> <span data-ttu-id="b9e2c-132">也就是說，只有資料表可以直接在 磁碟機 （資料庫），建立，而且可以在資料表底下建立只有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-132">That is, only a table can be created directly under the drive (the database), and only a row can be created under a table.</span></span> <span data-ttu-id="b9e2c-133">如果指定的路徑和項目類型不符合這種方式，此方法會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-133">If the specified path and item type don't match in this way, the method throws an exception.</span></span>

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a><span data-ttu-id="b9e2c-134">CopyItem 實作</span><span class="sxs-lookup"><span data-stu-id="b9e2c-134">Implementing CopyItem</span></span>

<span data-ttu-id="b9e2c-135">[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)將指定的項目複製到指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-135">The [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copies the specified item to the specified path.</span></span> <span data-ttu-id="b9e2c-136">PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.PowerShell.Commands.Copy 項目](/dotnet/api/Microsoft.PowerShell.Commands.Copy-Item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-136">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Copy-Item](/dotnet/api/Microsoft.PowerShell.Commands.Copy-Item) cmdlet.</span></span> <span data-ttu-id="b9e2c-137">這個方法也可以是遞迴的複製所有項目子系，除了項目本身。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-137">This method can also be recursive, copying all of the items children in addition to the item itself.</span></span>

<span data-ttu-id="b9e2c-138">類似於[System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，這個方法會執行邏輯，以確定指定的項目是否屬於正確的型別，要複製的路徑。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-138">Similarly to the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method, this method performs logic to make sure that the specified item is of the correct type for the path to which it is being copied.</span></span> <span data-ttu-id="b9e2c-139">比方說，如果目的地路徑是資料表時，要複製的項目必須是一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-139">For example, if the destination path is a table, the item to be copied must be a row.</span></span>

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a><span data-ttu-id="b9e2c-140">實作 RemoveItem</span><span class="sxs-lookup"><span data-stu-id="b9e2c-140">Implementing RemoveItem</span></span>

<span data-ttu-id="b9e2c-141">[System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法會移除位於指定路徑的項目。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-141">The [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method removes the item at the specified path.</span></span> <span data-ttu-id="b9e2c-142">PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.PowerShell.Commands.Remove 項目](/dotnet/api/Microsoft.PowerShell.Commands.Remove-Item)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-142">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.Remove-Item](/dotnet/api/Microsoft.PowerShell.Commands.Remove-Item) cmdlet.</span></span>

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a><span data-ttu-id="b9e2c-143">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="b9e2c-143">Next steps</span></span>

<span data-ttu-id="b9e2c-144">典型的實際提供者可以將項目從某個路徑移到另一個磁碟機中。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-144">A typical real-world provider is capable of moving items from one path to another within the drive.</span></span> <span data-ttu-id="b9e2c-145">如需支援移動的項目提供者的範例，請參閱 <<c0> [ 撰寫瀏覽提供者](./writing-a-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="b9e2c-145">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e2c-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9e2c-146">See Also</span></span>

[<span data-ttu-id="b9e2c-147">撰寫瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="b9e2c-147">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="b9e2c-148">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="b9e2c-148">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)