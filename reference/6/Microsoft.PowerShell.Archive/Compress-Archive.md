---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 7bf349c82133b275f0539db7b78c3583d00da31c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93203844"
---
# Compress-Archive

## 概要
從指定的檔案和目錄建立壓縮封存或壓縮檔案。

## SYNTAX

### 路徑 (預設值)

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithUpdate

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### PathWithForce

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithUpdate

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPathWithForce

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Compress-Archive`Cmdlet 會從一或多個指定的檔案或目錄建立壓縮或壓縮的封存檔案。 封存會將多個檔案（具有選擇性壓縮）封裝成單一壓縮檔案，以方便散發和儲存。 您可以使用 **CompressionLevel** 參數所指定的壓縮演算法來壓縮封存檔案。

此 `Compress-Archive` Cmdlet 會使用 Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) 來壓縮檔案。
檔案大小上限為 2 GB，因為基礎 API 有限制。

某些範例會使用展開來減少程式碼範例的行長度。 如需詳細資訊，請參閱 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)。

## 範例

### 範例1：壓縮檔案以建立保存檔案

此範例會壓縮來自不同目錄的檔案，並建立封存檔案。 萬用字元可用來取得具有特定副檔名的所有檔案。 封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

**Path** 參數接受具有萬用字元的特定檔案名和檔案名 `*.vsd` 。 **路徑** 使用以逗號分隔的清單，從不同的目錄中取得檔案。 壓縮等級是 **最快** 的，可縮短處理時間。 **DestinationPath** 參數會指定檔案的位置 `Draft.zip` 。 檔案 `Draft.zip` 包含 `Draftdoc.docx` 和所有副檔名為的檔案 `.vsd` 。

### 範例2：使用 LiteralPath 壓縮檔案

此範例會壓縮特定的命名檔案，並建立新的封存檔案。 封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

因為 **LiteralPath** 參數不接受萬用字元，所以會使用絕對路徑和檔案名。 **路徑** 使用以逗號分隔的清單，從不同的目錄中取得檔案。 壓縮等級是 **最快** 的，可縮短處理時間。 **DestinationPath** 參數會指定檔案的位置 `Draft.zip` 。 檔案 `Draft.zip` 僅包含 `Draftdoc.docx` 和 `diagram2.vsd` 。

### 範例3：壓縮包含根目錄的目錄

此範例會壓縮目錄並建立封存檔案，其中 **包含** 根目錄及其所有檔案和子目錄。 封存檔案具有目錄結構，因為 **路徑** 指定了根目錄。

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 參數來指定根目錄 `C:\Reference` 。 **DestinationPath** 參數會指定保存檔案的位置。 封存 `Draft.zip` 包含 `Reference` 根目錄及其所有檔案和子目錄。

### 範例4：壓縮排除根目錄的目錄

此範例會壓縮目錄並建立保存 **根目錄的封存** 盤案，因為 **路徑** 使用星號 (`*`) 萬用字元。 封存包含目錄結構，其中包含根目錄的檔案和子目錄。

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 參數指定根目錄， `C:\Reference` 並以星號 (`*`) 萬用字元。 **DestinationPath** 參數會指定保存檔案的位置。 封存 `Draft.zip` 包含根目錄的檔案和子目錄。 `Reference`從封存中排除根目錄。

### 範例5：只壓縮根目錄中的檔案

此範例只會壓縮根目錄中的檔案，並建立封存檔案。 封存中沒有目錄結構，因為只會壓縮檔案。

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

`Compress-Archive` 使用 **Path** 參數指定根目錄， `C:\Reference` 並以 **星形點星號** (`*.*`) 萬用字元。 **DestinationPath** 參數會指定保存檔案的位置。 封存 `Draft.zip` 只 `Reference` 會包含根目錄的檔案，而且會排除根目錄。

### 範例6：使用管線來保存檔案

此範例會將檔案傳送至管線，以建立封存。 封存檔案中沒有目錄結構，因為 **路徑** 只會指定檔案名。

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

`Get-ChildItem` 使用 **Path** 參數來指定不同目錄中的兩個檔案。 每個檔案都是由 **FileInfo** 物件表示，並且會向下傳送到管線 `Compress-Archive` 。
這兩個指定的檔案會封存在中 `PipelineFiles.zip` 。

### 範例7：使用管線來保存目錄

此範例會將目錄向下傳送至管線以建立封存。 檔案會以 **FileInfo** 物件和目錄的形式傳送到 **DirectoryInfo** 物件。 封存的目錄結構不包含根目錄，但其檔案和子目錄會包含在封存中。

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

`Get-ChildItem` 使用 **Path** 參數來指定 `C:\LogFiles` 根目錄。 每個 **FileInfo** 和 **DirectoryInfo** 物件都會沿著管線向下傳送。

`Compress-Archive` 將每個物件新增至封存 `PipelineDir.zip` 。 未指定 **Path** 參數，因為管線物件已接收到參數位置0。

### 範例8：遞迴會如何影響封存

此範例顯示遞迴如何在封存中複製檔案。 例如，如果您使用 `Get-ChildItem` With **遞迴** 參數。 作為遞迴進程，每個 **FileInfo** 和 **DirectoryInfo** 物件都會向下傳送到該管線，並新增至封存。

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

`C:\TestLog`目錄不包含任何檔案。 它包含名為 `testsub` 且包含檔案的子目錄 `testlog.txt` 。

`Get-ChildItem` 使用 **Path** 參數來指定根目錄 `C:\TestLog` 。 **遞迴** 參數會處理檔案和目錄。 建立 **DirectoryInfo** 物件 `testsub` ，以及 **FileInfo** 物件 `testlog.txt` 。

每個物件都會向下傳送到管線 `Compress-Archive` 。 **DestinationPath** 指定保存檔案的位置。 未指定 **Path** 參數，因為管線物件已接收到參數位置0。

下列摘要描述 `PipelineRecurse.zip` 包含重複檔案的封存內容：

- **DirectoryInfo** 物件會建立 `testsub` 目錄，並包含 `testlog.txt` 可反映原始目錄結構的檔案。
- **FileInfo** 物件會 `testlog.txt` 在保存庫的根目錄中建立重複的。 由於遞迴將檔案物件傳送至，所以會建立重複的檔案 `Compress-Archive` 。 這是預期的行為，因為管線中傳送的每個物件都會新增至封存。

### 範例9：更新現有的封存檔案

此範例會更新目錄中的現有封存檔案 `Draft.Zip` `C:\Archives` 。 在此範例中，現有的封存檔案包含根目錄及其檔案和子目錄。

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

此命令會更新 `Draft.Zip` `C:\Reference` 目錄及其子目錄中現有檔案的較新版本。 此外，已新增至 `C:\Reference` 或其子目錄的新檔案會包含在更新的封存中 `Draft.Zip` 。

## PARAMETERS

### -CompressionLevel

指定當您在建立封存檔案時要套用多少壓縮。 更快的壓縮需要較少的時間來建立檔案，但可能會產生較大的檔案大小。

如果未指定此參數，此命令會使用預設值 [ **最佳** ]。

以下是此參數可接受的值：

- **最快速** 。 使用可用的最快壓縮方法來減少處理時間。 更快的壓縮可能會產生較大的檔案大小。
- **NoCompression** 。 不會壓縮原始檔案案。
- **最佳** ： 處理時間取決於檔案大小。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

在執行 Cmdlet 前提示您確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -DestinationPath

此為必要參數，並指定封存輸出檔案的路徑。 **DestinationPath** 應該包含 zip 壓縮檔案的名稱，以及壓縮檔案的絕對或相對路徑。

如果 **DestinationPath** 中的檔案名沒有 `.zip` 副檔名，此 Cmdlet 會加入副檔名 `.zip` 。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

強制執行命令而不要求使用者確認。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

指定您想要新增至封存壓縮檔案的檔案路徑或路徑。 與 **Path** 參數不同， **LiteralPath** 的值將完全依照其輸入值來使用。 沒有字元會被視為萬用字元。 如果路徑包含 escape 字元，請用單引號括住每個 escape 字元，以指示 PowerShell 不要將任何字元解釋為 escape 序列。
若要指定多個路徑，並將檔案包含在輸出壓縮檔案中的多個位置，請使用逗號來分隔路徑。

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

導致 Cmdlet 輸出檔案物件，代表已建立的封存檔案。

此參數是在 PowerShell 6.0 中引進。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

指定您想要新增至封存壓縮檔案的檔案路徑或路徑。 若要指定多個路徑，並將檔案包含在多個位置，請使用逗號來分隔路徑。

此參數接受萬用字元。 萬用字元可讓您將目錄中的所有檔案新增至您的封存檔案。

使用萬用字元搭配根目錄會影響封存的內容：

- 若要建立 **包含** 根目錄及其所有檔案和子目錄的封存，請在 **路徑** 中指定不含萬用字元的根目錄。 例如：`-Path C:\Reference`
- 若要建立封存以 **排除** 根目錄，但 zips 其所有檔案和子目錄，請使用星號 (`*`) 萬用字元。 例如：`-Path C:\Reference\*`
- 若要建立只 zips 根目錄中檔案的封存，請使用 **星號--星號** (`*.*`) 萬用字元。 根目錄的子目錄不包含在封存中。 例如：`-Path C:\Reference\*.*`

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -更新

將封存中較舊的檔案版本取代為具有相同名稱的較新檔案版本，以更新指定的封存。 您也可以新增此參數，以將檔案新增至現有的封存。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。 不會執行此 Cmdlet。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

這個 Cmdlet 支援一般參數：-Debug、-ErrorAction、-ErrorVariable、-InformationAction、-InformationVariable、-OutVariable、-OutBuffer、-PipelineVariable、-Verbose、-WarningAction 和 -WarningVariable。 如需詳細資訊，請參閱 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)。

## 輸入

### System.String

您可以使用管線將包含路徑的字串傳送至一或多個檔案。

## 輸出

### System.IO.FileInfo

當您使用 **PassThru** 參數時，此 Cmdlet 只會傳回 **FileInfo** 物件。

## 注意

使用遞迴並將物件沿著管線向下傳送，可以在您的封存中複製檔案。 例如，如果您使用 `Get-ChildItem` With **遞迴** 參數，則每個向下傳送管線的 **FileInfo** 和 **DirectoryInfo** 物件都會新增至封存。

[ZIP 檔案規格](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT)不會指定編碼包含非 ASCII 字元之檔案名的標準方式。 此 `Compress-Archive` Cmdlet 會使用 utf-8 編碼。 其他 ZIP 封存工具可能會使用不同的編碼配置。 使用 UTF-8 編碼方式解壓縮未儲存的檔案時，會使用在封存 `Expand-Archive` 中找到的原始值。 這可能會產生與儲存在封存中的來原始檔案名不同的檔案名。

## 相關連結

[Expand-Archive](Expand-Archive.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)
