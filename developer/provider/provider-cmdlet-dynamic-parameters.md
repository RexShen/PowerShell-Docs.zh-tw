---
title: 提供者 cmdlet 的動態參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058227"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>提供者 Cmdlet 動態參數

提供者可以定義當使用者指定的特定值的其中一個靜態參數的 cmdlet 會加入至提供者 cmdlet 的動態參數。 比方說，提供者可以將不同的動態參數，以何種路徑上的使用者會指定當呼叫`Get-Item`或`Set-Item`提供者 cmdlet。

## <a name="dynamic-parameter-methods"></a>動態參數方法

動態參數由實作其中一個動態參數的方法，例如[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)的方法。 這些方法會傳回具有使用類似於獨立的指令程式的屬性裝飾的公用屬性的物件。 以下是實作的範例[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)摘錄自憑證提供者的方法：

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

不同於提供者 cmdlet 的靜態參數，您可以指定這些參數的特性參數定義在獨立的指令程式的方式相同。 摘錄自憑證提供者的動態參數類別的範例如下：

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

以下是可用來將動態參數的靜態參數的清單。

`Clear-Content` cmdlet，您可以定義所觸發的動態參數`Path`清除清除 cmdlet 實作參數[System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法。

`Clear-Item` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Clear-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法。

`Clear-ItemProperty` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Clear-ItemProperty`cmdlet，藉由實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法。

`Copy-Item` cmdlet，您可以定義所觸發的動態參數`Path`， `Destination`，並`Recurse`的參數`Copy-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。

取得 ChildItems cmdlet，您可以定義所觸發的動態參數`Path`並`Recurse`的參數`Get-ChildItem`cmdlet，藉由實作[System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。

`Get-Content` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Get-Content`cmdlet，藉由實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法。

`Get-Item` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Get-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法。

`Get-ItemProperty` cmdlet，您可以定義所觸發的動態參數`Path`並`Name`的參數`Get-ItemProperty`cmdlet，藉由實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。

`Invoke-Item` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Invoke-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。

`Move-Item` cmdlet，您可以定義所觸發的動態參數`Path`並`Destination`的參數`Move-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法。

`New-Item` cmdlet，您可以定義所觸發的動態參數`Path`， `ItemType`，並`Value`的參數`New-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。

`New-ItemProperty` cmdlet，您可以定義所觸發的動態參數`Path`， `Name`， `PropertyType`，以及`Value`參數`New-ItemProperty`cmdlet，藉由實作[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。

`New-PSDrive` cmdlet，您可以定義所觸發的動態參數[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)所傳回的物件`New-PSDrive`cmdlet，藉由實作[System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。

`Remove-Item` 您可以定義所觸發的動態參數`Path`並`Recurse`的參數`Remove-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法。

`Remove-ItemProperty` 您可以定義所觸發的動態參數`Path`並`Name`的參數`Remove-ItemProperty`cmdlet，藉由實作[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。

`Rename-Item` cmdlet，您可以定義所觸發的動態參數`Path`並`NewName`的參數`Rename-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。

`Rename-ItemProperty` 您可以定義所觸發的動態參數`Path`， `Name`，並`NewName`的參數`Rename-ItemProperty`cmdlet，藉由實作[System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。

`Set-Content` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Set-Content`cmdlet，藉由實作[System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法。

`Set-Item` cmdlet，您可以定義所觸發的動態參數`Path`並`Value`的參數`Set-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法。

`Set-ItemProperty` cmdlet，您可以定義所觸發的動態參數`Path`並`Value`的參數`Set-Item`cmdlet，藉由實作[System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。

`Test-Path` cmdlet，您可以定義所觸發的動態參數`Path`的參數`Test-Path`cmdlet，藉由實作[System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)