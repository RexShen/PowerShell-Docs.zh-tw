---
ms.date: 08/21/2019
ms.topic: reference
title: 提供者類型
description: 提供者類型
ms.openlocfilehash: 9d3b458d7647a297fcda086db3540a0c15c576db
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661752"
---
# <a name="provider-types"></a>提供者類型

提供者藉由變更 PowerShell 提供的提供者 Cmdlet 如何執行其動作，來定義其基本功能。 例如，提供者可以使用指令程式的預設功能 `Get-Item` ，也可以在從資料存放區中抓取專案時變更該 Cmdlet 的運作方式。 本檔中所述的提供者功能包含從特定提供者基類和介面覆寫方法所定義的功能。

> [!NOTE]
> 如需 PowerShell 預先定義的提供者功能，請參閱 [提供者功能](/previous-versions//ee126189(v=vs.85))。

## <a name="drive-enabled-providers"></a>啟用磁片磁碟機的提供者

啟用磁片磁碟機的提供者會指定使用者可用的預設磁片磁碟機，並允許使用者新增或移除磁片磁碟機。 在大部分的情況下，提供者是磁片磁碟機的提供者，因為它們需要一些預設磁片磁碟機來存取資料存放區。 不過，撰寫您自己的提供者時，您可能會想要允許使用者建立和移除磁片磁碟機。

若要建立已啟用磁片磁碟機的提供者，您的提供者類別必須衍生自 [DriveCmdletProvider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 類別或衍生自該類別的其他類別。 **DriveCmdletProvider** 類別會定義下列方法，以執行提供者的預設磁片磁碟機以及支援 `New-PSDrive` 和 `Remove-PSDrive` Cmdlet。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet （例如 `NewDrive` Cmdlet 的方法 `New-PSDrive` ），並選擇性地覆寫第二個方法（例如 `NewDriveDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [System.Management.Automation.Provider.DriveCmdletProvider.Ini的 tializeDefaultDrives](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法會定義每次使用提供者時，可供使用者使用的預設磁片磁碟機。

- [DriveCmdletProvider. >newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletProvider. NewDriveDynamicParameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法會定義您的提供者如何支援提供者指令程式的功能。 `New-PSDrive` 此 Cmdlet 可讓使用者建立磁片磁碟機來存取資料存放區。

- [DriveCmdletProvider. >removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法會定義提供者如何支援 `Remove-PSDrive` 提供者 Cmdlet。 此 Cmdlet 可讓使用者從資料存放區中移除磁片磁碟機。

## <a name="item-enabled-providers"></a>啟用專案的提供者

啟用專案的提供者可讓使用者取得、設定或清除資料存放區中的專案。 「專案」是使用者可以獨立存取或管理的資料存放區元素。 若要建立已啟用專案的提供者，您的提供者類別必須衍生自 [system.management.automation.provider.itemCmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 類別或衍生自該類別的其他類別。

**System.management.automation.provider.itemCmdletprovider** 類別會定義下列方法來執行特定的提供者 Cmdlet。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet （例如 `ClearItem` Cmdlet 的方法 `Clear-Item` ），並選擇性地覆寫第二個方法（例如 `ClearItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [System.management.automation.provider.itemCmdletprovider. ClearItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和[system.management.automation.provider.itemCmdletprovider.. ClearItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Clear-Item` 此 Cmdlet 可讓使用者移除資料存放區中專案的值。

- [System.management.automation.provider.itemCmdletprovider. GetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[system.management.automation.provider.itemCmdletprovider.. GetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Get-Item` 此 Cmdlet 可讓使用者從資料存放區中取出資料。

- [System.management.automation.provider.itemCmdletprovider. SetItem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和[system.management.automation.provider.itemCmdletprovider.. SetItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Set-Item` 此 Cmdlet 可讓使用者更新資料存放區中的專案值。

- [System.management.automation.provider.itemCmdletprovider. InvokeDefaultAction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和[system.management.automation.provider.itemCmdletprovider.. InvokeDefaultActionDynamicParameters](/dotnet/api/system.management.automation.provider.itemcmdletprovider.invokedefaultactiondynamicparameters)方法會定義提供者如何支援提供者指令程式的方式。 `Invoke-Item` 這個 Cmdlet 可讓使用者執行專案指定的預設動作。

- [System.management.automation.provider.itemCmdletprovider. ItemExists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和[system.management.automation.provider.itemCmdletprovider.. ItemExistsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Test-Path` 這個 Cmdlet 可讓使用者判斷路徑的所有元素是否都存在。

除了用來實作為提供者 Cmdlet 的方法之外， **system.management.automation.provider.itemCmdletprovider** 類別也會定義下列方法：

- [System.management.automation.provider.itemCmdletprovider. ExpandPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)方法可讓使用者在指定提供者路徑時使用萬用字元。

- [System.management.automation.provider.itemCmdletprovider. IsValidPath](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)是用來判斷路徑的語法是否正確，以及是否對提供者而言是語義有效。

## <a name="container-enabled-providers"></a>啟用容器的提供者

啟用容器的提供者可讓使用者管理容器的專案。 容器是常見父項目底下的一組子項目。 若要建立啟用容器的提供者，您的提供者類別必須衍生自 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 類別或衍生自該類別的其他類別。

> [!IMPORTANT]
> 啟用容器的提供者無法存取包含嵌套容器的資料存放區。 如果容器的子專案是另一個容器，則您必須執行具備流覽功能的提供者。

**ContainerCmdletProvider** 類別會定義下列方法來執行特定的提供者 Cmdlet。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet （例如 `CopyItem` Cmdlet 的方法 `Copy-Item` ），並選擇性地覆寫第二個方法（例如 `CopyItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和[ContainerCmdletProvider.. CopyItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Copy-Item` 這個 Cmdlet 可讓使用者將專案從某個位置複製到另一個位置。

- [ContainerCmdletProvider. GetChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)和[ContainerCmdletProvider.. GetChildItemsDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Get-ChildItem` 這個 Cmdlet 可讓使用者抓取父專案的子專案。

- [ContainerCmdletProvider. GetChildNames](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)和[ContainerCmdletProvider.. GetChildNamesDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法會定義您的提供者如何支援 `Get-ChildItem` 提供者 Cmdlet （如果 `Name` 指定了其參數的話）。

- [ContainerCmdletProvider. NewItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)和[ContainerCmdletProvider.. NewItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `New-Item` 此 Cmdlet 可讓使用者在資料存放區中建立新專案。

- [ContainerCmdletProvider. RemoveItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和[ContainerCmdletProvider.. RemoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Remove-Item` 此 Cmdlet 可讓使用者從資料存放區移除專案。

- [ContainerCmdletProvider. RenameItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和[ContainerCmdletProvider.. RenameItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Rename-Item` 此 Cmdlet 可讓使用者重新命名資料存放區中的專案。

除了用來實作為提供者 Cmdlet 的方法之外， **ContainerCmdletProvider** 類別也會定義下列方法：

- 提供者類別可使用 [ContainerCmdletProvider. HasChildItems](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 方法來判斷專案是否有子專案，而不是。

- 提供者類別可使用 [ContainerCmdletProvider. ConvertPath](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath) 方法，從指定的路徑建立新的提供者特定路徑。

## <a name="navigation-enabled-providers"></a>啟用導覽的提供者

啟用導覽的提供者可讓使用者在資料存放區中移動專案。 若要建立具備導覽功能的提供者，您的提供者類別必須衍生自 [>navigationCmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 類別。

**>navigationCmdletprovider** 類別會定義下列方法來執行特定的提供者 Cmdlet。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet （例如 `MoveItem` Cmdlet 的方法 `Move-Item` ），並選擇性地覆寫第二個方法（例如 `MoveItemDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [>navigationCmdletprovider. MoveItem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[>navigationCmdletprovider.. MoveItemDynamicParameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Move-Item` 這個 Cmdlet 可讓使用者將專案從存放區中的某個位置移到另一個位置。

- [>navigationCmdletprovider. MakePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法會定義提供者如何支援 `Join-Path` 提供者 Cmdlet。 此 Cmdlet 可讓使用者合併父系和子路徑區段，以建立提供者內部路徑。

除了用來實作為提供者 Cmdlet 的方法之外， **>navigationCmdletprovider** 類別也會定義下列方法：

- [>navigationCmdletprovider. GetChildName](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法會將路徑之子節點的名稱解壓縮出來。

- [>navigationCmdletprovider. GetParentPath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法會將路徑的父部分解壓縮出來。

- [>navigationCmdletprovider. IsItemContainer](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法會判斷該專案是否為容器專案。 在此內容中，容器是一般父專案下的子專案群組。

- [>navigationCmdletprovider. NormalizeRelativePath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法會傳回相對於所指定基底路徑之專案的路徑。

## <a name="content-enabled-providers"></a>啟用內容的提供者

啟用內容的提供者可讓使用者清除、取得或設定資料存放區中專案的內容。
例如，FileSystem 提供者可讓您清除、取得和設定檔案系統中的檔案內容。 若要建立啟用內容的提供者，您的提供者類別必須執行 [IContentCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) 介面的方法。

**IContentCmdletProvider** 介面會定義下列方法來執行特定的提供者 Cmdlet。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet （例如 `ClearContent` Cmdlet 的方法 `Clear-Content` ），並選擇性地覆寫第二個方法（例如 `ClearContentDynamicParameters` ），以將動態參數新增至 Cmdlet。

- [IContentCmdletProvider. ClearContent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[IContentCmdletProvider.. ClearContentDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Clear-Content` 這個 Cmdlet 可讓使用者在不刪除專案的情況下，刪除專案的內容。

- [IContentCmdletProvider. GetContentReader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[IContentCmdletProvider.. GetContentReaderDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Get-Content` 這個 Cmdlet 可讓使用者取得專案的內容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader`方法會傳回[IContentReader](/dotnet/api/System.Management.Automation.Provider.IContentReader)介面，此介面會定義用來讀取內容的方法。

- [IContentCmdletProvider. GetContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[IContentCmdletProvider.. GetContentWriterDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Set-Content` 這個 Cmdlet 可讓使用者更新專案的內容。 `System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter`方法會傳回[IContentWriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)介面，此介面會定義用來寫入內容的方法。

## <a name="property-enabled-providers"></a>啟用屬性的提供者

啟用屬性的提供者可讓使用者管理資料存放區中專案的屬性。
若要建立已啟用屬性的提供者，您的提供者類別必須執行 [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) 和 [IDynamicPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider) 介面的方法（provider）。 在大多數情況下，若要支援提供者 Cmdlet，您必須覆寫 PowerShell 引擎呼叫的方法來叫用 Cmdlet，例如 `ClearProperty` Clear-Property Cmdlet 的方法，並選擇性地覆寫第二個方法（例如），以 `ClearPropertyDynamicParameters` 將動態參數新增至 Cmdlet。

**IPropertyCmdletProvider** 介面會定義下列方法來執行特定的提供者 Cmdlet：

- [IPropertyCmdletProvider. ClearProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[IPropertyCmdletProvider.. ClearPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Clear-ItemProperty` 這個 Cmdlet 可讓使用者刪除屬性的值。

- [IPropertyCmdletProvider. GetProperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[IPropertyCmdletProvider.. GetPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Get-ItemProperty` 這個 Cmdlet 可讓使用者取得專案的屬性。

- [IPropertyCmdletProvider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和 SetPropertyDynamicParameters 方法會定義您的提供者如何支援提供者指令程式（Provider. [](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法） `Set-ItemProperty` 。 這個 Cmdlet 可讓使用者更新專案的屬性。

  **IDynamicPropertyCmdletProvider** 介面會定義下列方法來執行特定的提供者 Cmdlet：

- [IDynamicPropertyCmdletProvider. CopyProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[IDynamicPropertyCmdletProvider.. CopyPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Copy-ItemProperty` 這個 Cmdlet 可讓使用者將屬性和其值從一個位置複製到另一個位置。

- [IDynamicPropertyCmdletProvider. MoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[IDynamicPropertyCmdletProvider.. MovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `Move-ItemProperty` 這個 Cmdlet 可讓使用者將屬性和其值從一個位置移到另一個位置。

- [IDynamicPropertyCmdletProvider. NewProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[IDynamicPropertyCmdletProvider.. NewPropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法會定義提供者如何支援提供者指令程式的方式。 `New-ItemProperty` 這個 Cmdlet 可讓使用者建立新的屬性，並設定其值。

- [IDynamicPropertyCmdletProvider. RemoveProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[IDynamicPropertyCmdletProvider. RemovePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法會定義您的提供者如何支援此指令程式的 `Remove-ItemProperty` 功能。 這個 Cmdlet 可讓使用者刪除屬性及其值。

- [IDynamicPropertyCmdletProvider. RenameProperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[IDynamicPropertyCmdletProvider. RenamePropertyDynamicParameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法會定義您的提供者如何支援此指令程式的 `Rename-ItemProperty` 功能。 這個 Cmdlet 可讓使用者變更屬性的名稱。

## <a name="see-also"></a>請參閱

[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)
