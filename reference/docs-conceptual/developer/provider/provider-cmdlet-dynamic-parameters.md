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
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="fbf98-102">提供者 Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="fbf98-102">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="fbf98-103">當使用者為 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至 provider Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="fbf98-103">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="fbf98-104">例如，提供者可以根據使用者在呼叫 `Get-Item` 或 @no__t 1 提供者 Cmdlet 時所指定的路徑，來新增不同的動態參數。</span><span class="sxs-lookup"><span data-stu-id="fbf98-104">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="fbf98-105">動態參數方法</span><span class="sxs-lookup"><span data-stu-id="fbf98-105">Dynamic Parameter Methods</span></span>

<span data-ttu-id="fbf98-106">動態參數的定義方式是執行其中一個動態參數方法，例如[ItemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[ItemCmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 的方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-106">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="fbf98-107">這些方法會傳回具有公用屬性的物件，這些屬性會以類似獨立 Cmdlet 的屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="fbf98-107">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="fbf98-108">以下是從憑證提供者所取得的[ItemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的執行範例：</span><span class="sxs-lookup"><span data-stu-id="fbf98-108">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="fbf98-109">不同于提供者 Cmdlet 的靜態參數，您可以指定這些參數的特性，方法與在獨立 Cmdlet 中定義參數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="fbf98-109">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="fbf98-110">以下是取自憑證提供者的動態參數類別範例：</span><span class="sxs-lookup"><span data-stu-id="fbf98-110">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

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

## <a name="dynamic-parameters"></a><span data-ttu-id="fbf98-111">動態參數</span><span class="sxs-lookup"><span data-stu-id="fbf98-111">Dynamic Parameters</span></span>

<span data-ttu-id="fbf98-112">以下是可用於新增動態參數的靜態參數清單。</span><span class="sxs-lookup"><span data-stu-id="fbf98-112">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="fbf98-113">`Clear-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Clearcontentdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) ，定義由 clear Cmdlet 的 `Path` 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-113">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-114">`Clear-Item` 指令程式，您可以藉由執行[Clearitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法，來定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="fbf98-114">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-115">`Clear-ItemProperty` 指令程式，您可以藉由[IpropertyCmdletprovider. Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數.</span><span class="sxs-lookup"><span data-stu-id="fbf98-115">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-116">`Copy-Item` 指令程式可讓您定義動態參數，由 `Path`、`Destination` 和 `Copy-Item` Cmdlet 的 `Recurse` 參數所觸發，方法是執行[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-116">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-117">ChildItems 指令程式：您可以藉由執行[，來定義由 `Path` 和 `Recurse` 參數所觸發的動態參數，方法是在 @no__t 2 CmdletContainerCmdletprovider. Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[ContainerCmdletprovider. Getchildnamesdynamicparameters \* 方法....](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)</span><span class="sxs-lookup"><span data-stu-id="fbf98-117">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="fbf98-118">`Get-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-118">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-119">`Get-Item` 指令程式，您可以藉由執行[Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法，來定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="fbf98-119">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-120">`Get-ItemProperty` 指令程式：您可以藉由[IpropertyCmdletprovider. Getpropertydynamicparameters \*，定義由 `Get-ItemProperty` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-120">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-121">`Invoke-Item` 指令程式，您可以藉由[ItemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-121">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-122">`Move-Item` 指令程式：您可以藉由[NavigationCmdletprovider. Moveitemdynamicparameters \*，定義由 `Move-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-122">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-123">`New-Item` 指令程式可讓您定義動態參數，由 `Path`、`ItemType` 和 `New-Item` Cmdlet 的 `Value` 參數所觸發，方法是執行[ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-123">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-124">`New-ItemProperty` 指令程式可讓您定義由 `Path`、`Name`、`PropertyType`，以及 `New-ItemProperty` Cmdlet 的 `Value` 參數所觸發的動態參數，方法是執行[IdynamicpropertyCmdletprovider. Newpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-124">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-125">`New-PSDrive` 指令程式，您可以定義由 `New-PSDrive` Cmdlet 所傳回的[PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo)物件所觸發的動態參數，方法是執行[DriveCmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-125">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-126">`Remove-Item` 您可以藉由[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) ，定義由 `Remove-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-126">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-127">`Remove-ItemProperty` 您可以藉由執行[，來定義由 `Path` 和 `Name` 參數所觸發的動態參數（由 `Remove-ItemProperty` Cmdlet）IdynamicpropertyCmdletprovider. Removepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-127">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-128">`Rename-Item` 指令程式：您可以藉由[ContainerCmdletprovider. Renameitemdynamicparameters \*，定義由 `Rename-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-128">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-129">`Rename-ItemProperty` 您可以藉由執行[，來定義由 `Path`、`Name`，以及 `Rename-ItemProperty` Cmdlet 的 `NewName` 參數所觸發的動態參數。IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-129">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-130">`Set-Content` 指令程式，您可以藉由[IcontentCmdletprovider. Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-130">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-131">`Set-Item` 指令程式：您可以藉由[ItemCmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) ，定義由 `Set-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-131">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-132">`Set-ItemProperty` 指令程式：您可以藉由[IpropertyCmdletprovider. Setpropertydynamicparameters \*，定義由 `Set-Item` Cmdlet 的 `Path` 和 @no__t 2 參數所觸發的動態參數。](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="fbf98-132">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="fbf98-133">`Test-Path` 指令程式，您可以藉由[ItemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) ，定義由 @no__t 2 Cmdlet 的 `Path` 參數所觸發的動態參數。方法.</span><span class="sxs-lookup"><span data-stu-id="fbf98-133">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbf98-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf98-134">See Also</span></span>

[<span data-ttu-id="fbf98-135">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="fbf98-135">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)