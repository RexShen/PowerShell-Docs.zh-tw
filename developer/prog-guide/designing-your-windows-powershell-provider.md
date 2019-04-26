---
title: 設計您的 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], designing
ms.assetid: 11d20319-cc40-4227-b810-4af33372b182
caps.latest.revision: 10
ms.openlocfilehash: 711a85e9b2eade7b9095d7560f53610e709e380a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081813"
---
# <a name="designing-your-windows-powershell-provider"></a>設計 Windows PowerShell 提供者

如果您的產品或組態會公開一組預存的資料，例如，使用者會想要瀏覽，或瀏覽資料庫，您應該實作的 Windows PowerShell 提供者。 此外，如果您的產品會提供一種容器，即使它不是多層級的容器，合理來實作 Windows PowerShell 提供者。 比方說，您可能要實作的 Windows PowerShell 容器提供者 cmdlet 動詞命令複製、 移動、 新增、 重新命名或移除有意義的話會以對產品或組態資料作業。

## <a name="windows-powershell-paths-identify-your-provider"></a>Windows PowerShell 路徑找出您的提供者

Windows PowerShell 執行階段會使用 Windows PowerShell 路徑來存取適當的 Windows PowerShell 提供者。 當指令程式指定其中一個路徑時，執行階段就會知道用來存取相關聯的資料存放區的提供者。 這些路徑包括磁碟機限定路徑、 提供者限定路徑、 提供者直接路徑，與內部提供者路徑。 每個 Windows PowerShell 提供者必須支援一或多個這些路徑。

如需有關 Windows PowerShell 路徑的詳細資訊，請參閱 < Windows PowerShell 的運作方式。

### <a name="defining-a-drive-qualified-path"></a>定義磁碟機限定路徑

若要允許使用者存取位於實體磁碟機的資料，您的 Windows PowerShell 提供者必須支援的磁碟機限定的路徑。 此路徑的開頭加上冒號 （:），例如 mydrive:\abc\bar 的磁碟機名稱。

### <a name="defining-a-provider-qualified-path"></a>定義提供者限定路徑

若要允許的 Windows PowerShell 執行階段，以初始化並取消初始化提供者，您的 Windows PowerShell 提供者必須支援的提供者限定的路徑。 例如，檔案系統::\\\uncshare\abc\bar 是彙編 Windows powershell filesystem 提供者的提供者限定路徑。

### <a name="defining-a-provider-direct-path"></a>定義提供者直接路徑

若要允許遠端存取您的 Windows PowerShell 提供者，它應該支援的提供者直接路徑，直接傳遞至 Windows PowerShell 提供者目前的位置。 比方說，可以使用登錄 Windows PowerShell 提供者\\\server\regkeypath 為提供者直接路徑。

### <a name="defining-a-provider-internal-path"></a>定義提供者內部的路徑

若要允許使用非 Windows PowerShell 應用程式開發介面 (Api) 來存取資料提供者 cmdlet，您的 Windows PowerShell 提供者應該支援的提供者內部的路徑。 此路徑會指出之後":: 「 提供者限定路徑中。 例如，filesystem Windows PowerShell 提供者的提供者內部路徑是\\\uncshare\abc\bar。

## <a name="changing-stored-data"></a>變更預存的資料

當覆寫修改基礎資料存放區的方法，務必呼叫[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)所變更之項目的最新版本的方法方法。 提供者基礎結構會判斷要傳遞到管線中，例如當使用者指定-PassThru 參數時是否需要的項目物件。 如果擷取的最新的項目 （此舉） 是昂貴的作業，您可以測試 Context.PassThru 屬性來判斷您是否真的需要將產生的項目寫入。

## <a name="choose-a-base-class-for-your-provider"></a>選擇您的提供者的基底類別

Windows PowerShell 提供幾個可用來實作您自己的 Windows PowerShell 提供者的基底類別。 當設計提供者，請選擇 基底類別，此區段中，最適合您的需求中所述。

