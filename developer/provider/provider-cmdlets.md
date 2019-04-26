---
title: 提供者 cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080946"
---
# <a name="provider-cmdlets"></a>提供者 Cmdlet

使用者可以管理的資料存放區執行的 cmdlet 被指提供者 cmdlet。 若要支援這些 cmdlet，您需要覆寫一些基底提供者類別和介面所定義的方法。

## <a name="provider-cmdlets"></a>提供者 Cmdlet

以下是可以由使用者執行的提供者 cmdlet:

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet

- `Get-PSDrive`:此 cmdlet 會傳回目前工作階段中的 Windows PowerShell 磁碟機。 您不需要覆寫任何方法來支援此 cmdlet。

- `New-PSDrive`:此 cmdlet 可讓使用者建立存取資料存放區的 Windows PowerShell 磁碟機。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

- `Remove-PSDrive`:此 cmdlet 可讓使用者存取資料存放區的 Windows PowerShell 磁碟機上移除。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Drivecmdletprovider.Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。

### <a name="item-cmdlets"></a>Item cmdlet

- `Clear-Item`:此 cmdlet 可讓使用者在資料存放區中移除項目的值。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

- `Copy-Item`:此 cmdlet 可讓使用者將項目從一個位置複製到另一個。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Containercmdletprovider.Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

- `Get-Item`:此 cmdlet 可讓使用者從資料存放區擷取資料。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

- `Get-ChildItem`:此 cmdlet 可讓使用者擷取父項目的子項目。 若要支援此 cmdlet，覆寫下列方法：

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`:此 cmdlet 可讓使用者執行項目所指定的預設動作。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

- `Move-Item`:此 cmdlet 可讓使用者將項目從一個位置移到另一個位置。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)的方法。

- `New-ItemProperty`:此 cmdlet 可讓使用者在 資料存放區中建立新的項目。

- `Remove-Item`:此 cmdlet 可讓使用者從資料存放區中移除項目。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Containercmdletprovider.Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

- `Rename-Item`:此 cmdlet 可讓使用者重新命名資料存放區中的項目。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Containercmdletprovider.Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

- `Set-Item`:此 cmdlet 可讓使用者更新資料存放區中的項目值。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

### <a name="item-content-cmdlets"></a>項目內容的 cmdlet

- `Add-Content`:此 cmdlet 可讓使用者將內容新增至項目。

- `Clear-Content`:此 cmdlet 可讓使用者從項目中刪除內容，而不會刪除項目。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

- `Get-Content`:此 cmdlet 可讓使用者擷取項目的內容。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法會傳回[System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)定義的介面用來讀取內容的方法。

- `Set-Content`:此 cmdlet 可讓使用者更新的項目內容。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法。 [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法會傳回[System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)定義的介面用來寫入內容的方法。

### <a name="item-property-cmdlets"></a>Item 屬性 cmdlet

- `Clear-ItemProperty`:此 cmdlet 可讓使用者刪除屬性的值。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。

- `Copy-ItemProperty`:此 cmdlet 可讓使用者將屬性和它的值從一個位置複製到另一個。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法。

- `Get-ItemProperty`:此 cmdlet 會擷取項目的屬性。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

- `Move-ItemProperty`:此 cmdlet 可讓使用者的屬性和它的值從一個位置移到另一個。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法。

- `New-ItemProperty`:此 cmdlet 可讓使用者建立新的屬性，並將其值設定。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

- `Remove-ItemProperty`:此 cmdlet 可讓使用者刪除的屬性和其值。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

- `Rename-ItemProperty`:此 cmdlet 可讓使用者變更的屬性名稱。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

- `Set-ItemProperty`:此 cmdlet 可讓使用者更新項目的屬性。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)和[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

### <a name="location-cmdlets"></a>Location cmdlet

- `Get-Location`:擷取目前的工作位置的相關資訊。 您不需要覆寫任何方法來支援此 cmdlet。

- `Pop-Location`:此 cmdlet 會將目前的位置變更至最近推送到堆疊上的位置。 您不需要覆寫任何方法來支援此 cmdlet。

- `Push-Location`:此 cmdlet 會將目前的位置加入至的位置 （「 堆疊 」） 清單的頂端。 您不需要覆寫任何方法來支援此 cmdlet。

- `Set-Location`:此 cmdlet 會設定目前的工作位置，以指定的位置。 您不需要覆寫任何方法來支援此 cmdlet。

### <a name="path-cmdlets"></a>Path cmdlet

- `Join-Path`:此 cmdlet 可讓使用者結合父系和子系的路徑區段，來建立提供者內部路徑。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Navigationcmdletprovider.Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

- `Convert-Path`:此 cmdlet 會將路徑從 Windows PowerShell 路徑轉換成 Windows PowerShell 提供者路徑。

- `Split-Path`:傳回路徑的指定部分。

- `Resolve-Path`:解析路徑中的萬用字元，並顯示路徑內容。

- `Test-Path`:此 cmdlet 會判斷路徑的所有元素是否都存在。 若要支援此 cmdlet，覆寫[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和[System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。

### <a name="psprovider-cmdlets"></a>PSProvider cmdlet

- `Get-PSProvider`:此 cmdlet 會傳回工作階段中可用的提供者的相關資訊。 您不需要覆寫任何方法來支援此 cmdlet。