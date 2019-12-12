---
title: 如何撰寫 PowerShell 二進位模組 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb4e72e6-24c4-42b6-b7b9-a62585c17f26
caps.latest.revision: 15
ms.openlocfilehash: ed614de125f78cbcf8411cc334baf3c95933dd47
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367117"
---
# <a name="how-to-write-a-powershell-binary-module"></a>如何撰寫 PowerShell 二進位模組

二進位模組可以是包含 Cmdlet 類別的任何元件（.dll）。 根據預設，匯入二進位模組時，會匯入元件中的所有 Cmdlet。 不過，您可以藉由建立模組資訊清單（其根模組是元件）來限制匯入的 Cmdlet。 （例如，資訊清單的 CmdletsToExport 索引鍵只能用來匯出所需的 Cmdlet）。此外，二進位模組也可以包含其他檔案、目錄結構，以及單一 Cmdlet 無法使用的其他實用管理資訊片段。

下列程式說明如何建立和安裝 PowerShell 二進位模組。

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>如何建立和安裝 PowerShell 二進位模組

1. 使用您所需的功能，建立二進位 PowerShell 解決方案（ C#例如以撰寫的 Cmdlet），並確保其正常執行。

   從程式碼的觀點來看，二進位模組的核心只是一個 Cmdlet 元件。 事實上，在載入和卸載時，PowerShell 會將單一 Cmdlet 元件視為模組，而不會對開發人員進行任何額外的工作。 如需撰寫 Cmdlet 的詳細資訊，請參閱[撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

2. 如有必要，請建立解決方案的其餘部分：（其他 Cmdlet、XML 檔案等等），並使用模組資訊清單來描述它們。

   除了描述解決方案中的 Cmdlet 元件，模組資訊清單可以描述您要如何匯出和匯入模組、會公開哪些 Cmdlet，以及要將哪些其他檔案加入模組中。
   如先前所述，PowerShell 可以將二元 Cmdlet 視為模組，而不需要額外的工作。
   因此，模組資訊清單主要適用于將多個檔案結合成單一封裝，或用於明確控制指定元件的發行集。
   如需詳細資訊，請參閱[如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。

   下列程式碼是非常簡單C#的程式碼區塊，其中包含相同檔案中的三個 Cmdlet，可做為模組使用。

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

3. 封裝您的解決方案，並將套件儲存至 PowerShell 模組路徑中的某處。

   `PSModulePath` 全域環境變數描述 PowerShell 將用來尋找模組的預設路徑。 例如，在系統上儲存模組的一般路徑會是 `%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。 如果您未使用預設路徑，您必須在安裝期間明確陳述模組的位置。 請務必建立一個資料夾來儲存您的模組，因為您可能需要資料夾來儲存方案的多個元件和檔案。

   請注意，技術上來說，您不需要將模組安裝在 `PSModulePath` 上的任何位置，這些只是 PowerShell 會針對您的模組尋找的預設位置。 不過，除非您將模組儲存在其他位置，否則會被視為最佳做法。 如需詳細資訊，請參閱[安裝 Powershell 模組](./installing-a-powershell-module.md)和[修改 Powershell 模組安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

4. 使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)的呼叫，將您的模組匯入 PowerShell。

   呼叫 Import-module 會將您的模組載入到使用中[的](/powershell/module/Microsoft.PowerShell.Core/Import-Module)記憶體。 如果您使用 PowerShell 3.0 和更新版本，只要在程式碼中呼叫模組的名稱，也會將它匯入。如需詳細資訊，請參閱匯[入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="importing-snap-in-assemblies-as-modules"></a>將嵌入式管理單元元件匯入為模組

位於嵌入式管理單元元件中的 Cmdlet 和提供者可以載入為二進位模組。 當嵌入式管理單元元件載入為二進位模組時，嵌入式管理單元中的 Cmdlet 與提供者可供使用者使用，但會忽略元件中的嵌入式管理單元類別，而且嵌入式管理單元也不會註冊。 因此，即使會話可以使用 Cmdlet 和提供者，Windows PowerShell 提供的嵌入式管理單元 Cmdlet 也無法偵測嵌入式管理單元。

此外，此嵌入式管理單元所參考的任何格式或類型檔案，都無法匯入為二進位模組的一部分。
若要匯入格式和類型檔案，您必須建立模組資訊清單。
請參閱[如何撰寫 PowerShell 模組資訊清單](how-to-write-a-powershell-module-manifest.md)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
