---
title: AccessDBProviderSample01 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 50ec218e8d0fe6b2be5c8ac00956f72c6723f84a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786912"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

這個範例會示範如何宣告直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。 包含在此僅為完整性用途。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> - [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> - [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> - [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。

- 定義可直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。

## <a name="example"></a>範例

這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
