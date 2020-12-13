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
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="5f47c-103">提供者 Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="5f47c-103">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="5f47c-104">當使用者針對 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至提供者 Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-104">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="5f47c-105">例如，提供者可以根據使用者在呼叫 `Get-Item` 或提供者 Cmdlet 時所指定的路徑，加入不同的動態參數 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="5f47c-105">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="5f47c-106">動態參數方法</span><span class="sxs-lookup"><span data-stu-id="5f47c-106">Dynamic Parameter Methods</span></span>

<span data-ttu-id="5f47c-107">動態參數是藉由實作為其中一個動態參數方法（例如 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 和 [system.management.automation.provider.itemCmdletprovider... Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法）來定義。</span><span class="sxs-lookup"><span data-stu-id="5f47c-107">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="5f47c-108">這些方法會傳回具有公用屬性的物件，這些屬性會以類似于獨立 Cmdlet 的屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="5f47c-108">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="5f47c-109">以下是從憑證提供者取得的 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 方法的執行方式範例：</span><span class="sxs-lookup"><span data-stu-id="5f47c-109">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="5f47c-110">與提供者 Cmdlet 的靜態參數不同，您可以用在獨立 Cmdlet 中定義參數的相同方式來指定這些參數的特性。</span><span class="sxs-lookup"><span data-stu-id="5f47c-110">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="5f47c-111">以下是取自憑證提供者的動態參數類別範例：</span><span class="sxs-lookup"><span data-stu-id="5f47c-111">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

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

## <a name="dynamic-parameters"></a><span data-ttu-id="5f47c-112">動態參數</span><span class="sxs-lookup"><span data-stu-id="5f47c-112">Dynamic Parameters</span></span>

<span data-ttu-id="5f47c-113">以下是可用於新增動態參數的靜態參數清單。</span><span class="sxs-lookup"><span data-stu-id="5f47c-113">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="5f47c-114">`Clear-Content` Cmdlet：您可以藉 `Path` 由執行 [IcontentCmdletprovider. Clearcontentdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) 方法，來定義由 Clear-Clear Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-114">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-115">`Clear-Item` Cmdlet：您可以藉 `Path` `Clear-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Clearitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-115">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-116">`Clear-ItemProperty` Cmdlet：您可以藉 `Path` `Clear-ItemProperty` 由執行 [IpropertyCmdletprovider. Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-116">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-117">`Copy-Item` Cmdlet：您可以藉 `Path` `Destination` `Recurse` `Copy-Item` 由執行 [ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-117">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-118">Get-ChildItems Cmdlet，您可以藉 `Path` `Recurse` `Get-ChildItem` 由執行 [ContainerCmdletprovider. Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 和 [ContainerCmdletprovider.. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 方法，來定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-118">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="5f47c-119">`Get-Content` Cmdlet：您可以藉 `Path` `Get-Content` 由執行 [IcontentCmdletprovider. Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-119">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-120">`Get-Item` Cmdlet：您可以藉 `Path` `Get-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-120">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-121">`Get-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `Get-ItemProperty` 由執行 [IpropertyCmdletprovider. Getpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-121">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-122">`Invoke-Item` Cmdlet：您可以藉 `Path` `Invoke-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-122">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-123">`Move-Item` Cmdlet：您可以藉 `Path` `Destination` `Move-Item` 由執行 [>navigationCmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-123">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-124">`New-Item` Cmdlet：您可以藉 `Path` `ItemType` `Value` `New-Item` 由執行 [ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-124">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-125">`New-ItemProperty` Cmdlet：您可以藉 `Path` `Name` `PropertyType` `Value` `New-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Newpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) 方法，定義由 Cmdlet 的、、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-125">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-126">`New-PSDrive`Cmdlet：您可以藉[](/dotnet/api/System.Management.Automation.PSDriveInfo) `New-PSDrive` 由[DriveCmdletprovider Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法，定義由 Cmdlet 傳回的System.Management.Automation.PSDriveinfo 物件所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-126">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-127">`Remove-Item` 您可以藉 `Path` `Recurse` `Remove-Item` 由執行 [ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-127">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-128">`Remove-ItemProperty` 您可以藉 `Path` `Name` `Remove-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Removepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-128">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-129">`Rename-Item` Cmdlet：您可以藉 `Path` `NewName` `Rename-Item` 由執行 [ContainerCmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-129">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-130">`Rename-ItemProperty` 您可以藉 `Path` `Name` `NewName` `Rename-ItemProperty` 由執行 [IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) 方法，定義由 Cmdlet、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-130">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-131">`Set-Content` Cmdlet：您可以藉 `Path` `Set-Content` 由執行 [IcontentCmdletprovider. Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-131">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-132">`Set-Item` Cmdlet：您可以藉 `Path` `Value` `Set-Item` 由執行 [system.management.automation.provider.itemCmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-132">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-133">`Set-ItemProperty` Cmdlet：您可以藉 `Path` `Value` `Set-Item` 由執行 [IpropertyCmdletprovider. Setpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) 方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-133">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="5f47c-134">`Test-Path` Cmdlet：您可以藉 `Path` `Test-Path` 由執行 [system.management.automation.provider.itemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) 方法，定義由 Cmdlet 的參數觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="5f47c-134">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f47c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f47c-135">See Also</span></span>

[<span data-ttu-id="5f47c-136">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="5f47c-136">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)
