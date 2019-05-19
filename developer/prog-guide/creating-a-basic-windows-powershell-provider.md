---
title: 建立基本的 Windows PowerShell 提供者 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: 5ebc22067b20f0e1d35d31d5f33e599f50cb7564
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855074"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>建立基本的 Windows PowerShell 提供者

本主題是起始點，以了解如何建立 Windows PowerShell 提供者。 此處所述的基本提供者會提供方法來啟動和停止提供者，與此提供者不能用來存取資料存放區，或取得或設定資料存放區中的資料，雖然它提供所需的基本功能所有的提供者。

前面提過，所述的基本提供者這裡實作方法來啟動和停止提供者。 Windows PowerShell 執行階段呼叫這些方法來初始化，並取消初始化提供者。

> [!NOTE]
> 您可以在 Windows PowerShell 所提供的 AccessDBSampleProvider01.cs 檔案中找到此提供者的範例。

## <a name="defining-the-windows-powershell-provider-class"></a>定義 Windows PowerShell 提供者類別

建立 Windows PowerShell 提供者的第一個步驟是定義它的.NET 類別。 此基本提供者會定義一個叫做類別`AccessDBProvider`衍生自[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別。

建議您將放在您提供者類別`Providers`API 命名空間，比方說，xxx 的命名空間。PowerShell.Providers。 此提供者使用`Microsoft.Samples.PowerShell.Provider`命名空間，在其中執行所有的 Windows PowerShell 提供者範例。

> [!NOTE]
> Windows PowerShell 提供者的類別必須明確標示為公用。 未標示為公用的類別會預設為內部，並且將找不到 Windows PowerShell 執行階段。

以下是此基本提供者的類別定義：

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

直接在類別定義之前，您必須宣告[System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性，且 [CmdletProvider()] 的語法。

您可以設定屬性的關鍵字，以進一步在必要時在類別宣告。 請注意， [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)此宣告的屬性包括兩個參數。 第一個屬性參數會指定預設的易記名稱的提供者，使用者之後可以修改。 第二個參數指定命令處理期間提供者會公開 Windows PowerShell 執行階段的 Windows PowerShell 定義功能。 所定義的提供者功能的可能值[System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉型別。 因為這是基底提供者時，它會支援任何功能。

> [!NOTE]
> Windows PowerShell 提供者的完整的名稱包括組件名稱和其他屬性取決於 Windows PowerShell 提供者註冊時。

## <a name="defining-provider-specific-state-information"></a>定義提供者專屬的狀態資訊

[System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基底類別及所有衍生的類別會視為無狀態，因為 Windows PowerShell 執行階段會建立只有所需的提供者執行個體。 因此，如果您的提供者的提供者特定資料，需要完整控制和維護狀態，它必須衍生的類別[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)類別。 您的衍生的類別應該定義需要維護狀態，以便在 Windows PowerShell 執行階段呼叫時，就可存取的提供者特定資料成員[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者。

Windows PowerShell 提供者也可以維護連接為基礎的狀態。 如需有關維護連線狀態的詳細資訊，請參閱[建立 PowerShell 磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

## <a name="initializing-the-provider"></a>初始化提供者

若要初始化提供者，Windows PowerShell 執行階段會呼叫[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)啟動 Windows PowerShell 時的方法。 大部分的情況下，您的提供者可以使用這個方法，只會傳回的預設實作[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，描述您的提供者。 不過，在您要新增額外的初始化資訊的情況下，您應該實作您自己[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法會傳回的修改的版本[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)傳遞至您的提供者的物件。 一般情況下，此方法應傳回提供[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件傳遞給它或已修改[System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件包含其他的初始化資訊。

此基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示這個方法的預設實作：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

提供者可以維護提供者專屬資訊的狀態，如中所述[定義提供者特有資料狀態](#defining-provider-specific-state-information)。 在此情況下，您的實作必須覆寫[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回衍生的類別的執行個體。

## <a name="start-dynamic-parameters"></a>啟動 動態參數

提供者實作的[System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法可能會需要額外的參數。 在此情況下，提供者應該覆寫[System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法，並傳回的物件具有屬性和欄位的剖析屬性類似於cmdlet 類別或[System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件。

此基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示這個方法的預設實作：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>未初始化的提供者

若要釋出 Windows PowerShell 提供者所使用的資源，您的提供者必須實作自己[System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。 停止初始化工作階段關閉提供者的 Windows PowerShell 執行階段會呼叫這個方法。

此基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示這個方法的預設實作：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>程式碼範例

完整的範例程式碼，請參閱[AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

一旦您的 Windows PowerShell 提供者註冊使用 Windows PowerShell 之後，您可以藉由在命令列上執行受支援的 cmdlet 來進行測試。 此基本提供者，請執行新的殼層，並使用`Get-PSProvider`cmdlet 來擷取提供者的清單，並確保有 AccessDb 提供者。

```powershell
Get-PSProvider
```

會出現下列輸出：

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>另請參閱

[建立 Windows PowerShell 提供者](./how-to-create-a-windows-powershell-provider.md)

[設計您的 Windows PowerShell 提供者](./designing-your-windows-powershell-provider.md)