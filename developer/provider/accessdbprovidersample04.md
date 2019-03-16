---
title: AccessDBProviderSample04 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3a7e56-7331-4f71-9ecb-7a59b8021c68
caps.latest.revision: 10
ms.openlocfilehash: d9109e8d5b69a25ad52b90bcaff9628b01067211
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057615"
---
# <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

此範例示範如何覆寫容器方法，以支援呼叫`Copy-Item`， `Get-ChildItem`， `New-Item`，和`Remove-Item`cmdlet。 當資料存放區包含容器項目時，就應該實作這些方法。 容器是常見父項目底下的一組子項目。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

此範例示範下列作業：

- 宣告`CmdletProvider`屬性。

- 定義提供者類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。

- 覆寫[System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，以變更的行為`Copy-Item`cmdlet 可讓使用者從一個位置的項目複製到另一個。 (此範例不會顯示如何加入動態參數，以便`Copy-Item`指令程式。)

- 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)方法來取得 ChildItems cmdlet，可讓使用者擷取父項目的子項目的行為變更. （此範例不會顯示如何將動態參數新增至 Get ChildItems cmdlet）。

- 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，以變更 Get ChildItems cmdlet 的行為時`Name`指定此 cmdlet 的參數。

- 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，以變更的行為`New-Item`cmdlet，可讓使用者將項目加入至資料存放區。 (此範例不會顯示如何加入動態參數，以便`New-Item`指令程式。)

- 覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，以變更的行為`Remove-Item`cmdlet。 (此範例不會顯示如何加入動態參數，以便`Remove-Item`指令程式。)

## <a name="example"></a>範例

此範例示範如何覆寫來複製、 建立和移除項目，以及方法讓子系的父項目的項目所需的方法。

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)