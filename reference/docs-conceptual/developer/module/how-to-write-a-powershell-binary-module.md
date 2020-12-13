---
ms.date: 09/13/2016
ms.topic: reference
title: 如何撰寫 PowerShell 二進位模組
description: 如何撰寫 PowerShell 二進位模組
ms.openlocfilehash: 1d5cea474ac418f78cc782360b7c23b7614d6669
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663061"
---
# <a name="how-to-write-a-powershell-binary-module"></a>如何撰寫 PowerShell 二進位模組

二進位模組可以是包含 Cmdlet 類別 ( .dll) 的任何元件。 根據預設，匯入二進位模組時，會匯入元件中的所有 Cmdlet。 不過，您可以藉由建立根模組是元件的模組資訊清單來限制匯入的 Cmdlet。  (例如，資訊清單的 CmdletsToExport 索引鍵只能用來匯出所需的 Cmdlet。 ) 此外，二進位模組也可以包含其他檔案、目錄結構，以及單一 Cmdlet 無法使用的其他有用的管理資訊。

下列程式說明如何建立和安裝 PowerShell 二進位模組。

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>如何建立和安裝 PowerShell 二進位模組

1. 建立二進位 PowerShell 解決方案 (例如以 c # ) 撰寫的 Cmdlet，以及您所需的功能，並確保它能正常執行。

   從程式碼的觀點來看，二進位模組的核心只是一個 Cmdlet 元件。 事實上，在載入和卸載的過程中，PowerShell 會將單一 Cmdlet 元件視為模組，而不會對開發人員進行額外的工作。 如需撰寫 Cmdlet 的詳細資訊，請參閱 [撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

2. 如有必要，請建立解決方案的其餘部分： (其他 Cmdlet、XML 檔案等) 並使用模組資訊清單加以描述。

   除了描述您解決方案中的 Cmdlet 元件之外，模組資訊清單也可以描述您要如何匯出和匯入模組、要公開哪些 Cmdlet，以及模組中會有哪些其他檔案。
   如先前所述，PowerShell 可以將二進位 Cmdlet 視為模組，而不需要額外投入。
   因此，模組資訊清單主要適用于將多個檔案結合成單一封裝，或針對指定的元件明確地控制發行集。
   如需詳細資訊，請參閱 [如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。

   下列程式碼是非常簡單的 c # 程式碼區塊，其中包含在相同檔案中可當做模組使用的三個 Cmdlet。

   ```csharp
   using System.Management.Automation;           // Windows PowerShell namespace.

   namespace ModuleCmdlets
   {
     [Cmdlet(VerbsDiagnostic.Test,"BinaryModuleCmdlet1")]
     public class TestBinaryModuleCmdlet1Command : Cmdlet
     {
       protected override void BeginProcessing()
       {
         WriteObject("BinaryModuleCmdlet1 exported by the ModuleCmdlets module.");
       }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet2")]
     public class TestBinaryModuleCmdlet2Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet2 exported by the ModuleCmdlets module.");
         }
     }

     [Cmdlet(VerbsDiagnostic.Test, "BinaryModuleCmdlet3")]
     public class TestBinaryModuleCmdlet3Command : Cmdlet
     {
         protected override void BeginProcessing()
         {
             WriteObject("BinaryModuleCmdlet3 exported by the ModuleCmdlets module.");
         }
     }

   }
   ```

3. 封裝您的解決方案，並將套件儲存至 PowerShell 模組路徑中的某個位置。

   `PSModulePath`全域環境變數描述 PowerShell 將用來尋找您模組的預設路徑。 例如，在系統上儲存模組的常見路徑是 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>` 。 如果您未使用預設路徑，則必須在安裝期間明確陳述模組的位置。 請務必建立資料夾來儲存您的模組，因為您可能需要資料夾來儲存解決方案的多個元件和檔案。

   請注意，技術上而言，您不需要在任何位置安裝模組，它們 `PSModulePath` 只是 PowerShell 將為您的模組尋找的預設位置。 不過，除非您有充分的理由將模組儲存在其他位置，否則會被視為最佳做法。 如需詳細資訊，請參閱 [安裝 Powershell 模組](./installing-a-powershell-module.md) 和 [修改 Powershell 模組安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

4. 使用 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)的呼叫，將模組匯入 PowerShell。

   呼叫 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 會將您的模組載入至使用中記憶體。 如果您使用 PowerShell 3.0 和更新版本，只要在程式碼中呼叫模組的名稱，也會將它匯入;如需詳細資訊，請參閱匯 [入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="importing-snap-in-assemblies-as-modules"></a>將嵌入式管理單元元件匯入為模組

存在於嵌入式管理單元元件中的 Cmdlet 和提供者，可以載入為二進位模組。 當嵌入式管理單元元件以二進位模組的形式載入時，嵌入式管理單元中的 Cmdlet 和提供者可供使用者使用，但會忽略元件中的嵌入式管理單元類別，而且不會註冊嵌入式管理單元。 如此一來，Windows PowerShell 提供的嵌入式管理單元 Cmdlet 就無法偵測到此嵌入式管理單元，即使會話可以使用 Cmdlet 和提供者也一樣。

此外，嵌入式管理單元所參考的任何格式或類型檔案都無法匯入為二進位模組的一部分。
若要匯入格式化和類型檔案，您必須建立模組資訊清單。
請參閱 [如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
