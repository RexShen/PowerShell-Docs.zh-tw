---
title: "資源撰寫檢查清單"
ms.date: 2016-07-11
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 4a7c9bfa0f22930732776b510d5cc4b0275424ff
ms.openlocfilehash: b2900987b1102cf41880e5af0a0cc44bc6499ef5

---

# 資源撰寫檢查清單
此檢查清單是撰寫新 DSC 資源時的最佳做法清單。
## 資源模組包含各項資源的 .psd1 檔案和 schema.mof 
檢查資源有沒有正確的結構，以及是否包含所有必要的檔案。 每個資源模組都應該包含 .psd1 檔案，且每個非複合資源都應該有 schema.mof 檔案。 **Get-DscResource** 不會列出不包含結構描述的資源，使用者也不能在撰寫針對 ISE 這些模組的程式碼時，使用 IntelliSense。 xRemoteFile 資源的目錄結構，是 [xPSDesiredStateConfiguration 資源模組](https://github.com/PowerShell/xPSDesiredStateConfiguration)的一部分，看起來像這樣︰


```
xPSDesiredStateConfiguration
    DSCResources
        MSFT_xRemoteFile
            MSFT_xRemoteFile.psm1
            MSFT_xRemoteFile.schema.mof
    Examples
        xRemoteFile_DownloadFile.ps1
    ResourceDesignerScripts
        GenerateXRemoteFileSchema.ps1
    Tests
        ResourceDesignerTests.ps1
    xPSDesiredStateConfiguration.psd1
```

## 資源和結構描述正確##
驗證資源結構描述 (*.schema.mof) 檔案。 您可以使用 [DSC 資源設計工具](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)協助開發及測試您的結構描述。 請確認︰
- 屬性類型正確 (例如，接受數值的屬性不使用字串，應改用 UInt32 或其他數值類型)
- 已正確指定屬性 (property) 屬性 (attribute)：([key]、[required]、[write]、[read])
- 結構描述中至少要有一個參數標示為 [key]
- [read] 屬性和後列任一項不並存：[required]、[key]、[write]
- 如果除 [read] 以外指定了多個限定詞，則 [key] 優先
- 如果指定 [write] 和 [required]，則 [required] 優先
- 適當的位置會指定 ValueMap

範例：
```
[Read, ValueMap{"Present", "Absent"}, Values{"Present", "Absent"}, Description("Says whether DestinationPath exists on the machine")] String Ensure;
```

- 指定易記的名稱並確認 DSC 命名慣例

範例：
```[ClassVersion("1.0.0.0"), FriendlyName("xRemoteFile")]```

- 每個欄位都有具意義的描述。 PowerShell GitHub 存放庫有很好的範例，例如[用於 xRemoteFile 的 .schema.mof](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCResources/MSFT_xRemoteFile/MSFT_xRemoteFile.schema.mof)。

另外，您應使用 [DSC 資源設計工具](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)的 **Test-xDscResource** 和 **Test-xDscSchema** Cmdlet 自動驗證資源和結構描述：
```
Test-xDscResource <Resource_folder>
Test-xDscSchema <Path_to_resource_schema_file>
```
例如：
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof
```

## 資源載入無錯誤 ##
檢查是否可以成功載入資源模組。
這可以手動方式操作，執行 `Import-Module <resource_module> -force ` 並確認無任何錯誤發生，或撰寫測試自動化。 如果是後者，您可以在測試案例遵循這個結構：
```powershell
$error = $null
Import-Module <resource_module> –force
If ($error.count –ne 0) {
    Throw “Module was not imported correctly. Errors returned: $error”
}
```
## 資源在正案例中為等冪 
DSC 資源的其中一個基本特性為等冪。 這表示多次套用包含該資源的 DSC 設定，都會得到相同的結果。 例如，如果我們建立包含下列檔案資源的設定：
```powershell
File file {
    DestinationPath = "C:\test\test.txt"
    Contents = "Sample text"
} 
```
第一次套用後，檔案 test.txt 應該會出現在 C:\test 資料夾中。 不過，後續執行的相同設定應該不會變更機器的狀態 (例如，應該不會建立任何 test.txt 檔案複本)。
為確保資源為等冪，您可以在直接測試資源時重複呼叫 **Set-TargetResource**，或在執行端對端測試時多次呼叫 **Start-DscConfiguration**。 每次執行後的結果都應該相同。 


## 測試使用者修改案例 ##
變更電腦狀態，再重新執行 DSC，您就可以正確驗證 **Set-TargetResource** 和 **Test-TargetResource** 函式。 以下為應該採取的步驟：
1.  請從不在預期狀態的資源開始。
2.  以資源執行設定
3.  確認 **Test-DscConfiguration** 傳回 true
4.  將已設定的項目修改為不在所需狀態
5.  驗證 **Test-DscConfiguration** 傳回 false。以下是更具體的登錄資源使用範例：
1.  請從不在預期狀態的登錄機碼開始
2.  對設定執行 **Start-DscConfiguration** 使其進入預期狀態，並確認通過。
3.  執行 **Test-DscConfiguration** 並確認它傳回 true
4.  修改機碼值，使它不在預期狀態
5.  執行 **Test-DscConfiguration** 並確認它傳回 false
6.  已使用 Get-DscConfiguration 驗證 Get-TargetResource 功能

Get-TargetResource 應該傳回資源目前狀態的詳細資料。 請確定以此方法測試：在套用設定後呼叫 Get-DscConfiguration，確認輸出會正確反映電腦目前的狀態。 請務必分開測試，因為呼叫 Start-DscConfiguration 時，不會顯示這個區域的任何問題。

## 直接呼叫 **Get/Set/Test-TargetResource** 函式 ##

請務必測試在資源中實作的 **Get/Set/Test-TargetResource** 函式，方法是直接呼叫這些函式並確認其如預期般運作。

## 使用 **Start-DscConfiguration** 驗證端對端 ##

以直接呼叫的方式測試這些 **Get/Set/Test-TargetResource** 函式很重要，但並非所有的問題都能以這種方式發現。 測試重點應該放在使用 **Start-DscConfiguration** 或提取伺服器上。 事實上，這就是使用者使用資源的方法，所以請勿低估這種測試的重要性。 可能有的問題類型：
- 因為 DSC 代理程式以服務方式執行，所以認證/工作階段的行為可能不同。  請務必在此端對端測試所有功能。
- **Start-DscConfiguration** 輸出的錯誤，和直接呼叫 **Set-TargetResource** 函式所顯示的錯誤可能不同。

## 測試所有 DSC 支援平台的相容性 ##
資源應該能在所有 DSC 支援的平台上運作 (Windows Server 2008 R2 及更新版本)。 在您的作業系統上安裝最新的 WMF (Windows Management Framework)，以取得最新版的 DSC。 如果最初設計的資源在部分這些平台上無法運作，應該會傳回特定的錯誤訊息。 亦請確定資源檢查特定電腦上是否有呼叫中的 Cmdlet。 Windows Server 2012 加入的大量新 Cmdlet，是即使安裝 WMF，Windows Server 2008R2 也不提供的。 

## 在 Windows 用戶端上驗證 (如果適用) ##
一個極常見的測試間距正在驗證資源是否只能存在於 Windows 的伺服器版本。 許多資源也設計在用戶端 SKU 上運作，如果這符合您的情況，請記得也要在這些平台上進行測試。 
## Get-DSCResource 列出這些資源 ##
部署模組之後，呼叫 Get-DscResource 最後應該會列出您的資源和其他項目。 如果清單中找不到您的資源，請確定您有該資源的 schema.mof 檔案。 
## 資源模組包含範例 ##
建立可幫助其他人了解用法的優質範例。 特別是許多使用者視範例程式碼為文件，這十分重要。 
- 首先，您應該決定模組要包含的範例，起碼應涵蓋最重要的資源使用案例：
- 如果模組包含的數項資源，在端對端案例中必須一起工作，基本的端對端範例最好排第一。
- 初始範例應該簡單易懂：如何在小而易於管理的區塊中 (例如建立新的 VHD) 開始使用資源
- 後續的範例應建置於這些範例上 (例如，從 VHD 建立 VM、移除 VM、修改 VM)，顯示進階的功能 (例如，建立具有動態記憶體的 VM)
- 範例設定應該參數化 (所有值都應該當做參數傳遞至設定，不該有任何硬式編碼值)：
```powershell
configuration Sample_xRemoteFile_DownloadFile
{
    param
    (
        [string[]] $nodeName = 'localhost',

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $destinationPath,

        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String] $uri,

        [String] $userAgent,

        [Hashtable] $headers
    )

    Import-DscResource -Name MSFT_xRemoteFile -ModuleName xPSDesiredStateConfiguration

    Node $nodeName
    {
        xRemoteFile DownloadFile
        {
            DestinationPath = $destinationPath
            Uri = $uri
            UserAgent = $userAgent
            Headers = $headers
        }
    }
} 
```
- 包含這樣一種 (註解化) 範例：如何呼叫在範例指令碼結尾有實際值的設定，是個不錯的做法。 例如，在上述的設定中，將 UserAgent 指定為下列項目，明顯不是最佳做法：

`UserAgent = [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer`  
在註解可以釐清設定預期執行的案例中︰
```
<# 
Sample use (parameter values need to be changed according to your scenario):

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg"

Sample_xRemoteFile_DownloadFile -destinationPath "$env:SystemDrive\fileName.jpg" -uri "http://www.contoso.com/image.jpg" `
-userAgent [Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer -headers @{"Accept-Language" = "en-US"}
#>  
```
- 每個範例請撰寫簡短的描述，說明其用途及參數意義。 
- 請確定範例涵蓋資源多數的重要案例，而且如果沒有任何缺漏，請確認它們是否都可執行，並能讓電腦處於預期狀態。  

## 錯誤訊息容易了解，且能幫助使用者解決問題 ##
好的錯誤訊息應該是：
- 有訊息：錯誤訊息的最大問題是它們通常不存在，所以請確定要有錯誤訊息存在。 
- 容易了解︰一般人看得懂，沒有晦澀難懂的錯誤代碼
- 精確：確切描述問題
- 建設性︰建議如何修正問題
- 有禮︰不責怪使用者或讓他們覺得不舒服。請務必驗證端對端案例中的錯誤 (使用 **Start-DscConfiguration**)，因為它們可能會與直接執行資源函式時所傳回的錯誤不同。 

## 記錄檔訊息容易了解且提供資訊 (包括 –verbose、–debug 和 ETW 記錄檔) ##
請確保資源輸出的記錄檔容易了解並向使用者提供值。 資源應該要輸出所有對使用者可能有幫助的資訊，但記錄愈多不一定愈好。 您應該避免備援以及輸出不提供附加價值的資料 – 不要讓使用者翻找數百筆記錄後才找到自己要找的。 當然，全無記錄檔也不是這個問題可以接受的解決方案。 

測試時，您也應該要分析詳細資訊和偵錯記錄 (方法是正確執行 **Start-DscConfiguration** 與 -verbose 和 -debug 參數) 以及 ETW 記錄。 若要查看 DSC ETW 記錄檔，請移至 [事件檢視器] 並開啟下列資料夾︰[應用程式及服務] - [Microsoft] - [Windows] - [預期狀態設定]。  預設會有操作通道，但請確定先啟用分析與偵錯通道，再執行設定。 若要啟用分析/偵錯通道，您可以執行下列指令碼︰
```powershell
$statusEnabled = $true
# Use "Analytic" to enable Analytic channel
$eventLogFullName = "Microsoft-Windows-Dsc/Debug" 
$commandToExecute = "wevtutil set-log $eventLogFullName /e:$statusEnabled /q:$statusEnabled   "
$log = New-Object System.Diagnostics.Eventing.Reader.EventLogConfiguration $eventLogFullName
if($statusEnabled -eq $log.IsEnabled)
{
    Write-Host -Verbose "The channel event log is already enabled"
    return
}     
Invoke-Expression $commandToExecute 
```
## 資源實作不包含硬式編碼路徑 ##
請確定資源實作中沒有硬式編碼路徑，特別是當它們假設語言 (en-us) 或有可用的系統變數時。
如果您的資源需要存取特定的路徑，請使用環境變數，不要使用硬式編碼路徑，因為它在其他電腦上可能不同。

範例：

不要：
```
$tempPath = "C:\Users\kkaczma\AppData\Local\Temp\MyResource"
$programFilesPath = "C:\Program Files (x86)"
 ```
您可以撰寫︰
```
$tempPath = Join-Path $env:temp "MyResource"
$programFilesPath = ${env:ProgramFiles(x86)} 
```
## 資源實作不包含使用者資訊 ##
請確認程式碼中沒有任何電子郵件名稱、帳戶資訊或人名。
## 資源已使用有效/無效的認證測試 ##
如果資源使用認證為參數：
- 確認當本機系統 (或遠端資源的電腦帳戶) 無存取權時，資源可運作。
- 確認資源能搭配為 Get、Set 和 Test 指定的認證運作 
- 如果資源存取權是共用的，請測試所有需要支援的變數，如：
  - 標準的 Windows 共用。
  - DFS 共用。
  - SAMBA 共用 (如想要支援 Linux)。

## 資源不需要互動式輸入 ##
**Get/Set/Test-TargetResource** 函式應該要自動執行，絕不能等到使用者在執行的任何階段輸入才動作 (例如，這些函式內不應該使用 **Get-Credential**)。 如果您需要提供使用者輸入，就應該在編譯階段將它當做參數傳遞至設定。 
## 已徹底測試資源功能 ##
這份檢查清單包含要測試和/或經常遺漏的重要項目。 還有一些測試，主要是資源特定的功能測試，而這裡未提及。 別忘了反向測試案例。 
## 最佳做法︰資源模組包含附有 ResourceDesignerTests.ps1 指令碼的測試資料夾 ##
這是個不錯的做法：在資源模組內建立「測試」資料夾，建立 ResourceDesignerTests.ps1 檔案，並為指定模組中的所有資源加入使用 **Test-xDscResource** 和 **Test-xDscSchema** 的測試。 如此，就可以快速驗證指定模組中所有資源的結構描述，並在發行前執行例行性檢查。
至於 xRemoteFile，ResourceTests.ps1 可能看起來這麼簡單：
```powershell
Test-xDscResource ..\DSCResources\MSFT_xRemoteFile
Test-xDscSchema ..\DSCResources\MSFT_xRemoteFile\MSFT_xRemoteFile.schema.mof 
```
##最佳做法︰資源資料夾包含產生結構描述的資源設計工具指令碼##
每個資源都應該包含資源設計工具指令碼，它會產生資源的 MOF 結構描述。 這個檔案應該置於 <ResourceName>\ResourceDesignerScripts，且命名為 Generate<ResourceName>Schema.ps1。若為 xRemoteFile 資源，這個檔案就會稱之為 GenerateXRemoteFileSchema.ps1 且包含︰
```powershell 
$DestinationPath = New-xDscResourceProperty -Name DestinationPath -Type String -Attribute Key -Description 'Path under which downloaded or copied file should be accessible after operation.'
$Uri = New-xDscResourceProperty -Name Uri -Type String -Attribute Required -Description 'Uri of a file which should be copied or downloaded. This parameter supports HTTP and HTTPS values.'
$Headers = New-xDscResourceProperty -Name Headers -Type Hashtable[] -Attribute Write -Description 'Headers of the web request.'
$UserAgent = New-xDscResourceProperty -Name UserAgent -Type String -Attribute Write -Description 'User agent for the web request.' 
$Ensure = New-xDscResourceProperty -Name Ensure -Type String -Attribute Read -ValidateSet "Present", "Absent" -Description 'Says whether DestinationPath exists on the machine'
$Credential = New-xDscResourceProperty -Name Credential -Type PSCredential -Attribute Write -Description 'Specifies a user account that has permission to send the request.'
$CertificateThumbprint = New-xDscResourceProperty -Name CertificateThumbprint -Type String -Attribute Write -Description 'Digital public key certificate that is used to send the request.'

New-xDscResource -Name MSFT_xRemoteFile -Property @($DestinationPath, $Uri, $Headers, $UserAgent, $Ensure, $Credential, $CertificateThumbprint) -ModuleName xPSDesiredStateConfiguration2 -FriendlyName xRemoteFile 
```
## 最佳做法︰資源支援 -whatif ##
如果資源執行的是「危險」作業，實作 -whatif 功能是個不錯的做法。 完成後，請確定 whatif 輸出會正確描述不使用 whatif 參數執行命令時，作業會發生的狀況。
亦請確認當出現 –whatif 參數時不執行作業 (不會變更節點狀態)。 例如，假設現在要測試檔案資源。 以下的簡單設定會建立有內容 “test” 的檔案 “test.txt”：
```powershell
configuration config
{
    node localhost 
    {
        File file
        {
            Contents="test"
            DestinationPath="C:\test\test.txt"
        }
    }
}
config 
```
如果編譯後以 –whatif 參數執行設定，輸出就會告訴我們執行設定時所發生的確切狀況。 但設定本身並未執行 (未建立 test.txt 檔案)。
```powershell 
Start-DscConfiguration -path .\config -ComputerName localhost -wait -verbose -whatif
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer CHARLESX1 with user sid
S-1-5-21-397955417-626881126-188441444-5179871.
What if: [X]: LCM:  [ Start  Set      ]
What if: [X]: LCM:  [ Start  Resource ]  [[File]file]
What if: [X]: LCM:  [ Start  Test     ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]: LCM:  [ End    Test     ]  [[File]file]  in 0.0270 seconds.
What if: [X]: LCM:  [ Start  Set      ]  [[File]file]
What if: [X]:                            [[File]file] The system cannot find the file specified.
What if: [X]:                            [[File]file] The related file/directory is: C:\test\test.txt.
What if: [X]:                            [C:\test\test.txt] Creating and writing contents and setting attributes.
What if: [X]: LCM:  [ End    Set      ]  [[File]file]  in 0.0180 seconds.
What if: [X]: LCM:  [ End    Resource ]  [[File]file]
What if: [X]: LCM:  [ End    Set      ]
VERBOSE: [X]: LCM:  [ End    Set      ]    in  0.1050 seconds.
VERBOSE: Operation 'Invoke CimMethod' complete.
```

這不是完整詳盡的清單，但涵蓋了許多在設計、開發和測試 DSC 資源時所遇到的重要問題。



<!--HONumber=Jul16_HO2-->


