---
title: 撰寫 PowerShell 模組的說明
ms.date: 04/10/2020
ms.openlocfilehash: 496b7e6cadff4d2db15b6452e9d38efcdf1739ec
ms.sourcegitcommit: 8f55c0157280afa4598fe385a706faf330e723a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81219654"
---
# <a name="writing-help-for-powershell-modules"></a>撰寫 PowerShell 模組的說明

PowerShell 模組可以包含關於模組的說明主題以及模組成員，例如 Cmdlet、提供者、函式和腳本。 `Get-Help` Cmdlet 會以顯示其他 PowerShell 專案說明的相同格式來顯示模組說明主題，而使用者會使用標準`Get-Help`命令來取得說明主題。

本檔說明模組說明主題的格式和正確位置，並建議模組說明內容的指導方針。

## <a name="types-of-module-help"></a>模組的類型說明

模組可以包含下列類型的說明。

- **Cmdlet**說明。 描述模組中 Cmdlet 的說明主題是使用命令說明架構的 XML 檔案。

- **提供者**說明。 描述模組中提供者的說明主題，是使用提供者說明架構的 XML 檔案。

- **函數**說明。 描述模組中之函式的說明主題可以是 XML 檔案，這些檔案會使用函式或腳本或腳本模組中的命令說明架構或以批註為基礎的說明主題。

- **腳本**說明。 描述模組中腳本的說明主題可以是使用腳本或腳本模組中的命令說明架構或以批註為基礎之說明主題的 XML 檔案。

- **概念性（"About"）** 說明。 您可以使用概念（「關於」）說明主題來描述模組及其成員，並說明如何將成員一起用來執行工作。
  概念性說明主題是具有 Unicode （UTF-8）編碼的文字檔。 檔案名必須使用`about_<name>.help.txt`格式，例如`about_MyModule.help.txt`。 根據預設，PowerShell 包含超過100的關於說明主題的概念，其格式如下列範例所示。

  ```
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

所有架構檔案都可以在`$PSHOME\Schemas\PSMaml`資料夾中找到。

## <a name="placement-of-module-help"></a>模組說明的位置

此`Get-Help` Cmdlet 會在模組目錄的特定語言子目錄中尋找模組說明主題檔案。

例如，下列目錄結構圖表會顯示 SampleModule 模組的說明主題位置。

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> 在此範例中， `<ModulePath>`預留位置代表`PSModulePath`環境變數中的其中一個路徑，例如`$HOME\Documents\Modules`、 `$PSHOME\Modules`或使用者指定的自訂路徑。

## <a name="getting-module-help"></a>取得模組說明

當使用者將模組匯入會話時，該模組的說明主題會連同模組一起匯入到會話中。 在模組資訊清單中，您可以在 FileList 索引鍵的值中列出說明主題檔案，但是說明主題不會受到`Export-ModuleMember` Cmdlet 的影響。

您可以提供不同語言的模組說明主題。 `Get-Help` Cmdlet 會在 [控制台] 的 [地區及語言選項] 專案中，自動以目前使用者指定的語言顯示模組說明主題。 在 Windows Vista 和更新版本的 Windows 中`Get-Help` ，會根據針對 Windows 所建立的語言回溯標準，搜尋模組目錄的特定語言子目錄中的說明主題。

從 PowerShell 3.0 開始，執行 Cmdlet `Get-Help`或函式的命令會觸發自動匯入模組。 `Get-Help` Cmdlet 會立即顯示模組中說明主題的內容。

如果模組不包含說明主題，而且使用者電腦上的模組中沒有命令的說明主題， `Get-Help`則會顯示自動產生的說明。 自動產生的說明包括命令語法、參數，以及輸入和輸出類型，但不包含任何描述。 自動產生的說明包含文字，可指示使用者嘗試使用`Update-Help` Cmdlet，從網際網路或檔案共用下載命令的說明。 此外，也建議使用**Online** `Get-Help` Cmdlet 的 online 參數來取得說明主題的線上版本。

## <a name="supporting-updatable-help"></a>支援可更新的說明

Powershell 3.0 和更新版本的 PowerShell 使用者可以從網際網路或本機檔案共用下載並安裝模組的已更新說明檔。 `Update-Help`和`Save-Help` Cmdlet 會隱藏使用者的管理詳細資料。 使用者執行`Update-Help` Cmdlet，然後使用`Get-Help` Cmdlet 在 PowerShell 命令提示字元中讀取模組的最新說明檔案。
使用者不需要重新開機 Windows 或 PowerShell。

防火牆後方的使用者和沒有網際網路存取的使用者，也可以使用「可更新的說明」。
具有網際網路存取權的系統`Save-Help`管理員使用 Cmdlet 將最新的說明檔下載並安裝到檔案共用。 然後，使用者會使用**Path** `Update-Help` Cmdlet 的 Path 參數，從檔案共用取得最新的說明檔案。

模組作者可以在模組中包含說明檔，並使用可更新的說明來更新說明檔，或省略模組的說明檔，並使用可更新的說明來安裝和更新這些檔案。

如需「可更新的說明」的詳細資訊，請參閱[支援可更新的協助](./supporting-updatable-help.md)。

## <a name="supporting-online-help"></a>支援線上說明

無法或未在電腦上安裝已更新說明檔案的使用者，通常會依賴線上版本的模組說明主題。 Cmdlet 的 Online 參數會在使用者的預設網際網路瀏覽器中開啟 Cmdlet 或 advanced function 說明主題的線上版本。 **Online** `Get-Help`

此`Get-Help` Cmdlet 會使用 Cmdlet 或函式的**HelpUri**屬性值來尋找說明主題的線上版本。

從 PowerShell 3.0 開始，您可以透過在 Cmdlet 類別上定義 HelpUri 屬性或**CmdletBinding**屬性的**HelpUri**屬性，協助使用者尋找線上版本的 Cmdlet 和功能說明主題。 屬性的值是 Cmdlet 或函式的**HelpUri**屬性值。

如需詳細資訊，請參閱[支援線上說明](./supporting-online-help.md)。

## <a name="see-also"></a>另請參閱

[撰寫 PowerShell 模組](./writing-a-windows-powershell-module.md)

[支援可更新的說明](./supporting-updatable-help.md)

[支援線上說明](./supporting-online-help.md)
