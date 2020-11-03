---
description: 描述 PowerShell 的群組原則設定
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 1533908be91703efd8509653b30d30de6b7c4a84
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207075"
---
# <a name="about-group-policy-settings"></a>關於群組原則設定

## <a name="short-description"></a>簡短描述
描述 PowerShell 的群組原則設定

## <a name="long-description"></a>完整描述

PowerShell 包含群組原則設定，可協助您在企業環境中為 Windows 電腦定義一致的設定值。

PowerShell 群組原則設定位於下列群組原則路徑：

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

使用者設定路徑中的群組原則設定優先于電腦設定路徑中群組原則的設定。

安裝範本之後，您可以在群組原則編輯器中編輯這些設定 (`gpedit.msc`) 。

原則如下所示：

- 開啟模組記錄：設定模組的 **LogPipelineExecutionDetails** 屬性。
- 開啟 PowerShell 指令碼區塊記錄：啟用所有 PowerShell 指令碼的詳細記錄。
- 開啟指令碼執行：設定 PowerShell 執行原則。
- 開啟 PowerShell 轉譯：將 PowerShell 命令的輸入和輸出，擷取到以文字為基礎的文字記錄。
- 設定的預設來源路徑 `Update-Help` ：將可更新的說明的來源設定為目錄，而不是網際網路。

如需取得其他範本及設定群組原則的詳細資訊，請參閱 [如何在 Windows 中建立和管理群組原則系統管理範本的集中存放區][gpstore]。

## <a name="turn-on-module-logging"></a>開啟模組記錄

[ **開啟模組記錄** ] 原則設定會開啟所選 PowerShell 模組的記錄功能。 設定在所有受影響電腦上的所有會話中都有效。

如果您啟用此原則設定並指定一或多個模組，則會在事件檢視器的 Windows PowerShell 記錄檔中記錄指定模組的管線執行事件。

如果您停用此原則設定，則會停用所有 PowerShell 模組的執行事件記錄。

如果未設定此原則設定，則每個模組的 **LogPipelineExecutionDetails** 屬性會決定是否要記錄模組的執行事件。 依預設，所有模組的 **LogPipelineExecutionDetails** 屬性都設定為 False。

若要開啟模組的模組記錄，請使用下列命令格式。 模組必須匯入會話中，而且此設定只會在目前的會話中生效。

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

若要為特定電腦上的所有會話開啟模組記錄，請將上述命令新增至 [所有使用者的 PowerShell 設定檔] (`$Profile.AllUsersAllHosts`) 。

如需模組記錄的詳細資訊，請參閱 [about_Modules](about_Modules.md)。

## <a name="turn-on-powershell-script-block-logging"></a>開啟 PowerShell 腳本區塊記錄

**開啟 Powershell 腳本區塊記錄** 原則設定可讓您將所有 PowerShell 腳本輸入記錄到 Microsoft Windows Powershell/操作事件記錄檔。 如果您啟用此原則設定，PowerShell Core 將會記錄命令、腳本區塊、函式和腳本的處理（無論是以互動方式叫用，還是透過 automation）。

如果您停用此原則設定，則會停用 PowerShell 指令碼輸入的記錄功能。 如果您啟用指令碼區塊引動過程記錄，PowerShell 會額外記錄命令、指令碼區塊、函式或指令碼啟動或停止時的事件。 啟用引動過程記錄會產生大量的事件記錄檔。

## <a name="turn-on-script-execution"></a>開啟腳本執行

[ **開啟腳本執行** ] 原則設定會設定電腦和使用者的執行原則，以決定允許執行的腳本。

如果您啟用此原則設定，您可以從下列原則設定中進行選取。

- 只有 **已簽署的腳本** 才能讓腳本只有在由受信任的發行者簽署時才能執行。 此原則設定相當於 AllSigned 執行原則。

- **允許本機腳本和遠端簽署的腳本** 允許執行所有本機腳本。 源自網際網路的腳本必須由信任的發行者簽署。 此原則設定相當於 RemoteSigned 執行原則。

