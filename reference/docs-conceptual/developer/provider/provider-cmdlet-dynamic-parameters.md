---
title: 提供者 Cmdlet 動態參數 |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4aaa5ee39e98de9a9925fc65cac3cc6c32d9c2bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786810"
---
# <a name="provider-cmdlet-dynamic-parameters"></a><span data-ttu-id="24e58-102">提供者 Cmdlet 動態參數</span><span class="sxs-lookup"><span data-stu-id="24e58-102">Provider cmdlet dynamic parameters</span></span>

<span data-ttu-id="24e58-103">當使用者為 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至 provider Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-103">Providers can define dynamic parameters that are added to a provider cmdlet when the user specifies a certain value for one of the static parameters of the cmdlet.</span></span> <span data-ttu-id="24e58-104">例如，提供者可以根據使用者呼叫 `Get-Item` 或提供者 Cmdlet 時所指定的路徑，來新增不同的動態參數 `Set-Item` 。</span><span class="sxs-lookup"><span data-stu-id="24e58-104">For example, a provider can add different dynamic parameters based on what path the user specifies when they call the `Get-Item` or `Set-Item` provider cmdlets.</span></span>

## <a name="dynamic-parameter-methods"></a><span data-ttu-id="24e58-105">動態參數方法</span><span class="sxs-lookup"><span data-stu-id="24e58-105">Dynamic Parameter Methods</span></span>

