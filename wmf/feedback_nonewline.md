# NoNewLine 參數
**Out-File****Add-Content** 和 **Set-Content** 現在有新的 **–NoNewline** 參數，只會省略輸出之後的新行。
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
如未指定 **–NoNewline**，每個片段都會放在不同的行︰
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
<!--HONumber=Mar16_HO2-->
