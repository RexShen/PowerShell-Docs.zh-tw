---
title: 提供者 Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2465420-0970-4408-9ee5-260cf444cb67
caps.latest.revision: 8
ms.openlocfilehash: e6a0711cff6a550100f584fb64ae7f59f71a3cfb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359977"
---
# <a name="provider-cmdlets"></a>提供者 Cmdlet

使用者可以執行來管理資料存放區的 Cmdlet 稱為提供者 Cmdlet。 若要支援這些 Cmdlet，您必須覆寫基底提供者類別和介面所定義的一些方法。

## <a name="provider-cmdlets"></a>提供者 Cmdlet

以下是使用者可執行檔提供者 Cmdlet：

### <a name="psdrive-cmdlets"></a>PSDrive Cmdlet

- `Get-PSDrive`：此 Cmdlet 會傳回目前會話中的 Windows PowerShell 磁片磁碟機。 您不需要覆寫任何方法來支援此 Cmdlet。

- `New-PSDrive`：此 Cmdlet 可讓使用者建立 Windows PowerShell 磁片磁碟機來存取資料存放區。 若要支援這個指令程式，請覆寫[DriveCmdletprovider. Newdrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive)和[DriveCmdletprovider... Newdrivedynamicparameters](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

- `Remove-PSDrive`：此 Cmdlet 可讓使用者移除存取資料存放區的 Windows PowerShell 磁片磁碟機。 若要支援此 Cmdlet，請覆寫[DriveCmdletprovider. Removedrive](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)方法。

### <a name="item-cmdlets"></a>Item Cmdlet

- `Clear-Item`：此 Cmdlet 可讓使用者移除資料存放區中的專案值。 若要支援這個指令程式，請覆寫[ItemCmdletprovider. Clearitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)和[ItemCmdletprovider... Clearitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

- `Copy-Item`：此 Cmdlet 可讓使用者將專案從一個位置複製到另一個位置。 若要支援這個指令程式，請覆寫[ContainerCmdletprovider. Copyitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)和[ContainerCmdletprovider... Copyitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

- `Get-Item`：此 Cmdlet 可讓使用者從資料存放區取出資料。 若要支援這個指令程式，請覆寫[ItemCmdletprovider. Getitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)和[ItemCmdletprovider... Getitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

- `Get-ChildItem`：此 Cmdlet 可讓使用者抓取父專案的子專案。 若要支援此 Cmdlet，請覆寫下列方法：

  - [提供者： ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)

  - [提供者： ContainerCmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)

  - [提供者： ContainerCmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)

  - [提供者： ContainerCmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

- `Invoke-Item`：此 Cmdlet 可讓使用者執行專案所指定的預設動作。 若要支援這個指令程式，請覆寫[ItemCmdletprovider. Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)和[ItemCmdletprovider... Invokedefaultaction](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

- `Move-Item`：此 Cmdlet 可讓使用者將專案從一個位置移到另一個位置。 若要支援此 Cmdlet，請覆寫[NavigationCmdletprovider. Moveitem](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)和[NavigationCmdletprovider. Moveitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)s 方法的程式。

- `New-ItemProperty`：此 Cmdlet 可讓使用者在資料存放區中建立新的專案。

- `Remove-Item`：此 Cmdlet 可讓使用者從資料存放區移除專案。 若要支援這個指令程式，請覆寫[ContainerCmdletprovider. Removeitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)和[ContainerCmdletprovider... Removeitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

- `Rename-Item`：此 Cmdlet 可讓使用者重新命名資料存放區中的專案。 若要支援這個指令程式，請覆寫[ContainerCmdletprovider. Renameitem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)和[ContainerCmdletprovider... Renameitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

- `Set-Item`：此 Cmdlet 可讓使用者更新資料存放區中的專案值。 若要支援這個指令程式，請覆寫[ItemCmdletprovider. Setitem](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)和[ItemCmdletprovider... Setitemdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

### <a name="item-content-cmdlets"></a>專案內容 Cmdlet

- `Add-Content`：此 Cmdlet 可讓使用者將內容新增至專案。

- `Clear-Content`：此 Cmdlet 可讓使用者刪除專案中的內容，而不刪除專案。 若要支援這個指令程式，請覆寫[IcontentCmdletprovider. Clearcontent](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)和[IcontentCmdletprovider... Clearcontentdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

- `Get-Content`：此 Cmdlet 可讓使用者取得專案的內容。 若要支援這個指令程式，請覆寫[IcontentCmdletprovider. Getcontentreader](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)和[IcontentCmdletprovider. Getcontentreaderdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 。方法. [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法會傳回[Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)介面，其會定義用來讀取內容的方法（該介面會使用）。

- `Set-Content`：此 Cmdlet 可讓使用者更新專案的內容。 若要支援這個指令程式，請覆寫[IcontentCmdletprovider. Getcontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)和[IcontentCmdletprovider. Getcontentwriterdynamicparameters](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 。方法. [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法會傳回[Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)介面，其會定義用來寫入內容的方法（method）。）。

### <a name="item-property-cmdlets"></a>Item 屬性 Cmdlet

- `Clear-ItemProperty`：此 Cmdlet 可讓使用者刪除屬性的值。 若要支援這個指令程式，請覆寫[IpropertyCmdletprovider. Clearproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)和[IpropertyCmdletprovider. Clearpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 。方法.

- `Copy-ItemProperty`：此 Cmdlet 可讓使用者將屬性和其值從一個位置複製到另一個位置。 若要支援此 Cmdlet，請覆寫[IdynamicpropertyCmdletprovider. Copyproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyProperty)和[IdynamicpropertyCmdletprovider. Copypropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.CopyPropertyDynamicParameters)方法的。

- `Get-ItemProperty`：此 Cmdlet 會抓取專案的屬性。 若要支援這個指令程式，請覆寫[IpropertyCmdletprovider. Getproperty](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)和[IpropertyCmdletprovider... Getpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

- `Move-ItemProperty`：此 Cmdlet 可讓使用者將屬性和其值從一個位置移到另一個位置。 若要支援此 Cmdlet，請覆寫[IdynamicpropertyCmdletprovider. Moveproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MoveProperty)和[IdynamicpropertyCmdletprovider. Movepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.MovePropertyDynamicParameters)方法的。

- `New-ItemProperty`：此 Cmdlet 可讓使用者建立新的屬性，並設定其值。 若要支援這個指令程式，請覆寫[IdynamicpropertyCmdletprovider. Newproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewProperty)和[IdynamicpropertyCmdletprovider. Newpropertydynamicparameters。](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

- `Remove-ItemProperty`：此 Cmdlet 可讓使用者刪除屬性及其值。 若要支援此 Cmdlet，請覆寫[IdynamicpropertyCmdletprovider. Removeproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)和[IdynamicpropertyCmdletprovider. Removepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法的。

- `Rename-ItemProperty`：此 Cmdlet 可讓使用者變更屬性的名稱。 若要支援此 Cmdlet，請覆寫[IdynamicpropertyCmdletprovider. Renameproperty](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)和[IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法的。

- `Set-ItemProperty`：此 Cmdlet 可讓使用者更新專案的屬性。 若要支援此指令程式，請覆寫[IpropertyCmdletprovider.](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) [IpropertyCmdletprovider. Setpropertydynamicparameters](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法.....。

### <a name="location-cmdlets"></a>Location Cmdlet

- `Get-Location`：抓取目前工作位置的相關資訊。 您不需要覆寫任何方法來支援此 Cmdlet。

- `Pop-Location`：此 Cmdlet 會將目前的位置變更為最近推送到堆疊上的位置。 您不需要覆寫任何方法來支援此 Cmdlet。

- `Push-Location`：此 Cmdlet 會將目前的位置新增至位置清單頂端（「堆疊」）。 您不需要覆寫任何方法來支援此 Cmdlet。

- `Set-Location`：此 Cmdlet 會將目前的工作位置設定為指定的位置。 您不需要覆寫任何方法來支援此 Cmdlet。

### <a name="path-cmdlets"></a>Path Cmdlet

- `Join-Path`：此 Cmdlet 可讓使用者結合父系和子路徑區段，以建立提供者內部路徑。 若要支援此 Cmdlet，請覆寫[NavigationCmdletprovider. Makepath](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)方法。

- `Convert-Path`：此 Cmdlet 會將路徑從 Windows PowerShell 路徑轉換成 Windows PowerShell 提供者路徑。

- `Split-Path`：傳回路徑的指定部分。

- `Resolve-Path`：解析路徑中的萬用字元，並顯示路徑內容。

- `Test-Path`：此 Cmdlet 會判斷路徑的所有元素是否都存在。 若要支援這個指令程式，請覆寫[ItemCmdletprovider. Itemexists](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists)和[ItemCmdletprovider... Itemexistsdynamicparameters](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters)方法。

### <a name="psprovider-cmdlets"></a>PSProvider Cmdlet

- `Get-PSProvider`：此 Cmdlet 會傳回會話中可用提供者的相關資訊。 您不需要覆寫任何方法來支援此 Cmdlet。