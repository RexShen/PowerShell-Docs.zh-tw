---
title: "取得詳細的說明資訊"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 1c514b101f708f11f095e1c95e12d7eff403e3bb

---

# 取得詳細的說明資訊
Windows PowerShell 包含詳細的說明主題，說明 Windows PowerShell 概念和 Windows PowerShell 語言。 此外，還有針對每個 Cmdlet 和提供者，以及許多函式和指令碼的說明主題。

您可以在命令提示字元中顯示這些說明主題，或在 Microsoft TechNet Library 中檢視這些主題的最近更新版本。 許多裝載 Windows PowerShell 的程式 (例如 Windows PowerShell 整合式指令碼環境) 都提供額外的說明功能，例如即時線上說明和編譯的說明檔案 (.chm)。

## 取得 Cmdlet 的說明
若要取得 Windows PowerShell Cmdlet 的相關說明，請使用 [Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) Cmdlet。 例如，若要取得 [Get-ChildItem [m2]](https://technet.microsoft.com/en-us/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) Cmdlet 的說明，請輸入：

```
get-help get-childitem
```

或

```
get-childitem -?
```

您甚至可以取得 Get\-Help Cmdlet 的相關說明。 例如：

```
get-help get-help
```

若要取得工作階段中的所有 Cmdlet 說明主題清單，請輸入︰

```
get-help -category cmdlet
```

若要一次顯示一頁說明主題，請使用 **help** 函式或其別名 **man**。 例如，若要顯示 Get\-ChildItem Cmdlet 的說明，請輸入

```
man get-childitem
```

或

```
help get-childitem
```

若要顯示 Cmdlet、函數或指令碼的詳細資訊，包括其參數的描述及其使用範例，請使用 Get\-Help Cmdlet 的 *Detailed* 參數。 例如，若要取得 Get\-ChildItem Cmdlet 的詳細資訊，請輸入：

```
get-help get-childitem -detailed
```

若要顯示說明主題中的所有內容，請使用 Get\-Help Cmdlet 的 *Full* 參數。 例如，若要顯示 Get\-ChildItem Cmdlet 之說明主題中的所有內容，請輸入：

```
get-help get-childitem -full
```

若要取得 Cmdlet 之參數的詳細說明，請使用 Get\-Help Cmdlet 的 *Parameter* 參數。 例如，若要取得 Get\-ChildItem Cmdlet 之所有參數的詳細說明，請輸入：

```
get-help get-childitem -parameter *
```

若只要顯示說明主題中的範例，請使用 Get\-Help 的 *Example* 參數。 例如，若只要顯示 Get\-ChildItem Cmdlet 之說明主題中的範例，請輸入：

```
get-help get-childitem -examples
```

如需如何為您撰寫的 Cmdlet 撰寫說明主題的資訊，請參閱 MSDN 中的＜How to Write Cmdlet Help＞(如何撰寫 Cmdlet 說明) 主題。

## 取得概念性說明
Get\-Help Cmdlet 也會顯示有關 Windows PowerShell 中概念性主題的相關資訊，包括 Windows PowerShell 語言的相關主題。 概念性說明主題是以 "about\_" 首碼為開頭，例如 about\_line\_editing。 (概念性主題的名稱必須以英文輸入，即使是在非英文版的 Windows PowerShell 中也一樣)。

若要顯示概念性主題清單，請輸入︰

```
get-help about_*
```

若要顯示特定說明主題，請輸入主題名稱，例如︰

```
get-help about_command_syntax
```

Get\-Help 的參數 (例如 *Detailed*、*Parameter* 和 *Examples*) 不會影響概念性說明主題的顯示方式。

## 取得提供者的相關說明
Get\-Help Cmdlet 會顯示 Windows PowerShell 提供者的相關資訊。 若要取得提供者的說明，請輸入 "Get\-Help"，後面接著提供者名稱。 例如，若要取得登錄提供者的說明，請輸入：

```
get-help registry
```

若要取得工作階段中的所有提供者說明主題清單，請輸入

```
get-help -category provider
```

Get\-Help 的參數 (例如 *Detailed*、*Parameter* 和 *Examples*) 不會影響提供者說明主題的顯示方式。

## 取得指令碼和函式的相關說明
Windows PowerShell 中的許多指令碼和函式都有說明主題。 使用 Get\-Help Cmdlet 可顯示指令碼和函數的說明主題。

若要顯示函數的說明，請輸入"get\-help"，後面接著函數名稱。 例如，若要取得 Disable\-PSRemoting 函數的說明，請輸入︰

```
get-help disable-psremoting
```

若要顯示指令碼的說明，請輸入指令碼檔案的完整路徑。 如果指令碼位於 Path 環境變數中所列的路徑，您可以省略命令中的路徑。

例如，如果您的 C:\\PS\-Test 目錄中有稱為 "TestScript.ps1" 的指令碼，若要顯示該指令碼的說明主題，請輸入︰

```
get-help c:\ps-test\TestScript.ps1
```

為顯示 Cmdlet 說明所設計的參數 (例如 *Detailed*、*Full*、*Examples* 和 *Parameter*) 也適用於指令碼說明和函式說明。 不過，當您顯示所有說明時，若輸入"get\-help \*"，則不會顯示函數和指令碼的說明。

如需撰寫函式和指令碼說明主題的資訊，請參閱 [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)、[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) 和 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)。

## 線上取得說明
如果您連線到網際網路，取得說明的最佳方式之一是線上檢視說明主題。 由於線上主題很容易更新，因此可能會提供最新的內容。

若要線上取得說明，請嘗試 Get\-Help Cmdlet 的 *Online* 參數。 Get\-Help Cmdlet 的 *Online* 參數只適用於 Cmdlet 說明、函數說明和指令碼說明。 您無法對概念性 (關於) 主題或提供者說明主題使用 *Online* 參數。 此外，由於這是選擇性功能，因此並非每一個 Cmdlet、函式或指令碼說明主題都適用。

不過，您可以在 Microsoft TechNet Library 的 [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) 區段中，線上取得 Windows PowerShell 隨附的所有說明主題，包括提供者說明和概念性 (關於) 說明主題。

若要使用 Get\-Help Cmdlet 的 *Online* 參數，請使用下列命令格式。

```
get-help <command-name> -online
```

例如，若要取得 Get\-ChildItem Cmdlet 相關說明主題的線上版本，請輸入：

```
get-help get-childitem -online
```

如果此說明主題有線上版本可用，就會在您的預設瀏覽器中開啟。

如果某個說明主題支援線上說明，您也可以檢視該說明主題的網際網路位址 (URL)。 網際網路位址會出現在說明主題的 [相關連結] 區段中。

例如，若要查看 Add\-Computer Cmdlet 的線上版本 URL，請輸入︰

```
get-help add-computer
```

該主題之 [相關連結] 區段中的第一行會如下所示。

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

如需如何提供說明主題之線上支援的資訊，請參閱 [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)，並請參閱 MSDN (Microsoft Developer Network) Library 中的＜How to Write Cmdlet Help＞(如何撰寫 Cmdlet 說明) ([http://go.microsoft.com/fwlink/?LinkID=123415](http://go.microsoft.com/fwlink/?LinkID=123415))。

## 另請參閱
[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)
[about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
[about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
[Get-Help [m2]](https://technet.microsoft.com/en-us/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)




<!--HONumber=Jun16_HO4-->


