---
description: PSModulePath 環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_PSModulePath?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSModulePath
ms.openlocfilehash: 6e0307996bf619bc887b076a1f8c0faa619964fe
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524454"
---
# <a name="about-psmodulepath"></a>關於 PSModulePath

`$env:PSModulePath`環境變數包含要搜尋以尋找模組和資源的資料夾位置清單。 PowerShell 會以遞迴方式搜尋模組 (或) 檔案的每個資料夾 `.psd1` `.psm1` 。

依預設，指派給的有效位置 `$env:PSModulePath` 為：

- 全系統位置：這些資料夾包含 PowerShell 隨附的模組。 這些模組會儲存在 `$PSHOME\Modules` 資料夾中。 這也是安裝 Windows 管理模組的位置。

- 使用者安裝的模組：這些是使用者所安裝的模組。
  `Install-Module` 具有 **範圍** 參數，可讓您指定是否為目前的使用者或所有使用者安裝模組。 如需詳細資訊，請參閱 [Install 模組](xref:PowerShellGet.Install-Module)。

  - 在 Windows 中，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME\Documents\PowerShell\Modules` 資料夾。 **AllUsers** 範圍的位置是 `$env:ProgramFiles\PowerShell\Modules` 。
  - 在非 Windows 系統上，使用者專屬 **CurrentUser** 範圍的位置是 `$HOME/.local/share/powershell/Modules` 資料夾。 **AllUsers** 範圍的位置是 `/usr/local/share/powershell/Modules` 。

此外，在其他目錄中安裝模組的安裝程式（例如 [Program Files] 目錄）可以將其位置附加至的值 `$env:PSModulePath` 。

> [!NOTE]
> 在 Windows 中，使用者專屬的位置是 `PowerShell\Modules` 位於使用者設定檔的 [ **檔** ] 資料夾中的資料夾。 該位置的特定路徑會因 Windows 版本而異，以及您是否正在使用資料夾重新導向。 Microsoft OneDrive 也可以變更您的 [ **檔** ] 資料夾的位置。 您可以使用下列命令來確認 [ **檔** ] 資料夾的位置： `[Environment]::GetFolderPath('MyDocuments')` 。

## <a name="modifying-psmodulepath"></a>修改 PSModulePath

若要變更目前會話的預設模組目錄，請使用下列命令格式來變更 `PSModulePath` 環境變數的值。

例如，若要將 `C:\Program Files\Fabrikam\Modules` 目錄新增至 PSModulePath 環境變數的值，請輸入：

```powershell
$Env:PSModulePath = $Env:PSModulePath+";C:\Program Files\Fabrikam\Modules"
```

命令中的分號 (`;`) 會將新路徑與清單中該路徑前面的路徑隔開。 在非 Windows 平臺上，冒號 (`:`) 分隔環境變數中的路徑位置。

若要變更 `PSModulePath` 每個會話中的值，請將上述命令新增至 PowerShell 設定檔，或使用 **環境** 類別的 **SetEnvironmentVariable** 方法。

下列命令會使用 **GetEnvironmentVariable** 方法來取得的電腦設定 `PSModulePath` ，並使用 **SetEnvironmentVariable** 方法將 `C:\Program Files\Fabrikam\Modules` 路徑新增至值。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'Machine')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'Machine')
```

若要將路徑新增至使用者設定，請將目標值變更為 [ **使用者** ]。

```powershell
$path = [Environment]::GetEnvironmentVariable('PSModulePath', 'User')
$newpath = $path + ';C:\Program Files\Fabrikam\Modules'
[Environment]::SetEnvironmentVariable('PSModulePath', $newpath, 'User')
```

如需 **System. 環境** 類別方法的詳細資訊，請參閱 [環境方法](/dotnet/api/system.environment)。

## <a name="powershell-psmodulepath-construction"></a>PowerShell PSModulePath 結構

`$env:PSModulePath`每次 PowerShell 啟動時，就會建立的值。
值會因 PowerShell 版本和其啟動方式而有所不同。

### <a name="windows-powershell-startup"></a>Windows PowerShell 啟動

Windows PowerShell 會在啟動時使用下列邏輯來建立 `PSModulePath` ：

- 如果 `PSModulePath` 不存在，請結合 **CurrentUser** 、 **AllUsers** 和 `$PSHOME` 模組路徑
- 如果 `PSModulePath` 存在：
  - 如果 `PSModulePath` 包含 `$PSHOME` 模組路徑：
    - 在模組路徑之前插入 **AllUsers** 模組路徑 `$PSHOME`
  - 還：
    - 只是 `PSModulePath` 使用者刻意移除位置之後，才使用定義 `$PSHOME`

