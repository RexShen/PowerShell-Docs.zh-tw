---
title: 提供者 Cmdlet 動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359947"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 動態參數

當使用者為 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至 provider Cmdlet 的動態參數。 例如，提供者可以根據使用者在呼叫 `Get-Item` 或 @no__t 1 提供者 Cmdlet 時所指定的路徑，來新增不同的動態參數。

## <a name="dynamic-parameter-methods"></a>動態參數方法

動態參數的定義方式是執行其中一個動態參數方法，例如[ItemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[ItemCmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 的方法。 這些方法會傳回具有公用屬性的物件，這些屬性會以類似獨立 Cmdlet 的屬性裝飾。 以下是從憑證提供者所取得的[ItemCmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的執行範例：

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

不同于提供者 Cmdlet 的靜態參數，您可以指定這些參數的特性，方法與在獨立 Cmdlet 中定義參數的方式相同。 以下是取自憑證提供者的動態參數類別範例：

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

`Clear-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) ，定義由 clear Cmdlet 的 `Path` 參數所觸發的動態參數。方法.

`Clear-Item` 指令程式，您可以藉由執行[Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法，來定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。

`Clear-ItemProperty` 指令程式，您可以藉由[IpropertyCmdletprovider. Clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數.

`Copy-Item` 指令程式可讓您定義動態參數，由 `Path`、`Destination` 和 `Copy-Item` Cmdlet 的 `Recurse` 參數所觸發，方法是執行[ContainerCmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

ChildItems 指令程式：您可以藉由執行[，來定義由 `Path` 和 `Recurse` 參數所觸發的動態參數，方法是在 @no__t 2 CmdletContainerCmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[ContainerCmdletprovider. Getchildnamesdynamicparameters * 方法....](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)

`Get-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.

`Get-Item` 指令程式，您可以藉由執行[Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法，來定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。

`Get-ItemProperty` 指令程式：您可以藉由[IpropertyCmdletprovider. Getpropertydynamicparameters *，定義由 `Get-ItemProperty` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

`Invoke-Item` 指令程式，您可以藉由[ItemCmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.

`Move-Item` 指令程式：您可以藉由[NavigationCmdletprovider. Moveitemdynamicparameters *，定義由 `Move-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法。

`New-Item` 指令程式可讓您定義動態參數，由 `Path`、`ItemType` 和 `New-Item` Cmdlet 的 `Value` 參數所觸發，方法是執行[ContainerCmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。

`New-ItemProperty` 指令程式可讓您定義由 `Path`、`Name`、`PropertyType`，以及 `New-ItemProperty` Cmdlet 的 `Value` 參數所觸發的動態參數，方法是執行[IdynamicpropertyCmdletprovider. Newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

`New-PSDrive` 指令程式，您可以定義由 `New-PSDrive` Cmdlet 所傳回的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件所觸發的動態參數，方法是執行[DriveCmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

`Remove-Item` 您可以藉由[ContainerCmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) ，定義由 `Remove-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。方法.

`Remove-ItemProperty` 您可以藉由執行[，來定義由 `Path` 和 `Name` 參數所觸發的動態參數（由 `Remove-ItemProperty` Cmdlet）IdynamicpropertyCmdletprovider. Removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

`Rename-Item` 指令程式：您可以藉由[ContainerCmdletprovider. Renameitemdynamicparameters *，定義由 `Rename-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

`Rename-ItemProperty` 您可以藉由執行[，來定義由 `Path`、`Name`，以及 `Rename-ItemProperty` Cmdlet 的 `NewName` 參數所觸發的動態參數。IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

`Set-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.

`Set-Item` 指令程式：您可以藉由[ItemCmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) ，定義由 `Set-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。方法.

`Set-ItemProperty` 指令程式：您可以藉由[IpropertyCmdletprovider. Setpropertydynamicparameters *，定義由 `Set-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

`Test-Path` 指令程式，您可以藉由[ItemCmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)