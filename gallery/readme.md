# PowerShell 資源庫

PowerShell 資源庫是 PowerShell 內容的集中存放庫。 您可以在資源庫中找到新的 PowerShell 命令或預期狀態設定 (DSC) 資源。

# PowerShellGet 概觀

PowerShellGet 模組包含來自 https://www.PowerShellGallery.com 及其他私用存放庫，用於探索、安裝、更新及發行 PowerShell 成品 (例如模組、DSC 資源、角色功能與指令碼) 的 Cmdlet。

## 開始使用資源庫

要從資源庫安裝項目需要最新版本的 PowerShellGet 模組，其在 Windows 10、Windows Management Framework (WMF) 5.0 或 MSI 安裝程式 (適用於 PowerShell 3 及 4) 均有提供。

- [**取得 Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409)、
- [**取得 WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175) 或
- [**取得 MSI 安裝程式**](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

使用最新 [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 模組，您可以：

-   使用 [**Find-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 與 [**Find-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 在資源庫中搜尋項目
-   使用 [**Save-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 與 [**Save-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 從資源庫將項目儲存到您的系統
-   使用 [**Install-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 與 [**Install-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 從資源庫安裝項目
-   使用 [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 與 [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 將項目上傳到資源庫
-   使用 [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 新增您自己的自訂存放庫

如需如何在資源庫使用 PowerShellGet 命令的詳細資訊，請查看[開始使用](psgallery/psgallery_gettingstarted.md)頁面。 您也可以執行 *Update-Help -Module PowerShellGet* 以安裝這些命令的本機說明。

## 支援的作業系統

**PowerShellGet** 模組需要 **PowerShell 3.0 或更新版本**。

因此，**PowerShellGet** 需要下列其中一個作業系統：

- Windows 10
- Windows 8.1 專業版
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016 TP5
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** 也需要 .NET Framework 4.5 或更新版本。 您可以從[這裡](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。


## 有任何問題嗎？ 想提供任何意見？

如需 PowerShell 資源庫與 PowerShellGet 的詳細資料，請前往[開始使用](psgallery/psgallery_gettingstarted.md)頁面。 請使用 [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell) 提供意見反應及回報問題。



<!--HONumber=Aug16_HO3-->


