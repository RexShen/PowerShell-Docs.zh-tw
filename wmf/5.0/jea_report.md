# JEA 上的報告
若要報告 JEA 組態的狀態，您可以使用︰
1.  **Get-PSSessionConfiguration** 以傳回指定電腦上所有註冊端點的清單。
2.  **Get-PSSessionCapability** 以報告任何指定使用者在特定端點上具備的功能。

以下是 **Get PSSessionCapability** 的範例：
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source           
-----------     ----                                               -------    ------           
Alias           clear -> Clear-Host                                                            
Alias           cls -> Clear-Host                                                              
Alias           exsn -> Exit-PSSession                                                         
Alias           gcm -> Get-Command                                                             
Alias           measure -> Measure-Object                                                      
Alias           select -> Select-Object                                                        
Function        Clear-Host                                                                     
Function        Exit-PSSession                                                                 
Function        Get-Command                                                                    
Function        Get-FormatData                                                                 
Function        Get-Help                                                                       
Function        Get-UserInfo                                                                   
Function        Measure-Object                                                                 
Function        Out-Default                                                                    
Function        Select-Object                                                                  
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

若要報告使用者在 JEA 工作階段期間進行的_動作_，您可以︰
1. 啟用該 JEA 端點的「即時權限提升」("over-the-shoulder") 記錄，並查閱記錄目錄中每個使用者動作的完整記錄
2. 開啟 PowerShell 模組的記錄，並檢查 PowerShell 事件記錄檔。

<!--HONumber=Jun16_HO4-->


