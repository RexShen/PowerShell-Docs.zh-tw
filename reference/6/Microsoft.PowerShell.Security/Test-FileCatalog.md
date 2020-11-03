---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 072e0b4420613f2de356b35e741a558501c05e1c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "93204724"
---
# Test-FileCatalog

## 概要
`Test-FileCatalog` 驗證目錄檔案中包含的雜湊 ( .cat) 是否符合實際檔案的雜湊，以便驗證其真實性。

只有在 Windows 上才支援此 Cmdlet。

## SYNTAX

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## DESCRIPTION

`Test-FileCatalog` 藉由比較類別目錄檔案 ( 的檔案雜湊來驗證檔案的真實性，並將實際檔案的雜湊與磁片上的實際檔案雜湊) 。
如果偵測到任何不符的狀況，則會以 >validationfailed 的形式傳回狀態。 使用者可以使用 -Detailed 參數來擷取此資訊的完整內容。
它也會在 [簽章] 屬性中顯示目錄的簽章狀態，這相當於 `Get-AuthenticodeSignature` 在類別目錄檔案上呼叫 Cmdlet。
使用者也可以使用 -FilesToSkip 參數，在驗證期間略過任何檔案。

只有在 Windows 上才支援此 Cmdlet。

## 範例

### 範例1：建立和驗證檔案類別目錄

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### 範例2：使用詳細輸出驗證檔案類別目錄

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## PARAMETERS

### -CatalogFilePath

類別目錄檔案的路徑 ( .cat) ，其中包含要用於驗證的雜湊。

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### -Detailed

傳回更詳細的資訊， `CatalogInformation` 其中包含所測試的檔案、其預期/實際的雜湊，以及類別目錄檔案的 Authenticode 簽章（如果已簽署的話）。

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### ->-filestoskip

不應在驗證過程中測試的路徑陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

應針對類別目錄檔案進行驗證的資料夾或檔案陣列。

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -WhatIf

顯示執行 Cmdlet 後會發生的情況。
Cmdlet 並不會執行。

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

這個 Cmdlet 支援一般參數： `-Debug` 、 `-ErrorAction` 、 `-ErrorVariable` 、 `-InformationAction` 、、、、、 `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` 、 `-WarningAction` 和 `-WarningVariable` 。 如需詳細資訊，請參閱 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)。

## 輸入

### DirectoryInfo []、System.string []

管線接受字串或物件的陣列 `DirectoryInfo` ，這些字串或物件代表需要驗證之檔案的路徑。

## 輸出

### CatalogValidationStatus。

預設傳回型別，其中包含或的 `Valid` 值 `ValidationFailed` 。

### CatalogInformation。

當使用時，會傳回更詳細的物件 `-Detailed` ，可用於分析可能或可能尚未通過驗證的特定檔案、預期的雜湊與找到的雜湊，以及用於目錄中的演算法。

## 注意

## 相關連結

[New-FileCatalog](New-FileCatalog.md)

[PowerShellGet](/powershell/module/PowerShellGet)
