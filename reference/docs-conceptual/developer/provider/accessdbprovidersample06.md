---
title: AccessDBProviderSample06 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 893eb80574c7f142f92906961588e22b1ced0052
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786827"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

這個範例示範如何覆寫內容方法，以支援對 `Clear-Content` 、 `Get-Content` 和 Cmdlet 的呼叫 `Set-Content` 。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 這個範例中的提供者類別衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且它會執行[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面（可能為例）。

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
- 定義一個衍生自[NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的提供者類別，並宣告[IcontentCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的，並將其宣告為。
- 覆寫[IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更 Cmdlet 的行為 `Clear-Content` ，讓使用者可以從專案中移除內容。  (此範例不會示範如何將動態參數新增至 `Clear-Content` Cmdlet。 ) 
- 覆寫[IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更 Cmdlet 的行為 `Get-Content` ，讓使用者能夠抓取專案的內容（content）。  (此範例不會示範如何將動態參數新增至 `Get-Content` Cmdlet。 ) 。
- 覆寫[Filesystemprovider. Getcontentwriter *](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更 Cmdlet 的行為 `Set-Content` ，讓使用者可以更新專案的內容。  (此範例不會示範如何將動態參數新增至 `Set-Content` Cmdlet。 ) 

## <a name="example"></a>範例

這個範例會示範如何覆寫在 Microsoft Access 資料基底中清除、取得及設定專案內容所需的方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
