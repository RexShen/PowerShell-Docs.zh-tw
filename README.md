# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 開放原始碼管理辦法

本專案已採用 [Microsoft 開放原始碼管理辦法 (英文)](https://opensource.microsoft.com/codeofconduct/)。
如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

[![組建狀態](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>PowerShell 文件

歡迎使用裝載正式 PowerShell 文件的 PowerShell-Docs 存放庫。

## <a name="repository-structure"></a>存放庫結構

此存放庫中每個下列頂層資料夾都包含發行到 [Microsoft Docs](https://docs.microsoft.com/powershell) 的 DocSet。

- [/developer/](https://docs.microsoft.com/powershell/developer/) 是 PowerShell SDK 文件的未來位置
  - 我們正在從 MSDN 移轉此內容
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) 適用於「預期狀態設定」功能
- [/gallery/](https://docs.microsoft.com/powershell/gallery) 適用於 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) 適用於 Just Enough Administration 功能
- [/reference/](https://docs.microsoft.com/powershell/scripting/) 適用於 PowerShell 概念性主題與模組參考，包括 3.0、4.0、5.0、5.1 與 6.0 版
  - 此內容也是 `Get-Help` Cmdlet 所擷取之說明內容的來源
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) 包含 Windows Management Framework 的版本資訊，這是用來將新的 PowerShell 版本發佈至舊版 Windows 的套件。

## <a name="contributing"></a>貢獻

我們透過[提取要求](https://help.github.com/articles/using-pull-requests/)到「預備」分支，主動將貢獻合併到此存放庫。
請注意，您提交提取要求之前，必須先[簽署貢獻授權合約](https://cla.microsoft.com/)，以確保社群可以自由使用您提出的內容。

如需如何參與的詳細資訊，請閱讀我們的[參與者指南](CONTRIBUTING.md)。
參與者指南包含有關如何參與文件、建議工具與樣式和格式需求的詳細資訊。
請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。

## <a name="licenses"></a>授權

此專案有兩個授權檔案。
MIT 授權適用於此存放庫中包含的程式碼。
而 Creative Commons 授權則適用於文件。