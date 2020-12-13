---
ms.date: 09/13/2016
ms.topic: reference
title: 載入及匯出格式設定資料
description: 載入及匯出格式設定資料
ms.openlocfilehash: 38857526801051bf6d31d300d5be1a3fd2c80391
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666513"
---
# <a name="loading-and-exporting-formatting-data"></a>載入及匯出格式設定資料

建立格式化檔案之後，您必須將檔案載入目前的會話，以更新會話的格式資料。  (Windows PowerShell 所提供的格式化檔案，是在目前會話開啟時註冊的嵌入式管理單元所載入。 ) 當目前會話的格式資料更新後，Windows PowerShell 會使用該資料來顯示與載入的格式化檔案中定義之視圖相關聯的 .NET 物件。 在目前的會話中，您可以載入的格式化檔案數目沒有任何限制。 除了更新格式化資料以外，您還可以將目前會話中的格式資料匯出回格式化檔案。

## <a name="loading-format-data"></a>載入格式資料

您可以使用下列方法，將檔案格式化以載入目前的會話：

- 您可以從命令列將格式化檔案匯入至目前的會話。 使用 [FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet，如下列程式所述。

- 您可以建立參考格式化檔案的模組資訊清單。 模組可讓您封裝格式化檔案以進行散發。 使用 [ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) 資訊清單來建立資訊清單，並使用 [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) Cmdlet 將模組載入至目前的會話。 如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 您可以建立參考格式化檔案的嵌入式管理單元。 使用 [PSSnapIn 格式](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) 來參考您的格式化檔案。 強烈建議您使用模組來封裝 Cmdlet，以及任何相關聯的格式和類型檔案來進行散發。 如需模組的詳細資訊，請參閱 [撰寫 Windows PowerShell 模組](../module/writing-a-windows-powershell-module.md)。

- 如果您以程式設計方式叫用命令，您可以在執行命令的運行時的初始會話狀態中新增格式化檔案專案。 如需有關用來新增格式化檔案之 .NET 類型的詳細資訊，請參閱 [Sessionstateformatentry？Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) 類別。

載入格式化檔案時，它會新增至內部清單，Windows PowerShell 用來決定在命令列顯示物件時所要使用的視圖。 您可以在清單的開頭加上格式化檔案，也可以將它附加至清單的結尾。 如果您要載入的格式檔案定義了已定義現有視圖的物件，例如，當您想要變更 Windows PowerShell core Cmdlet 所傳回之物件的顯示方式時，瞭解將格式化檔案新增到此清單的位置是很重要的。 如果您要載入的格式化檔案定義物件的唯一觀點，您可以使用先前所述的任何方法。  如果您要載入為物件定義另一個視圖的格式化檔案，您必須使用 FormatData 指令 [程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) ，並在清單開頭加上您的檔案。

## <a name="storing-your-formatting-file"></a>儲存您的格式化檔案

您不需要將格式化檔案儲存在磁片上的位置。 不過，強烈建議您將它們儲存在下列資料夾中： `user\documents\windowspowershell\`

#### <a name="loading-a-format-file-using-import-formatdata"></a>使用 Import-FormatData 載入格式檔案

1. 將您的格式化檔案儲存至磁片。

2. 使用下列其中一個命令來執行 [FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) Cmdlet。

   若要將格式化檔案新增至清單前面，請使用此命令。 如果您要變更物件的顯示方式，請使用此命令。

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   若要將格式化檔案新增至清單結尾，請使用此命令。

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   當您使用 [FormatData 指令程式](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 新增檔案之後，您就無法在會話開啟時從清單中移除該檔案。 您必須關閉會話，以從清單中移除格式化檔案。

## <a name="exporting-format-data"></a>匯出格式資料

在此插入章節主體。
