---
title: 撰寫瀏覽提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734721"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="910ba-102">撰寫瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="910ba-102">Writing a navigation provider</span></span>

<span data-ttu-id="910ba-103">本主題描述如何實作的 Windows PowerShell 提供者支援巢狀的容器 （多層級的資料存放區），移動項目和相對路徑的方法。</span><span class="sxs-lookup"><span data-stu-id="910ba-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="910ba-104">瀏覽提供者必須衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="910ba-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="910ba-105">本主題中的範例中的提供者會使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="910ba-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="910ba-106">有幾個 helper 方法和類別，用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="910ba-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="910ba-107">完整的範例，其中包含協助程式方法，請參閱 < [AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="910ba-108">如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 < [Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="910ba-109">實作巡覽方法</span><span class="sxs-lookup"><span data-stu-id="910ba-109">Implementing navigation methods</span></span>

<span data-ttu-id="910ba-110">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會實作方法，可支援巢狀的容器、 相對路徑，並將項目。</span><span class="sxs-lookup"><span data-stu-id="910ba-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="910ba-111">如需這些方法的完整清單，請參閱 < [NavigationCmdletProvider 方法](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)。</span><span class="sxs-lookup"><span data-stu-id="910ba-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="910ba-112">本主題中的資訊是根據[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="910ba-113">本主題並未涵蓋如何設定提供者專案的基本概念，或如何實作方法繼承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，建立和移除磁碟機。</span><span class="sxs-lookup"><span data-stu-id="910ba-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="910ba-114">本主題也不會說明如何實作所公開的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)或[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="910ba-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="910ba-115">如需示範如何實作 item cmdlet 的範例，請參閱 <<c0> [ 撰寫項目提供者](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="910ba-116">如需示範如何實作容器 cmdlet 的範例，請參閱 <<c0> [ 撰寫容器提供者](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="910ba-117">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="910ba-117">Declaring the provider class</span></span>

<span data-ttu-id="910ba-118">宣告提供者衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="910ba-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="910ba-119">實作 IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="910ba-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="910ba-120">[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會檢查是否位於指定路徑的項目是容器。</span><span class="sxs-lookup"><span data-stu-id="910ba-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="910ba-121">實作 GetChildName</span><span class="sxs-lookup"><span data-stu-id="910ba-121">Implementing GetChildName</span></span>

<span data-ttu-id="910ba-122">[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會取得位於指定路徑的子系項目的名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="910ba-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="910ba-123">如果位於指定路徑的項目不是容器的子系，則這個方法應傳回路徑。</span><span class="sxs-lookup"><span data-stu-id="910ba-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="910ba-124">實作 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="910ba-124">Implementing GetParentPath</span></span>

<span data-ttu-id="910ba-125">[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會取得位於指定路徑之父代的項目路徑。</span><span class="sxs-lookup"><span data-stu-id="910ba-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="910ba-126">如果位於指定路徑的項目 （因此它有沒有父代） 的資料存放區的根目錄，則這個方法應傳回的根路徑。</span><span class="sxs-lookup"><span data-stu-id="910ba-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="910ba-127">實作 MakePath</span><span class="sxs-lookup"><span data-stu-id="910ba-127">Implementing MakePath</span></span>

<span data-ttu-id="910ba-128">[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法加入指定的父路徑和指定的子路徑來建立內部提供者的路徑 （如需路徑的相關資訊類型提供者可以支援，請參閱[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="910ba-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="910ba-129">PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910ba-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="910ba-130">實作 NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="910ba-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="910ba-131">[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會採用`path`和`basepath`參數，並傳回標準化的路徑相當於`path`參數，相對於`basepath`參數。</span><span class="sxs-lookup"><span data-stu-id="910ba-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="910ba-132">實作 MoveItem</span><span class="sxs-lookup"><span data-stu-id="910ba-132">Implementing MoveItem</span></span>

<span data-ttu-id="910ba-133">[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法從指定的路徑移動的項目至指定的目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="910ba-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="910ba-134">PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="910ba-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="910ba-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="910ba-135">See Also</span></span>

[<span data-ttu-id="910ba-136">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="910ba-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="910ba-137">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="910ba-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)