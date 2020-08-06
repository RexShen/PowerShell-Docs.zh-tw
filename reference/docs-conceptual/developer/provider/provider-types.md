---
title: 提供者類型 |Microsoft Docs
ms.date: 08/21/2019
ms.openlocfilehash: 03b6b2d02d603632399ea455c2832742e0964d62
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87778247"
---
# <a name="provider-types"></a>提供者類型

提供者會藉由變更 PowerShell 所提供的提供者 Cmdlet 來執行其動作，藉此定義其基本功能。 例如，提供者可以使用 Cmdlet 的預設功能 `Get-Item` ，也可以變更從資料存放區抓取專案時該 Cmdlet 的運作方式。 本檔中所述的提供者功能包含從特定提供者基類和介面覆寫方法所定義的功能。

> [!NOTE]
> 如需 PowerShell 預先定義的提供者功能，請參閱[提供者功能](/previous-versions//ee126189(v=vs.85))。

## <a name="drive-enabled-providers"></a>啟用磁片磁碟機的提供者

啟用磁片磁碟機的提供者會指定使用者可用的預設磁片磁碟機，並允許使用者新增或移除磁片磁碟機。 在大部分情況下，提供者都是已啟用磁片磁碟機的提供者，因為它們需要一些預設磁片磁碟機來存取資料存放區。 不過，撰寫自己的提供者時，您可能會想要允許使用者建立和移除磁片磁碟機。

若要建立已啟用磁片磁碟機的提供者，您的提供者類別必須衍生自[DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別，或衍生自該類別的另一個類別。 **DriveCmdletProvider**類別會定義下列方法，以執行提供者的預設磁片磁碟機，並支援 `New-PSDrive` 和 `Remove-PSDrive` Cmdlet。 在大部分情況下，若要支援 provider Cmdlet，您必須覆寫 PowerShell 引擎呼叫以叫用 Cmdlet 的方法（例如 `NewDrive` Cmdlet 的方法 `New-PSDrive` ），並選擇性地覆寫第二個方法（例如 `NewDriveDynamicParameters` ），以將動態參數新增至 Cmdlet。

- 當使用提供者時， [System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法會定義可供使用者使用的預設磁片磁碟機。

- [DriveCmdletProvider. NewDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法會定義您的提供者支援提供者指令程式的方式 `New-PSDrive` ：。 此 Cmdlet 可讓使用者建立磁片磁碟機來存取資料存放區。

- [DriveCmdletProvider. RemoveDrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法會定義提供者支援 `Remove-PSDrive` provider Cmdlet 的方式。 此 Cmdlet 可讓使用者從資料存放區移除磁片磁碟機。

## <a name="item-enabled-providers"></a>啟用專案的提供者

啟用專案的提供者可讓使用者取得、設定或清除資料存放區中的專案。 「專案」是資料存放區的元素，可供使用者獨立存取或管理。 若要建立啟用專案的提供者，您的提供者類別必須衍生自[ItemCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別，或衍生自該類別的另一個類別。

**ItemCmdletProvider**類別會定義用來執行特定提供者 Cmdlet 的下列方法。 在大部分情況下，若要支援 provider Cmdlet，您必須覆寫 PowerShell 引擎呼叫以叫用 Cmdlet 的方法（例如 `ClearItem` Cmdlet 的方法 `Clear-Item` ），並選擇性地覆寫第二個方法（例如 `ClearItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [ItemCmdletProvider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和[ItemCmdletProvider. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Clear-Item` 此 Cmdlet 可讓使用者移除資料存放區中某個專案的值。

- [ItemCmdletProvider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletProvider. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Get-Item` 此 Cmdlet 可讓使用者從資料存放區取出資料。

- [ItemCmdletProvider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和[ItemCmdletProvider. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Set-Item` 此 Cmdlet 可讓使用者更新資料存放區中的專案值。

- [ItemCmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和[ItemCmdletprovider. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Invoke-Item` 此 Cmdlet 可讓使用者執行專案所指定的預設動作。

- [ItemCmdletProvider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和[ItemCmdletProvider. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Test-Path` 此 Cmdlet 可讓使用者判斷路徑的所有元素是否都存在。

除了用來執行提供者 Cmdlet 的方法之外， **ItemCmdletProvider**類別也會定義下列方法：

- [ItemCmdletProvider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)方法可讓使用者在指定提供者路徑時使用萬用字元。

- [ItemCmdletProvider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)是用來判斷路徑是否在語法上，以及是否對提供者而言是有效的。

## <a name="container-enabled-providers"></a>啟用容器的提供者

啟用容器的提供者可讓使用者管理容器的專案。 容器是常見父項目底下的一組子項目。 若要建立啟用容器的提供者，您的提供者類別必須衍生自[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別，或衍生自該類別的另一個類別。

> [!IMPORTANT]
> 啟用容器的提供者無法存取包含嵌套容器的資料存放區。 如果容器的子專案是另一個容器，您必須執行具備導覽功能的提供者。

**ContainerCmdletProvider**類別會定義用來執行特定提供者 Cmdlet 的下列方法。 在大部分情況下，若要支援 provider Cmdlet，您必須覆寫 PowerShell 引擎呼叫以叫用 Cmdlet 的方法（例如 `CopyItem` Cmdlet 的方法 `Copy-Item` ），並選擇性地覆寫第二個方法（例如 `CopyItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和[ContainerCmdletProvider. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Copy-Item` 此 Cmdlet 可讓使用者將專案從一個位置複製到另一個位置。

- [ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)和[ContainerCmdletProvider. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Get-ChildItem` 此 Cmdlet 可讓使用者抓取父專案的子專案。

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法會定義您的提供者如何支援提供者 Cmdlet （如果已指定它的參數[），則](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) `Get-ChildItem` 會定義您的 provider。 `Name`

- [ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)和[ContainerCmdletProvider. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `New-Item` 此 Cmdlet 可讓使用者在資料存放區中建立新的專案。

- [ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和[ContainerCmdletProvider. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Remove-Item` 此 Cmdlet 可讓使用者從資料存放區移除專案。

- [ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和[ContainerCmdletProvider. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Rename-Item` 此 Cmdlet 可讓使用者重新命名資料存放區中的專案。

除了用來執行提供者 Cmdlet 的方法之外， **ContainerCmdletProvider**類別也會定義下列方法：

- 提供者類別可以使用[ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法，來判斷專案是否有子專案存在。

- 提供者類別可以使用[ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath)方法，從指定的路徑建立新的提供者特定路徑。

## <a name="navigation-enabled-providers"></a>具備導覽功能的提供者

啟用流覽功能的提供者可讓使用者移動資料存放區中的專案。 若要建立具備導覽功能的提供者，您的提供者類別必須衍生自[NavigationCmdletProvider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

**NavigationCmdletProvider**類別會定義用來執行特定提供者 Cmdlet 的下列方法。 在大部分情況下，若要支援 provider Cmdlet，您必須覆寫 PowerShell 引擎呼叫以叫用 Cmdlet 的方法（例如 `MoveItem` Cmdlet 的方法 `Move-Item` ），並選擇性地覆寫第二個方法（例如 `MoveItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [NavigationCmdletProvider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[NavigationCmdletProvider. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Move-Item` 此 Cmdlet 可讓使用者將專案從存放區中的一個位置移到另一個位置。

- [NavigationCmdletProvider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法會定義提供者支援 `Join-Path` provider Cmdlet 的方式。 此 Cmdlet 可讓使用者結合父系和子路徑區段，以建立提供者內部路徑。

除了用來執行提供者 Cmdlet 的方法之外， **NavigationCmdletProvider**類別也會定義下列方法：

- [NavigationCmdletProvider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會將路徑的子節點的名稱解壓縮出來。

- [NavigationCmdletProvider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會將路徑的父系部分解壓縮出來。

- [NavigationCmdletProvider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會判斷此專案是否為容器專案。 在此內容中，容器是通用父專案底下的子專案群組。

- [NavigationCmdletProvider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會傳回相對於指定之基底路徑之專案的路徑。

## <a name="content-enabled-providers"></a>啟用內容的提供者

啟用內容的提供者可讓使用者清除、取得或設定資料存放區中的專案內容。
例如，FileSystem 提供者可讓您清除、取得及設定檔案系統中的檔案內容。 若要建立啟用內容的提供者，您的提供者類別必須執行[IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面的方法。

**IContentCmdletProvider**介面會定義用來執行特定提供者 Cmdlet 的下列方法。 在大部分情況下，若要支援 provider Cmdlet，您必須覆寫 PowerShell 引擎呼叫以叫用 Cmdlet 的方法（例如 `ClearContent` Cmdlet 的方法 `Clear-Content` ），並選擇性地覆寫第二個方法（例如 `ClearContentDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[IContentCmdletProvider. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Clear-Content` 此 Cmdlet 可讓使用者刪除專案的內容，而不需刪除專案。

- [IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[IContentCmdletProvider. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Get-Content` 此 Cmdlet 可讓使用者取得專案的內容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`方法會傳回[IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader)介面，以定義用來讀取內容的方法。

- [IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[IContentCmdletProvider. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Set-Content` 此 Cmdlet 可讓使用者更新專案的內容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`方法會傳回[IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)介面，其定義用來寫入內容的方法。

## <a name="property-enabled-providers"></a>啟用屬性的提供者

啟用屬性的提供者可讓使用者管理資料存放區中專案的屬性。
若要建立已啟用屬性的提供者，您的提供者類別必須實[IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)和[IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)介面的方法，才能執行。 在大部分情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法，以叫用 Cmdlet，例如 `ClearProperty` 清除屬性 Cmdlet 的方法，並選擇性地覆寫第二個方法（例如 `ClearPropertyDynamicParameters` ），以將動態參數新增至 Cmdlet。

**IPropertyCmdletProvider**介面會定義用來執行特定提供者 Cmdlet 的下列方法：

- [IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[IPropertyCmdletProvider. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Clear-ItemProperty` 此 Cmdlet 可讓使用者刪除屬性的值。

- [IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[IPropertyCmdletProvider. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Get-ItemProperty` 此 Cmdlet 可讓使用者取得專案的屬性。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[IPropertyCmdletProvider. SetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者指令程式。 `Set-ItemProperty` 此 Cmdlet 可讓使用者更新專案的屬性。

  **IDynamicPropertyCmdletProvider**介面會定義用來執行特定提供者 Cmdlet 的下列方法：

- [IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[IDynamicPropertyCmdletProvider. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Copy-ItemProperty` 此 Cmdlet 可讓使用者將屬性和其值從一個位置複製到另一個位置。

- [IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[IDynamicPropertyCmdletProvider. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `Move-ItemProperty` 此 Cmdlet 可讓使用者將屬性和其值從一個位置移到另一個位置。

- [IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[IDynamicPropertyCmdletProvider. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法會定義您的提供者如何支援 provider 指令程式的提供者。 `New-ItemProperty` 此 Cmdlet 可讓使用者建立新的屬性，並設定其值。

- [IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法會定義您的提供者支援此 Cmdlet 的方式。（） `Remove-ItemProperty` 此 Cmdlet 可讓使用者刪除屬性及其值。

- [IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法會定義您的提供者支援此 Cmdlet 的方式。（） `Rename-ItemProperty` 此 Cmdlet 可讓使用者變更屬性的名稱。

## <a name="see-also"></a>另請參閱

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)
