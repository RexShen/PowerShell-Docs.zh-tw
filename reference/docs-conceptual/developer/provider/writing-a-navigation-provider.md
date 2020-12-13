---
ms.date: 09/13/2016
ms.topic: reference
title: 撰寫瀏覽提供者
description: 撰寫瀏覽提供者
ms.openlocfilehash: 3123672d3365c97714557bd0e72a6e444ac228a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355216"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="636b9-103">撰寫瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="636b9-103">Writing a navigation provider</span></span>

<span data-ttu-id="636b9-104">本主題說明如何執行 Windows PowerShell 提供者的方法，以支援 (多層級資料存放區) 、移動專案和相對路徑的嵌套容器。</span><span class="sxs-lookup"><span data-stu-id="636b9-104">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="636b9-105">流覽提供者必須衍生自 >navigationCmdletprovider 類別，才能使用此 [功能](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 。</span><span class="sxs-lookup"><span data-stu-id="636b9-105">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="636b9-106">本主題中的範例提供者使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="636b9-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="636b9-107">有幾個 helper 方法和類別可用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="636b9-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="636b9-108">如需包含 helper 方法的完整範例，請參閱 [AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="636b9-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="636b9-109">如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 [Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="636b9-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="636b9-110">執行流覽方法</span><span class="sxs-lookup"><span data-stu-id="636b9-110">Implementing navigation methods</span></span>

<span data-ttu-id="636b9-111">[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會實作為支援嵌套容器、相對路徑和移動專案的方法。</span><span class="sxs-lookup"><span data-stu-id="636b9-111">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="636b9-112">如需這些方法的完整清單，請參閱 [>navigationCmdletprovider 方法](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods)。</span><span class="sxs-lookup"><span data-stu-id="636b9-112">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="636b9-113">本主題是以 [Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)中的資訊為基礎。</span><span class="sxs-lookup"><span data-stu-id="636b9-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="636b9-114">本主題並未涵蓋如何設定提供者專案的基本概念，或如何執行繼承自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別的方法，以建立和移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="636b9-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="636b9-115">本主題也不會討論如何實 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 或 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別所公開的方法，以執行此項操作。</span><span class="sxs-lookup"><span data-stu-id="636b9-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="636b9-116">如需示範如何執行專案 Cmdlet 的範例，請參閱 [撰寫專案提供者](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="636b9-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="636b9-117">如需示範如何執行容器 Cmdlet 的範例，請參閱 [撰寫容器提供者](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="636b9-117">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="636b9-118">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="636b9-118">Declaring the provider class</span></span>

<span data-ttu-id="636b9-119">宣告提供者，以衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別，並使用 Cmdletproviderattribute 來裝飾該提供者的裝飾 [元件](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)。</span><span class="sxs-lookup"><span data-stu-id="636b9-119">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="636b9-120">執行 IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="636b9-120">Implementing IsItemContainer</span></span>

<span data-ttu-id="636b9-121">[>navigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會檢查位於指定路徑的專案是否為容器，。</span><span class="sxs-lookup"><span data-stu-id="636b9-121">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="636b9-122">執行 GetChildName</span><span class="sxs-lookup"><span data-stu-id="636b9-122">Implementing GetChildName</span></span>

<span data-ttu-id="636b9-123">[>navigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會取得指定路徑之子專案的 name 屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="636b9-123">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="636b9-124">如果指定路徑的專案不是容器的子系，則這個方法應該會傳回路徑。</span><span class="sxs-lookup"><span data-stu-id="636b9-124">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="636b9-125">執行 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="636b9-125">Implementing GetParentPath</span></span>

<span data-ttu-id="636b9-126">[>navigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會取得位於指定路徑之專案的父代路徑（）。</span><span class="sxs-lookup"><span data-stu-id="636b9-126">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="636b9-127">如果指定路徑的專案是資料存放區的根目錄 (因此沒有父) ，則這個方法應該會傳回根路徑。</span><span class="sxs-lookup"><span data-stu-id="636b9-127">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="636b9-128">執行 MakePath</span><span class="sxs-lookup"><span data-stu-id="636b9-128">Implementing MakePath</span></span>

<span data-ttu-id="636b9-129">[>navigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法會聯結指定的父路徑和指定的子路徑來建立提供者內部路徑 (如需提供者可支援之路徑類型的詳細資訊，請參閱[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="636b9-129">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="636b9-130">當使用者呼叫 [JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="636b9-130">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="636b9-131">執行 NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="636b9-131">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="636b9-132">[>navigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會採用 `path` 和 `basepath` 參數，並傳回相當於參數的正規化路徑 `path` 和參數的相對路徑 `basepath` 。</span><span class="sxs-lookup"><span data-stu-id="636b9-132">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="636b9-133">執行 MoveItem</span><span class="sxs-lookup"><span data-stu-id="636b9-133">Implementing MoveItem</span></span>

<span data-ttu-id="636b9-134">[>navigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法會將專案從指定的路徑移動到指定的目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="636b9-134">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="636b9-135">當使用者呼叫 [MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="636b9-135">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="636b9-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="636b9-136">See Also</span></span>

[<span data-ttu-id="636b9-137">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="636b9-137">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="636b9-138">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="636b9-138">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
