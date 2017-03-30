## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft 開放原始碼管理辦法

本專案已採用 [Microsoft 開放原始碼管理辦法 (英文)](https://opensource.microsoft.com/codeofconduct/)。
如需詳細資訊，請參閱[管理辦法常見問題集 (英文)](https://opensource.microsoft.com/codeofconduct/faq/)。如果有任何其他疑問或意見，請連絡 [opencode@microsoft.com](mailto:opencode@microsoft.com)。

[![組建狀態](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>PowerShell 文件

歡迎使用裝載正式 Windows PowerShell 文件的 PowerShell-Docs 存放庫。 

## <a name="repository-structure"></a>存放庫結構
此存放庫中的每個資料夾都會發佈至 [MSDN (英文)](https://msdn.microsoft.com/en-us/powershell)。 資料夾對應至下列 PowerShell 資產：
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) 適用於「預期狀態設定」功能
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) 適用於 [PowerShell 資源庫 (英文)](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) 適用於 Just Enough Administration 功能
* [/reference/](https://msdn.microsoft.com/powershell/reference/) 適用於 PowerShell 模組參考，包括版本 2.0、3.0、4.0、5.0、5.1 和 6.0
  * 未來可透過 `Get-Help` Cmdlet 擷取此內容
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) 是一般的 PowerShell 參考內容
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) 包含 Windows Management Framework 的版本資訊，這是用來將新的 PowerShell 版本發佈至舊版 Windows 的套件。 



## <a name="contributing"></a>貢獻

我們透過[提取要求](https://help.github.com/articles/using-pull-requests/)到「預備」分支，主動將貢獻合併到此存放庫。 請注意，您提交提取要求之前，必須先[簽署貢獻授權合約](https://cla.microsoft.com/)，以確保社群可以自由使用您提出的內容。
如需如何貢獻的詳細資訊，請閱讀我們的[貢獻指南](CONTRIBUTING.md)。
進行貢獻之前，請先檢閱[樣式指南](./style.md)草稿。
請使用「問題」和「提取要求」範本，以協助維持文件在不同版本之間的一致性。 
