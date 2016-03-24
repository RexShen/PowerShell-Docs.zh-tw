# 剪貼簿 Cmdlet
**Get-Clipboard** 和 **Set-Clipboard** 讓您更輕鬆地與 Windows PowerShell 工作階段來回傳送內容。 下列範例使用檔案總管複製下列三個檔案︰

現在，您可以輕鬆地將剪貼簿內容作為檔案的清單存取︰

PS C:\\> Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt

剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。
<!--HONumber=Mar16_HO2-->
