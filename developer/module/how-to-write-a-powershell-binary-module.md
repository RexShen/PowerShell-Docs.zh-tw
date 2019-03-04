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
ms.openlocfilehash: 9ddb3bc172c66314603d2be4df5192a76c92e05d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856484"
---
# <a name="how-to-write-a-powershell-binary-module"></a>如何撰寫 PowerShell 二進位模組

二進位模組可以包含 cmdlet 類別之任何組件 (.dll)。 根據預設，匯入的二進位模組時，會匯入組件中的所有 cmdlet。 不過，您可以限制會藉由建立根模組是組件的模組資訊清單匯入的 cmdlet。 （例如，資訊清單的 CmdletsToExport 索引鍵可用來匯出只在需要的 cmdlet。）此外，二進位模組可以包含其他檔案、 目錄結構和其他項單一 cmdlet 無法有用的管理資訊。

下列程序描述如何建立和安裝 PowerShell 二進位模組。

#### <a name="how-to-create-and-install-a-powershell-binary-module"></a>如何建立和安裝 PowerShell 二進位模組

1. 建立二進位 PowerShell 解決方案 (例如撰寫的 cmdlet C#)，功能，也確保正常執行。

   程式碼的觀點而言，二進位模組的核心是只要 cmdlet 的組件。 事實上，PowerShell 會視為單一 cmdlet 組件的模組，以載入和卸載，與開發人員執行任何額外的工作。 如需有關如何撰寫 cmdlet 的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell Cmdlet](../cmdlet/writing-a-windows-powershell-cmdlet.md)。

2. 如有必要，建立您的解決方案的其餘部分: （其他 cmdlet、 XML 檔案等等），並描述其使用模組資訊清單。

   除了描述在您的方案中的指令程式組件時，模組資訊清單可以描述，請決定要如何匯出和匯入模組、 指令程式將會公開，和其他檔案將會移到模組。 如先前所述不過，PowerShell 可以處理像透過任何額外的模組二進位 cmdlet。 因此，模組資訊清單是主要用於將多個檔案結合成單一封裝中，或是明確控制針對指定的組件的發行集時才有用。 如需詳細資訊，請參閱 <<c0> [ 如何撰寫 PowerShell 模組資訊清單](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。

   下列程式碼應用程式非常簡單C#包含三個 cmdlet，在相同的檔案，可用做為模組的程式碼區塊。

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

3. 封裝您的方案，並將封裝儲存至某處 PowerShell 模組路徑中。

   `PSModulePath`全域環境變數描述 PowerShell 用來尋找您的模組的預設路徑。 比方說，是常見的路徑，以在系統上儲存模組`%SystemRoot%\users\<user>\Documents\WindowsPowerShell\Modules\<moduleName>`。 如果您未使用的預設路徑，您必須明確在安裝期間指定模組的位置。 請務必建立一個資料夾來儲存您的模組中，因為您可能需要儲存多個組件和您的解決方案檔案的資料夾。

   請注意，技術上您不需要在任何地方安裝您的模組`PSModulePath`-這些是只會尋找 PowerShell 模組的預設位置。 不過，它會被視為最佳的作法，除非您有很好的理由來儲存您的模組其他地方。 如需詳細資訊，請參閱 <<c0> [ 安裝 PowerShell 模組](./installing-a-powershell-module.md)並[修改 PowerShell 模組的安裝路徑](./modifying-the-psmodulepath-installation-path.md)。

4. 在 PowerShell 匯入您的模組，藉由呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)。

   若要呼叫[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module)會將您的模組載入使用中記憶體。 如果您使用 PowerShell 3.0 和更新版本中，只要呼叫程式碼中的 模組的名稱也會匯入它;如需詳細資訊，請參閱 <<c0> [ 匯入 PowerShell 模組](./importing-a-powershell-module.md)。

## <a name="importing-snap-in-assemblies-as-modules"></a>匯入做為模組的嵌入式管理單元的組件

可以做為二進位模組載入 Cmdlet 和嵌入式管理單元的組件中存在的提供者。 二進位模組以載入嵌入式管理單元的組件時，cmdlet 和嵌入式管理單元的提供者會提供給使用者，嵌入式管理單元中的類別組件會被忽略，但不登錄嵌入式管理單元。 如此一來，Windows PowerShell 所提供的嵌入式管理單元 cmdlet 無法偵測嵌入式管理單元中，即使 cmdlet 與提供者可用於工作階段。

此外，任何格式或類型檔案所參考的嵌入式管理單元無法匯入二進位模組的一部分。 若要匯入的格式和類型的檔案中，您必須建立模組資訊清單。 查看，請[如何撰寫 PowerShell 模組資訊清單](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)。

## <a name="see-also"></a>另請參閱

[撰寫 Windows PowerShell 模組](./writing-a-windows-powershell-module.md)
