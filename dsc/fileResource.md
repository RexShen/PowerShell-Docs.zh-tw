# DSC 檔案資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的檔案資源會提供一個機制，在目標節點管理檔案和資料夾。

## 語法
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| DestinationPath| 表示您要確認檔案或目錄狀態的位置。| 
| 屬性| 指定目標檔案或目錄的屬性所需狀態。| 
| 總和檢查碼| 指出判斷兩個檔案是否相同時所使用的密碼總和類型。 如不指定 __Checksum__，只會使用檔案或目錄名稱進行比較。 有效值包括：SHA-1、SHA-256、SHA-512、createdDate、modifiedDate。| 
| 內容| 指定檔案的內容，例如特定字串。| 
| 認證| 指出存取資源的必要認證，例如來源檔案 (如果需要這類存取)。| 
| Ensure| 表示檔案或目錄是否存在。 設定此屬性為 "Absent" 以確保檔案或目錄不存在。 將此屬性設定為 "Present"，以確保檔案或目錄存在。 預設值是 "Present"。| 
| Force| 某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。 使用 Force 屬性會覆寫此類錯誤。 預設值為 __$false__。| 
| Recurse| 表示是否包含子目錄。 將此屬性設定為 __$true__，表示您想要包含子目錄。 預設值為 __$false__。 **注意**：僅當 Type 屬性設定為 Directory 時，這個屬性才有效。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| SourcePath| 表示要從中複製檔案或資料夾資源的路徑。| 
| 類型| 表示正在設定的資源是否為目錄或檔案。 將此屬性設定為 "Directory"，表示該資源為目錄。 將此屬性設定為 "File"，表示該資源為檔案。 預設值為 "File"。| 
| MatchSource| 如果設定為 __$false__ 的預設值，則當第一次套用此設定時，會將來源 (例如檔案 A、B 和 C) 上的任何檔案加入目的地。 如果將新的檔案 (D) 加入來源，就不會將這個檔案加入目的地，即使稍後重新套用此設定亦同。 如果值為 __$true__，則每次套用此設定時，會將此來源 (例如，在此範例中的檔案 D) 上後續找到的新檔案加入目的地。| 

## 範例

下列範例示範如何使用檔案資源，以確保來源電腦上路徑為 `C:\Users\Public\Documents\DSCDemo\DemoSource` (例如「提取」伺服器) 的目錄 (以及所有子目錄) 也會出現在目標節點上。 此外，也會在完成時將確認訊息寫入記錄檔，並包含陳述式，以確保記錄作業之前先執行檔案檢查作業。

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```
<!--HONumber=Feb16_HO4-->
