---
description: 描述 Windows PowerShell 的嵌入式管理單元，並示範如何使用和管理它們。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207619"
---
# <a name="about-pssnapins"></a>關於 PSSnapins

## <a name="short-description"></a>簡短描述

描述 Windows PowerShell 的嵌入式管理單元，並示範如何使用和管理它們。

## <a name="long-description"></a>詳細描述

Windows PowerShell 嵌入式管理單元是包含 Windows PowerShell 提供者和或 Cmdlet 的 Microsoft .NET Framework 元件 \/ 。 Windows PowerShell 包含一組基本的嵌入式管理單元，但您可以藉由新增包含您所建立之提供者和 Cmdlet 的嵌入式管理單元，來擴充 Windows PowerShell 的威力和價值。

當您新增嵌入式管理單元時，它所包含的 Cmdlet 和提供者可以立即在目前的會話中使用，但這項變更只會影響目前的會話。

若要將嵌入式管理單元新增至所有未來的會話，請將它儲存在您的 Windows PowerShell 設定檔中。 您也可以使用 Export-Console Cmdlet，將嵌入式管理單元名稱儲存到主控台檔案，然後在未來的會話中使用。 您甚至可以儲存多個主控台檔案，每個檔案都有一組不同的嵌入式管理單元。

注意： Windows PowerShell 嵌入式管理單元 (PSSnapins) 可在 Windows PowerShell 3.0 和 Windows PowerShell 2.0 中使用。 它們可能會在後續版本中變更或無法使用。 若要封裝 Windows PowerShell Cmdlet 和提供者，請使用模組。 如需建立模組並將嵌入式管理單元轉換成模組的相關資訊，請參閱 [撰寫 Windows PowerShell 模組](/powershell/scripting/developer/module/writing-a-windows-powershell-module)。

### <a name="finding-snap-ins"></a>尋找嵌入式管理單元

若要取得電腦上 Windows PowerShell 的嵌入式管理單元清單，請輸入：

```powershell
Get-PSSnapin
```

若要取得每個 Windows PowerShell 提供者的嵌入式管理單元，請輸入：

```powershell
Get-PSProvider | Format-List name, pssnapin
```

若要取得 Windows PowerShell 嵌入式管理單元中的 Cmdlet 清單，請輸入：

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a>安裝嵌入式管理單元

內建的嵌入式管理單元會在系統中註冊，並在您開始 Windows PowerShell 時新增到預設會話中。 不過，您必須註冊您建立或從其他人取得的嵌入式管理單元，然後將嵌入式管理單元新增至您的會話。

### <a name="registering-a-snap-in"></a>註冊嵌入式管理單元

Windows PowerShell 嵌入式管理單元是以編譯成 .dll 檔案的 .NET Framework 語言撰寫的程式。 若要在嵌入式管理單元中使用提供者和 Cmdlet，您必須先註冊嵌入式管理單元， (將它新增至登錄) 。

