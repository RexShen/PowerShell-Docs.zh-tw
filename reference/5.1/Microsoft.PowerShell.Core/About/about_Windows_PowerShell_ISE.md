---
description: 說明 Windows PowerShell 整合式腳本環境 (ISE) 的功能和系統需求。
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ec99dec9ea5012b41c10a56a688b23a6fa2c9dd8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "93207871"
---
# <a name="about-windows-powershell-ise"></a>關於 Windows PowerShell ISE

## <a name="short-description"></a>簡短描述

說明 Windows PowerShell 整合式腳本環境 (ISE) 的功能和系統需求。

## <a name="long-description"></a>詳細描述

Windows PowerShell ISE 是 Windows PowerShell 的圖形化主機應用程式。
在 Windows PowerShell ISE 中，您可以在以 Windows 為基礎的單一圖形化使用者介面中執行命令，以及撰寫、測試和調試腳本。 其功能包括 Intellisense、多行編輯、tab 鍵自動完成、自動儲存、語法著色、選擇性執行、即時線上說明、顯示命令 (在視窗) 撰寫命令，以及支援雙位元組字元集和從右至左的語言。

Windows PowerShell ISE 是適用于初學者的絕佳工具。 [顯示命令視窗] 和 [新增遠端 PowerShell] 索引標籤會引導您完成工作，讓您可以在第一次嘗試時成功。 程式碼片段和錯誤指標可協助您在工作時學習 Windows PowerShell 的語言。

Advanced users 可以利用精密的偵錯工具功能、附加元件和 Windows PowerShell ISE 物件模型。

Windows PowerShell 4.0 中 Windows PowerShell ISE 的新功能

Windows PowerShell ISE 在 Windows PowerShell 4.0 中引進了兩項新功能。

- Windows PowerShell ISE 現在支援 Windows PowerShell 工作流程調試和遠端腳本的調試。 如需詳細資訊，請參閱 about_Debuggers。

- 已新增對 Windows PowerShell 預期狀態設定之提供者與設定的 IntelliSense 支援。

## <a name="starting-windows-powershell-ise"></a>開始 Windows PowerShell ISE

您可以在所有支援的 Windows 版本中安裝、啟用和準備使用 Windows PowerShell ISE。

