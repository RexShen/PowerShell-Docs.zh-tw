## 如何解決「警告：無法下載封裝『您的封裝名稱』」問題？




有人回報 Install-Module 或 Update-Module 有時候在某些機器上會失敗。
根據我們的調查，這和網路連線有關。
我們近期更新了 NuGet 套件，使其能夠確實下載封裝。
您可以遵循下方指示安裝 NuGet 提供者的最新組建，然後安裝或更新您的模組。
以下使用 'Azure' 模組為例。

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```


<!--HONumber=Aug16_HO3-->

