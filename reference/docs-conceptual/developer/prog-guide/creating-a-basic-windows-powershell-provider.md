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
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360517"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>建立基本的 Windows PowerShell 提供者

本主題是學習如何建立 Windows PowerShell 提供者的起點。 這裡所述的基本提供者提供啟動和停止提供者的方法，雖然此提供者並未提供存取資料存放區或取得或設定資料存放區中之資料的方式，但它確實提供了所需的基本功能所有提供者。

如先前所述，這裡所描述的基本提供者會執行啟動和停止提供者的方法。 Windows PowerShell 執行時間會呼叫這些方法，以初始化並解除初始化提供者。

> [!NOTE]
> 您可以在 Windows PowerShell 所提供的 AccessDBSampleProvider01.cs 檔案中找到此提供者的範例。

## <a name="defining-the-windows-powershell-provider-class"></a>定義 Windows PowerShell 提供者類別

建立 Windows PowerShell 提供者的第一個步驟是定義它的 .NET 類別。 這個基本提供者會定義一個名為 `AccessDBProvider` 的類別，衍生自[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類。

建議您將提供者類別放在 API 命名空間的 `Providers` 命名空間中，例如 xxx。PowerShell. 提供者。 此提供者會使用 `Microsoft.Samples.PowerShell.Provider` 命名空間，其中所有的 Windows PowerShell 提供者範例都會在其中執行。

> [!NOTE]
> Windows PowerShell 提供者的類別必須明確標示為公用。 未標示為公用的類別會預設為內部，且不會由 Windows PowerShell 執行時間找到。

以下是此基本提供者的類別定義：

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

在類別定義之前，您必須使用語法 [CmdletProvider （）] 來宣告[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性（attribute）。

您可以設定屬性關鍵字，以便在必要時進一步宣告類別。 請注意，此處所宣告的[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)屬性包含兩個參數。 第一個屬性參數會指定提供者的預設易記名稱，供使用者稍後修改。 第二個參數會指定在命令處理期間，提供者公開給 Windows PowerShell 執行時間的 Windows PowerShell 定義功能。 提供者功能的可能值是由[Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)列舉所定義。 因為這是基底提供者，所以不支援任何功能。

> [!NOTE]
> Windows PowerShell 提供者的完整名稱包括在註冊提供者時，由 Windows PowerShell 決定的元件名稱和其他屬性。

## <a name="defining-provider-specific-state-information"></a>定義提供者特定的狀態資訊

[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider)基類和所有衍生類別都會被視為無狀態，因為 Windows PowerShell 執行時間只會在必要時建立提供者實例。 因此，如果您的提供者需要提供者特定資料的完整控制和狀態維護，它必須從[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)類別衍生類別。 您的衍生類別應該定義維護狀態所需的成員，如此一來，當 Windows PowerShell 執行時間呼叫[Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法來初始化提供者時，即可存取提供者特定的資料。

Windows PowerShell 提供者也可以維護以連接為基礎的狀態。 如需維護線上狀態的詳細資訊，請參閱[建立 PowerShell 磁片磁碟機提供者](./creating-a-windows-powershell-drive-provider.md)。

## <a name="initializing-the-provider"></a>初始化提供者

若要初始化提供者，當 Windows PowerShell 啟動時，Windows PowerShell 執行時間會呼叫[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法。 在大部分的情況下，您的提供者可以使用這個方法的預設實值，這只會傳回描述提供者的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件。 不過，如果您想要加入額外的初始化資訊，則應該執行自己的[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回已修改的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件版本，並將其傳遞給您的提供者。 一般來說，這個方法應該會傳回傳遞給它的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，或已修改的[Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo)物件，其中包含其他的初始化資訊。

這個基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示此方法的預設執行：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

提供者可以維護提供者特定資訊的狀態，如[定義提供者特定的資料狀態](#defining-provider-specific-state-information)中所述。 在此情況下，您的執行必須覆寫[Cmdletprovider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)方法，以傳回衍生類別的實例。

## <a name="start-dynamic-parameters"></a>啟動動態參數

您的提供者[Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start)可能需要額外的參數，才能執行。 在這種情況下，提供者應該覆寫[Cmdletprovider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters)方法，並傳回具有屬性和欄位的物件，其具有類似 Cmdlet 類別或[Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)物件的剖析屬性。

這個基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示此方法的預設執行：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>取消初始化提供者

為了釋放 Windows PowerShell 提供者所使用的資源，您的提供者應該執行自己的[Cmdletprovider *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop)方法。 這個方法是由 Windows PowerShell 執行時間呼叫，以便在會話結束時將提供者解除初始化。

這個基本提供者不會覆寫這個方法。 不過，下列程式碼會顯示此方法的預設執行：

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>範例程式碼

如需完整的範例程式碼，請參閱[AccessDbProviderSample01 程式碼範例](./accessdbprovidersample01-code-sample.md)。

## <a name="testing-the-windows-powershell-provider"></a>測試 Windows PowerShell 提供者

當您的 Windows PowerShell 提供者已向 Windows PowerShell 註冊之後，您可以在命令列上執行支援的 Cmdlet 來進行測試。 針對此基本提供者，請執行新的 shell，並使用 `Get-PSProvider` Cmdlet 來抓取提供者清單，並確認 AccessDb 提供者存在。

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