大部分的嵌入式管理單元都包含一個安裝程式， (.exe 或 .msi 檔案) 為您註冊 .dll 檔案。 但是，如果您以 .dll 檔案的形式接收嵌入式管理單元，您可以在系統上註冊。 如需詳細資訊，請參閱 MSDN library 中的 [如何註冊 Cmdlet、提供者和主機應用程式](https://go.microsoft.com/fwlink/?LinkID=143619) 。

若要取得系統上所有已註冊的嵌入式管理單元，或確認已註冊嵌入式管理單元，請輸入：

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a>將嵌入式管理單元新增至目前的會話

若要將已註冊的嵌入式管理單元新增至目前的會話，請使用 Add-PsSnapin Cmdlet。 例如，若要將 Microsoft SQL Server 嵌入式管理單元新增至會話，請輸入：

```powershell
Add-PSSnapin sql
```

命令完成之後，就可以在會話中使用嵌入式管理單元中的提供者和 Cmdlet。 不過，只有在目前的會話中才能使用它們，除非您儲存它們。

### <a name="saving-the-snap-ins"></a>儲存嵌入式管理單元

若要在未來的 Windows PowerShell 會話中使用嵌入式管理單元，請在 Windows PowerShell 設定檔中新增 Add-PsSnapin 命令。 或者，將嵌入式管理單元名稱匯出到主控台檔案。

如果您將 Add-PSSnapin 命令新增至您的設定檔，它在所有未來的 Windows PowerShell 會話中都可以使用。 如果您在會話中匯出嵌入式管理單元的名稱，只有在需要嵌入式管理單元時，才能使用匯出檔案。

若要將 Add-PsSnapin 命令新增至您的 Windows PowerShell 設定檔，請開啟您的設定檔、貼上或輸入命令，然後儲存設定檔。 如需詳細資訊，請參閱 about_Profiles。

若要將嵌入式管理單元從主控台檔案中的會話儲存 ( console01.psc1) ，請使用 Export-Console Cmdlet。 例如，若要將目前會話設定中的嵌入式管理單元儲存到目前目錄中的 Newconsole.psc1. console01.psc1 檔案，請輸入：

```powershell
Export-Console NewConsole
```

如需詳細資訊，請參閱匯出主控台。

### <a name="opening-windows-powershell-with-a-console-file"></a>使用主控台檔案開啟 WINDOWS POWERSHELL

若要使用包含嵌入式管理單元的主控台檔案，請從 Cmd.exe 或另一個 Windows PowerShell 會話中的命令提示字元開始 Windows PowerShell ( # A0) 。 使用 PsConsoleFile 參數來指定包含嵌入式管理單元的主控台檔案。 例如，下列命令會使用 Newconsole.psc1. console01.psc1 主控台檔案啟動 Windows PowerShell：

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

嵌入式管理單元中的提供者和 Cmdlet 現在可在會話中使用。

### <a name="removing-a-snap-in"></a>移除嵌入式管理單元

若要從目前的會話移除 Windows PowerShell 嵌入式管理單元，請使用 Remove-PsSnapin Cmdlet。 例如，若要從目前的會話移除 SQL Server 嵌入式管理單元，請輸入：

```powershell
Remove-PSSnapin sql
```

此 Cmdlet 會從會話中移除嵌入式管理單元。 仍會載入此嵌入式管理單元，但它支援的提供者和 Cmdlet 已無法再使用。

### <a name="built-in-commands"></a>內建命令

在 Windows PowerShell 2.0 和 Windows PowerShell 3.0 和更新版本中舊版的主機程式中，隨 Windows PowerShell 安裝的內建命令會封裝在自動加入至每個 Windows PowerShell 會話的嵌入式管理單元中。

從 Windows PowerShell 3.0 開始，在較新樣式的主機程式中（使用 >initialsessionstate. CreateDefault2 方法啟動會話的程式）--內建命令會封裝在模組中。 例外狀況是，一律會顯示為嵌入式管理單元的例外狀況。 核心嵌入式管理單元預設會包含在每個會話中。 內建模組會在第一次使用時自動載入。

注意：遠端會話（包括使用 New-PSSession Cmdlet 啟動的會話）是舊版的會話，其中內建的命令會封裝在嵌入式管理單元中。

下列嵌入式管理單元 (或模組) 與 Windows PowerShell 一起安裝。

- Microsoft. Core-包含用來管理 Windows PowerShell 基本功能的提供者和 Cmdlet。 它包含 FileSystem、登錄、別名、環境、函式和變數提供者，以及基本 Cmdlet，例如 Get-help、Get-Command 和 Get 歷程記錄。

- Microsoft. Host-包含 Windows PowerShell 主機所使用的 Cmdlet，例如 Start-Transcript 和停止文字記錄。

- Microsoft. 管理-包含用來管理 Windows 功能的 Cmdlet，例如 Get-Service 和 Get-ChildItem。

- Get-authenticodesignature：包含用來管理 Windows PowerShell 安全性的憑證提供者和 Cmdlet，例如和 ConvertTo-SecureString。

- （公用程式）包含用來操作物件和資料的 Cmdlet，例如，取得成員、寫入主機和格式清單。

- WSManCredSSP：包含用來管理 Windows 遠端管理服務的 WSMan 提供者和 Cmdlet，例如 Connect-WSMan 和。

## <a name="logging-snap-in-events"></a>記錄嵌入式管理單元事件

從 Windows PowerShell 3.0 開始，您可以將模組和嵌入式管理單元的 LogPipelineExecutionDetails 屬性設定為 TRUE，以記錄 Windows PowerShell 模組和嵌入式管理單元中 Cmdlet 的執行事件。 如需詳細資訊，請參閱 [about_EventLogs](about_EventLogs.md)。

## <a name="see-also"></a>另請參閱

[新增-PsSnapin](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[PsSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[移除-PsSnapin](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[Export-Console](xref:Microsoft.PowerShell.Core.Export-Console)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[about_Profiles](about_Profiles.md)

[about_Modules](about_Modules.md)

## <a name="keywords"></a>關鍵 字

about_Snapins、about_Snap_ins、about_Snap 宏
