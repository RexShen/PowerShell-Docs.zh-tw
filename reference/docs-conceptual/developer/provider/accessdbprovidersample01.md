---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDBProviderSample01
description: AccessDBProviderSample01
ms.openlocfilehash: 8bdfa3ad492935a22ce06846294c02961cab2c65
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653755"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

這個範例會示範如何宣告直接衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別的提供者類別。 包含在此僅為完整性用途。

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

- 定義可直接衍生自 [Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) 類別的提供者類別。

## <a name="example"></a>範例

這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>另請參閱

[System.management.automation.provider.itemCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[ContainerCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[>navigationCmdletprovider （系統管理）](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
