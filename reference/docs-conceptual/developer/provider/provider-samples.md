---
title: 提供者範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4933dad-fec9-4337-a1a9-9dc16ee87cc3
caps.latest.revision: 9
ms.openlocfilehash: 1e7aeb5bcb6bd5a2845648c3327e2245e6c428ba
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366297"
---
# <a name="provider-samples"></a>提供者範例

本節包含存取 Microsoft Access 資料庫之提供者的範例。 這些範例包括衍生自所有基底提供者類別的提供者類別。

## <a name="in-this-section"></a>在本節中

本節包含下列主題：

[AccessDBProviderSample01 範例](./accessdbprovidersample01.md)這個範例會示範如何宣告直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。 包含在此僅為完整性用途。

[AccessDBProviderSample02](./accessdbprovidersample02.md)這個範例會示範如何覆寫[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援 `New-PSDrive` 和 `Remove-PSDrive` Cmdlet 的呼叫，並將其提供給。 這個範例中的提供者類別衍生自[DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。

[AccessDBProviderSample03](./accessdbprovidersample03.md)這個範例會示範如何覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援 `Get-Item` 和 `Set-Item` Cmdlet 的呼叫，並將其提供給。 這個範例中的提供者類別衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。

[AccessDBProviderSample04](./accessdbprovidersample04.md)這個範例示範如何覆寫容器方法，以支援對 `Copy-Item`、`Get-ChildItem`、`New-Item`和 `Remove-Item` Cmdlet 的呼叫。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 這個範例中的提供者類別衍生自[ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。

[AccessDBProviderSample05](./accessdbprovidersample05.md)這個範例示範如何覆寫容器方法，以支援對 `Move-Item` 和 `Join-Path` Cmdlet 的呼叫。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

[AccessDBProviderSample06](./accessdbprovidersample06.md)這個範例示範如何覆寫內容方法，以支援對 `Clear-Content`、`Get-Content`和 `Set-Content` Cmdlet 的呼叫。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它會執行[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面（可能為例）。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)