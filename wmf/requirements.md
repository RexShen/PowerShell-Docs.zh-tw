# 系統需求

- 先安裝最新的 Windows 更新，然後安裝 WMF 5.0 RTM。
- 您只能在下列作業系統上安裝 WMF 5.0 RTM：

    | 作業系統       | 版本         | 必要條件        |  封裝連結 |
    |------------------------|--------------|------------------|----------------------| --------------|
    | Windows Server 2012 R2 |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2012    |  |  | <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717506)">W2K12-KB3134759-x64.msu</ctype="x-NOTFOUND"> |
    | Windows Server 2008 R2 SP1 | 全部，IA64 除外 | 已安裝 <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> 和 <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 或更新版本</ctype="x-NOTFOUND">| <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">|
    | Windows 8.1 | 專業版、企業版 | | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64：</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717507)">Win8.1AndW2K12R2-KB3134758-x64.msu</ctype="x-NOTFOUND"> </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86：</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717963)">Win8.1-KB3134758-x86.msu</ctype="x-NOTFOUND">|
    | Windows 7 SP1 | 全部 | 已安裝 <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND"> 和 <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 或更新版本</ctype="x-NOTFOUND"> | <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x64：</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkId=717504)">Win7AndW2K8R2-KB3134760-x64.msu</ctype="x-NOTFOUND">  </br> <ctype="x-NOTFOUND" mdpre="**" mdpost="**">x86：</ctype="x-NOTFOUND">  <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://go.microsoft.com/fwlink/?LinkID=717962)">Win7-KB3134760-x86.msu</ctype="x-NOTFOUND">|

# 安裝指示

### 若要從 Windows 檔案總管 (或檔案總管) 安裝 WMF 5.0：

1. 瀏覽至您用來下載 MSU 檔案的資料夾。

2. 按兩下 MSU 以執行。

### 若要從 [命令提示字元] 安裝 WMF 5.0：

1. 下載您電腦架構的正確封裝之後，以提高的使用者權限 (以系統管理員身分執行) 開啟 [命令提示字元] 視窗。 在 Windows Server 2012 R2 或 Windows Server 2012 或 Windows Server 2008 R2 SP1 的 Server Core 安裝選項上，預設會以提高的使用者權限開啟 [命令提示字元]。

2. 將目錄變更為您已下載或複製 WMF 5.0 安裝封裝的資料夾。

3. 執行下列其中一個命令：
    - 在執行 Windows Server 2012 R2 或 Windows 8.1 x64 的電腦上執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1AndW2K12R2-KB3134758-x64.msu /quiet</ctype="x-NOTFOUND">。
    - 在執行 Windows Server 2012 的電腦上執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">W2K12-KB3134759-x64.msu /quiet</ctype="x-NOTFOUND">。
    - 在執行 Windows Server 2008 R2 SP1 或 Windows 7 SP1 x64 的電腦上執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7AndW2K8R2-KB3134760-x64.msu /quiet</ctype="x-NOTFOUND">。
    - 在執行 Windows 8.1 x86 的電腦上執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win8.1-KB3134758-x86.msu /quiet</ctype="x-NOTFOUND">。
    - 在執行 Windows 7 SP1 x86 的電腦上執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Win7-KB3134760-x86.msu /quiet</ctype="x-NOTFOUND">。

### Windows Server 2008 R2 SP1 和 Windows 7 SP1 的其他安裝注意事項︰

請確定已符合下列先決條件︰
- 已安裝最新的 Service Pack。
- 已安裝 <ctype="x-NOTFOUND" mdpre="[" mdpost="](http://www.microsoft.com/en-us/download/details.aspx?id=40855)">WMF 4.0</ctype="x-NOTFOUND">。
- 已安裝 <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)">.NET Framework 4.5 或更新版本</ctype="x-NOTFOUND">。

**WMF 4.0 相依性**

Windows Server 2008 R2 SP1 和 Windows 7 SP1 系統內建 PowerShell 2.0、WinRM 和 WMI。 發行 Windows Server 2008 R2 SP1 和 Windows 7 SP1 之後，已發行 WMF 3.0 和 WMF 4.0 套件，可更新這些內建元件。 安裝/解除安裝 WMF 3.0 和 WMF 4.0 套件在下列升級路徑中有一些問題︰

- 內建 --> WMF 4.0
- 內建 --> WMF 3.0 --> WMF4.0。 

我們在 WMF 4.0 套件中已修正上述所有問題。 因此，您必須有 WMF 4.0，才能在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上安裝 WMF 5.0。 以下是未安裝 WMF 4.0 便升級至 WMF 5.0 可能遇到的特定問題︰

- 在 Windows 7 SP1 和 Windows Server 2008 R2 SP1 中解除安裝 WMF 3.0 或 WMF 5.0 (而未安裝必要的 WMF 4.0) 之後，轉送的事件記錄無法使用，而且事件檢視器中未顯示 EventCollector 記錄 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2809215)">KB2809215</ctype="x-NOTFOUND">)。
- <ctype="x-NOTFOUND" mdpre="*" mdpost="*">PSModulePath</ctype="x-NOTFOUND"> 環境變數的自訂在下列情況會重設為預設值：當您在 Windows 7 SP1 和 Windows Server 2008 R2 SP1 中，從內建 PowerShell 2.0 直接升級至 WMF 5.0 時 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872035)">KB2872035</ctype="x-NOTFOUND">)，或是從 WMF 3.0 直接升級至 WMF 5.0 時 (<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/2872047)">KB2872047</ctype="x-NOTFOUND">)。

**WinRM 相依性**

Windows PowerShell 預期狀態設定 (DSC) 取決於 WinRM。 在 Windows Server 2008 R2 SP1 和 Windows 7 SP1 上預設不啟用 WinRM。 若要啟用 WinRM，請在 Windows PowerShell 提高權限的工作階段中，執行 <ctype="x-NOTFOUND" mdpre="**" mdpost="**">Set-WSManQuickConfig</ctype="x-NOTFOUND">。

# 解除安裝指示

### 使用 [命令提示字元]

1.  開啟 [命令提示字元]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。

2.  執行 <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://support.microsoft.com/en-us/kb/934307)">Windows Update 獨立啟動程式</ctype="x-NOTFOUND">，如下所示︰

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

1.  開啟 [控制台]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。

2.  開啟 [程式集]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">，然後開啟 [解除安裝程式]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。

3.  按一下 [檢視安裝的更新]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。

4.  從已安裝的更新清單中選取 [Windows Management Framework 5.0]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。 這會對應到 <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134758</ctype="x-NOTFOUND">、<ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134759</ctype="x-NOTFOUND"> 或 <ctype="x-NOTFOUND" mdpre="*" mdpost="*">KB3134760</ctype="x-NOTFOUND">。 按一下 [解除安裝]<ctype="x-NOTFOUND" mdpre="**" mdpost="**"></ctype="x-NOTFOUND">。


<!--HONumber=Mar16_HO4-->


