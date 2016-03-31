# DSC 套件資源

> 適用於：Windows PowerShell 4.0、Windows PowerShell 5.0

Windows PowerShell 預期狀態設定 (DSC) 中的 **Package** 資源，提供一個機制在目標節點上安裝或解除安裝套件，例如 Windows Installer 和 setup.exe 套件。

## 語法

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## [內容]
|  屬性  |  描述   | 
|---|---| 
| 名稱| 指出您要確保其特定狀態的套件名稱。| 
| 路徑| 指出套件所在的檔案路徑| 
| ProductId| 指出唯一識別套件的產品識別碼。| 
| 引數| 列出將如同所提供來傳遞至套件的引數字串。| 
| 認證| 提供遠端來源套件的存取權。 這個屬性不會用於安裝套件。 在本機系統上一律安裝此套件。| 
| Ensure| 指出是否要安裝此套件。 設定此屬性為 "Absent" 以確保不會安裝此套件 (或如果已安裝，則解除安裝此套件)。 將它設定為 "Present" (預設值) 以確保已安裝此套件。| 
| LogPath| 指出您想要提供者儲存記錄檔來安裝或解除安裝此套件的完整路徑。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的識別碼是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 
| ReturnCode| 指出預期的傳回碼。 如果實際的傳回碼不符這裡提供的預期值，此設定就會傳回錯誤。| 

## 範例

這個範例會執行 .msi 安裝程式，其位於指定路徑，且具有指定的產品識別碼。

```powershell
Package PackageExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path  = "$Env:SystemDrive\TestFolder\TestProject.msi"
    Name = "TestPackage"
    ProductId = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
} 
```


<!--HONumber=Feb16_HO4-->


