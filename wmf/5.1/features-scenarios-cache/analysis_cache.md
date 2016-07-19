# 模組分析快取 #

從 5.1 版開始，PowerShell 提供下列功能控制快取模組資料所用的檔案，例如匯出的命令。

此快取預設儲存在 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 檔案中。
快取一般在啟動同時搜尋命令時讀取，並在模組匯入一段時間後寫入背景執行緒。

若要變更快取的預設位置，請先設定環境變數 PSModuleAnalysisCachePath 再啟動 PowerShell。 此環境變數的變更只會影響子處理程序。
該值應該命名 PowerShell 有權建立和寫入檔案的完整路徑 (包括檔名)。
若要停用檔案快取，此值可設定於無效的位置，例如︰

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

這會將路徑設定到無效的裝置。 如果 PowerShell 無法寫入該路徑，就不會有任何錯誤，但您可以透過追蹤查看錯誤報告︰

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

寫出快取時，PowerShell 會檢查確認模組已不存在，避免不必要的大型快取。
有時候不需要這些檢查，在此情況下，您可以透過設定下列項目關閉這些檢查：

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

此環境變數設定會立即在目前的程序中生效。

<!--HONumber=Jul16_HO1-->


