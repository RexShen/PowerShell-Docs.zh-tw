---
ms.date: 09/13/2016
ms.topic: reference
title: 提供者 Cmdlet 參數
description: 提供者 Cmdlet 參數
ms.openlocfilehash: 6fd340f22202d984b7111c34806e3461a356c670
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662780"
---
# <a name="provider-cmdlet-parameters"></a>提供者 Cmdlet 參數

提供者 Cmdlet 隨附一組靜態參數，可供所有支援此 Cmdlet 的提供者使用，以及當使用者針對提供者 Cmdlet 的特定靜態參數指定特定值時新增的動態參數。

## <a name="provider-cmdlet-static-parameters"></a>提供者 Cmdlet 靜態參數

靜態參數是由 Windows PowerShell 定義。 這些參數的大型集合是由 Windows PowerShell 所執行，以在所有提供者之間提供一致性，並提供更簡單的開發體驗。 這些參數的範例包括 `literalPath` Cmdlet 的、 `exclude` 和 `include` 參數 `Get-Item` 。 您可以覆寫一組較小的參數，以提供提供者專屬的動作。 這些參數的範例包括 `Path` Cmdlet 的和 `Value` 參數 `Set-Item` 。 以下是可針對提供者 Cmdlet 覆寫的參數清單。

`Clear-Content` Cmdlet：您可以藉 `Path` `Clear-Content` 由執行 [IcontentCmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Clear-Item` Cmdlet：您可以藉 `Path` `Clear-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Clear-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `Clear-ItemProperty` 由執行 [IpropertyCmdletprovider. Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Copy-Item` Cmdlet 可讓您定義提供者如何使用傳遞給 `Path` Cmdlet 的、和參數的值，方法 `Destination` `Recurse` `Copy-Item` 是執行 [ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 方法。

Get-ChildItems Cmdlet，您可以藉 `Path` `Recurse` `Get-ChildItem` 由執行 [ContainerCmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 和 [ContainerCmdletprovider... Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Get-Content` Cmdlet：您可以藉 `Path` `Get-Content` 由執行 [IcontentCmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Get-Item` Cmdlet：您可以藉 `Path` `Get-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Get-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `Get-ItemProperty` 由執行 [IpropertyCmdletprovider. Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Invoke-Item` Cmdlet：您可以藉 `Path` `Invoke-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Move-Item` Cmdlet：您可以藉 `Path` `Destination` `Move-Item` 由執行 [>navigationCmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`New-Item` Cmdlet：您可以藉 `Path` `ItemType` `Value` `New-Item` 由執行 [ContainerCmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 方法，定義提供者如何使用傳遞給 Cmdlet 的、和參數的值。

`New-ItemProperty` Cmdlet 可讓您定義提供者如何使用傳遞給 `Path` Cmdlet 的、 `Name` 、和參數的值， `PropertyType` `Value` `New-ItemProperty` 方法是執行 [Registryprovider. Newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty) 方法。

`Remove-Item` 您可以藉 `Path` `Recurse` `Remove-Item` 由執行 [ContainerCmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Remove-ItemProperty` 您可以藉 `Path` `Name` `Remove-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Rename-Item` Cmdlet：您可以藉 `Path` `NewName` `Rename-Item` 由執行 [ContainerCmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Rename-ItemProperty` 您可以藉 `Path` `NewName` `Name` `Rename-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty) 方法，來定義提供者如何使用傳遞給 Cmdlet 的、和參數的值。

`Set-Content` Cmdlet：您可以藉 `Path` `Set-Content` 由執行 [IcontentCmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

`Set-Item` Cmdlet：您可以藉 `Path` `Value` `Set-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 方法，來定義提供者將如何使用傳遞給 Cmdlet 和參數的值。

`Set-ItemProperty`Cmdlet：您可以藉由執行 IpropertyCmdletprovider，來定義提供者如何使用傳遞給 `Path` `Value` Cmdlet 和參數的值， `Set-Item` 方法[](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)是執行。

`Test-Path` Cmdlet：您可以藉 `Path` `Test-Path` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) 方法，來定義提供者如何使用傳遞給 Cmdlet 參數的值。

此外，您不能指定這些參數的特性，例如它們是否為選用或必要，也不能為這些參數指定別名或指定任何驗證屬性。 相反地，您可以使用屬性（例如屬性），在獨立 Cmdlet 中指定參數特性 `Parameters` 。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 動態參數

Cmdlet 提供者的動態參數類似于獨立 Cmdlet 的動態提供者。 在這兩種情況下，當使用者為其中一個預設參數指定特定值（例如參數）時，就會將參數新增至 Cmdlet `path` 。 不過，並非所有的靜態參數都可以用來觸發動態參數的加入。 如需動態參數的詳細資訊，請參閱 [提供者 Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另請參閱

[提供者 Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)
