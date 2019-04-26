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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080929"
---
# <a name="provider-samples"></a>提供者範例

本節包含可存取 Microsoft Access 資料庫提供者的範例。 這些範例包含提供者類別衍生自基底提供者的所有類別。

## <a name="in-this-section"></a>在本節中

本節包含下列主題：

[範例 AccessDBProviderSample01](./accessdbprovidersample01.md)這個範例示範如何宣告直接衍生自提供者類別[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別。 包含在此僅為完整性用途。

[AccessDBProviderSample02](./accessdbprovidersample02.md)這個範例示範如何覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援呼叫`New-PSDrive`和`Remove-PSDrive`cmdlet。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別。

[AccessDBProviderSample03](./accessdbprovidersample03.md)這個範例示範如何覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援呼叫`Get-Item`和`Set-Item`cmdlet。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。

[AccessDBProviderSample04](./accessdbprovidersample04.md)這個範例示範如何覆寫容器方法，以支援呼叫`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。

[AccessDBProviderSample05](./accessdbprovidersample05.md)這個範例示範如何覆寫容器方法，以支援呼叫`Move-Item`和`Join-Path`cmdlet。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

[AccessDBProviderSample06](./accessdbprovidersample06.md)這個範例示範如何覆寫內容方法，以支援呼叫`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且會實作[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)