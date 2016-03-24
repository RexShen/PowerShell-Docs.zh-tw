# 系統需求

- 先安裝最新的 Windows 更新，然後安裝 WMF 5.0 RTM。
- 您只能在下列作業系統上安裝 WMF 5.0 RTM：

    | 作業系統       | 版本         | 必要條件        |  封裝連結 |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
    | Windows Server 2012    |  |  | [W2K12-KB3134759-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
    | Windows Server 2008 R2 SP1 | 全部，IA64 除外 | [已安裝 WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) 和 [.NET Framework 4.5 或更新版本](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) | [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)|
    | Windows 8.1 | Pro、Enterprise | | **x64：** [Win8.1AndW2K12R2-KB3134758-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) </br> **x86：** [Win8.1-KB3134758-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963)|
    | Windows 7 SP1 | 全部 | [已安裝 WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) 和 [.NET Framework 4.5 或更新版本](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx) | **x64：** [Win7AndW2K8R2-KB3134760-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504)  </br> **x86：** [Win7-KB3134760-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962)|

# 安裝指示

### 若要從 Windows 檔案總管 (或檔案總管) 安裝 WMF 5.0：

1. 瀏覽至您用來下載 MSU 檔案的資料夾。

2. 按兩下 MSU 以執行。

### 若要從 [命令提示字元] 安裝 WMF 5.0：

1. 下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。 在 Windows Server 2012 R2 或 Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。

2. 將目錄變更為您已下載或複製 WMF 5.0 安裝封裝的資料夾。

3. 執行下列其中一個命令：
    - 在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 **Win8.1AndW2K12R2-KB3134758-x64.msu /quiet**。
    - 在執行 Windows Server 2012 的電腦上執行 **W2K12-KB3134759-x64.msu /quiet**。
    - 在執行 Windows Server 2008 R2 SP1 或 Windows 7 SP1 x64 的電腦上執行 **Win7AndW2K8R2-KB3134760-x64.msu /quiet**。
    - 在執行 Windows 8.1 x86 的電腦上執行 **Win8.1-KB3134758-x86.msu /quiet**。
    - 在執行 x86 Windows 7 SP1 的電腦上執行 **Win7-KB3134760-x86.msu /quiet**。

### Windows Server 2008 SP1 和 Windows 7 SP1 的其他安裝注意事項︰

請確定已符合下列先決條件︰
- 已安裝最新的 Service Pack。
- 已安裝 [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)。
- [已安裝 .NET framework 4.5 或更新版本](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)。

*WinRM 相依性︰*
Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 和 Windows 7 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 **Set-WSManQuickConfig**。

# 解除安裝指示

### 使用 [命令提示字元]

1.  開啟 **[命令提示字元]**。

2.  執行 [Windows Update 獨立啟動器](https://support.microsoft.com/en-us/kb/934307)，如下所示︰

在 Windows Server 2012 R2 和 Windows 8.1 上：
```powershell
wusa /uninstall /kb:3134758
```
在 Windows Server 2012 上：
```powershell
wusa /uninstall /kb:3134759
```
在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上：
```powershell
wusa /uninstall /kb:3134760
```

### 使用 [控制台]

1.  開啟 **[控制台]**。

2.  開啟 **[程式集]**，然後開啟 **[解除安裝程式]**。

3.  按一下 **[檢視安裝的更新]**。

4.  從已安裝的更新清單中選取 **[Windows Management Framework 5.0]**。 這會對應到 *KB3134758*、*KB3134759* 或 *KB3134760*。 按一下 **[解除安裝]**。
<!--HONumber=Mar16_HO2-->
