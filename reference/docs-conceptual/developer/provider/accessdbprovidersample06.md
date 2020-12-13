---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample06
description: AccessDBProviderSample06
ms.openlocfilehash: a2037c6f13ba24ba2dcb4ffecbd802566452d64e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92656923"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

這個範例會示範如何覆寫內容方法，以支援對 `Clear-Content` 、 `Get-Content` 和 Cmdlet 的呼叫 `Set-Content` 。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 此範例中的提供者類別衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別，它會實 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面，並將它實作為。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> - [System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。 請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。
> - [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。 請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。
> - [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。
>
> 如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。
- 定義一個衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別的提供者類別，以及宣告 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面的提供者類別（class）。
- 覆寫 [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法，以變更 Cmdlet 的行為 `Clear-Content` ，讓使用者可以從專案中移除內容。  (此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet。 ) 
- 覆寫 [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 方法，以變更 Cmdlet 的行為 `Get-Content` ，讓使用者可以取出專案的內容，。  (此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet。 ) 。
- 覆寫 [Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) 方法，以變更 Cmdlet 的行為 `Set-Content` ，讓使用者可以更新專案的內容。  (此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet。 ) 

## <a name="example"></a>範例

此範例示範如何覆寫在 Microsoft Access 資料基底中清除、取得和設定專案內容所需的方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>另請參閱

[System.management.automation.provider.itemCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[ContainerCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[>navigationCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
