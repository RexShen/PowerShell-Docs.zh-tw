---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample02
description: AccessDBProviderSample02
ms.openlocfilehash: ebba2381370cf73f1e39015990f81dc4fd6dd937
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667431"
---
# <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

這個範例會示範如何覆寫 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 和 [DriveCmdletprovider... >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法，以支援對 `New-PSDrive` 和 Cmdlet 的呼叫 `Remove-PSDrive` 。 此範例中的提供者類別衍生自 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> - [System.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別（System）。 請參閱 [AccessDBProviderSample03](./accessdbprovidersample03.md)。
> - [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別（System）。 請參閱 [AccessDBProviderSample04](./accessdbprovidersample04.md)。
> - [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別（System）。 請參閱 [AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需根據提供者功能選擇要衍生自哪一個提供者類別的詳細資訊，請參閱 [設計您的 Windows PowerShell 提供者](./provider-types.md)。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。

- 定義提供者類別，該類別會驅動 [DriveCmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別的驅動程式。

- 覆寫 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 方法，以支援建立新的磁片磁碟機。  (此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet。 ) 

- 覆寫 [DriveCmdletprovider. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法，以支援移除現有的磁片磁碟機。

## <a name="example"></a>範例

這個範例會示範如何覆寫 [DriveCmdletprovider. >newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 和 [DriveCmdletprovider.. >removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 方法的覆寫。 針對此範例提供者，建立磁片磁碟機時，它的連接資訊會儲存在 `AccessDBPsDriveInfo` 物件中。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a>另請參閱

[System.management.automation.provider.itemCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[ContainerCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[>navigationCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
