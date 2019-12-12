---
title: 載入和匯出格式化資料 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365117"
---
# <a name="loading-and-exporting-formatting-data"></a>載入及匯出格式設定資料

建立格式檔案之後，您必須將檔案載入目前的會話，以更新會話的格式資料。 （Windows PowerShell 所提供的格式化檔案是由目前會話開啟時註冊的嵌入式管理單元載入）。一旦更新了目前會話的格式資料，Windows PowerShell 就會使用該資料來顯示與已載入的格式檔案中所定義的視圖相關聯的 .NET 物件。 您可以載入目前會話的格式化檔案數目沒有限制。 除了更新格式化資料以外，您還可以將目前會話中的格式資料匯出回格式化檔案。

## <a name="loading-format-data"></a>正在載入格式資料

使用下列方法，可以將檔案格式化為目前的會話：

- 您可以從命令列將格式化檔案匯入到目前的會話。 依照下列程式所述，使用[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。

- 您可以建立會參考您的格式化檔案的模組資訊清單。 模組可讓您封裝要散發的格式化檔案。 使用[new-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) Cmdlet 來建立資訊清單，並使用[import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 將模組載入目前的會話。 如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 您可以建立一個嵌入式管理單元來參考您的格式化檔案。 請使用[PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn.Formats)格式來參考您的格式化檔案。 強烈建議使用模組來封裝 Cmdlet，以及任何相關聯的格式化和類型檔案以進行散發。 如需模組的詳細資訊，請參閱[撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 如果您以程式設計方式叫用命令，可以將格式化檔案專案新增至執行命令之運行時的初始會話狀態。 如需用來新增格式化檔案之 .NET 類型的詳細資訊，請參閱[Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry)類別。

當格式化檔案已載入時，它會新增至內部清單，Windows PowerShell 會使用它來決定在命令列顯示物件時所要使用的視圖。 您可以在清單的開頭加上您的格式化檔案，也可以將它附加至清單結尾。 如果您要載入的格式檔案定義的是已定義現有視圖之物件的視圖，例如當您想要變更 Windows PowerShell core Cmdlet 所傳回物件的方式時，要知道您的格式化檔案新增到此清單的位置是很重要的： 看到. 如果您要載入定義物件唯一視圖的格式化檔案，您可以使用先前所述的任何方法。  如果您要載入為物件定義另一個視圖的格式化檔案，您必須使用 FormatData 指令[程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData)，並在清單的開頭加上您的檔案。

## <a name="storing-your-formatting-file"></a>儲存您的格式化檔案

您的格式化檔案儲存在磁片上的位置並不需要。 不過，強烈建議您將它們儲存在下列資料夾中： `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>使用匯入 FormatData 載入格式檔案

1. 將您的格式化檔案儲存至磁片。

2. 使用下列其中一個命令來執行[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。

   若要將您的格式化檔案新增至清單的前端，請使用此命令。 如果您要變更物件的顯示方式，請使用此命令。

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   若要將您的格式化檔案新增至清單結尾，請使用此命令。

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   當您使用[FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet 新增檔案之後，當會話開啟時，就無法從清單中移除該檔案。 您必須關閉會話，才能從清單中移除格式化檔案。

## <a name="exporting-format-data"></a>匯出格式資料

在此插入區段主體。
