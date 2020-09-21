---
title: 使用 PlatyPS 建立 XML 格式的說明
description: 使用 PlatyPS 建立 XML 格式其說明是快速且有效率的方式。
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972574"
---
# <a name="create-xml-based-help-using-platyps"></a>使用 PlatyPS 建立 XML 格式的說明

建立 PowerShell 模組時，強烈建議一併包含所建立 Cmdlet 的詳細說明。 如果在已編譯的程式碼中實作 Cmdlet ，即必須使用 XML 格式的說明。 此 XML 格式稱為 Microsoft 協助標記語言 (MAML)。

舊版 PowerShell SDK 文件內容涵蓋建立封裝於模組內 PowerShell Cmdlet 的詳細說明。 不過，PowerShell 不會提供任何工具來建立 XML 格式的說明。 SDK 文件雖然會詳述 MAML 說明的結構，但將需要手動建立複雜且深度巢狀化的 MAML 內容。

這就是 [PlatyPS][] 模組可提供協助的地方。

## <a name="what-is-platyps"></a>什麼是 PlatyPS？

PlatyPS 是一種[開放原始碼][platyps-repo]工具，其以 _Hackathon_ 專案的形式啟動，讓建立與維護 MAML 變得更加輕鬆。 PlatyPS 記載參數集的語法，以及模組中每個 Cmdlet 的個別參數。 PlatyPS 會建立包含語法資訊的結構化 [Markdown][] 檔案， 但無法建立描述或提供範例。

PlatyPS 會建立預留位置，以供填寫描述與範例。 在新增必要資訊之後，PlatyPS 會將 Markdown 檔案編譯為 MAML 檔案。 PowerShell 的說明系統也允許 (與主題相關的) 純文字概念說明檔案。 PlatyPS 具有 Cmdlet，可為新的「關於」檔案建立結構化 Markdown 範本，但這些 `about_*.help.txt` 檔案必須以手動方式進行維護。

您可將 MAML 與文字說明檔納入模組中。 您也可使用 PlatyPS，將說明檔編譯成 CAB 套件，以託管可更新的說明。

## <a name="get-started-using-platyps"></a>開始使用 PlatyPS

首先，您必須從 PowerShell 資源庫安裝 PlatyPS。

```powershell
Install-Module platyps -Force
Import-Module platyps
```

下列流程圖會概述建立或更新 PowerShell 參考內容的流程。

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="使用 PlatyPS 建立以 XML 格式來說明的工作流程":::

##  <a name="create-markdown-content-for-a-powershell-module"></a>建立 PowerShell 模組的 Markdown 內容

1. 將新模組匯入至工作階段。 針對所需記載的每個模組重複此步驟。

   執行下列命令以匯入模組：

   ```powershell
   Import-Module <your module name>
   ```

