---
title: 載入及匯出格式的資料 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 08c64d4094d8ba6c551b454887331666f0694f11
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860624"
---
# <a name="loading-and-exporting-formatting-data"></a>載入及匯出格式設定資料

當您建立您格式化檔案之後時，您需要將目前的工作階段載入您的檔案更新的工作階段的格式資料。 （藉由開啟目前的工作階段時註冊的嵌入式管理單元會載入 Windows PowerShell 所提供的格式化檔案）。目前工作階段的格式資料更新之後，Windows PowerShell 會使用該資料來顯示載入的格式化檔案中定義的檢視相關聯的.NET 物件。 沒有任何限制，您可以載入目前的工作階段的格式化檔案的數目。 除了更新格式化資料，您可以回到格式化檔案目前的工作階段中匯出的格式資料。

## <a name="loading-format-data"></a>正在載入格式資料

格式檔案可以載入目前的工作階段使用下列方法：

- 您可以從命令列目前的工作階段，以匯入的格式化檔案。 使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，如下列程序中所述。
- 您可以從命令列目前的工作階段，以匯入的格式化檔案。 使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，如下列程序中所述。

- 您可以建立模組資訊清單參考格式的檔案。 模組可讓您將封裝格式化檔案中的散佈您。 使用[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 來建立資訊清單中，而[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 將模組載入目前的工作階段。 如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。
- 您可以建立模組資訊清單參考格式的檔案。 模組可讓您將封裝格式化檔案中的散佈您。 使用[New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet 來建立資訊清單中，而[Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet 將模組載入目前的工作階段。 如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 您可以建立一個嵌入式管理單元，參考您的格式化檔案。 使用[System.Management.Automation.Pssnapin.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)來參考您的格式化檔案。 它是鼓勵使用散發套件 cmdlet 的模組，以及任何相關聯的格式和類型檔案。 如需有關模組的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 如果您以程式設計方式叫用命令，您可以加入初始工作階段狀態的 runspace，執行命令來格式化的檔案項目。 如需有關用來新增的格式化檔案的.NET 類型的詳細資訊，請參閱[System.Management.Automation.Runspaces.Sessionstateformatentry 嗎？Displayproperty = Fullname>](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)類別。

載入格式化檔案時，它會加入內部清單來判斷何種檢視將顯示在命令列的物件時，使用 Windows PowerShell。 您可以在前面加上您的清單中，開頭的格式化檔案，或您可以將它附加至清單結尾。 了解您的格式化檔案新增至清單的位置是很重要，如果您載入格式化檔案，定義具有現有的檢視定義，例如當您想要變更 Windows PowerShell 核心 cmdlet 所傳回的物件有何物件的檢視 顯示此項目。 如果您載入格式化檔案，定義物件的唯一檢視，您可以使用任何先前所述的方法。  如果您載入格式化檔案，定義物件的另一個檢視，您必須使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 並在前面加上您的檔案清單的開頭。
載入格式化檔案時，它會加入內部清單來判斷何種檢視將顯示在命令列的物件時，使用 Windows PowerShell。 您可以在前面加上您的清單中，開頭的格式化檔案，或您可以將它附加至清單結尾。 了解您的格式化檔案新增至清單的位置是很重要，如果您載入格式化檔案，定義具有現有的檢視定義，例如當您想要變更 Windows PowerShell 核心 cmdlet 所傳回的物件有何物件的檢視 顯示此項目。 如果您載入格式化檔案，定義物件的唯一檢視，您可以使用任何先前所述的方法。  如果您載入格式化檔案，定義物件的另一個檢視，您必須使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 並在前面加上您的檔案清單的開頭。

## <a name="storing-your-formatting-file"></a>儲存您的格式化檔案

沒有格式檔案在磁碟上的儲存位置的需求。 不過，強烈建議您將它們儲存在下列資料夾： `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>正在載入格式檔案使用匯入 FormatData

1. 儲存您到磁碟的格式化檔案。

2. 執行[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 使用下列命令之一。
2. 執行[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 使用下列命令之一。

   若要新增您的格式設定清單的最上層的檔案會使用此命令。 如果您要變更物件的顯示方式，請使用此命令。

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   若要新增您的格式設定清單結尾的檔案會使用此命令。

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   一旦您加入檔案，使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，您無法從清單移除檔案，開啟工作階段時。 您必須關閉工作階段，若要從清單中移除的格式化檔案。
   一旦您加入檔案，使用[Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet，您無法從清單移除檔案，開啟工作階段時。 您必須關閉工作階段，若要從清單中移除的格式化檔案。

## <a name="exporting-format-data"></a>匯出格式資料

在此插入區段主體。
