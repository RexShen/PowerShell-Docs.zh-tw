# 封存 Cmdlet

兩個新的 Cmdlet，**Compress-Archive** 和 **Expand-Archive**，讓您可以壓縮和解壓縮 ZIP 檔案。

## Compress-Archive
**Compress-Archive** Cmdlet 會從指定的檔案中建立新的封存檔案。 封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。 封存檔案可以用 **-CompressionLevel** 參數中指定的壓縮演算法壓縮。
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## Expand-Archive
**Expand-Archive** Cmdlet 會從指定的封存檔案中解壓縮檔案。 封存檔案可讓多個檔案進行封裝，並可選擇性地壓縮成單一檔案，以方便處理和儲存。
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```
<!--HONumber=Mar16_HO2-->
