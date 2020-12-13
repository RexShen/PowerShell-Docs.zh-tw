---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample04
description: AccessDBProviderSample04
ms.openlocfilehash: 962d0ab673ff797a60b56ccae7a16a810cc43c58
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649050"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

這個範例會示範如何覆寫容器方法，以支援對 `Copy-Item` 、 `Get-ChildItem` 、 `New-Item` 和 `Remove-Item` Cmdlet 的呼叫。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 此範例中的提供者類別衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自[>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。
- 定義一個衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別的提供者類別。
- 覆寫 [ContainerCmdletProvider CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法來變更 Cmdlet 的行為， `Copy-Item` 讓使用者可以將專案從一個位置複製到另一個位置。  (此範例不會示範如何將動態參數新增至 `Copy-Item` Cmdlet。 ) 
- 覆寫 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 方法，以變更 Get-ChildItems Cmdlet 的行為，讓使用者能夠取得父項目的子專案，而不需要。  (此範例不會示範如何將動態參數新增至 Get-ChildItems Cmdlet。 ) 
- 當指定 Cmdlet 的參數時，覆寫 [ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法，以變更 Get-ChildItems Cmdlet 的行為 `Name` 。
- 覆寫 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法來變更 Cmdlet 的行為 `New-Item` ，讓使用者能夠將專案新增至資料存放區。  (此範例不會示範如何將動態參數新增至 `New-Item` Cmdlet。 ) 
- 覆寫 [ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法，以變更 Cmdlet 的行為 `Remove-Item` 。  (此範例不會示範如何將動態參數新增至 `Remove-Item` Cmdlet。 ) 

## <a name="example"></a>範例

這個範例會示範如何覆寫複製、建立和移除專案所需的方法，以及用來取得父專案子專案的方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="11-1635":::

## <a name="see-also"></a>另請參閱

[System.management.automation.provider.itemCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[ContainerCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[>navigationCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
