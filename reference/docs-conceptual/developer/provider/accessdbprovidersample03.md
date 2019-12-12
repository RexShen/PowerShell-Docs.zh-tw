---
title: AccessDBProviderSample03 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e576199-49c7-4355-9686-f9ed40c64a5f
caps.latest.revision: 10
ms.openlocfilehash: aa67bb605f90c1ea40323b4583766069ff1226fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359987"
---
# <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

這個範例會示範如何覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，以支援 `Get-Item` 和 `Set-Item` Cmdlet 的呼叫，並將其提供給。 這個範例中的提供者類別衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別。

## <a name="demonstrates"></a>示範

> [!IMPORTANT]
> 您的提供者類別很可能會衍生自下列其中一個類別，而且可能會執行其他提供者介面：
>
> -   [ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的功能。
> -   [ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample04](./accessdbprovidersample04.md)。
> -   [NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別的功能。 請參閱[AccessDBProviderSample05](./accessdbprovidersample05.md)。
>
> 如需有關根據提供者功能來選擇衍生自哪個提供者類別的詳細資訊，請參閱[設計您的 Windows PowerShell 提供者](./provider-types.md)。

這個範例示範下列作業：

- 宣告 `CmdletProvider` 屬性。

- 定義一個衍生自[ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別的提供者類別。

- 覆寫[DriveCmdletprovider. Newdrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)方法來變更 `New-PSDrive` Cmdlet 的行為，讓使用者能夠建立新的磁片磁碟機。 （此範例不會示範如何將動態參數新增至 `New-PSDrive` Cmdlet）。

- 覆寫[DriveCmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法，以支援移除現有的磁片磁碟機。

- 覆寫[ItemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法來變更 `Get-Item` Cmdlet 的行為，讓使用者可以從資料存放區抓取專案。 （此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet）。

- 覆寫[ItemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法來變更 `Set-Item` Cmdlet 的行為，讓使用者可以更新資料存放區中的專案。 （此範例不會示範如何將動態參數新增至 `Get-Item` Cmdlet）。

- 覆寫[ItemCmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)方法，以變更 `Test-Path` Cmdlet 的行為。 （此範例不會示範如何將動態參數新增至 `Test-Path` Cmdlet）。

- 覆寫[ItemCmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)方法，以判斷提供的路徑是否有效。

## <a name="example"></a>範例

這個範例會示範如何覆寫在 Microsoft Access 資料基底中取得和設定專案所需的方法。

[!code-csharp[AccessDBProviderSample03.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L976 "AccessDBProviderSample03.cs")]

## <a name="see-also"></a>另請參閱

[提供者： ItemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[提供者： ContainerCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[提供者： NavigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[設計您的 Windows PowerShell 提供者](./provider-types.md)
