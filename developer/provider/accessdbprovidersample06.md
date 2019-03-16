---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055541"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

此範例示範如何覆寫內容方法，以支援呼叫`Clear-Content`， `Get-Content`，和`Set-Content`cmdlet。 當使用者需要管理資料存放區的項目內容時，就應該實作這些方法。 在此範例中的提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，而且會實作[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別會很有可能是衍生自下列類別的其中一個，並且可能實作其他提供者介面：
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。 請參閱[AccessDBProviderSample03](./accessdbprovidersample03.md)。
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。
>
> 如需有關選擇哪一個提供者類別衍生自基礎提供者功能，請參閱 <<c0> [ 設計您的 Windows PowerShell 提供者](./provider-types.md)。

此範例示範下列作業：

- 宣告`CmdletProvider`屬性。

- 定義提供者類別衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別，宣告[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。

- 覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，以變更的行為`Clear-Content`cmdlet，可讓使用者從項目移除內容。 (此範例不會顯示如何加入動態參數，以便`Clear-Content`指令程式。)

- 覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，以變更的行為`Get-Content`cmdlet，讓使用者能夠擷取內容的項目。 (此範例不會顯示如何加入動態參數，以便`Get-Content`指令程式。)。

- 覆寫[Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter)方法，以變更的行為`Set-Content`cmdlet，可讓使用者更新的項目內容。 (此範例不會顯示如何加入動態參數，以便`Set-Content`指令程式。)

## <a name="example"></a>範例

此範例示範如何覆寫清除、 取得及設定 Microsoft Access 資料中的項目內容的基底所需的方法。

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>另請參閱

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)