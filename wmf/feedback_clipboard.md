# 剪貼簿 Cmdlet
**Get-Clipboard** 和 **Set-Clipboard** 讓您更輕鬆地與 Windows PowerShell 工作階段來回傳送內容。 例如，如果使用 Windows 檔案總管將這三個檔案複製到剪貼簿 (例如，選取檔案後按下 `ctrl-c`)，即可輕鬆地以檔案清單的方式存取剪貼簿內容︰

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。


<!--HONumber=Jun16_HO4-->