- **允許** 所有腳本都可執行所有腳本。 此原則設定相當於不受限制的執行原則。

如果您停用此原則設定，則不允許執行任何腳本。 此原則設定等同于限制的執行原則。

如果您停用或未設定此原則設定，則 Cmdlet 為電腦或使用者設定的執行原則會 `Set-ExecutionPolicy` 決定是否允許執行腳本。 預設值為 [受限制]。

如需詳細資訊，請參閱 [about_Execution_Policies](about_Execution_Policies.md)。

## <a name="turn-on-powershell-transcription"></a>開啟 powershell 轉譯

[ **開啟 PowerShell** 轉譯原則] 設定可讓您將 PowerShell Core 命令的輸入和輸出，捕捉到文字型文字記錄中。 如果您啟用此原則設定，PowerShell Core 將會啟用 PowerShell Core 的轉譯記錄，以及利用 PowerShell Core 引擎的任何其他應用程式。 根據預設，PowerShell Core 會將文字記錄輸出記錄到每個使用者的我的檔目錄中，檔案名會包含 ' PowerShell_transcript '，以及電腦名稱稱和開始時間。
啟用此原則相當於在每個 PowerShell Core 會話上呼叫 Start-Transcript Cmdlet。

如果您停用此原則設定，則預設會停用以 PowerShell 為基礎之應用程式的轉譯記錄，不過仍然可以透過 Start-Transcript Cmdlet 啟用轉譯。

如果您使用 OutputDirectory 設定來啟用將記錄記錄到共用位置，請務必限制對該目錄的存取，以防止使用者查看其他使用者或電腦的文字記錄。

## <a name="set-the-default-source-path-for-update-help"></a>設定 Update-Help 的預設來源路徑

[ **設定 update-help 的預設來源路徑** ] 原則設定會設定 Cmdlet 之 **SourcePath** 參數的預設值 `Update-Help` 。
此設定可防止使用者使用此 `Update-Help` Cmdlet 從網際網路下載說明檔。

> [!NOTE]
> 此群組原則設定會出現在 [ **電腦** 設定和 **使用者** 設定] 之下。 不過，只有 [ **電腦** 設定] 下的群組原則設定才會生效。 [ **使用者** 設定] 下的群組原則設定會被忽略。

指令 `Update-Help` 程式會下載並安裝適用于 PowerShell 模組的最新說明檔案，並將它們安裝在電腦上。 根據預設，會 `Update-Help` 從模組所指定的網際網路位置下載新的說明檔。

不過，您可以使用 `Save-Help` Cmdlet 將最新的說明檔下載到檔案系統位置（例如網路共用），然後使用指令程式 `Update-Help` 從檔案系統位置取得說明檔，並將它們安裝在電腦上。 Cmdlet 的 **SourcePath** 參數會 `Update-Help` 指定檔案系統位置。

藉由提供 **sourcepath** 參數的預設值，此群組原則設定會以隱含方式將 **sourcepath** 參數新增至所有 `Update-Help` 命令。 使用者可以藉由輸入不同的檔案系統位置，覆寫指定為預設值的特定檔案系統位置。
但它們無法從命令移除 **SourcePath** 參數 `Update-Help` 。

如果您啟用此原則設定，您可以指定 **SourcePath** 參數的預設值。 輸入檔案系統位置。

如果此原則設定已停用或未設定，則 Cmdlet 的 **SourcePath** 參數沒有預設值 `Update-Help` 。 使用者可以從網際網路或任何檔案系統位置下載說明。

如需詳細資訊，請參閱 [about_Updatable_Help](about_Updatable_Help.md)。

## <a name="keywords"></a>關鍵字

about_Group_Policies about_GroupPolicy

## <a name="see-also"></a>另請參閱

[about_Execution_Policies](about_Execution_Policies.md)

[about_Modules](about_Modules.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-executionpolicy](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[Get-Module](xref:Microsoft.PowerShell.Core.Get-Module)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
