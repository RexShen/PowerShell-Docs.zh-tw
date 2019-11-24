---
title: Windows PowerShell 提供者總覽 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82244fbd-07b9-47f3-805c-3fb90ebbf58a
caps.latest.revision: 13
ms.openlocfilehash: 81f6c8cd75ccea9e711cd8f6d6daa6cca5a499a0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366287"
---
# <a name="windows-powershell-provider-overview"></a>Windows PowerShell 提供者概觀

Windows PowerShell 提供者可讓任何資料存放區與檔案系統一樣公開，就像它是裝載的磁片磁碟機一樣。 例如，內建的登錄提供者可讓您流覽登錄，就像流覽電腦的 `c` 磁片磁碟機一樣。 提供者也可以覆寫 `Item` 的 Cmdlet （例如，`Get-Item`、`Set-Item`等等），讓您的資料存放區中的資料可以被處理，例如在流覽檔案系統時處理檔案和目錄。 如需提供者和磁片磁碟機的詳細資訊，以及 Windows PowerShell 中的內建提供者，請參閱[about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers)。

## <a name="providers-and-drives"></a>提供者和磁片磁碟機

提供者會定義用來存取、流覽和編輯資料存放區的邏輯，而磁片磁碟機會指定提供者所定義之類型的特定進入點給資料存放區（或資料存放區的一部分）。 例如，登錄提供者可讓您存取登錄中的 hive 和機碼，而 HKLM 和 HKCU 磁片磁碟機會在登錄中指定對應的 hive。 HKLM 和 HKCU 磁片磁碟機都使用登錄提供者。

當您撰寫提供者時，可以指定在提供者可用時自動建立的預設磁片磁碟機（磁片磁碟機）。 您也會定義方法，以建立使用該提供者的新磁片磁碟機。

## <a name="type-of-providers"></a>提供者類型

有數種類型的提供者，每個都提供不同層級的功能。 提供者會實作為衍生自[SessionStateCategory](/dotnet/api/system.management.automation.sessionstatecategory?view=pscore-6.2.0) **CmdletProvider**類別的其中一個子系的類別。 如需不同類型之提供者的詳細資訊，請參閱[提供者類型](./provider-types.md)。

## <a name="provider-cmdlets"></a>提供者 Cmdlet

提供者可以執行對應至 Cmdlet 的方法，並在該提供者的磁片磁碟機中使用這些 Cmdlet 時，建立這些指令程式的自訂行為。 視提供者的類型而定，有不同的 Cmdlet 集可供使用。 如需提供者中可供自訂的 Cmdlet 完整清單，請參閱[提供者 Cmdlet](./provider-cmdlets.md)。

## <a name="provider-paths"></a>提供者路徑

使用者流覽提供者磁片磁碟機，例如檔案系統。 因此，它們預期路徑的語法會對應至檔案系統導覽中使用的路徑。 當使用者執行 provider Cmdlet 時，它們會指定要存取之專案的路徑。 您可以透過數種方式來解讀指定的路徑。 提供者應支援下列一或多個路徑類型。

### <a name="drive-qualified-paths"></a>磁片磁碟機限定路徑

磁片磁碟機限定路徑是專案名稱、專案所在的容器和子容器的組合，以及用來存取專案的 Windows PowerShell 磁片磁碟機。 （磁片磁碟機是由用來存取資料存放區的提供者所定義。 這個路徑的開頭是磁片磁碟機名稱，後面接著冒號（:)。 例如：`get-childitem C:`

### <a name="provider-qualified-paths"></a>提供者限定路徑

為了讓 Windows PowerShell 引擎初始化和取消初始化您的提供者，提供者必須支援提供者限定的路徑。 例如，使用者可以初始化並解除初始化 FileSystem 提供者，因為它會定義下列提供者限定的路徑： `FileSystem::\\uncshare\abc\bar`。

