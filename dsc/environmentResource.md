# DSC 環境資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 的__環境__資源會提供管理系統環境變數的機制。

## 語法
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## [內容]

|  屬性  |  描述   | 
|---|---| 
| 名稱| 指出您要確保其特定狀態的環境變數名稱。| 
| Ensure| 指出變數是否存在。 如果沒有環境變數，請將這個屬性設為 __Present__ 以建立環境變數；或如果已有變數，則確保其值符合透過 __Value__ 屬性所提供的值。 如果有變數，將它設為 __Absent__ 可刪除變數。| 
| 路徑| 定義設定中的環境變數。 如果變數是 __Path__ 變數，請將這個屬性設為 __$true__，否則請設為 __$false__。 預設值為 __$false__。 如果要設定的變數是 __Path__ 變數，則透過 __Value__ 屬性提供的值就會附加至現有的值。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 __ResourceName__，而它的類型是 __ResourceType__，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| 值| 要指派給環境變數的值。| 

## 範例

下例確保 __TestEnvironmentVariable__ 存在，且有值 __TestValue__。 如果不存在，就會建立它。

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
<!--HONumber=Feb16_HO4-->
