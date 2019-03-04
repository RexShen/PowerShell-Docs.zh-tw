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
ms.openlocfilehash: a789b392bddd344ad583c93a1a55302329df9917
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863534"
---
# <a name="writing-a-navigation-provider"></a>撰寫瀏覽提供者

本主題描述如何實作的 Windows PowerShell 提供者支援巢狀的容器 （多層級的資料存放區），移動項目和相對路徑的方法。 瀏覽提供者必須衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

本主題中的範例中的提供者會使用 Access 資料庫作為其資料存放區。 有幾個 helper 方法和類別，用來與資料庫互動。 完整的範例，其中包含協助程式方法，請參閱 < [AccessDBProviderSample05](./accessdbprovidersample05.md)。

如需有關 Windows PowerShell 提供者的詳細資訊，請參閱 < [Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。

## <a name="implementing-navigation-methods"></a>實作巡覽方法

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會實作方法，可支援巢狀的容器、 相對路徑，並將項目。 如需這些方法的完整清單，請參閱 < [NavigationCmdletProvider 方法](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx)。

> [!NOTE]
> 本主題中的資訊是根據[Windows PowerShell 提供者的快速入門](./windows-powershell-provider-quickstart.md)。 本主題並未涵蓋如何設定提供者專案的基本概念，或如何實作方法繼承自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，建立和移除磁碟機。 本主題也不會說明如何實作所公開的方法[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)或[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。 如需示範如何實作 item cmdlet 的範例，請參閱 <<c0> [ 撰寫項目提供者](./writing-an-item-provider.md)。 如需示範如何實作容器 cmdlet 的範例，請參閱 <<c0> [ 撰寫容器提供者](./writing-a-container-provider.md)。

### <a name="declaring-the-provider-class"></a>宣告提供者類別

宣告提供者衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它與裝飾[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>實作 IsItemContainer

[System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會檢查是否位於指定路徑的項目是容器。

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

### <a name="implementing-getchildname"></a>實作 GetChildName

[System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會取得位於指定路徑的子系項目的名稱屬性。 如果位於指定路徑的項目不是容器的子系，則這個方法應傳回路徑。

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

### <a name="implementing-getparentpath"></a>實作 GetParentPath

[System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會取得位於指定路徑之父代的項目路徑。 如果位於指定路徑的項目 （因此它有沒有父代） 的資料存放區的根目錄，則這個方法應傳回的根路徑。

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

### <a name="implementing-makepath"></a>實作 MakePath

[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法加入指定的父路徑和指定的子路徑來建立內部提供者的路徑 （如需路徑的相關資訊類型提供者可以支援，請參閱[Windows PowerShell 提供者概觀](./windows-powershell-provider-overview.md)。 PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.Powershell.Commands.Join 路徑](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path)cmdlet。

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

### <a name="implementing-normalizerelativepath"></a>實作 NormalizeRelativePath

[System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會採用`path`和`basepath`參數，並傳回標準化的路徑相當於`path`參數，相對於`basepath`參數。

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

### <a name="implementing-moveitem"></a>實作 MoveItem

[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法從指定的路徑移動的項目至指定的目的地路徑。 PowerShell 引擎會呼叫這個方法，當使用者呼叫[Microsoft.Powershell.Commands.Move 項目](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item)cmdlet。

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