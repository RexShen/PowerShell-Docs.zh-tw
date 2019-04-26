---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081116"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

此範例示範如何宣告直接衍生自提供者類別[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別。 包含在此僅為完整性用途。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別會很有可能是衍生自下列類別的其中一個，並且可能實作其他提供者介面：
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。 請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需有關選擇哪一個提供者類別衍生自基礎提供者功能，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./provider-types.md)。

此範例示範下列作業：

- 宣告`CmdletProvider`屬性。

- 定義提供者類別直接衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別。

## <a name="example"></a>範例

這個範例示範如何定義的提供者類別以及如何宣告`CmdletProvider`屬性。

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)