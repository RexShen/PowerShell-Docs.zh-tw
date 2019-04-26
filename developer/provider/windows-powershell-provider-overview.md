---
title: Windows PowerShell 提供者概觀 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 0d4addc0a064873701ae15c204dbd335f3374ab7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080897"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell 提供者概觀

Windows PowerShell 提供者可讓任何資料存放區，如同它已掛接的磁碟機，例如檔案系統公開。 例如，內建的登錄提供者可讓您瀏覽登錄，例如，請瀏覽`c`您電腦的磁碟機。 提供者也可以覆寫`Item`cmdlet (例如`Get-Item`，`Set-Item`等等)，使您的資料存放區中的資料可以被視為檔案，並且瀏覽檔案系統時，會視為目錄。 如需有關提供者磁碟機和在 Windows PowerShell 中內建的提供者的詳細資訊，請參閱 < [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。

## <a name="providers-and-drives"></a>提供者和磁碟機

提供者會定義用來存取、 巡覽及編輯的資料存放區中，而磁碟機指定提供者所定義的類型的特定進入點的資料存放區 （或資料存放區的一部分） 的邏輯。 比方說，登錄提供者可讓您存取 hive 和在登錄中，索引鍵和 HKLM 與 HKCU 的磁碟機指定對應的登錄區中登錄。 HKLM 與 HKCU 磁碟機這兩個使用登錄提供者。

當您撰寫的提供者時，您可以指定預設磁碟機磁碟機提供者可用時自動建立。 您也會定義方法，以建立新的磁碟機，使用該提供者。

## <a name="type-of-providers"></a>提供者的型別

有數種類型的提供者，其中每個提供不同的層級的功能。 提供者會實作為類別衍生自其中一個子系[System.Management.Automation.Sessionstatecategory.Cmdletprovider](/dotnet/api/System.Management.Automation.SessionStateCategory.CmdletProvider)類別。 如需不同類型的提供者資訊，請參閱[提供者類型](./provider-types.md)。

## <a name="provider-cmdlets"></a>提供者 Cmdlet

提供者可實作方法對應至 cmdlet，建立在磁碟機中使用該提供者時，這些 cmdlet 的自訂行為。 提供者的類型，根據不同的 cmdlet 可用。 自訂提供者中可用之 cmdlet 的完整清單，請參閱 <<c0> [ 提供者 cmdlet](./provider-cmdlets.md)。

## <a name="provider-paths"></a>提供者路徑

使用者瀏覽檔案系統等的提供者磁碟機。 基於這個原因，則會預期要對應至用於檔案系統巡覽路徑的路徑語法。 當使用者執行的提供者 cmdlet 時，它們會指定要存取之項目的路徑。 以數種方式可以解譯為指定的路徑。 提供者應該支援一或多個下列的路徑類型。

### <a name="drive-qualified-paths"></a>磁碟機限定路徑

磁碟機限定的路徑是項目名稱、 容器和子容器中的項目所在，以及透過它存取的 Windows PowerShell 磁碟機的組合。 （磁碟機是用來存取資料存放區提供者所定義的。 此路徑的開頭加上冒號 （:） 磁碟機名稱。 例如：`get-childitem C:`

### <a name="provider-qualified-paths"></a>提供者限定路徑

若要讓 Windows PowerShell 引擎初始化，並取消初始化您的提供者，提供者必須支援的提供者限定的路徑。 例如，使用者可以初始化和解除初始化 FileSystem 提供者，因為它會定義下列的提供者限定路徑： `FileSystem::\\uncshare\abc\bar`。

### <a name="provider-direct-paths"></a>提供者直接路徑

若要允許遠端存取您的 Windows PowerShell 提供者，它應該支援的提供者直接路徑，直接傳遞至 Windows PowerShell 提供者目前的位置。 比方說，可以使用登錄 Windows PowerShell 提供者`\\server\regkeypath`為提供者直接路徑。

### <a name="provider-internal-paths"></a>提供者內部的路徑

若要允許使用非 Windows PowerShell 應用程式開發介面 (Api) 來存取資料提供者 cmdlet，您的 Windows PowerShell 提供者應該支援的提供者內部的路徑。 此路徑會指出之後":: 「 提供者限定路徑中。 例如，filesystem Windows PowerShell 提供者的提供者內部路徑是`\\uncshare\abc\bar`。

## <a name="overriding-cmdlet-parameters"></a>覆寫的 cmdlet 參數

提供者可以覆寫某些提供者特定 cmdlet 的行為。 一份參數可覆寫，以及如何在您的提供者類別中覆寫它們，請參閱[提供者 cmdlet 參數](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>動態參數

提供者可以定義當使用者指定的特定值的其中一個靜態參數的 cmdlet 會加入至提供者 cmdlet 的動態參數。 提供者會藉由實作一或多個動態參數的方法。 如需可用來將動態參數，以及用來實作它們的方法的 cmdlet 參數的清單，請參閱 <<c0> [ 提供者 cmdlet 的動態參數](./provider-cmdlet-dynamic-parameters.md)。

## <a name="provider-capabilities"></a>提供者功能

[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別定義數個提供者可支援的功能。 其中包括能夠使用萬用字元，篩選項目，並支援交易。 若要指定提供者功能，新增的值清單[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別，與邏輯結合`OR`作業，做為[System.Management.Automation.Provider.Cmdletproviderattribute.Providercapabilities*](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities)屬性 （屬性的第二個參數） [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性提供者類別。 例如，下列屬性會指定提供者支援[System.Management.Automation.Provider.Providercapabilities.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.ShouldProcess)和[System.Management.Automation.Provider.Providercapabilities.Transactions](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities.Transactions)功能。

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>提供者 cmdlet 說明

當撰寫提供者，您可以實作您自己的您所支援的提供者 cmdlet 的說明。 這包括單一的 [說明] 主題，每個提供者 cmdlet 或多個版本的情況下的提供者 cmdlet，可根據動態參數的使用說明主題。 若要支援提供者特定 cmdlet 的說明，您的提供者必須實作[System.Management.Automation.Provider.Icmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp)介面。

Windows PowerShell 引擎會呼叫[System.Management.Automation.Provider.Icmdletprovidersupportshelp.Gethelpmaml*](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml)方法，以顯示您的提供者 cmdlet 的說明主題。 引擎會提供使用者在執行時所指定的 cmdlet 名稱`Get-Help`指令程式和使用者的目前路徑。 如果您的提供者實作不同版本的不同磁碟機的相同提供者 cmdlet 需要目前的路徑。 此方法必須傳回字串，包含用於 cmdlet 說明的 XML。

說明檔的內容是使用 PSMAML XML 所撰寫的。 這是相同的 XML 結構描述，用於寫入獨立 cmdlet 的說明內容。 新增您的自訂 cmdlet 的說明檔說明您的提供者的內容下`CmdletHelpPaths`項目。 下列範例所示`command`單一提供者 cmdlet，而且它的項目會顯示您指定的提供者 cmdlet 名稱的方式，您的提供者。 支援

```xml
<CmdletHelpPaths>
  <command:command>
    <command:details>
      <command:name>ProviderCmdletName</command:name>
      <command:verb>Verb</command:verb>
      <command:noun>Noun</command:noun>
    <command:details>
  </command:command>
<CmdletHelpPath>
```

## <a name="see-also"></a>另請參閱

[Windows PowerShell 提供者功能](./provider-types.md)

[提供者 Cmdlet](./provider-cmdlets.md)

[撰寫 Windows PowerShell 提供者](./writing-a-windows-powershell-provider.md)