1. 使用 PlatyPS 來為模組頁面以及模組內所有相關聯的 Cmdlet 產生 Markdown 檔案。 針對所需記載的每個模組重複此步驟。

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   如果輸出資料夾不存在，`New-MarkdownHelp` 會加以建立。 在此範例中，`New-MarkdownHelp` 會為模組中的每個 Cmdlet 建立 Markdown 檔案， 並且會在名為 `<ModuleName>.md` 的檔案中建立「模組頁面」。 此模組頁面包含模組中的 Cmdlet 清單，以及**概要**描述的預留位置。 模組頁面中的中繼資料來自模組資訊清單，其由 PlatyPS 用來建立 HelpInfo XML 檔案 ([如下所述](#creating-an-updateable-help-package))。

   `New-MarkdownAboutHelp` 會建立名為 `about_topic_name.md` 的新「關於」檔案。

   如需詳細資訊，請參閱 [New-MarkdownHelp][] 和 [New-MarkdownAboutHelp][]。

### <a name="update-existing-markdown-content-when-the-module-changes"></a>當模組變更時，更新現有的 Markdown 內容

PlatyPS 也可為模組更新現有的 Markdown 檔案。 您可使用此步驟來更新現有的模組，其包含新的 Cmdlet、新的參數或已變更的參數。

1. 將新模組匯入至工作階段。 針對所需記載的每個模組重複此步驟。

   執行下列命令以匯入模組：

   ```powershell
   Import-Module <your module name>
   ```

1. 使用 PlatyPS 來更新模組登陸頁面以及模組內所有相關聯 Cmdlet 的 Markdown 檔案。 針對所需記載的每個模組重複此步驟。

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   `Update-MarkdownHelpModule` 會更新指定資料夾中的 Cmdlet 與模組 Markdown 檔案，
   但不會更新 `about_*.md` 檔案。 模組檔案 (`ModuleName.md`) 會接收所有已新增至 Cmdlet 檔案的**概要**文字。 Cmdlet 檔案的更新包含下列變更：

   - 新參數集
   - 新參數
   - 更新的參數中繼資料
   - 更新的輸入和輸出類型資訊

   如需詳細資訊，請參閱 [Update-MarkdownHelpModule][]。

## <a name="edit-the-new-or-updated-markdown-files"></a>編輯新的或已更新的 Markdown 檔案

PlatyPS 記錄參數集和個別參數的語法， 但無法建立描述或提供範例。 大括號內為需要填入內容的特定區域。 例如：`{{ Fill in the Description }}`

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="VS Code 中顯示預留位置的 Markdown 範本":::

您需要新增概要、Cmdlet 的描述、每個參數的描述，以及至少一個範例。

如需撰寫 PowerShell 內容的詳細資訊，請參閱下列文章：

- [PowerShell 樣式指南](/powershell/scripting/community/contributing/powershell-style-guide)
- [編輯參考文章](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> PlatyPS 具有用於 Cmdlet 參考的特定結構描述。 該結構描述只允許文件中特定區段的某些 Markdown 區塊。 如果將內容放在錯誤的位置，PlatyPS 建置步驟就會失敗。 如需詳細資訊，請參閱 PlatyPS 存放庫中的[結構描述][]文件。 如需正確格式 Cmdlet 參考的完整範例，請參閱 [Get-Item][]。

提供每個 Cmdlet 所需的內容之後，您必須確定已更新模組登陸頁面。 請確認模組在 `<module-name>.md` 檔案的 YAML 中繼資料中具有正確 `Module Guid` 和 `Download Help Link` 值， 新增任何缺少的中繼資料。

此外，您可能會注意到某些 Cmdlet 可能缺少 **概要** (「簡短描述」)。 下列命令會使用**概要**描述文字來更新模組登陸頁面。 開啟模組登陸頁面，以驗證描述。

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

現在已輸入所有內容，您可建立 MAML 說明檔，這些檔案會在 PowerShell 主控台中透過 `Get-Help` 顯示。

## <a name="create-the-external-help-files"></a>建立外部說明檔

此步驟會建立 MAML 說明檔，這些檔案會在 PowerShell 主控台中透過 `Get-Help` 顯示。

請執行下列命令來建置 MAML 檔案：

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

`New-ExternalHelp` 會將所有 Cmdlet Markdown 檔案轉換成一或多個 MAML 檔案。 「關於」檔案會轉換成具有下列名稱格式的純文字檔案：`about_topic_name.help.txt`。
Markdown 內容必須符合 PlatyPS 結構描述的需求。 當內容未遵循結構描述時，`New-ExternalHelp` 將會結束並發生錯誤。 您必須編輯檔案以修正結構描述違規。

> [!CAUTION]
> PlatyPS 不善於將 `about_*.md` 檔案轉換成純文字。 您必須使用非常簡單的 Markdown，才能取得可接受的結果。 您可能會希望以純文字 `about_topic_name.help.txt` 格式來維護檔案，而不是透過 PlatyPS 轉換這些檔案。

完成此步驟之後，您會在目標輸出資料夾中看到 `*-help.xml` 與 `about_*.help.txt` 檔案。

如需詳細資訊，請參閱 [New-ExternalHelp][]

### <a name="test-the-compiled-help-files"></a>測試已編譯的說明檔

您可使用 [Get-HelpPreview][] Cmdlet 來驗證內容：

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

Cmdlet 會讀取已編譯的 MAML 檔案，並使用從 `Get-Help` 所收到的相同格式來輸出內容。 這可供檢查結果，以確認 Markdown 檔案已正確編譯並產生所要的結果。 如果發現錯誤，請重新編輯 Markdown 檔案，並重新編譯 MAML。

您現在已完成發佈說明檔的準備了。

## <a name="publishing-your-help"></a>發佈說明

現在已將 Markdown 檔案編譯成 PowerShell 說明檔，您可讓使用者使用這些檔案。 您有兩種方式可在 PowerShell 主控台中提供說明。

- 使用模組來封裝說明檔
- 建立可更新的說明套件，讓使用者透過 `Update-Help` Cmdlet 安裝

### <a name="packaging-help-with-the-module"></a>使用模組封裝說明

說明檔可封裝至模組內。 如需資料夾結構的詳細資料，請參閱[撰寫模組的說明][]。 在模組資訊清單內，會需將說明檔清單納入 **FileList** 索引鍵的值中。

### <a name="creating-an-updateable-help-package"></a>建立可更新的說明套件

概括而言，建立可更新說明的步驟包含：

1. 尋找可裝載說明檔的網際網路網站
1. 將 **HelpInfoURI** 索引鍵新增至模組資訊清單
1. 建立 HelpInfo XML 檔案
1. 建立 CAB 檔案
1. 上傳檔案

如需詳細資訊，請參閱[支援的可更新說明：逐步解說][step-by-step]。

PlatyPS 可協助執行上述部分步驟。

**HelpInfoURI** 是一個 URL，其指向說明檔裝載在網際網路上的位置。 這個值可在模組資訊清單中進行設定。 `Update-Help` 會讀取模組資訊清單以取得此 URL，並下載可更新說明的內容。 這個 URL 只應指向資料夾位置，而非個別檔案。 `Update-Help` 會根據模組資訊清單以及 HelpInfo XML 檔案中的其他資訊來建構待下載檔案的名稱。

> [!IMPORTANT]
> **HelpInfoURI** 的結尾必須是斜線字元 (`/`)。 如果沒有該字元，`Update-Help` 就無法建構正確的檔案路徑來下載內容。 此外，大部分 HTTP 式的檔案服務都會區分大小寫。 HelpInfo XML 檔案中的模組中繼資料必須包含適當的字母大小寫。

`New-ExternalHelp` Cmdlet 會在輸出資料夾中建立 HelpInfo XML 檔案。 HelpInfo XML 檔案是使用模組 Markdown 檔案 (`ModuleName.md`) 中所包含的 YAML 中繼資料來建立。

`New-ExternalHelpCab` Cmdlet 會建立 ZIP 和 CAB 檔案，並包含所編譯的 MAML 與 `about_*.help.txt` 檔案。 CAB 檔案與所有 PowerShell 版本皆相容，
但 PowerShell 6 或更新版本才可使用 ZIP 檔案。

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

建立 ZIP 和 CAB 檔案之後，請將 ZIP、CAB 以及 HelpInfo XML 檔案上傳到 HTTP 檔案伺服器。 將檔案放在 **HelpInfoURI** 所指示的位置。

如需詳細資訊，請參閱 [New-ExternalHelpCab][]。

### <a name="other-publishing-options"></a>其他發佈選項

Markdown 是一種多樣化的格式，能夠輕易地轉換成其他格式來進行發佈。 使用 [Pandoc][] 等工具即可將 Markdown 說明檔轉換成許多不同文件格式，包含純文字、HTML、PDF 以及 Office 文件格式。

此外，PowerShell 6 和更新版本中的 [ConvertFrom-Markdown][] 與 [Show-Markdown][] Cmdlet 可用來將 Markdown 轉換成 HTML，或在 PowerShell 主控台中建立彩色顯示。

## <a name="known-issues"></a>已知問題

對於所建立和編譯的 Markdown 檔案結構而言，PlatyPS 對其[結構描述][]非常敏感。 撰寫出有效但違反其結構描述的 Markdown 是相當常見的情況。 如需詳細資訊，請參閱 [PowerShell 樣式指南][]與[編輯參考文章][]。

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell 樣式指南]: /powershell/scripting/community/contributing/powershell-style-guide
[編輯參考文章]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[撰寫模組的說明]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
