---
title: 指令程式概觀 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK]
- cmdlets [PowerShell SDK], described
ms.assetid: 0aa32589-4447-4ead-a5dd-a3be99113140
caps.latest.revision: 21
ms.openlocfilehash: a53b1ada46ad614af3522e6cc11e187afb76e7b1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855314"
---
# <a name="cmdlet-overview"></a>Cmdlet 概觀

Cmdlet 是 Windows PowerShell 環境中使用的輕量型命令。 Windows PowerShell 執行階段會叫用這些 cmdlet，在命令列提供的自動化指令碼的內容中。 Windows PowerShell 執行階段也會叫用它們以程式設計方式透過 Windows PowerShell Api。

## <a name="cmdlets"></a>Cmdlet

Cmdlet 會執行動作，以及通常在管線中下一個命令會傳回 Microsoft.NET Framework 物件。 若要撰寫的 cmdlet，您必須實作 cmdlet 類別衍生自兩個特製化的指令程式的基底類別的其中一個。 在衍生的類別必須是：

- 宣告屬性，可識別為 cmdlet 的衍生的類別。

- 定義以識別做為指令程式參數的公用屬性的屬性裝飾的公用屬性。

- 覆寫一個或多個的輸入處理方法來處理記錄。

您可以載入該組件包含的類別是直接使用[Import-module](/powershell/module/microsoft.powershell.core/import-module) cmdlet，或您可以建立使用載入的組件的主應用程式[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) API。 這兩種方法提供程式設計的方式和命令列功能存取權的 cmdlet。

## <a name="cmdlet-terms"></a>Cmdlet 名詞

下列詞彙常用於 Windows PowerShell cmdlet 文件：

- **Cmdlet 屬性**:用來宣告為 cmdlet 的 cmdlet 類別將.NET Framework 屬性。 雖然 Windows PowerShell 會使用數個其他屬性，都是選擇性，但 Cmdlet 屬性是必要的。 如需有關這個屬性的詳細資訊，請參閱 < [Cmdlet 屬性宣告](./cmdlet-attribute-declaration.md)。

- **Cmdlet 參數**:定義提供給使用者或應用程式執行此 cmdlet 的參數的公用屬性。 Cmdlet 可以具有必要的具名、 位置，並*切換*參數。 切換參數可讓您定義的參數指定在呼叫時，才會進行評估的參數。 如需不同類型的參數的詳細資訊，請參閱[Cmdlet 參數](./cmdlet-parameters.md)。

- **參數集**:可在相同命令中用來執行特定動作的一組參數。 Cmdlet 可以有多個參數集，但每個參數集必須是唯一的至少一個參數。 良好的 cmdlet 設計強烈建議唯一的參數也是必要的參數。 如需參數集的詳細資訊，請參閱[指令程式參數設定](./cmdlet-parameter-sets.md)。

- **動態參數**:新增至 cmdlet，在執行階段參數。 一般而言，動態參數會加入至 cmdlet 的另一個參數設定為特定值時。 如需有關動態參數的詳細資訊，請參閱[Cmdlet 的動態參數](./cmdlet-dynamic-parameters.md)。

