---
title: AccessDBProviderSample03 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f6de1397bc592cd1b59924a4425a5b17b290a8c8
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786878"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

這個範例會示範如何覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援對 `Get-Item` 和 Cmdlet 的呼叫，並提供。 `Set-Item` 這個範例中的提供者類別衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> - [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。
> - [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> - [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

本範例示範以下項目:

- 宣告 `CmdletProvider` 屬性。
- 定義一個衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的提供者類別。
- 覆寫[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法來變更 Cmdlet 的行為 `New-PSDrive` ，讓使用者能夠建立新的磁片磁碟機。
   (此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet。 ) 
- 覆寫[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援移除現有的磁片磁碟機。
- 覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法來變更 Cmdlet 的行為 `Get-Item` ，讓使用者可以從資料存放區抓取專案。  (此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet。 ) 
- 覆寫[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法以變更 Cmdlet 的行為 `Set-Item` ，讓使用者可以更新資料存放區中的專案。  (此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet。 ) 
- 覆寫[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以變更 Cmdlet 的行為 `Test-Path` 。  (此範例不會示範如何將動態參數新增至 `Test-Path` Cmdlet。 ) 
- 覆寫[ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以判斷提供的路徑是否有效。

## <a name="example"></a>範例

這個範例會示範如何覆寫在 Microsoft Access 資料基底中取得和設定專案所需的方法。

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs" range="11-976":::

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計 Windows PowerShell 提供者](./provider-types.md)
