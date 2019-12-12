---
title: AccessDBProviderSample01 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359997"
---
# <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

這個範例會示範如何宣告直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。 包含在此僅為完整性用途。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> -   [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

這個範例示範下列作業：

- 宣告 `CmdletProvider` 屬性。

- 定義可直接衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別的提供者類別。

## <a name="example"></a>範例

這個範例會示範如何定義提供者類別，以及如何宣告 `CmdletProvider` 屬性。

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

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)