- **輸入處理方法**:Cmdlet 可用來處理接收為輸入之記錄的方法。 輸入的處理方法包括[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法， [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法]、 [ [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法，而[System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing)方法。 當您實作的 cmdlet 時，您必須覆寫至少其中一個[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)， [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)，和[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法。 通常[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)方法是您覆寫，因為它會呼叫指令程式會處理每一筆記錄的方法。 相反地， [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)方法並[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)方法會呼叫一次執行前置處理或後置處理的記錄。 如需這些方法的詳細資訊，請參閱[輸入處理方法](./cmdlet-input-processing-methods.md)。

- **ShouldProcess 功能**:Windows PowerShell 可讓您建立 cmdlet，此 cmdlet 會在系統中進行變更之前，提示使用者提供意見反應。 若要使用這項功能，此 cmdlet 必須宣告它支援 ShouldProcess 功能，當您宣告 Cmdlet 屬性，而且 cmdlet 必須呼叫[System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)和[System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)內輸入處理方法的方法。 如需如何支援 ShouldProcess 功能的詳細資訊，請參閱[要求確認](./requesting-confirmation-from-cmdlets.md)。

- **交易**:會被視為單一工作的命令邏輯群組。 如果群組中的任何命令失敗，而且使用者可以選擇接受或拒絕在交易內執行的動作，自動就會失敗的工作。 若要參與交易，此 cmdlet 必須宣告 Cmdlet 屬性宣告時支援交易。 在 Windows PowerShell 2.0 中引進了交易的支援。 如需有關交易的詳細資訊，請參閱[Windows PowerShell 交易](http://msdn.microsoft.com/en-us/74d7bac7-bc53-49f1-a47a-272e8da84710)。

## <a name="how-cmdlets-differ-from-commands"></a>與命令的指令程式有何不同

利用下列方式，與其他命令殼層環境中的命令不同 Cmdlet:

- Cmdlet 是.NET Framework 類別; 的執行個體它們不是獨立的可執行檔。

- 您可以從只需要十幾行程式碼建立 Cmdlet。

- Cmdlet 通常沒有自己的剖析時，錯誤簡報] 或 [輸出格式設定。 Windows PowerShell 執行階段會處理剖析、 錯誤簡報及輸出格式。

- Cmdlet 處理輸入物件從管線中，而不是從資料流的文字，以及 cmdlet 通常會將物件傳遞到管線的輸出。

- Cmdlet 屬於記錄導向因為它們一次處理單一物件。

## <a name="cmdlet-base-classes"></a>指令程式的基底類別

Windows PowerShell 支援從下列兩個基底類別衍生的 cmdlet。

- 大多數的 cmdlet 根據.NET Framework 類別衍生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)基底類別。 衍生自這個類別可讓 cmdlet 在 Windows PowerShell 執行階段上使用相依性的最小集合。 這有兩個優點。 第一個好處是，cmdlet 物件比較小，而且您較不容易受到變更，Windows PowerShell 執行階段。 第二個優點是，如果您需要可以直接建立 cmdlet 物件的執行個體，並叫用將它直接而不是透過 Windows PowerShell 執行階段叫用。

- 更複雜的指令程式根據.NET Framework 類別衍生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)基底類別。 衍生自這個類別可讓您更多存取 Windows PowerShell 執行階段。 此存取權可讓您呼叫指令碼，來存取提供者，並存取目前工作階段狀態的 cmdlet。 （若要存取目前工作階段狀態，您取得和設定工作階段變數與喜好設定。）不過，衍生自這個類別會增加 cmdlet 物件的大小，這表示您的 cmdlet 會更緊密地結合至目前版本的 Windows PowerShell 執行階段。

一般情況下，除非您需要擴充的存取的 Windows PowerShell 執行階段時，您應該衍生自[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別。 不過，Windows PowerShell 執行階段有廣泛的記錄功能的 cmdlet 執行。 如果您稽核的模型取決於這項記錄，您還可以防止您從另一個 cmdlet 中的 cmdlet 執行，藉由衍生自[System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet)類別。

## <a name="input-processing-methods"></a>輸入處理方法

[System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet)類別提供用來處理記錄的下列虛擬方法。 所有衍生的 cmdlet 類別必須覆寫一個或多個第三個方法：

- [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing):用來為 cmdlet 提供選用的一次性、 前置處理功能。

- [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord):用來提供 cmdlet 的-記錄處理功能。 [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)任意數目的次數，或完全沒有，根據指令程式的輸入可能會呼叫方法。

- [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing):用來為 cmdlet 提供選用的一次性、 後置處理功能。

- [System.Management.Automation.Cmdlet.Stopprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing):用來停止處理當使用者停止 cmdlet 以非同步方式 （例如，藉由按下 CTRL + C）。

如需這些方法的詳細資訊，請參閱[Cmdlet 的輸入處理方法](./cmdlet-input-processing-methods.md)。

## <a name="cmdlet-attributes"></a>Cmdlet 屬性

Windows PowerShell 會定義數個管理 cmdlet，並指定通用的功能，Windows PowerShell 所提供，且，可能會需要指令程式所使用的.NET Framework 屬性。 例如，屬性用來指定某個類別，為 cmdlet，以指定之參數的 cmdlet，並要求輸入的驗證，如此 cmdlet 開發人員就不必在其 cmdlet 的程式碼中實作該功能。 如需有關屬性的詳細資訊，請參閱 < [Windows PowerShell 屬性](./cmdlet-attributes.md)。

## <a name="cmdlet-names"></a>Cmdlet 名稱

Windows PowerShell 會使用名稱 cmdlet 動詞和名詞名稱配對。 比方說，`Get-Command`隨附於 Windows PowerShell 的 cmdlet 可用來取得所有 cmdlet，在命令殼層中註冊。 動詞命令識別 cmdlet 所執行的動作和名詞識別此 cmdlet 會在其執行其動作的資源。

.NET Framework 類別宣告為 cmdlet 時，會指定這些名稱。 如需如何將.NET Framework 類別宣告為 cmdlet 的詳細資訊，請參閱[Cmdlet 屬性宣告](./cmdlet-class-declaration.md)。

## <a name="writing-cmdlet-code"></a>撰寫 Cmdlet 程式碼

本文件提供兩種方式可以探索 cmdlet 程式碼撰寫的方式。 如果您想要查看的程式碼，而不需要說明，請參閱[指令程式碼範例](./examples-of-cmdlet-code.md)。 如果您偏好的程式碼有關的詳細說明，請參閱[GetProc 教學課程](./getproc-tutorial.md)， [StopProc 教學課程](./stopproc-tutorial.md)，或[SelectStr 教學課程](./selectstr-tutorial.md)主題。

如需詳細的指導方針撰寫 cmdlet 的詳細資訊，請參閱[指令程式的開發指導](./cmdlet-development-guidelines.md)。

## <a name="see-also"></a>另請參閱

[Windows PowerShell 指令程式概念](./windows-powershell-cmdlet-concepts.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
