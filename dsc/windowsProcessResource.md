# DSC WindowsProcess 資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的 **WindowsProcess** 資源提供了在目標節點設定程序的機制。

## 語法

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## [內容]
|  屬性  |  描述   | 
|---|---| 
| 引數| 表示要保持原狀傳遞至處理程序的引數字串。 如果需要傳遞數個引數，請將它們都放在這個字串裡。| 
| 路徑| 表示處理程序可執行檔的路徑。 這個屬性如果設定為可執行檔的名稱，DSC 就會在 __Path__ 變數中查看。 如果您提供完整的網域名稱，此處就一定要有處理程序，因為 DSC 在這種情況下不會檢查 __Path__ 變數。| 
| 認證| 表示啟動處理程序的認證。| 
| Ensure| 表示處理程序是否存在。 將這個屬性設定為 "Present" 以確保處理程序存在。 否則，請設定為 "Absent"。 預設值是 "Present"。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"``。| 
| StandardErrorPath| 表示寫入標準錯誤的目錄路徑。 此處的所有檔案都會被覆寫。| 
| StandardInputPath| 表示標準輸入的位置。| 
| StandardOutputPath| 表示寫入標準輸出的位置。 此處的所有檔案都會被覆寫。| 
| WorkingDirectory| 表示會用為處理程序目前工作目錄的位置。| 
<!--HONumber=Feb16_HO4-->
