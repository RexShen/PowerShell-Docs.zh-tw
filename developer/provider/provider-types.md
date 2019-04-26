---
title: 提供者類型 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e523a8e1-42e4-4633-887f-fb74b3464561
caps.latest.revision: 12
ms.openlocfilehash: 37689571eb1650e5991af2e7002cd037ae99dd68
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080898"
---
# <a name="provider-types"></a>提供者類型

提供者會定義其基本功能，藉由變更提供者 cmdlet （由 Windows PowerShell） 執行其動作的方式。 例如，提供者可以使用的預設功能`Get-Item`cmdlet，或它們可能會變更從資料存放區擷取項目時，該 cmdlet 的運作方式。 本主題中所述的提供者功能包含藉由覆寫來自特定提供者的基底類別和介面的方法定義的功能。

> [!NOTE]
> 如需預先定義的 Windows PowerShell 提供者功能，請參閱[提供者功能](http://msdn.microsoft.com/en-us/864e4807-554a-4016-80ea-bf643a090fc6)。

## <a name="drive-enabled-providers"></a>啟用磁碟機的提供者

啟用磁碟機的提供者指定的預設磁碟機提供給使用者，並允許使用者加入或移除磁碟機。 在大部分情況下，提供者會是磁碟機啟用提供者，因為它們需要一些預設的磁碟機來存取資料存放區。 不過，在撰寫自己的提供者可能會或可能不想要允許使用者建立和移除磁碟機。

若要建立的磁碟機啟用提供者，您的提供者類別必須衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別或衍生自該類別的另一個類別。 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別會定義下列方法，實作提供者的預設磁碟機，並支援`New-PSDrive`和`Remove-PSDrive`cmdlet。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`NewDrive`方法`New-PSDrive`指令程式，而且 （選擇性） 您可以覆寫第二個方法，例如`NewDriveDynamicParameters`，將動態參數新增至 cmdlet。

- [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives)方法定義是可供使用者使用提供者時的預設磁碟機。

- [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)並[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法定義您的提供者如何支援`New-PSDrive`提供者 cmdlet。 此 cmdlet 可讓使用者建立存取資料存放區的磁碟機。

- [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法來定義您的提供者如何支援`Remove-PSDrive`提供者 cmdlet。 此 cmdlet 可讓使用者從資料存放區移除磁碟機。

## <a name="item-enabled-providers"></a>項目啟用的提供者

項目啟用的提供者可讓使用者取得、 設定或清除資料存放區中的項目。 「 項目 」 是使用者可以存取或獨立管理的資料存放區的項目。 若要建立的項目啟用的提供者，您的提供者類別必須衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別或衍生自該類別的另一個類別。

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別會定義下列方法來實作特定的提供者 cmdlet。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`ClearItem`方法`Clear-Item`指令程式，而且 （選擇性） 您可以覆寫第二個方法，例如`ClearItemDynamicParameters`，將動態參數新增至 cmdlet。

- [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)並[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法定義您的提供者如何支援`Clear-Item`提供者 cmdlet。 此 cmdlet 可讓使用者移除值的資料存放區中的項目。

- [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)並[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法會定義如何您的提供者支援`Get-Item`提供者 cmdlet。 此 cmdlet 可讓使用者從資料存放區擷取資料。

- [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)並[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法會定義如何您的提供者支援`Set-Item`提供者 cmdlet。 此 cmdlet 可讓使用者更新資料存放區中的項目值。

- [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)並[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法定義您的提供者如何支援`Invoke-Item`提供者 cmdlet。 此 cmdlet 可讓使用者執行項目所指定的預設動作。

- [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)並[System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法定義您的提供者如何支援`Test-Path`提供者 cmdlet。 此 cmdlet 可讓使用者判斷路徑中的所有元素是否都存在。

  用來實作提供者 cmdlet 的方法除了[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別也會定義下列方法：

- [System.Management.Automation.Provider.Itemcmdletprovider.Expandpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ExpandPath)方法可讓使用者指定的提供者路徑時，使用萬用字元。

- [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath)用來判斷路徑是否為語法和語意有效的提供者。

## <a name="container-enabled-providers"></a>容器功能的提供者

容器功能的提供者可讓使用者管理是容器的項目。 容器是常見父項目底下的一組子項目。 若要建立容器功能的提供者，您的提供者類別必須衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別或衍生自該類別的另一個類別。

> [!IMPORTANT]
> 容器功能的提供者無法存取包含巢狀的容器的資料存放區。 如果容器的子系項目是另一個容器，您必須實作導覽功能的提供者。

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別會定義下列方法來實作特定的提供者 cmdlet。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`CopyItem`方法`Copy-Item`指令程式，而且 （選擇性） 您可以覆寫第二個方法，例如`CopyItemDynamicParameters`，將動態參數新增至 cmdlet。

- [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)並[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法可讓您定義您的提供者如何支援`Copy-Item`提供者 cmdlet。 此 cmdlet 可讓使用者將項目從一個位置複製到另一個。

- [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)和[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)方法可讓您定義您的提供者如何支援`Get-ChildItem`提供者 cmdlet。 此 cmdlet 可讓使用者擷取父項目的子項目。

- [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)和[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法可讓您定義您的提供者支援的方式`Get-ChildItem`提供者 cmdlet 如果其`Name`指定參數。

- [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)並[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法可讓您定義您的提供者如何支援`New-Item`提供者 cmdlet。 此 cmdlet 可讓使用者在資料存放區中建立新的項目。

- [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)並[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法可讓您定義您的提供者如何支援`Remove-Item`提供者 cmdlet。 此 cmdlet 可讓使用者從資料存放區中移除項目。

- [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)並[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法可讓您定義您的提供者如何支援`Rename-Item`提供者 cmdlet。 此 cmdlet 可讓使用者重新命名資料存放區中的項目。

  用來實作提供者 cmdlet 的方法除了[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別也會定義下列方法：

- [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems)方法可以由提供者類別用來判斷項目是否具有子項目。

- [System.Management.Automation.Provider.Containercmdletprovider.Convertpath*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.ConvertPath)方法可以由提供者類別用來從指定的路徑建立新的提供者特定路徑。

## <a name="navigation-enabled-providers"></a>瀏覽啟用提供者

瀏覽啟用提供者允許使用者在資料存放區中移動項目。 若要建立導覽功能的提供者，您的提供者類別必須衍生自[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別。

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會定義下列方法來實作特定的提供者 cmdlet。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`MoveItem`方法`Move-Item`指令程式，而且 （選擇性） 您可以覆寫第二個方法，例如`MoveItemDynamicParameters`，將動態參數新增至 cmdlet。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)並[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法可讓您定義您的提供者如何支援`Move-Item`提供者 cmdlet。 此 cmdlet 可讓使用者將項目從存放區中的一個位置移到另一個位置。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法來定義您的提供者如何支援`Join-Path`提供者 cmdlet。 此 cmdlet 可讓使用者結合父系和子系的路徑區段，來建立提供者內部路徑。

  用來實作提供者 cmdlet 的方法除了[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別也會定義下列方法：

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName)方法擷取路徑的子節點的名稱。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath)方法擷取路徑的父組件。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer)方法可讓您判斷項目是否為容器項目。 在此情況下，容器是常見的父項目底下子項目群組。

- [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath)方法傳回的路徑是相對於指定的基底路徑的項目。

## <a name="content-enabled-providers"></a>啟用內容的提供者

啟用內容的提供者允許清除、 取得或設定資料存放區中的項目內容的使用者。 例如，FileSystem 提供者可讓您清除、 取得及設定檔案系統中的檔案的內容。 若要建立內容啟用的提供者，您的提供者類別必須實作的方法[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面。

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面會定義下列方法來實作特定的提供者 cmdlet。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`ClearContent`方法`Clear-Content`指令程式，而且 （選擇性） 您可以覆寫第二個方法，例如`ClearContentDynamicParameters`，將動態參數新增至 cmdlet。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法可讓您定義您的提供者如何支援`Clear-Content`提供者 cmdlet。 此 cmdlet 可讓使用者刪除的項目內容，而不會刪除項目。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法可讓您定義您的提供者如何支援`Get-Content`提供者 cmdlet。 此 cmdlet 可讓使用者擷取項目的內容。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法會傳回[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)定義的介面用來讀取內容的方法。

- [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法可讓您定義您的提供者如何支援`Set-Content`提供者 cmdlet。 此 cmdlet 可讓使用者更新的項目內容。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法會傳回[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)定義的介面用來寫入內容的方法。

## <a name="property-enabled-providers"></a>啟用屬性的提供者

啟用屬性的提供者可讓使用者管理的資料存放區中的項目屬性。 若要建立屬性啟用的提供者，您的提供者類別必須實作的方法[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)介面。 在大部分情況下，以支援提供者 cmdlet 您必須覆寫的方法，則 Windows PowerShell 引擎呼叫來叫用 cmdlet，例如`ClearProperty`清除屬性的指令程式，並選擇性的方法可以覆寫第二個方法，例如`ClearPropertyDynamicParameters`，將動態參數新增至 cmdlet。

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面會定義下列方法來實作特定的提供者 cmdlet:

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Clear-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者刪除屬性的值。

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Get-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者擷取項目的屬性。

- [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Set-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者更新項目的屬性。

  [System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)介面會定義下列方法來實作特定的提供者 cmdlet:

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Copy-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者將屬性和它的值從一個位置複製到另一個。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Move-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者的屬性和它的值從一個位置移到另一個。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法可讓您定義您的提供者如何支援`New-ItemProperty`提供者 cmdlet。 此 cmdlet 可讓使用者建立新的屬性，並將其值設定。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Remove-ItemProperty`cmdlet。 此 cmdlet 可讓使用者刪除的屬性和其值。

- [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法可讓您定義您的提供者如何支援`Rename-ItemProperty`cmdlet。 此 cmdlet 可讓使用者變更的屬性名稱。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)