### <a name="provider-direct-paths"></a>提供者-直接路徑

若要允許遠端存取您的 Windows PowerShell 提供者，它應該支援提供者直接路徑，以直接傳遞給目前位置的 Windows PowerShell 提供者。 例如，登錄 Windows PowerShell 提供者可以使用 `\\server\regkeypath` 做為提供者直接路徑。

### <a name="provider-internal-paths"></a>提供者-內部路徑

若要允許 provider Cmdlet 使用非 Windows PowerShell 應用程式開發介面（Api）來存取資料，您的 Windows PowerShell 提供者應該支援提供者內部路徑。 此路徑會在提供者限定路徑中的 "：：" 之後指出。 例如，檔案系統 Windows PowerShell 提供者的提供者內部路徑為 `\\uncshare\abc\bar`。

## <a name="overriding-cmdlet-parameters"></a>覆寫 Cmdlet 參數

某些提供者特定 Cmdlet 的行為可以由提供者覆寫。 如需可覆寫之參數的清單，以及如何在您的提供者類別中覆寫它們，請參閱[provider Cmdlet 參數](./provider-cmdlet-parameters.md)

## <a name="dynamic-parameters"></a>動態參數

當使用者為 Cmdlet 的其中一個靜態參數指定特定值時，提供者可以定義新增至 provider Cmdlet 的動態參數。 提供者會藉由執行一或多個動態參數方法來執行這項工作。 如需可用來新增動態參數的 Cmdlet 參數清單，以及用來執行它們的方法，請參閱[Provider Cmdlet 動態參數](./provider-cmdlet-dynamic-parameters.md)。

## <a name="provider-capabilities"></a>提供者功能

[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉定義了提供者可以支援的許多功能。」 其中包括使用萬用字元、篩選項目和支援交易的能力。 若要指定提供者的功能，請加入[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉的值清單，並結合邏輯 `OR` 作業，做為您提供者類別的 Cmdletproviderattribute[屬性（](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute）的[Providercapabilities *](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities)屬性（屬性（property）的第二個參數（property））的清單。 例如，下列屬性會指定提供者可支援[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **ShouldProcess**和[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities?view=pscore-6.2.0) **交易**功能的，而此元件則是。

```csharp
[CmdletProvider(RegistryProvider.ProviderName, ProviderCapabilities.ShouldProcess | ProviderCapabilities.Transactions)]

```

## <a name="provider-cmdlet-help"></a>提供者 Cmdlet 說明

撰寫提供者時，您可以針對您支援的提供者 Cmdlet，執行自己的說明。 這包括每個提供者 Cmdlet 的單一說明主題，或適用于提供者 Cmdlet 根據動態參數使用方式不同之案例的多個說明主題版本。 若要支援提供者 Cmdlet 特定的說明，您的提供者必須執行[ICmdletprovidersupportshelp](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp)介面。

Windows PowerShell 引擎會呼叫[ICmdletprovidersupportshelp. Gethelpmaml *](/dotnet/api/System.Management.Automation.Provider.ICmdletProviderSupportsHelp.GetHelpMaml)方法，以顯示提供者 Cmdlet 的說明主題。 引擎會提供使用者執行 `Get-Help` Cmdlet 時指定的 Cmdlet 名稱和使用者的目前路徑。 如果您的提供者針對不同的磁片磁碟機執行相同提供者 Cmdlet 的不同版本，則需要目前的路徑。 方法必須傳回包含 Cmdlet 說明之 XML 的字串。

說明檔的內容是使用 PSMAML XML 來撰寫。 這是用來撰寫獨立 Cmdlet 之說明內容的相同 XML 架構。 將自訂 Cmdlet 說明的內容新增至 `CmdletHelpPaths` 元素下提供者的說明檔。 下列範例顯示單一提供者 Cmdlet 的 `command` 元素，並顯示如何指定提供者的提供者 Cmdlet 名稱。 支援

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