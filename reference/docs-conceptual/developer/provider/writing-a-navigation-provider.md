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
# <a name="writing-a-navigation-provider"></a>撰寫瀏覽提供者

本主題說明如何執行 Windows PowerShell 提供者的方法，以支援 (多層級資料存放區) 、移動專案和相對路徑的嵌套容器。 流覽提供者必須衍生自 >navigationCmdletprovider 類別，才能使用此 [功能](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 。

本主題中的範例提供者使用 Access 資料庫作為其資料存放區。 有幾個 helper 方法和類別可用來與資料庫互動。 如需包含 helper 方法的完整範例，請參閱 [AccessDBProviderSample05](./accessdbprovidersample05.md)。

如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 [Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。

## <a name="implementing-navigation-methods"></a>執行流覽方法

[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會實作為支援嵌套容器、相對路徑和移動專案的方法。 如需這些方法的完整清單，請參閱 [>navigationCmdletprovider 方法](/dotnet/api/system.management.automation.provider.navigationcmdletprovider#methods)。

> [!NOTE]
> 本主題是以 [Windows PowerShell 提供者快速入門](./windows-powershell-provider-quickstart.md)中的資訊為基礎。 本主題並未涵蓋如何設定提供者專案的基本概念，或如何執行繼承自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別的方法，以建立和移除磁片磁碟機。 本主題也不會討論如何實 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 或 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別所公開的方法，以執行此項操作。 如需示範如何執行專案 Cmdlet 的範例，請參閱 [撰寫專案提供者](./writing-an-item-provider.md)。 如需示範如何執行容器 Cmdlet 的範例，請參閱 [撰寫容器提供者](./writing-a-container-provider.md)。

### <a name="declaring-the-provider-class"></a>宣告提供者類別

宣告提供者，以衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別，並使用 Cmdletproviderattribute 來裝飾該提供者的裝飾 [元件](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)。

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>執行 IsItemContainer

[>navigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會檢查位於指定路徑的專案是否為容器，。

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

### <a name="implementing-getchildname"></a>執行 GetChildName

[>navigationCmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會取得指定路徑之子專案的 name 屬性（property）。 如果指定路徑的專案不是容器的子系，則這個方法應該會傳回路徑。

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

### <a name="implementing-getparentpath"></a>執行 GetParentPath

[>navigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會取得位於指定路徑之專案的父代路徑（）。 如果指定路徑的專案是資料存放區的根目錄 (因此沒有父) ，則這個方法應該會傳回根路徑。

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

### <a name="implementing-makepath"></a>執行 MakePath

[>navigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法會聯結指定的父路徑和指定的子路徑來建立提供者內部路徑 (如需提供者可支援之路徑類型的詳細資訊，請參閱[Windows PowerShell 提供者總覽](./windows-powershell-provider-overview.md)。 當使用者呼叫 [JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。

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

### <a name="implementing-normalizerelativepath"></a>執行 NormalizeRelativePath

[>navigationCmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會採用 `path` 和 `basepath` 參數，並傳回相當於參數的正規化路徑 `path` 和參數的相對路徑 `basepath` 。

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

### <a name="implementing-moveitem"></a>執行 MoveItem

[>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法會將專案從指定的路徑移動到指定的目的地路徑。 當使用者呼叫 [MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) Cmdlet 時，PowerShell 引擎會呼叫這個方法。

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

## <a name="see-also"></a>另請參閱

[撰寫容器提供者](./writing-a-container-provider.md)

[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)
