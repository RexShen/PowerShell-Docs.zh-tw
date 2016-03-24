# FileInfo 物件的更新
檔案版本資訊可能會產生誤導，尤其是在已修補檔案的情況下。 這一版的 WMF Production Preview 將新的 **FileVersionRaw** 和 **ProductVersionRaw** 指令碼屬性加入 FileInfo 物件。 以下是為 powershell.exe 顯示的屬性︰

PS C:\\&gt; Get-Process -Id $pid -FileVersionInfo | fl \*version\* -Force

FileVersionRaw : 10.0.10055.0

ProductVersionRaw : 10.0.10055.0

FileVersion : 10.0.10055.0 (fbl\_srv2.150402-1826)

ProductVersion : 10.0.10055.0
<!--HONumber=Mar16_HO2-->
