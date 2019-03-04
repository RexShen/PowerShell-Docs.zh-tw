---
title: 提供者 cmdlet 參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b3d09eaa-924f-4e2b-adfb-14bb729090dd
caps.latest.revision: 8
ms.openlocfilehash: d0fb81ee1ca1f80e216c021e1bd64771b8de4dc3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860114"
---
# <a name="provider-cmdlet-parameters"></a>提供者 Cmdlet 參數

提供者 cmdlet 隨附一組可用於所有支援此 cmdlet 的提供者的靜態參數，以及為動態參數，當使用者指定特定的提供者 cmdlet 的靜態參數的特定值時，加入。

## <a name="provider-cmdlet-static-parameters"></a>提供者 Cmdlet 的靜態參數

靜態參數會定義 Windows PowerShell。 大量的這些參數被藉由提供所有提供者之間的一致性，並提供更簡單的開發體驗的 Windows PowerShell。 這些參數的範例包括`literalPath`， `exclude`，並`include`參數`Get-Item`cmdlet。 可以覆寫較少的這些參數，提供您的提供者特有的動作。 這些參數的範例包括`Path`並`Value`參數`Set-Item`cmdlet。 以下是可覆寫提供者 cmdlet 的參數清單。

`Clear-Content` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Clear-Content`cmdlet，藉由實作[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)方法。

`Clear-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Clear-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem)方法。

`Clear-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`Name`的參數`Clear-ItemProperty`藉由實作的 cmdlet [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)方法。

`Copy-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet `Path`， `Destination`，和`Recurse`的參數`Copy-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Copyitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)方法。

您可定義您的提供者會使用傳遞至的值的方式取得 ChildItems cmdlet`Path`和`Recures`的參數`Get-ChildItem`藉由實作的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems)並[System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames)方法。

`Get-Content` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Get-Content`cmdlet，藉由實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)方法。

`Get-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Get-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem)方法。

`Get-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`Name`的參數`Get-ItemProperty`藉由實作的 cmdlet [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)方法。

`Invoke-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Invoke-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

`Move-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`Destination`的參數`Move-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem)方法。

`New-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet `Path`， `ItemType`，和`Value`的參數`New-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem)方法。

`New-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet `Path`， `Name`， `PropertyType`，和`Value`參數`New-ItemProperty`藉由實作的 cmdlet [Microsoft.Powershell.Commands.Registryprovider.Newproperty*](/dotnet/api/Microsoft.PowerShell.Commands.RegistryProvider.NewProperty)方法。

`Remove-Item` 您可以定義如何您的提供者會使用的值傳遞給`Path`並`Recurse`的參數`Remove-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)方法。

`Remove-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給`Path`並`Name`的參數`Remove-ItemProperty`藉由實作的 cmdlet [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removeproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemoveProperty)方法。

`Rename-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`NewName`的參數`Rename-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem)方法。

`Rename-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給`Path`， `NewName`，並`Name`的參數`Rename-ItemProperty`藉由實作的 cmdlet [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renameproperty*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenameProperty)方法。

`Set-Content` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Set-Content`cmdlet，藉由實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)方法。

`Set-Item` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`Value`的參數`Set-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)方法。

`Set-ItemProperty` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`和`Value`的參數`Set-Item`藉由實作的 cmdlet [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)方法。

`Test-Path` 您可以定義如何您的提供者會使用的值傳遞給 cmdlet`Path`參數`Test-Path`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction)方法。

此外，您不能指定這些參數，例如是否為選擇性或必要的特性也提供這些參數別名或指定的任何驗證屬性。 相反地，使用屬性，例如獨立的 cmdlet 中指定參數特性`Parameters`屬性。

## <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 的動態參數

Cmdlet 提供者的動態參數是類似於獨立的 cmdlet 的動態提供者。 在這兩種情況下，參數會加入至指令程式時的使用者指定為某個值的其中一個預設的參數，例如`path`參數。 不過，並非所有的靜態參數可用來觸發程序的動態參數。 如需有關動態參數的詳細資訊，請參閱[提供者 Cmdlet 的動態參數](./provider-cmdlet-dynamic-parameters.md)。

## <a name="see-also"></a>另請參閱

[提供者 Cmdlet 的動態參數](./provider-cmdlet-dynamic-parameters.md)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)