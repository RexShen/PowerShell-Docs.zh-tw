---
ms.date: 09/13/2016
ms.topic: reference
title: 提供者範例
description: 提供者範例
ms.openlocfilehash: e6b1e8ce603092a3fd9dd44d7be428587544466b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651134"
---
# <a name="provider-samples"></a>提供者範例

本節包含存取 Microsoft Access 資料庫之提供者的範例。 這些範例包含衍生自所有基底提供者類別的提供者類別。

## <a name="in-this-section"></a>本節內容

本節包含下列主題：

[AccessDBProviderSample01 範例](./accessdbprovidersample01.md) 這個範例會示範如何宣告直接衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別的提供者類別。 包含在此僅為完整性用途。

[AccessDBProviderSample02](./accessdbprovidersample02.md) 這個範例會示範如何覆寫 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 和 [DriveCmdletprovider... >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法，以支援對 `New-PSDrive` 和 Cmdlet 的呼叫 `Remove-PSDrive` 。 此範例中的提供者類別衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別。

[AccessDBProviderSample03](./accessdbprovidersample03.md) 這個範例會示範如何覆寫 [system.management.automation.provider.itemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 和 [system.management.automation.provider.itemCmdletprovider... Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 方法，以支援對 `Get-Item` 和 Cmdlet 的呼叫 `Set-Item` 。 此範例中的提供者類別衍生自 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別。

[AccessDBProviderSample04](./accessdbprovidersample04.md) 這個範例會示範如何覆寫容器方法，以支援對 `Copy-Item` 、 `Get-ChildItem` 、 `New-Item` 和 `Remove-Item` Cmdlet 的呼叫。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 此範例中的提供者類別衍生自 [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別。

[AccessDBProviderSample05](./accessdbprovidersample05.md) 這個範例會示範如何覆寫容器方法，以支援對 `Move-Item` 和 `Join-Path` Cmdlet 的呼叫。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 此範例中的提供者類別衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別。

[AccessDBProviderSample06](./accessdbprovidersample06.md) 這個範例會示範如何覆寫內容方法，以支援對 `Clear-Content` 、 `Get-Content` 和 Cmdlet 的呼叫 `Set-Content` 。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 此範例中的提供者類別衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別，它會實 [IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面，並將它實作為。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)