只有當使用者範圍不存在時，才會加上 **CurrentUser** 模組路徑的前置詞 `$env:PSModulePath` 。 否則， `$env:PSModulePath` 會使用如定義的使用者範圍。

### <a name="powershell-core-6-startup"></a>PowerShell Core 6 啟動

PowerShell Core 6 `$env:PSModulePath` 如果偵測到它是從 PowerShell 啟動，就不會使用的內容。 它會以下列內容覆寫：

- **CurrentUser** 模組路徑 + **AllUsers** 模組路徑 + `$PSHOME` 模組路徑 + Windows PowerShell `$PSHOME` 模組路徑。

### <a name="powershell-7-startup"></a>PowerShell 7 啟動

在 Windows 中，在大部分的環境變數中，如果使用者範圍變數存在，則新的進程只會使用該值，即使有相同名稱的電腦範圍變數存在也一樣。

在 PowerShell 7 中，的 `PSModulePath` 處理方式類似于 `Path` Windows 上處理環境變數的方式。 在 Windows 上， `Path` 會以不同于其他環境變數的方式處理。 當處理常式啟動時，Windows 會將使用者範圍 `Path` 與電腦範圍結合在一起 `Path` 。

- 取出使用者範圍 `PSModulePath`
- 與進程繼承的 `PSModulePath` 環境變數比較
  - 如果相同：
    - 將 **AllUsers** 附加 `PSModulePath` 至 `Path` 環境變數之語義後面的結尾
    - Windows `System32` 路徑來自訂的電腦， `PSModulePath` 因此不需要明確新增
  - 如果不同，請將視為使用者明確修改它，而不要附加 **AllUsers**`PSModulePath`
- 以該順序 PS7 使用者、系統和路徑的前置詞 `$PSHOME`
  - 如果 `powershell.config.json` 包含使用者範圍 `PSModulePath` ，請使用此值，而不是使用者的預設值。
  - 如果 `powershell.config.json` 包含已設定範圍的系統 `PSModulePath` ，請使用此值，而不是系統的預設值。

Unix 系統沒有使用者和系統內容變數的分隔。
`PSModulePath` 會被繼承，而且 PS7 特定路徑的前置詞（如果尚未定義的話）。

### <a name="starting-windows-powershell-from-powershell-7"></a>從 PowerShell 7 開始 Windows PowerShell

在此討論中， _Windows PowerShell_ 表示 `powershell.exe` 和 `powershell_ise.exe` 。

的值 `$env:PSModulePath` 會複製到， `WinPSModulePath` 並進行下列修改：

- 移除 PS7 使用者模組路徑
- 移除 PS7 系統模組路徑
- 移除 `$PSHOME` 模組路徑的 PS7

PS7 路徑會被移除，因此不會在 Windows PowerShell 中載入 PS7 模組。 `WinPSModulePath`開始 Windows PowerShell 時，會使用此值。

### <a name="starting-powershell-7-from-windows-powershell"></a>從 Windows PowerShell 啟動 PowerShell 7

PowerShell 7 啟動會依原樣繼續進行，並新增 Windows PowerShell 新增的繼承路徑。 由於 PS7 特定的路徑會加上前置詞，因此沒有任何功能性問題。

### <a name="starting-powershell-6-from-powershell-7"></a>從 PowerShell 7 啟動 PowerShell 6

PowerShell Core 6 覆寫 `$env:PSModulePath` 。 未進行任何變更。

### <a name="starting-powershell-7-from-powershell-6"></a>從 PowerShell 6 啟動 PowerShell 7

PowerShell 7 啟動會繼續進行，並新增 PowerShell Core 6 新增的繼承路徑。 由於 PS7 特定的路徑會加上前置詞，因此沒有任何功能性問題。

## <a name="module-search-behavior"></a>模組搜尋行為

PowerShell 會以遞迴方式在 **PSModulePath** 中搜尋模組 (`.psd1` 或) 檔案的每個資料夾 `.psm1` 。 此搜尋模式允許在不同的資料夾中安裝相同模組的多個版本。 例如：

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules\PowerShellGet

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           8/14/2020  5:56 PM                1.0.0.1
d----           9/13/2019  3:53 PM                2.1.2
```

根據預設，當找到多個版本時，PowerShell 會載入模組的最高版本號碼。 若要載入特定版本，請使用 `Import-Module` With **FullyQualifiedName** 參數。 如需詳細資訊，請參閱 [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module)。

## <a name="see-also"></a>另請參閱

- [about_Modules](about_Modules.md)
- [環境方法](/dotnet/api/system.environment)
