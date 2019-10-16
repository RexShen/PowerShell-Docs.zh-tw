---
title: AccessDBProviderSample06 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: 9c00ec6de987729fec42dc57245a949d11e31f4b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366327"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

這個範例示範如何覆寫內容方法，以支援對 `Clear-Content`、`Get-Content` 和 @no__t 2 Cmdlet 的呼叫。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它會執行[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面（可能為例）。

## <a name="demonstrates"></a>演示

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> -   [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

這個範例會示範下列各項：

- 宣告 `CmdletProvider` 屬性。

- 定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別，並宣告[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的，並將其宣告為。

- 覆寫[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者可以從專案中移除該內容。 （此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet）。

- 覆寫[IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者能夠抓取專案的內容（content）。 （此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet）。

- 覆寫[Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更 @no__t 1 Cmdlet 的行為，讓使用者可以更新專案的內容。 （此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet）。

## <a name="example"></a>範例

這個範例會示範如何覆寫在 Microsoft Access 資料基底中清除、取得及設定專案內容所需的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)
