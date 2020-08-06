---
title: AccessDBProviderSample05 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 67a10d9192350b339da1b82d9eb367ee4af6ef86
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786844"
---
# <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

這個範例示範如何覆寫容器方法來支援對 `Move-Item` 和 Cmdlet 的呼叫 `Join-Path` 。 當使用者需要移動容器內的項目，而且資料存放區包含巢狀容器時，就應該實作這些方法。 這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> - [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> - [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> - [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。

- 定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別。

- 覆寫[NavigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法來變更 Cmdlet 的行為 `Move-Item` ，讓使用者可以將專案從一個位置移到另一個位置。  (此範例不會示範如何將動態參數新增至 `Move-Item` Cmdlet。 ) 

- 覆寫[NavigationCmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法，以變更 Cmdlet 的行為 `Join-Path` 。

- 正在覆寫[NavigationCmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法。

- 正在覆寫[NavigationCmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法。

- 正在覆寫[NavigationCmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法。

- 正在覆寫[NavigationCmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法。

## <a name="example"></a>範例

這個範例會示範如何覆寫在 Microsoft Access 資料基底中移動專案所需的方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs" range="11-1960":::

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
