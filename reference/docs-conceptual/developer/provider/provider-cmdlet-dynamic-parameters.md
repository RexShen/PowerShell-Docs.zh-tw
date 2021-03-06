---
ms.date: 09/13/2016
ms.topic: reference
title: 提供者 Cmdlet 動態參數
description: 提供者 Cmdlet 動態參數
ms.openlocfilehash: ac05a847afb0729c34d733fa4ba8da11f46746fe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662989"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 動態參數

當使用者針對 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至提供者 Cmdlet 的動態參數。 例如，提供者可以根據使用者在呼叫 `Get-Item` 或提供者 Cmdlet 時所指定的路徑，加入不同的動態參數 `Set-Item` 。

## <a name="dynamic-parameter-methods"></a>動態參數方法

動態參數是藉由實作為其中一個動態參數方法（例如 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 和 [system.management.automation.provider.itemCmdletprovider... Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法）來定義。 這些方法會傳回具有公用屬性的物件，這些屬性會以類似于獨立 Cmdlet 的屬性裝飾。 以下是從憑證提供者取得的 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 方法的執行方式範例：

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

與提供者 Cmdlet 的靜態參數不同，您可以用在獨立 Cmdlet 中定義參數的相同方式來指定這些參數的特性。 以下是取自憑證提供者的動態參數類別範例：

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>動態參數

以下是可用於新增動態參數的靜態參數清單。

`Clear-Content` Cmdlet：您可以藉 `Path` 由執行 [IcontentCmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 方法，來定義由 Clear-Clear Cmdlet 的參數所觸發的動態參數。

`Clear-Item` Cmdlet：您可以藉 `Path` `Clear-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Clear-ItemProperty` Cmdlet：您可以藉 `Path` `Clear-ItemProperty` 由執行 [IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Copy-Item` Cmdlet：您可以藉 `Path` `Destination` `Recurse` `Copy-Item` 由執行 [ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。

Get-ChildItems Cmdlet，您可以藉 `Path` `Recurse` `Get-ChildItem` 由執行 [ContainerCmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 和 [ContainerCmdletprovider.. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 方法，來定義由 Cmdlet 的和參數所觸發的動態參數。

`Get-Content` Cmdlet：您可以藉 `Path` `Get-Content` 由執行 [IcontentCmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Get-Item` Cmdlet：您可以藉 `Path` `Get-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Get-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `Get-ItemProperty` 由執行 [IpropertyCmdletprovider. Getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Invoke-Item` Cmdlet：您可以藉 `Path` `Invoke-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Move-Item` Cmdlet：您可以藉 `Path` `Destination` `Move-Item` 由執行 [>navigationCmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`New-Item` Cmdlet：您可以藉 `Path` `ItemType` `Value` `New-Item` 由執行 [ContainerCmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。

`New-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `PropertyType` `Value` `New-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 方法，定義由 Cmdlet 的、、和參數所觸發的動態參數。

`New-PSDrive`Cmdlet：您可以藉[](/dotnet/api/System.Management.Automation.PSDriveInfo) `New-PSDrive` 由[DriveCmdletprovider Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法，定義由 Cmdlet 傳回的System.Management.Automation.PSDriveinfo 物件所觸發的動態參數。

`Remove-Item` 您可以藉 `Path` `Recurse` `Remove-Item` 由執行 [ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Remove-ItemProperty` 您可以藉 `Path` `Name` `Remove-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Rename-Item` Cmdlet：您可以藉 `Path` `NewName` `Rename-Item` 由執行 [ContainerCmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Rename-ItemProperty` 您可以藉 `Path` `Name` `NewName` `Rename-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。

`Set-Content` Cmdlet：您可以藉 `Path` `Set-Content` 由執行 [IcontentCmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

`Set-Item` Cmdlet：您可以藉 `Path` `Value` `Set-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Set-ItemProperty` Cmdlet：您可以藉 `Path` `Value` `Set-Item` 由執行 [IpropertyCmdletprovider. Setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。

`Test-Path` Cmdlet：您可以藉 `Path` `Test-Path` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)
