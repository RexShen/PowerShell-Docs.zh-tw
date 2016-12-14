# <a name="contributing-to-powershell-documentation"></a>貢獻 PowerShell 文件

感謝您對 PowerShell 文件的興趣！ 如需如何為技術文件作出貢獻的詳情，請參閱下方。

>如需開始使用 Git 和 GitHub 的一般資訊，請參閱 [GitHub 說明](https://help.github.com/)。 

## <a name="sign-a-cla"></a>簽署 CLA

您必須[簽署 Microsoft 貢獻授權合約 (CLA)](https://cla.microsoft.com/)，才能貢獻到任何 PowerShell 存放庫。 如果您在過去已經貢獻到 PowerShell 存放庫，恭喜您！ 您已經完成此步驟。

## <a name="providing-feedback-on-powershell-documentation"></a>提供對於 PowerShell 文件的意見反應

您可以藉由在 [PowerShell-Docs 存放庫問題頁面](https://github.com/PowerShell/PowerShell-Docs/issues)上[建立問題](https://help.github.com/articles/creating-an-issue/)，指出錯誤、建議變更，或要求新的主題。

問題會由 PowerShell 文件小組的成員定期檢閱、分級、指派並進行相應的解決。

## <a name="writing-powershell-documentation"></a>撰寫 PowerShell 文件

貢獻到 Powershell 最簡單的方法之一，是協助撰寫及編輯文件。 我們所有裝載於 GitHub 的文件都是使用 [GitHub 特定 Markdown](https://help.github.com/articles/github-flavored-markdown/) 所撰寫。

## <a name="making-minor-edits-to-existing-topics"></a>對現有主題進行次要編輯

若要[編輯現有的檔案](https://help.github.com/articles/editing-files-in-another-user-s-repository/)，只要瀏覽到檔案，然後按一下 [編輯] 按鈕。 GitHub 會自動為您建立存放庫的專屬分岔，您可以在其中進行變更。 您完成後，請儲存編輯，並提交[提取要求](https://help.github.com/articles/creating-a-pull-request/)至 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存放庫的「預備」分支。 建立您的提取要求之後，PowerShell 文件小組的成員會先檢閱您的變更，然後才合併到「預備」分支。

## <a name="making-major-edits-to-existing-topics"></a>對現有主題進行重大編輯

如果您要對現有的發行項進行大幅變更、新增或變更影像，或貢獻新的文章，則需要手動建立 GitHub 分岔，然後將分岔複製到本機電腦。 分岔 (fork) 是主要存放庫的 GitHub 複本，位於您的 GitHub 帳戶下，並為您提供可以隔離使用的工作複本。 您將從您的分岔建立提取要求。 同樣地，複製 (clone) 是存放庫的本機複本，在此情況下，它將是您分岔的複製。 複製可讓您離線使用 Git 存放庫，以及使用更多強大的原生軟體/工具。

以下是針對現有文件進行重大編輯的工作流程︰

1. 針對 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存放庫[建立分岔](https://help.github.com/articles/fork-a-repo/)。
2. 在本機電腦上[建立分岔的複製](https://help.github.com/articles/cloning-a-repository/)。
3. 在複製的存放庫中建立新的本機分支。
4. 在 Markdown 編輯器中對您想要更新的檔案進行變更。 
   如需常用的 Markdown 編輯器，請參閱下方。
5. [推送您的本機分支](https://help.github.com/articles/pushing-to-a-remote/)到分岔。
6. [建立提取要求](https://help.github.com/articles/creating-a-pull-request/)至 [PowerShell-Docs](https://github.com/PowerShell/PowerShell-Docs) 存放庫的「預備」分支。

## <a name="creating-new-topics"></a>建立新主題

如果您想要貢獻新的文件，請先參閱[標記為 "in progress" 的問題](https://github.com/PowerShell/PowerShell-Docs/labels/in%20progress)，確定您不會重複工作。
如果看起來沒有人正在進行您規劃的工作︰

* 開啟新問題，並標示為 "in progress" (如果您是 PowerShell 組織的成員)，或加入 "in progress" 作為註解，告訴其他人您正在進行的工作
* 遵循上述的工作流程，對現有的主題進行重大編輯。
* 編輯 `TOC.md` 主題 (位於每個文件集的最上層資料夾)，將新主題新增到目錄中。 
  判斷您的新主題在目錄中所屬的位置，然後新增適當層級的標題，以及主題的連結 (`[My topic title](relative path to my topic)`)。

## <a name="markdown-editors"></a>Markdown 編輯器

以下是一些您可以嘗試的 Markdown 編輯器︰

* [Visual Studio Code](https://code.visualstudio.com)
* [Markdown Pad](http://markdownpad.com/)
* [Atom](https://atom.io/)
* [Sublime Text](http://www.sublimetext.com/)


## <a name="github-flavored-markdown-gfm"></a>GitHub 特定 Markdown (GFM)

此存放庫中的所有文章都使用 [GitHub 特定 Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/)。

一些基本 GFM 語法包括︰

* **分行符號與段落︰**在 Markdown 中沒有 HTML `<br />` 或 `<p />` 元素。 相反地，新的段落是以兩個文字區塊之間的空白行來指定。

> **請注意**︰請在每一句之後新增一個新行字元，以簡化 diffs 和 history 的命令列輸出。
這目前尚未在所有 PowerShell-Docs 採用，但我們正在朝此目標邁進。 如您願意，可以予以協助。 

* **斜體︰**HTML `<em>some text</em>` 元素寫成 `*some text*`
* **粗體︰** HTML `<strong>some text</strong>` 元素寫成 `**some text**`
* **標題︰**HTML 標題使用行開頭的 `#` 字元指定。 
  `#` 字元的數目對應到標題的階層層級 (例如，`#` = `<h1>` 和 `###` = ```<h3>```)。
* **編號清單︰**若要製作編號 (排序) 清單，請在該行開頭使用 `1. `。  
  如果您想要在單一清單元素內有多個元素，請格式化您的清單，如下所示︰
```        
1.  For the first element (like this one), insert a tab stop after the 1. 

    To include a second element (like this one), insert a line break after the first and align indentations.
```
取得此輸出︰

1.  對於第一個元素 (例如這個)，在 1 之後插入定位停駐點。 

    若要包含第二個元素 (例如這個)，在第一個之後插入分行符號並對齊縮排。

* **項目符號清單︰**項目符號 (未按順序) 清單與排序清單幾乎相同，除了 `1. ` 取代為 `* `、`- ` 或 `+ `。 多個元素清單與排序清單的運作方式相同。
* **連結︰**超連結的語法是 `[visible link text](link URL)`。
* **相同文件集內其他主題的連結︰**文件集是此存放庫中的最上層資料夾 (例如，"dsc"、"scripting")。
    相同文件集內某個主題的超連結語法是 `[topic title](relative path to topic)`。 
    如需詳細資訊，請參閱[ Relative links in READMEs](https://help.github.com/articles/relative-links-in-readmes/) (讀我檔案中的相對連結)。 
    若要連結到另一個最上層資料夾中的主題，請使用已發行頁面的 URL，如上所述。
