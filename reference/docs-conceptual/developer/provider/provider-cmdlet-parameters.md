---
title: 提供者 Cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: ad7f9737c646dd5cea5abb14b828236e40feac5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366307"
---
# <a name="provider-cmdlet-parameters"></a>提供者 Cmdlet 參數

提供者 Cmdlet 隨附一組可供所有支援 Cmdlet 的提供者使用的靜態參數，以及當使用者為提供者 Cmdlet 的特定靜態參數指定特定值時，所新增的動態參數。

## <a name="provider-cmdlet-static-parameters"></a>提供者 Cmdlet 靜態參數

靜態參數是由 Windows PowerShell 所定義。 Windows PowerShell 會執行一組大型的這些參數，以提供所有提供者的一致性，並提供更簡單的開發體驗。 這些參數的範例包括 `Get-Item` Cmdlet 的 `literalPath`、`exclude`和 `include` 參數。 您可以覆寫一組較小的這些參數，以提供提供者專屬的動作。 這些參數的範例包括 `Set-Item` Cmdlet 的 `Path` 和 `Value` 參數。 以下是可覆寫提供者 Cmdlet 的參數清單。

`Clear-Content` Cmdlet，您可以藉由[Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法，定義提供者將如何使用傳遞給 `Clear-Content` Cmdlet 之 `Path` 參數的值。

`Clear-Item` Cmdlet，您可以藉由[Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法，定義提供者將如何使用傳遞給 `Clear-Item` Cmdlet 之 `Path` 參數的值。

`Clear-ItemProperty` Cmdlet，您可以藉由[Clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法，定義提供者將如何使用傳遞給 `Path` 的值和 `Clear-ItemProperty` Cmdlet 的 `Name` 參數。

`Copy-Item` Cmdlet，您可以藉由[CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法，定義提供者將如何使用傳遞至 `Copy-Item` Cmdlet 之 `Path`、`Destination`和 `Recurse` 參數的值。

ChildItems 指令程式：您可以藉由 ContainerCmdletprovider [Getchilditems * 和](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) [*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法，來定義提供者將如何使用傳遞給 `Path` 的值，以及 `Get-ChildItem` Cmdlet 的 `Recurse` 參數，藉此來執行此程式。

`Get-Content` Cmdlet，您可以藉由[Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法，定義提供者將如何使用傳遞給 `Get-Content` Cmdlet 之 `Path` 參數的值。

`Get-Item` Cmdlet，您可以藉由[Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法，定義提供者將如何使用傳遞給 `Get-Item` Cmdlet 之 `Path` 參數的值。

`Get-ItemProperty` Cmdlet，您可以藉由[Getproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法，定義提供者將如何使用傳遞給 `Path` 的值和 `Get-ItemProperty` Cmdlet 的 `Name` 參數。

`Invoke-Item` Cmdlet，您可以藉由[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定義提供者將如何使用傳遞給 `Invoke-Item` Cmdlet 之 `Path` 參數的值。

`Move-Item` Cmdlet，您可以藉由[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法，定義提供者將如何使用傳遞給 `Path` 的值和 `Move-Item` Cmdlet 的 `Destination` 參數。

`New-Item` Cmdlet 中，您可以藉由[Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法，來定義提供者將如何使用傳遞至 `New-Item` Cmdlet 之 `Path`、`ItemType`和 `Value` 參數的值。

`New-ItemProperty` Cmdlet，您可以藉由[Registryprovider. Newproperty *](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty)方法，定義提供者如何使用傳遞至 `Value` Cmdlet 之 `Path`、`Name`、`PropertyType`和 `New-ItemProperty` 參數的值。

`Remove-Item` 您可以藉由[Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法，來定義提供者將如何使用傳遞給 `Path` 的值和 `Remove-Item` Cmdlet 的 `Recurse` 參數。

`Remove-ItemProperty` 您可以藉由[Removeproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)方法，來定義提供者將如何使用傳遞給 `Path` 的值和 `Remove-ItemProperty` Cmdlet 的 `Name` 參數。

`Rename-Item` Cmdlet，您可以藉由[Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法，定義提供者將如何使用傳遞給 `Path` 的值和 `Rename-Item` Cmdlet 的 `NewName` 參數。

`Rename-ItemProperty` 您可以藉由[Renameproperty *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)方法，來定義提供者將如何使用傳遞至 `Rename-ItemProperty` Cmdlet 之 `Path`、`NewName`和 `Name` 參數的值。

`Set-Content` Cmdlet，您可以藉由[Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法，定義提供者將如何使用傳遞給 `Set-Content` Cmdlet 之 `Path` 參數的值。

`Set-Item` Cmdlet，您可以藉由[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法，定義提供者將如何使用傳遞給 `Path` 的值和 `Set-Item` Cmdlet 的 `Value` 參數。

`Set-ItemProperty` Cmdlet，您可以藉由執行[IpropertyCmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) ，來定義提供者將如何使用傳遞給 `Path` 的值和 `Set-Item` Cmdlet 的 `Value` 參數。

`Test-Path` Cmdlet，您可以藉由[Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法，定義提供者將如何使用傳遞給 `Test-Path` Cmdlet 之 `Path` 參數的值。

此外，您不能指定這些參數的特性，例如它們是否為選擇性或必要，也不能為這些參數提供別名或指定任何驗證屬性。 相反地，您可以使用 `Parameters` 屬性之類的屬性，在獨立 Cmdlet 中指定參數特性。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 動態參數

Cmdlet 提供者的動態參數類似于獨立 Cmdlet 的動態提供者。 在這兩種情況下，當使用者指定其中一個預設參數的特定值（例如 `path` 參數）時，會將參數新增至 Cmdlet。 不過，並非所有的靜態參數都可以用來觸發新增動態參數。 如需動態參數的詳細資訊，請參閱[Provider Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另請參閱

[提供者 Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)