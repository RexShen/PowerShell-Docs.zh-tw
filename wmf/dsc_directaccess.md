# 直接存取 DSC 資源方法


`Invoke-DscResource` Cmdlet 已經加入，以允許直接存取 DSC 資源以及它們的方法 (Get、Set 或 Test)。 它可供想要充分利用的 DSC 資源的協力廠商使用。 這個 Cmdlet 通常用於搭配 `refreshMode = ‘Disabled’`，但可用於任何 refreshMode 設定。 以下是如何使用新 Cmdlet 的一些範例︰

## 請確定檔案存在

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 請測試檔案存在

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## 請取得檔案的內容

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```
<!--HONumber=Mar16_HO2-->