每個 Windows PowerShell 提供者的基底類別提供一組指令程式。 本章節描述 cmdlet，但它不會描述其參數。

使用工作階段狀態，Windows PowerShell 執行階段提供數個位置 cmdlet 到特定的 Windows PowerShell 提供者，例如`Get-Location`， `Set-Location`， `Pop-Location`，和`Push-Location`cmdlet。 您可以使用`Get-Help`cmdlet 來取得這些 location cmdlet 的相關資訊。

### <a name="cmdletprovider-base-class"></a>CmdletProvider 基底類別

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)類別會定義基本的 Windows PowerShell 提供者。 這個類別支援的提供者宣告，而且提供了許多的屬性和方法可用於所有 Windows PowerShell 提供者。 類別由`Get-PSProvider`cmdlet 來列出所有可用的提供者工作階段。 這個指令程式的實作是由工作階段狀態提供。

> [!NOTE]
> Windows PowerShell 提供者可供所有 Windows PowerShell 語言的領域。

### <a name="drivecmdletprovider-base-class"></a>DriveCmdletProvider 基底類別

[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)類別會定義 Windows PowerShell 磁碟機提供者支援為加入新的磁碟機、 移除現有的磁碟機，並初始化預設磁碟機的作業。 比方說，提供 Windows powershell FileSystem 提供者初始化所裝載，例如硬碟機和 CD/DVD 裝置磁碟機的所有磁碟區的磁碟機。

這個類別衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別。 下表列出這個類別所公開的 cmdlet。 除了所列， `Get-PSDrive` （由工作階段狀態） 的 cmdlet 是用來擷取可用的磁碟機的相關的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`New-PSDrive`|工作階段中，建立新的磁碟機，及資料流的磁碟機資訊。|
|`Remove-PSDrive`|從工作階段中移除的磁碟機。|

### <a name="itemcmdletprovider-base-class"></a>ItemCmdletProvider 基底類別

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)類別定義的資料存放區中，個別的項目執行作業的 Windows PowerShell 項目提供者並不會假設任何容器或瀏覽功能。 這個類別衍生自[System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)基底類別。 下表列出這個類別所公開的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`Clear-Item`|清除目前內容的指定位置的項目，並取代"clear"的值，指定提供者。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Get-Item`|從指定的位置，擷取項目及資料流結果物件。|
|`Invoke-Item`|叫用的項目位於指定路徑的預設動作。|
|`Set-Item`|在指定的值與指定的位置設定的項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Resolve-Path`|解析的 Windows PowerShell 路徑和資料流路徑資訊的萬用字元。|
|`Test-Path`|測試指定的路徑，並傳回`true`若有的話，`false`否則。 此 cmdlet 實作以支援`IsContainer`參數[System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)方法。|

### <a name="containercmdletprovider-base-class"></a>ContainerCmdletProvider 基底類別

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)類別定義，資料存放區項目的容器，向使用者公開 （expose） 的 Windows PowerShell 容器提供者。 請注意一個容器 （沒有巢狀容器），在它的項目時，可以使用 Windows PowerShell 容器提供者。 如果沒有巢狀的容器，您必須實作的 Windows PowerShell 巡覽提供者。

