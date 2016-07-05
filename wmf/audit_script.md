# 指令碼追蹤和記錄

雖然 Windows PowerShell 已有 **LogPipelineExecutionDetails** 群組原則設定會記錄 Cmdlet 的引動過程，但 PowerShell 的指令碼語言仍有許多功能，您可能想要記錄和/或稽核。 新的詳細指令碼追蹤功能可讓您啟用在系統上使用的 Windows PowerShell 指令碼詳細追蹤和分析。 啟用詳細指令碼追蹤後，Windows PowerShell 會將所有指令碼區塊記錄在 ETW 事件記錄檔中：**Microsoft-Windows-PowerShell/Operational**。 如果某個指令碼區塊建立了另一個指令碼區塊 (例如，字串上稱之為 Invoke-Expression Cmdlet 的指令碼)，也會記錄產生的指令碼區塊。

您可以透過 **[打開 PowerShell 指令碼區塊記錄]** 群組原則設定 (位於 [系統管理範本] -> Windows Components -> Windows PowerShell)，啟用這些事件的記錄作業。

這些事件為︰

| 頻道 | 操作                                 |
|---------|---------------------------------------------|
| 層級   | Verbose                                     |
| OpCode  | 建立                                      |
| 工作    | CommandStart                                |
| 關鍵字 | Runspace                                    |
| 事件識別碼 | Engine_ScriptBlockCompiled (0x1008 = 4104)  |
| 訊息 | 建立指令碼區塊文字 (%2 之 %1)： </br> %3 </br> ScriptBlock 識別碼：%4 |


訊息中的內嵌文字是編譯的指令碼區塊範圍。 識別碼是保留給指令碼區塊存留期的 GUID。

當您啟用詳細資訊記錄時，此功能會寫入開始和結束標記︰

| 頻道 | 操作                                            |
|---------|--------------------------------------------------------|
| 層級   | Verbose                                                |
| OpCode  | 開啟 (/ 關閉)                                         |
| 工作    | CommandStart (/ CommandStop)                           |
| 關鍵字 | Runspace                                               |
| 事件識別碼 | ScriptBlock\_Invoke\_Start\_Detail (0x1009 = 4105) / </br> ScriptBlock\_Invoke\_Complete\_Detail (0x100A = 4106) |
| 訊息 | 已啟動 (/ 已完成) ScriptBlock 識別碼的引動過程：%1 </br> Runspace 識別碼：%2 |

識別碼是代表指令碼區塊的 GUID (可與事件識別碼 0x1008 相互關聯)，Runspace 識別碼則代表之前執行這個指令碼區塊的 Runspace。

引動過程訊息中的百分比符號代表結構化的 ETW 屬性。 雖以訊息文字中的實際值取代了它們，但更健全的存取方式是以 Get-WinEvent Cmdlet 擷取訊息，然後使用訊息的**屬性**陣列。

下例說明這項功能如何協助解除包裝加密和模糊化指令碼的惡意嘗試：

```powershell
## Malware
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
             
    ## XOR “encryption”
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)
}

$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
Invoke-Expression $decrypted
```

執行這項功能會產生下列記錄項目︰

```
Compiling Scriptblock text (1 of 1):
function SuperDecrypt
{
    param($script)
    $bytes = [Convert]::FromBase64String($script)
    ## XOR "encryption"
    $xorKey = 0x42
    for($counter = 0; $counter -lt $bytes.Length; $counter++)
    {
        $bytes[$counter] = $bytes[$counter] -bxor $xorKey
    }
    [System.Text.Encoding]::Unicode.GetString($bytes)

}
ScriptBlock ID: ad8ae740-1f33-42aa-8dfc-1314411877e3

Compiling Scriptblock text (1 of 1):
$decrypted = SuperDecrypt "FUIwQitCNkInQm9CCkItQjFCNkJiQmVCEkI1QixCJkJlQg=="
ScriptBlock ID: ba11c155-d34c-4004-88e3-6502ecb50f52

Compiling Scriptblock text (1 of 1):
Invoke-Expression $decrypted
ScriptBlock ID: 856c01ca-85d7-4989-b47f-e6a09ee4eeb3

Compiling Scriptblock text (1 of 1):
Write-Host 'Pwnd'
ScriptBlock ID: 5e618414-4e77-48e3-8f65-9a863f54b4c8
```

如果指令碼區塊的長度超過 ETW 能保存在單一事件中的長度，Windows PowerShell 就會將指令碼切分成多個部分。 以下是從其記錄檔訊息重新合併指令碼的範例程式碼：

```powershell
$created = Get-WinEvent -FilterHashtable @{ ProviderName="Microsoft-Windows-PowerShell"; Id = 4104 } | Where-Object { $_.<...> }
$sortedScripts = $created | sort { $_.Properties[0].Value }
$mergedScript = -join ($sortedScripts | % { $_.Properties[2].Value })
```

如同具有有限保留緩衝區 (亦即 ETW 記錄檔) 的所有記錄系統，針對這個基礎結構的一種攻擊是濫發假性的事件記錄檔以隱藏較早的辨識項。 若要防範這種攻擊，請確定您已設定某種形式的事件記錄檔集合 (亦即 Windows 事件轉送，[利用 Windows 事件記錄檔監視找出敵人](http://www.nsa.gov/ia/_files/app/Spotting_the_Adversary_with_Windows_Event_Log_Monitoring.pdf))，儘快將事件記錄檔移出電腦。


<!--HONumber=Jun16_HO4-->