- 在 Windows 8.1、Windows 8、Windows Server 2012 R2 和 Windows Server 2012 的 [開始畫面上，輸入 PowerShell_ISE，然後按一下 [PowerShell_ISE] 或 [Windows PowerShell ISE]。

- 在 Windows Server 2012 R2 和 Windows Server 2012 的伺服器管理員中，按一下 [工具] 功能表上的 [Windows PowerShell ISE]。

- 在舊版的 Windows 中，依序按一下 [開始]、[所有程式]、[附屬應用程式] Windows PowerShell，然後按一下 [Windows PowerShell ISE]。

- 在 Windows PowerShell 主控台中，Cmd.exe，或 Windows 中的 [執行] 或 [搜尋] 方塊中，輸入 "PowerShell_ise.exe"。 您也可以使用命令列參數，包括 NoProfile 參數。 如需詳細資訊，請參閱 [PowerShell_ISE.exe 主控台](about_powershell_ise_exe.md)說明。

## <a name="running-interactive-commands"></a>執行互動式命令

您可以在 Windows PowerShell ISE 中執行任何 Windows PowerShell 運算式或命令。 您可以使用 Cmdlet、提供者、嵌入式管理單元和模組，就像在 Windows PowerShell 主控台中使用一樣。

您可以在主控台窗格中輸入或貼上互動式命令。 若要執行命令，您可以使用按鈕、功能表項目和鍵盤快速鍵。

您可以使用多行編輯功能，一次在主控台窗格中輸入或貼上數行程式碼。 當您按向上鍵來重新叫用先前的命令時，命令中的所有行都會被回收。 當您輸入命令時，請按 SHIFT + ENTER 鍵，讓新的空白行出現在目前的行下方。

## <a name="viewing-output"></a>查看輸出

命令和腳本的結果會顯示在主控台窗格中。 您可以使用鍵盤快速鍵或工具列上的 [複製] 按鈕來移動或複製主控台窗格中的結果，也可以在腳本窗格或主控台窗格或其他程式中貼上結果。 若要清除主控台窗格，請按一下 [清除輸出窗格] 按鈕，或輸入下列其中一個命令：

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a>撰寫腳本和函式

在腳本窗格中，您可以開啟、撰寫、編輯和執行腳本。 腳本窗格可讓您使用按鈕和鍵盤快速鍵來編輯腳本。 您也可以在腳本窗格和主控台窗格之間複製、剪下和貼上文字。

您可以使用選擇性執行功能來執行全部或部分的腳本。 若要執行腳本的一部分，請選取您要執行的文字，然後按一下 [執行選取範圍] 按鈕或按下 F8。 根據預設，F8 會執行目前的行。

先進的編輯功能包括大括弧比對、展開-折迭、行號、錯誤指標、區塊編輯和縮排、rich copy 和大小寫轉換。

## <a name="getting-help"></a>取得協助

Windows PowerShell ISE 包含描述其用法的說明主題。 此外，您可以從腳本和命令窗格存取所有已安裝的說明檔。

Windows PowerShell ISE 也支援即時線上說明。 若要取得特定 Cmdlet、提供者或關鍵字的說明，請將游標放在專案的名稱，然後按下 F1。 若要搜尋說明主題，請按 F1 並輸入搜尋字詞。

若要更新電腦上的說明主題，請使用 [說明] 功能表中的 [更新 Windows PowerShell 說明] 專案。 此專案會在目前的 UI 文化特性中，更新目前會話中模組的說明。 它相當於執行不含參數的 Update-Help Cmdlet。 若要更新 Windows PowerShell 隨附的 Cmdlet 說明，請使用 [以系統管理員身分執行] 選項開始 Windows PowerShell ISE。

您也可以在 Windows PowerShell ISE 中使用 Get-help、Save-Help 和 Update-Help Cmdlet，就像在 Windows PowerShell 主控台中使用一樣。 不過，在 Windows PowerShell ISE 中，Help 函式會顯示整個說明主題，而不是一次一個頁面。

## <a name="debugging-scripts"></a>調試腳本

您可以使用 Windows PowerShell ISE 偵錯工具來進行 Windows PowerShell 腳本或函式的偵錯工具。 當您對腳本進行偵錯工具時，您可以使用功能表項目和快速鍵來執行您在 Windows PowerShell 主控台中執行的許多相同工作。 例如，若要在腳本中設定行中斷點，請在程式程式碼上按一下滑鼠右鍵，然後按一下 [切換中斷點]。

當您在偵錯工具中逐步執行腳本時，偵錯工具會精確地顯示命令的哪個部分正在執行，並自動開啟包含所呼叫函式和腳本的檔案。

根據預設，切換中斷點功能表項目會在腳本中的整個程式列上設定中斷點，但您可以在變數或命令名稱上設定中斷點。
您也可以根據行號和資料行編號，在命令上設定中斷點，讓您更輕鬆地進行較長的管線命令的偵錯工具。

通常，您只要在 Windows PowerShell ISE 中開啟腳本檔案，就可以在腳本中進行語法錯誤的偵錯工具。 錯誤指標會識別語法錯誤和大綱功能，可讓您折迭腳本的各個部分以專注于問題點。

您也可以在命令窗格中使用 Windows PowerShell 偵錯工具 Cmdlet，就如同您在主控台中使用它們一樣。

## <a name="running-remote-commands"></a>執行遠端命令

新的遠端 PowerShell 索引標籤功能，可讓您輕鬆地在本機電腦或遠端電腦上建立持續性的使用者管理 Windows PowerShell 會話 ( 「PSSession」 ) 。 此命令會開啟一個快顯視窗，提示您輸入電腦名稱稱，以及有權在遠端電腦上執行命令的使用者帳戶。

## <a name="customizing-the-view"></a>自訂視圖

您可以使用 Windows PowerShell ISE 功能來移動和調整主控台窗格和腳本窗格的大小。 您可以顯示和隱藏任一個窗格，也可以變更所有窗格中的文字大小。

您也可以使用 [選項] 視窗來自訂 Windows PowerShell ISE 的外觀和操作。 此外，Windows PowerShell ISE 還有自訂主機變數 $psISE，您可以用來自訂 Windows PowerShell ISE，包括加入功能表和功能表項目。

## <a name="windows-powershell-ise-profile"></a>Windows PowerShell ISE 設定檔

Windows PowerShell ISE 有自己的 Windows PowerShell 設定檔 Microsoft.PowerShellISE_profile.ps1。 在此設定檔中，您可以儲存 Windows PowerShell ISE 中使用的函式、別名、變數與命令。

Windows PowerShell AllHosts 設定檔中的專案 (CurrentUser \\ AllHosts 和 AllUsers \\ AllHosts) 也可以在 Windows PowerShell ISE 中取得，就如同在任何 Windows PowerShell 主機程式中一樣。 不過，Windows PowerShell 主控台設定檔中的專案無法在 Windows PowerShell ISE 中使用。

您可以在 Windows PowerShell ISE 說明和 about_Profiles 中取得移動和重新設定設定檔的指示。

## <a name="notes"></a>注意

Windows PowerShell ISE 是選用的 Windows 功能，預設會在用戶端和伺服器版本的 Windows 上開啟。 若要在用戶端版本的 Windows 中啟用和停用 Windows PowerShell ISE，請使用主控台中的 [開啟或關閉 Windows 功能]。 若要在伺服器版本的 Windows 中啟用和停用 Windows PowerShell ISE，請使用伺服器管理員中的 [新增角色及功能]。

由於 Windows PowerShell ISE 需要使用者介面，因此無法在 Windows Server 的 Server Core 安裝上運作。 但是，如果您新增 Windows PowerShell ISE 功能，安裝會自動以 GUI 轉換成伺服器。

Windows PowerShell ISE 建置於 Windows Presentation Foundation (WPF) 上。
如果 Windows PowerShell ISE 的圖形化元素無法在您的系統上正確轉譯，您可以在系統上新增或調整「停用 WPF 硬體加速」圖形轉譯設定，以解決此問題。 如需詳細資訊，請參閱 MSDN library 中的圖形轉譯登錄 [設定](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings) 。

## <a name="see-also"></a>另請參閱

[about_Debuggers](about_Debuggers.md)

[about_Profiles](about_Profiles.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get-Help](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-IseSnippet](xref:ISE.Get-IseSnippet)

[Import-IseSnippet](xref:ISE.Import-IseSnippet)

[New-IseSnippet](xref:ISE.New-IseSnippet)

[Save-Help](xref:Microsoft.PowerShell.Core.Save-Help)

[Show-Command](xref:Microsoft.PowerShell.Utility.Show-Command)

[Update-Help](xref:Microsoft.PowerShell.Core.Update-Help)
