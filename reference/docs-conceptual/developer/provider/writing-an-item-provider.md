---
title: 撰寫專案提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359877"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="746ae-102">撰寫項目提供者</span><span class="sxs-lookup"><span data-stu-id="746ae-102">Writing an item provider</span></span>

<span data-ttu-id="746ae-103">本主題描述如何執行 Windows PowerShell 提供者的方法，以存取和運算元據存放區中的專案。</span><span class="sxs-lookup"><span data-stu-id="746ae-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="746ae-104">若要能夠存取專案，提供者必須衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別（provider）。</span><span class="sxs-lookup"><span data-stu-id="746ae-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="746ae-105">本主題的範例中的提供者會使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="746ae-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="746ae-106">有數個 helper 方法和類別可用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="746ae-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="746ae-107">如需包含 helper 方法的完整範例，請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="746ae-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="746ae-108">如需 Windows PowerShell 提供者的詳細資訊，請參閱[Windows Powershell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="746ae-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="746ae-109">執行專案方法</span><span class="sxs-lookup"><span data-stu-id="746ae-109">Implementing item methods</span></span>

<span data-ttu-id="746ae-110">[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會公開數個可用於存取和運算元據存放區中專案的方法。</span><span class="sxs-lookup"><span data-stu-id="746ae-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="746ae-111">如需這些方法的完整清單，請參閱[ItemCmdletProvider 方法](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods)。</span><span class="sxs-lookup"><span data-stu-id="746ae-111">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods).</span></span> <span data-ttu-id="746ae-112">在此範例中，我們將會執行這四種方法。</span><span class="sxs-lookup"><span data-stu-id="746ae-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="746ae-113">[ItemCmdletprovider. Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)會取得指定路徑上的專案。</span><span class="sxs-lookup"><span data-stu-id="746ae-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="746ae-114">[ItemCmdletprovider. Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)會設定指定之專案的值。</span><span class="sxs-lookup"><span data-stu-id="746ae-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="746ae-115">[ItemCmdletprovider. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會檢查項目是否存在於指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="746ae-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="746ae-116">[ItemCmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)會檢查路徑，以查看它是否對應至資料存放區中的位置。</span><span class="sxs-lookup"><span data-stu-id="746ae-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="746ae-117">本主題是以[Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)中的資訊為基礎。</span><span class="sxs-lookup"><span data-stu-id="746ae-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="746ae-118">本主題未涵蓋如何設定提供者專案的基本概念，或如何執行繼承自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的方法，以建立和移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="746ae-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="746ae-119">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="746ae-119">Declaring the provider class</span></span>

<span data-ttu-id="746ae-120">宣告提供者，以衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別，並使用[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)來裝飾該服務的程式，並將其裝飾。</span><span class="sxs-lookup"><span data-stu-id="746ae-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="746ae-121">執行 GetItem</span><span class="sxs-lookup"><span data-stu-id="746ae-121">Implementing GetItem</span></span>

<span data-ttu-id="746ae-122">當使用者在您的提供者上呼叫[GetItemCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand)程式時，PowerShell 引擎會呼叫[ItemCmdletprovider. Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ，而此介面會被呼叫。</span><span class="sxs-lookup"><span data-stu-id="746ae-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="746ae-123">方法會傳回指定路徑的專案。</span><span class="sxs-lookup"><span data-stu-id="746ae-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="746ae-124">在 Access 資料庫範例中，方法會檢查項目是否為磁片磁碟機本身、資料庫中的資料表，或資料庫中的資料列。</span><span class="sxs-lookup"><span data-stu-id="746ae-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="746ae-125">方法會藉由呼叫[Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法，將專案傳送至 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="746ae-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="746ae-126">執行 SetItem</span><span class="sxs-lookup"><span data-stu-id="746ae-126">Implementing SetItem</span></span>

<span data-ttu-id="746ae-127">當使用者呼叫[SetItemCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand)程式時，會呼叫[ItemCmdletprovider. Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法（由 PowerShell 引擎呼叫）來呼叫。</span><span class="sxs-lookup"><span data-stu-id="746ae-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="746ae-128">它會在指定的路徑設定專案的值。</span><span class="sxs-lookup"><span data-stu-id="746ae-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="746ae-129">在 Access 資料庫範例中，只有當專案是資料列時，才會設定專案的值，因此當專案不是資料列時，方法會擲回[NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) 。</span><span class="sxs-lookup"><span data-stu-id="746ae-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="746ae-130">執行 ItemExists</span><span class="sxs-lookup"><span data-stu-id="746ae-130">Implementing ItemExists</span></span>

<span data-ttu-id="746ae-131">當使用者呼叫[TestPathCommand 指令](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand)程式時，PowerShell 引擎會呼叫[ItemCmdletprovider. Itemexists \* 方法（System.](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) .）。</span><span class="sxs-lookup"><span data-stu-id="746ae-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="746ae-132">方法會判斷指定路徑上是否有專案。</span><span class="sxs-lookup"><span data-stu-id="746ae-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="746ae-133">如果專案存在，則方法會呼叫[Cmdletprovider. Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)，將它傳回給 PowerShell 引擎。</span><span class="sxs-lookup"><span data-stu-id="746ae-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="746ae-134">執行 IsValidPath</span><span class="sxs-lookup"><span data-stu-id="746ae-134">Implementing IsValidPath</span></span>

<span data-ttu-id="746ae-135">[ItemCmdletprovider. Isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法會檢查指定的路徑在語法上是否對目前的提供者有效。</span><span class="sxs-lookup"><span data-stu-id="746ae-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="746ae-136">它不會檢查項目是否存在於路徑。</span><span class="sxs-lookup"><span data-stu-id="746ae-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="746ae-137">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="746ae-137">Next steps</span></span>

<span data-ttu-id="746ae-138">一般的真實世界提供者可以支援包含其他專案的專案，以及將專案從某個路徑移至磁片磁碟機中的另一個路徑。</span><span class="sxs-lookup"><span data-stu-id="746ae-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="746ae-139">如需支援容器的提供者範例，請參閱[撰寫容器提供者](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="746ae-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="746ae-140">如需支援移動專案之提供者的範例，請參閱[撰寫導覽提供者](./writing-a-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="746ae-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="746ae-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="746ae-141">See Also</span></span>

[<span data-ttu-id="746ae-142">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="746ae-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="746ae-143">撰寫導覽提供者</span><span class="sxs-lookup"><span data-stu-id="746ae-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="746ae-144">Windows PowerShell 提供者總覽</span><span class="sxs-lookup"><span data-stu-id="746ae-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