<span data-ttu-id="24e58-106">動態參數是藉由實作為其中一個動態參數方法（例如， [ItemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)和[ItemCmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s 方法）來定義的。</span><span class="sxs-lookup"><span data-stu-id="24e58-106">Dynamic parameters are defined by implementing one of the dynamic parameter methods, such as the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) and [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s methods.</span></span> <span data-ttu-id="24e58-107">這些方法會傳回具有公用屬性的物件，這些屬性會以類似獨立 Cmdlet 的屬性裝飾。</span><span class="sxs-lookup"><span data-stu-id="24e58-107">These methods return an object that has public properties that are decorated with attributes similar to those of stand-alone cmdlets.</span></span> <span data-ttu-id="24e58-108">以下是從憑證提供者所取得的[ItemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法的執行範例：</span><span class="sxs-lookup"><span data-stu-id="24e58-108">Here is an example of an implementation of the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method taken from the Certificate provider:</span></span>

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

<span data-ttu-id="24e58-109">不同于提供者 Cmdlet 的靜態參數，您可以指定這些參數的特性，方法與在獨立 Cmdlet 中定義參數的方式相同。</span><span class="sxs-lookup"><span data-stu-id="24e58-109">Unlike the static parameters of provider cmdlets, you can specify the characteristics of these parameters in the same way that parameters are defined in stand-alone cmdlets.</span></span> <span data-ttu-id="24e58-110">以下是取自憑證提供者的動態參數類別範例：</span><span class="sxs-lookup"><span data-stu-id="24e58-110">Here is an example of a dynamic parameter class taken from the Certificate provider:</span></span>

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

## <a name="dynamic-parameters"></a><span data-ttu-id="24e58-111">動態參數</span><span class="sxs-lookup"><span data-stu-id="24e58-111">Dynamic Parameters</span></span>

<span data-ttu-id="24e58-112">以下是可用於新增動態參數的靜態參數清單。</span><span class="sxs-lookup"><span data-stu-id="24e58-112">Here is a list of the static parameters that can be used to add dynamic parameters.</span></span>

<span data-ttu-id="24e58-113">`Clear-Content`Cmdlet 您可以藉 `Path` 由執行[IcontentCmdletprovider. Clearcontentdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters)方法，定義由 clear Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-113">`Clear-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the Clear-Clear cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-114">`Clear-Item`Cmdlet 您可以藉 `Path` `Clear-Item` 由執行[ItemCmdletprovider. Clearitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-114">`Clear-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-115">`Clear-ItemProperty`Cmdlet 您可以藉 `Path` `Clear-ItemProperty` 由執行[IpropertyCmdletprovider. Clearpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-115">`Clear-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Clear-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-116">`Copy-Item`Cmdlet 您可以藉 `Path` `Destination` `Recurse` `Copy-Item` 由執行[ContainerCmdletprovider. Copyitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)方法，定義由 Cmdlet 的、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-116">`Copy-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Destination`, and `Recurse` parameters of the `Copy-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-117">ChildItems 指令程式：您可以藉由執行 ContainerCmdletprovider \* 方法，來定義由 Cmdlet 的和參數所觸發的動態參數 `Path` `Recurse` `Get-ChildItem` 。 [Getchilditemsdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters)和[system.web. ContainerCmdletprovider. Getchildnamesdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters)方法。</span><span class="sxs-lookup"><span data-stu-id="24e58-117">Get-ChildItems cmdlet You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Get-ChildItem` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) and [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) methods.</span></span>

<span data-ttu-id="24e58-118">`Get-Content`Cmdlet 您可以藉 `Path` `Get-Content` 由執行[IcontentCmdletprovider. Getcontentreaderdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-118">`Get-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-119">`Get-Item`Cmdlet 您可以藉 `Path` `Get-Item` 由執行[ItemCmdletprovider. Getitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-119">`Get-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Get-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-120">`Get-ItemProperty`Cmdlet 您可以藉 `Path` `Name` `Get-ItemProperty` 由執行[IpropertyCmdletprovider. Getpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-120">`Get-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Get-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-121">`Invoke-Item`Cmdlet 您可以藉 `Path` `Invoke-Item` 由執行[ItemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-121">`Invoke-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Invoke-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-122">`Move-Item`Cmdlet 您可以藉 `Path` `Destination` `Move-Item` 由執行[NavigationCmdletprovider. Moveitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-122">`Move-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Destination` parameters of the `Move-Item` cmdlet by implementing the [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-123">`New-Item`Cmdlet 您可以藉 `Path` `ItemType` `Value` `New-Item` 由執行[ContainerCmdletprovider. Newitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters)方法，定義由 Cmdlet 的、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-123">`New-Item` cmdlet You can define dynamic parameters that are triggered by the `Path`, `ItemType`, and `Value` parameters of the `New-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-124">`New-ItemProperty`Cmdlet 您可以藉 `Path` `Name` `PropertyType` `Value` `New-ItemProperty` 由執行[IdynamicpropertyCmdletprovider. Newpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters)方法，定義由 Cmdlet 的、、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-124">`New-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path`, `Name`, `PropertyType`, and `Value` parameters of the `New-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-125">`New-PSDrive`Cmdlet 您可以藉[System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) `New-PSDrive` 由執行[DriveCmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters)方法，定義由 Cmdlet 所傳回之System.Management.Automation.PSDriveinfo 物件所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-125">`New-PSDrive` cmdlet You can define dynamic parameters that are triggered by the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object returned by the `New-PSDrive` cmdlet by implementing the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-126">`Remove-Item`您可以藉 `Path` `Recurse` `Remove-Item` 由執行[ContainerCmdletprovider. Removeitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-126">`Remove-Item` You can define dynamic parameters that are triggered by the `Path` and `Recurse` parameters of the `Remove-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-127">`Remove-ItemProperty`您可以藉 `Path` `Name` `Remove-ItemProperty` 由執行[IdynamicpropertyCmdletprovider. Removepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-127">`Remove-ItemProperty` You can define dynamic parameters that are triggered by the `Path` and `Name` parameters of the `Remove-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-128">`Rename-Item`Cmdlet 您可以藉 `Path` `NewName` `Rename-Item` 由執行[ContainerCmdletprovider. Renameitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-128">`Rename-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `NewName` parameters of the `Rename-Item` cmdlet by implementing the [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-129">`Rename-ItemProperty`您可以藉 `Path` `Name` `NewName` `Rename-ItemProperty` 由執行[IdynamicpropertyCmdletprovider. Renamepropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters)方法，定義由 Cmdlet 的、和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-129">`Rename-ItemProperty` You can define dynamic parameters that are triggered by the `Path`, `Name`, and `NewName` parameters of the `Rename-ItemProperty` cmdlet by implementing the [System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-130">`Set-Content`Cmdlet 您可以藉 `Path` `Set-Content` 由執行[IcontentCmdletprovider. Getcontentwriterdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-130">`Set-Content` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Set-Content` cmdlet by implementing the [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-131">`Set-Item`Cmdlet 您可以藉 `Path` `Value` `Set-Item` 由執行[ItemCmdletprovider. Setitemdynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-131">`Set-Item` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-132">`Set-ItemProperty`Cmdlet 您可以藉 `Path` `Value` `Set-Item` 由執行[IpropertyCmdletprovider. Setpropertydynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)方法，定義由 Cmdlet 的和參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-132">`Set-ItemProperty` cmdlet You can define dynamic parameters that are triggered by the `Path` and `Value` parameters of the `Set-Item` cmdlet by implementing the [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) method.</span></span>

<span data-ttu-id="24e58-133">`Test-Path`Cmdlet 您可以藉 `Path` `Test-Path` 由執行[ItemCmdletprovider. Invokedefaultactiondynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters)方法，定義由 Cmdlet 的參數所觸發的動態參數。</span><span class="sxs-lookup"><span data-stu-id="24e58-133">`Test-Path` cmdlet You can define dynamic parameters that are triggered by the `Path` parameter of the `Test-Path` cmdlet by implementing the [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) method.</span></span>

## <a name="see-also"></a><span data-ttu-id="24e58-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e58-134">See Also</span></span>

[<span data-ttu-id="24e58-135">撰寫 Windows PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="24e58-135">Writing a Windows PowerShell Provider</span></span>](./writing-a-windows-powershell-provider.md)
