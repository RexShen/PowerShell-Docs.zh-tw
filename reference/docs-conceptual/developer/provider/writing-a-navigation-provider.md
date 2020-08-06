---
title: 撰寫導覽提供者 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2fd27314a2b8547a15dd1bb72aa8f970d40b18cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786776"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="f1bcc-102">撰寫瀏覽提供者</span><span class="sxs-lookup"><span data-stu-id="f1bcc-102">Writing a navigation provider</span></span>

<span data-ttu-id="f1bcc-103">本主題描述如何執行 Windows PowerShell 提供者的方法，以支援 (多層級資料存放區的嵌套容器，) 、移動專案和相對路徑。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="f1bcc-104">導覽提供者必須是衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="f1bcc-105">本主題的範例中的提供者會使用 Access 資料庫作為其資料存放區。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="f1bcc-106">有數個 helper 方法和類別可用來與資料庫互動。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="f1bcc-107">如需包含 helper 方法的完整範例，請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="f1bcc-108">如需 Windows PowerShell 提供者的詳細資訊，請參閱[Windows Powershell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="f1bcc-109">執行導覽方法</span><span class="sxs-lookup"><span data-stu-id="f1bcc-109">Implementing navigation methods</span></span>

<span data-ttu-id="f1bcc-110">[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會實作為支援嵌套容器、相對路徑和移動專案的方法。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="f1bcc-111">如需這些方法的完整清單，請參閱[NavigationCmdletProvider 方法](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="f1bcc-112">本主題是以[Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)中的資訊為基礎。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="f1bcc-113">本主題未涵蓋如何設定提供者專案的基本概念，或如何執行繼承自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別的方法，以建立和移除磁片磁碟機。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="f1bcc-114">本主題也不會涵蓋如何執行[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)或[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別所公開的方法，而不會有任何說明。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="f1bcc-115">如需示範如何執行 item Cmdlet 的範例，請參閱[撰寫專案提供者](./writing-an-item-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="f1bcc-116">如需示範如何執行容器 Cmdlet 的範例，請參閱[撰寫容器提供者](./writing-a-container-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="f1bcc-117">宣告提供者類別</span><span class="sxs-lookup"><span data-stu-id="f1bcc-117">Declaring the provider class</span></span>

<span data-ttu-id="f1bcc-118">宣告提供者，以衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，並使用[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)來裝飾該服務的程式，並將其裝飾。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="f1bcc-119">執行 IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="f1bcc-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="f1bcc-120">[NavigationCmdletprovider. Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會檢查指定路徑中的專案是否為一個容器。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="f1bcc-121">執行 GetChildName</span><span class="sxs-lookup"><span data-stu-id="f1bcc-121">Implementing GetChildName</span></span>

<span data-ttu-id="f1bcc-122">[NavigationCmdletprovider. Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會取得位於指定路徑之子專案的 name 屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="f1bcc-123">如果指定路徑的專案不是容器的子系，則這個方法應該會傳回路徑。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="f1bcc-124">執行 GetParentPath</span><span class="sxs-lookup"><span data-stu-id="f1bcc-124">Implementing GetParentPath</span></span>

<span data-ttu-id="f1bcc-125">[NavigationCmdletprovider. Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會取得位於指定路徑的專案之父系的路徑（parent）。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="f1bcc-126">如果指定路徑的專案是資料存放區的根 (因此沒有父) ，則這個方法應該會傳回根路徑。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="f1bcc-127">執行 MakePath</span><span class="sxs-lookup"><span data-stu-id="f1bcc-127">Implementing MakePath</span></span>

<span data-ttu-id="f1bcc-128">[NavigationCmdletprovider. Makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法會聯結指定的父路徑和指定的子路徑，以建立提供者內部路徑 (如需提供者可支援之路徑類型的相關資訊，請參閱[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="f1bcc-129">當使用者呼叫[JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="f1bcc-130">執行 NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="f1bcc-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="f1bcc-131">[NavigationCmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會採用 `path` 和 `basepath` 參數，並傳回相當於參數的正規化路徑， `path` 以及與參數相對的 `basepath` 。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="f1bcc-132">執行 MoveItem</span><span class="sxs-lookup"><span data-stu-id="f1bcc-132">Implementing MoveItem</span></span>

<span data-ttu-id="f1bcc-133">[NavigationCmdletprovider. Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法會將專案從指定的路徑移動到指定的目的地路徑。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="f1bcc-134">當使用者呼叫[MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f1bcc-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f1bcc-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1bcc-135">See Also</span></span>

[<span data-ttu-id="f1bcc-136">撰寫容器提供者</span><span class="sxs-lookup"><span data-stu-id="f1bcc-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="f1bcc-137">Windows PowerShell 提供者概觀</span><span class="sxs-lookup"><span data-stu-id="f1bcc-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
