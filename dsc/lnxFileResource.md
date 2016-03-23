# DSC for Linux nxFile 資源

PowerShell 預期狀態設定 (DSC) 的 **nxFile** 資源會提供在 Linux 節點上管理檔案和目錄的機制。

## 語法

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## [內容]

|  屬性 |  描述 | 
|---|---|
| DestinationPath| 指定您要確認檔案或目錄狀態的位置。| 
| SourcePath| 指定要從中複製檔案或資料夾資源的路徑。 此路徑可以是本機路徑，或 `http/https/ftp` URL。 當 **Type** 屬性的值是檔案，才支援遠端 `http/https/ftp` URL。| 
| Ensure| 決定是否要檢查檔案存在。 將此屬性設定為 "Present" 以確保檔案存在。 設為 "Absent" 以確保此檔案不存在。 預設值為 "Present"。| 
| 類型| 指定要設定的資源是目錄或檔案。 將此屬性設定為 "directory"，表示該資源為目錄。 將此屬性設定為 "file"，表示該資源為檔案。 預設值為 "file"。| 
| 內容| 指定檔案的內容，例如特定字串。| 
| 總和檢查碼| 定義判斷兩個檔案是否相同時所使用的類型。 如不指定 **Checksum**，只會使用檔案或目錄名稱進行比較。 值為："ctime"、"mtime" 或 "md5"。| 
| Recurse| 表示是否包含子目錄。 將此屬性設定為 **$true**，表示您想要包含子目錄。 預設值為 **$false**。 **注意**：僅當 **Type** 屬性設定為 directory 時，這個屬性才有效。| 
| Force| 某些檔案作業 (例如覆寫檔案，或刪除不是空的目錄) 會導致錯誤。 使用 **Force** 屬性會覆寫此類錯誤。 預設值為 **$false**。| 
| 連結| 指定符號連結的預期行為。 設定此屬性為 "follow"，以遵循符號連結，並在連結目標上執行 (例如， 複製檔案而非連結)。 設定此屬性為 "manage" 以在連結上執行 (例如， 複製連結本身)。 設定此屬性為 "ignore" 以忽略符號連結。| 
| 群組| 要擁有檔案或目錄的 **Group** 名稱。| 
| 模式| 以八進位或符號標記法指定資源的預期權限。 (例如，777 或 rwxrwxrwx)。 如果使用符號標記法，就不會提供表示目錄或檔案的第一個字元。| 
| DependsOn | 表示必須先執行另一個資源的設定，再設定這個資源。 例如，如果第一個想要執行的資源設定指令碼區塊的**識別碼**是 **ResourceName**，而它的類型是 **ResourceType**，則使用這個屬性的語法就是 `DependsOn = "[ResourceType]ResourceName"`。| 

## 其他資訊


Linux 和 Windows 預設在文字檔案中使用不同分行符號字元，而在 Linux 電腦上以 __nxFile__ 設定某些檔案時，可能會導致非預期的結果。 有多種方式來管理 Linux 檔案的內容，同時避免非預期的分行符號字元所造成的問題：

步驟 1：從遠端來源 (http、https 或 ftp) 複製檔案：在 Linux 上建立具有所需內容的檔案，並暫存於您將設定之可存取 Web 或 FTP 伺服器的節點。 以該檔案的 Web 或 FTP URL 定義 __nxFile__ 資源的 __SourcePath__ 屬性。

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


步驟 2：設定 __$OFS__ 屬性後，以 [Get-content](https://technet.microsoft.com/en-us/library/hh849787.aspx) 讀取 PowerShell 指令碼中的檔案內容，以使用 Linux 換行字元。


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


步驟 3：使用 PowerShell 函式，以 Linux 換行字元取代 Windows 分行符號。

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## 範例

下列範例可確保目錄 `/opt/mydir` 存在，且具有指定內容的檔案存在於此目錄中。

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```

<!--HONumber=Feb16_HO4-->
