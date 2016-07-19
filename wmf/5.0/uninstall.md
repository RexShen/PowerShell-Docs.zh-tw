# 解除安裝指示

## 使用 [命令提示字元]
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

## 使用 [控制台]
1.  開啟 **[控制台]**。
2.  開啟 **[程式集]**，然後開啟 **[解除安裝程式]**。
3.  按一下 **[檢視安裝的更新]**。
4.  從已安裝的更新清單中選取 **[Windows Management Framework 5.0]**。 這會對應到 *KB3134758*、*KB3134759* 或 *KB3134760*。 按一下 **[解除安裝]**。


<!--HONumber=Jun16_HO4-->


