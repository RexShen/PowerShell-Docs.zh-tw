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
# <a name="writing-an-item-provider"></a><span data-ttu-id="9ab37-102">撰寫項目提供者</span><span class="sxs-lookup"><span data-stu-id="9ab37-102">Writing an item provider</span></span>

<span data-ttu-id="9ab37-103">本主題描述如何實作 Windows PowerShell 提供者的方法，以存取和管理資料存放區中的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="9ab37-104">若要能夠存取的項目，提供者必須衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="9ab37-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="9ab37-105">本主題中的範例中的提供者會使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="9ab37-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="9ab37-106">有幾個 helper 方法和類別，用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="9ab37-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="9ab37-107">完整的範例，其中包含協助程式方法，請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="9ab37-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="9ab37-108">如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 < [Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="9ab37-109">實作的項目方法</span><span class="sxs-lookup"><span data-stu-id="9ab37-109">Implementing item methods</span></span>

<span data-ttu-id="9ab37-110">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會公開數種方法，可用來存取和操作資料存放區中的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="9ab37-111">如需這些方法的完整清單，請參閱 < [ItemCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="9ab37-112">在此範例中，我們會實作四種方法。</span><span class="sxs-lookup"><span data-stu-id="9ab37-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="9ab37-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)取得位於指定路徑的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="9ab37-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)設定所指定項目的值。</span><span class="sxs-lookup"><span data-stu-id="9ab37-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="9ab37-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)會檢查在指定的路徑是否存在的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="9ab37-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)會檢查以查看它對應到資料存放區中的位置路徑。</span><span class="sxs-lookup"><span data-stu-id="9ab37-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab37-117">本主題中的資訊是根據[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="9ab37-118">本主題並未涵蓋如何設定提供者專案的基本概念，或如何實作方法繼承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，建立和移除磁碟機。</span><span class="sxs-lookup"><span data-stu-id="9ab37-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="9ab37-119">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="9ab37-119">Declaring the provider class</span></span>

<span data-ttu-id="9ab37-120">宣告提供者衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別，而且它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="9ab37-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="9ab37-121">實作 GetItem</span><span class="sxs-lookup"><span data-stu-id="9ab37-121">Implementing GetItem</span></span>

<span data-ttu-id="9ab37-122">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)當使用者呼叫 PowerShell 引擎會呼叫[Microsoft.Powershell.Commands.Get 項目](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item)cmdlet 您提供者。</span><span class="sxs-lookup"><span data-stu-id="9ab37-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="9ab37-123">方法會傳回位於指定路徑的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="9ab37-124">在存取資料庫範例中，方法會檢查項目是否在磁碟機本身，在資料庫或資料庫中的資料列的資料表。</span><span class="sxs-lookup"><span data-stu-id="9ab37-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="9ab37-125">方法會將傳送之項目的 PowerShell 引擎藉由呼叫[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。</span><span class="sxs-lookup"><span data-stu-id="9ab37-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="9ab37-126">實作 SetItem</span><span class="sxs-lookup"><span data-stu-id="9ab37-126">Implementing SetItem</span></span>

<span data-ttu-id="9ab37-127">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)當使用者呼叫，方法由 PowerShell 引擎會呼叫呼叫[Microsoft.Powershell.Commands.Set 項目](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item)cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9ab37-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.Powershell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="9ab37-128">在指定的路徑，它就會設定項目的值。</span><span class="sxs-lookup"><span data-stu-id="9ab37-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="9ab37-129">在存取資料庫範例中，合理的設定項目的值，只有當該項目是資料列，因此這個方法會擲回[NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx)當項目不是一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9ab37-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="9ab37-130">實作 ItemExists</span><span class="sxs-lookup"><span data-stu-id="9ab37-130">Implementing ItemExists</span></span>

<span data-ttu-id="9ab37-131">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)當使用者呼叫 PowerShell 引擎便會呼叫方法[Microsoft.Powershell.Commands.Test 路徑](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path)cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9ab37-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.Powershell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="9ab37-132">方法會判斷是否有項目在指定的路徑。</span><span class="sxs-lookup"><span data-stu-id="9ab37-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="9ab37-133">如果項目不存在，此方法將它傳遞給 PowerShell 引擎藉由呼叫[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="9ab37-134">實作 IsValidPath</span><span class="sxs-lookup"><span data-stu-id="9ab37-134">Implementing IsValidPath</span></span>

<span data-ttu-id="9ab37-135">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法會檢查指定的路徑是否語法有效，目前提供者。</span><span class="sxs-lookup"><span data-stu-id="9ab37-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="9ab37-136">它不會檢查路徑是否存在的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="9ab37-137">接下來的步驟</span><span class="sxs-lookup"><span data-stu-id="9ab37-137">Next steps</span></span>

<span data-ttu-id="9ab37-138">典型的實際提供者都能支援包含其他項目，項目，並將項目從某個路徑移到另一個磁碟機中的項目。</span><span class="sxs-lookup"><span data-stu-id="9ab37-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="9ab37-139">如需支援容器的提供者的範例，請參閱 <<c0> [ 撰寫容器提供者](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="9ab37-140">如需支援移動的項目提供者的範例，請參閱 <<c0> [ 撰寫瀏覽提供者](./writing-a-navigation-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="9ab37-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9ab37-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab37-141">See Also</span></span>

[<span data-ttu-id="9ab37-142">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="9ab37-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="9ab37-143">撰寫瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="9ab37-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="9ab37-144">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="9ab37-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)