這個類別衍生自[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)基底類別。 下表定義這個類別所實作的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`Copy-Item`|將項目從一個位置到另一個。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Get-Childitem`|擷取的子系項目，在指定的位置，並將它們串流做為物件。|
|`New-Item`|在指定的位置，建立新的項目及資料流結果物件。|
|`Remove-Item`|從指定的位置移除項目。|
|`Rename-Item`|重新命名指定的位置處的項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|

### <a name="navigationcmdletprovider-base-class"></a>NavigationCmdletProvider 基底類別

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)類別會定義 Windows PowerShell 巡覽提供者，以執行作業使用多個容器的項目。 這個類別衍生自[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)基底類別。 下表列出這個類別所公開的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|Combine-Path|合併成單一路徑，使用特定提供者路徑之間分隔符號的兩個路徑。 這個指令程式串流處理字串。|
|`Move-Item`|將項目移到指定的位置。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|

相關的 cmdlet 是 Windows powershell 提供基本的剖析路徑 cmdlet。 此 cmdlet 可用來剖析支援的 Windows PowerShell 路徑`Parent`參數。 資料流處理的父路徑的字串。

## <a name="select-provider-interfaces-to-support"></a>選擇要支援的提供者介面

除了衍生自其中一個 Windows PowerShell 的基底類別，您的 Windows PowerShell 提供者可以藉由衍生自一或多個下列的提供者介面支援其他功能。 此區段會定義這些介面和支援的每個 cmdlet。 它不會描述介面支援 cmdlet 的參數。 Cmdlet 參數資訊，可使用線上`Get-Command`和`Get-Help`cmdlet。

### <a name="icontentcmdletprovider"></a>IContentCmdletProvider

[System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)介面會定義內容提供者上執行作業內容的資料項目。 下表列出此介面所公開的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`Add-Content`|將指定的值長度附加至指定的項目內容。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Clear-Content`|將指定項目的內容設定為"clear"的值。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Get-Content`|擷取指定的項目內容及資料流結果物件。|
|`Set-Content`|取代現有的內容，針對指定的項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|

### <a name="ipropertycmdletprovider"></a>IPropertyCmdletProvider

[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)介面會定義屬性的 Windows PowerShell 提供者執行的項目屬性的作業資料存放區中。 下表列出此介面所公開的 cmdlet。

> [!NOTE]
> `Path`需這些 cmdlet 的參數表示的項目，而不是識別屬性的路徑。

|Cmdlet|定義|
|------------|----------------|
|`Clear-ItemProperty`|將指定項目的屬性設定為"clear"的值。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Get-ItemProperty`|從指定的項目擷取屬性及資料流結果物件。|
|`Set-ItemProperty`|設定指定的項目，以指示的值的屬性。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|

### <a name="idynamicpropertycmdletprovider"></a>IDynamicPropertyCmdletProvider

[System.Management.Automation.Provider.Idynamicpropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider)介面，衍生自[System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider)，定義提供者來指定其支援的 cmdlet 的動態參數。 這種類型的提供者處理為其屬性可以定義在執行階段，比方說，新的屬性作業的作業。 無法以靜態方式定義屬性的項目上，可能發生這類作業。 下表列出此介面所公開的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`Copy-ItemProperty`|將屬性從指定的項目複製到另一個項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`Move-ItemProperty`|將屬性從指定的項目移至另一個項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|
|`New-ItemProperty`|建立屬性上指定的項目，並串流處理結果的物件。|
|`Remove-ItemProperty`|移除指定的項目屬性。|
|`Rename-ItemProperty`|重新命名屬性，以指定的項目。 此 cmdlet 未通過管線的輸出物件，除非其`PassThru`指定參數。|

### <a name="isecuritydescriptorcmdletprovider"></a>ISecurityDescriptorCmdletProvider

[System.Management.Automation.Provider.Isecuritydescriptorcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ISecurityDescriptorCmdletProvider)介面新增至提供者的安全性描述元的功能。 此介面可讓使用者取得和設定資料存放區中的項目之安全性描述元資訊。 下表列出此介面所公開的 cmdlet。

|Cmdlet|定義|
|------------|----------------|
|`Get-Acl`|擷取存取控制清單 (ACL)，也就是用來保護作業系統資源，例如安全性描述元、 檔案或物件的組件中所包含的資訊。|
|`Set-Acl`|設定 ACL 的資訊。 它的執行個體的格式[System.Security.Accesscontrol.Objectsecurity](/dotnet/api/System.Security.AccessControl.ObjectSecurity)上指定路徑所指定的項目。 這個指令程式可以在登錄或任何其他提供者項目設定檔、 金鑰和子機碼的相關資訊，如果 Windows PowerShell 提供者支援的安全性資訊的設定。|

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 的運作方式](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Windows PowerShell SDK](../windows-powershell-reference.md)