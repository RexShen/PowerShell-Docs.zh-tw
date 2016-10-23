---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: "powershell,cmdlet,組件庫"
ms.date: 2016-10-14
contributor: manikb
title: psgallery_faqs
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 96d38c487a311852a0f670b7d3de4929fab68e4d

---

# 常見問題集

## 什麼是 PowerShell 模組？

PowerShell 模組是包含一些 PowerShell 功能的可重複使用套件。 PowerShell 中的所有項目 (函數、變數、DSC 資源等) 都可以封裝成模組。 通常，模組是資料夾，內含特定路徑上所儲存的特定檔案類型。 這裡有數種不同類型的 PowerShell 模組。

## 什麼是 PowerShell 指令碼？

PowerShell 指令碼是儲存在 .ps1 檔案中的一系列命令，可啟用重複使用和共用。 PowerShell 工作流程也是 PowerShell 指令碼，可概述一組工作並提供這些工作的序列。 如需詳細資訊，請參閱[開始使用 PowerShell 工作流程](https://technet.microsoft.com/en-us/library/jj134242.aspx)。

## PowerShell 指令碼與 PowerShell 模組的差異為何？

模組一般最適合用於共用，但是我們將啟用指令碼共用，讓您更輕鬆地將工作流程和指令碼提供給社群。 如需詳細資訊，請參閱下列部落格︰

- [不要撰寫指令碼，撰寫 PowerShell 模組](http://blogs.technet.com/b/heyscriptingguy/archive/2011/06/27/don-t-write-scripts-write-powershell-modules.aspx)
- [了解 PowerShell 模組](http://blogs.technet.com/b/heyscriptingguy/archive/2015/07/10/understanding-powershell-modules.aspx)

## 如何發行至 PowerShell Gallery？

您必須在 PowerShell Gallery 中註冊帳戶，才能將項目發行至 Gallery。 原因是發行項目需要註冊時所提供的 NuGetApiKey。 若要註冊，請使用您的個人、工作或學校帳戶登入 PowerShell Gallery。 第一次登入時，需要單次註冊程序。 之後，就可以在設定檔頁面上使用 NuGetApiKey。

您在 Gallery 中進行註冊之後，請使用 [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet 將您的項目發行至 Gallery。 如需如何執行這些 Cmdlet 的詳細資訊，請瀏覽 [發行] 索引標籤，或閱讀 [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 文件。

**您不需要註冊或登入 Gallery，就可以安裝或儲存項目。**

## 我收到『無法處理要求。 「指定的 API 金鑰無效，或沒有存取所指定套件的權限。」。 遠端伺服器傳回錯誤：(403) 已禁止。』 錯誤 (當我嘗試將項目發行至 PowerShell Gallery 時)。 這是什麼意思？

下列原因會發生此錯誤：

- **指定的 API 金鑰無效。**
     請確定您已透過帳戶指定有效的 API 金鑰。 若要取得您的 API 金鑰，請檢視設定檔頁面。
- **指定的項目名稱不是歸您所有。**
     如果您已確認 API 金鑰正確，則可能已有與您嘗試使用之項目同名的項目。 擁有者可能未列出項目，在此情況下，它不會出現在任何搜尋結果中。 若要判斷是否已有同名的項目，請開啟瀏覽器，並瀏覽至項目的詳細資料頁面：`https://www.powershellgallery.com/packages/<itemName>`。 例如，直接瀏覽至 `https://www.powershellgallery.com/packages/pester` 會將您帶往 Pester 模組的詳細資料頁面 (不論是否列出)。 如果已有具有衝突名稱的項目，而且未列出，則可以︰
    - 為您的項目選取另一個名稱。
    - 連絡現有項目的擁有者。

## 為什麼無法使用我的個人帳戶登入，但我昨天還可以登入？

請注意，組件庫帳戶無法容納主要電子郵件別名的變更。 如需詳細資訊，請參閱[管理您 Microsoft 帳戶上的別名](http://windows.microsoft.com/en-us/windows/outlook/add-alias-account)。

## 選取 [項目] 索引標籤上的所有 [類別] 核取方塊時，為什麼看不到所有組件庫項目？

選取一個 [類別] 核取方塊，即表示「我想要查看這個類別的所有項目」。 只會顯示所選取類別中的項目。 同樣地，選取所有 [類別] 核取方塊，即表示「我想要查看任何類別的所有項目」。 但是，組件庫中的某些項目不屬於任何列出的類型，因此不會出現在結果中。 若要查看組件庫中的所有項目，請取消核取所有 [類別]，或再次選取 [項目] 索引標籤。

## 將模組發行至 PowerShell Gallery 的需求為何？

任何一種 PowerShell 模組 (指令碼模組、二進位模組或資訊清單模組) 都可以發行至組件庫。 若要發行模組，PowerShellGet 需要知道它的一些事項：版本、描述、作者和授權方式。 會從「模組資訊清單」(.psd1) 檔案或從 [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet 的 **LicenseUri** 參數值中讀取這項資訊，作為發行程序的一部分。 所有發行至 Gallery 的模組都必須具有模組資訊清單。 任何在資訊清單中包含下列資訊的模組都可以發行至 Gallery：

- 版本
- 描述
- 作者
- 模組授權條款 URI (為資訊清單之 **PrivateData** 區段的一部分，或在 [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet 的 **LicenseUri** 參數中)。

## 如何建立格式正確的模組資訊清單？

建立模組資訊清單的最簡單方式是執行 [**New-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。 在 PowerShell 5.0 或更新版本中，New-ModuleManifest 會使用有用中繼資料的空白欄位來產生格式正確的模組資訊清單 (例如 **ProjectUri**、**LicenseUri** 和 **Tags**)。 只要填上空白，或使用產生的資訊清單作為正確格式的範例。

若要確認已正確地填入所有必要中繼資料欄位，請使用 [**Test-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。

若要更新模組資訊清單檔案欄位，請使用 [**Update-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。

## 將指令碼發行至 Gallery 的需求為何？

任何一種 PowerShell 指令碼 (指令碼或工作流程) 都可以發行至組件庫。 若要發行指令碼，PowerShellGet 需要知道它的一些事項：版本、描述、作者和授權方式。 會從指令檔的 *PSScriptInfo* 或從 [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet 的 **LicenseUri** 參數值中讀取這項資訊，作為發行程序的一部分。 所有發行至 Gallery 的指令碼都必須具有中繼資料資訊。 任何在 PSScriptInfo 區段中包含下列資訊的指令碼都可以發行至 Gallery：

- 版本
- 描述
- 作者
- 指令碼授權條款 URI (為指令碼之 **PSScriptInfo** 區段的一部分，或在 [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet 的 **LicenseUri** 參數中)。

## 如何進行搜尋？

在文字方塊中，輸入您要尋找的內容。 例如，如果您想要尋找與 Azure SQL 相關的模組，只需要輸入 "azure sql"。 搜尋引擎會在所有已發行的項目 (包含標題、描述和中繼資料) 中尋找這些關鍵字。 然後，根據加權的品質分數，就會顯示最接近的相符項目。 您也可以在下列欄位的搜尋查詢中使用 field:"value" 語法，以依特定欄位進行搜尋：

- 標記
- 函式
- Cmdlet
- DscResources
- PowerShellVersion

因此，例如，當您搜尋 PowerShellVersion:"2.0" 時，只會顯示與 PowerShellVersion 2.0 相容的結果 (根據模組/指令碼資訊清單)。

## 如何建立格式正確的指令檔？

建立格式正確之指令檔的最簡單方式是執行 [**New-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。 在 PowerShell 5.0 中，New-ScriptFileInfo 會使用有用中繼資料的空白欄位來產生格式正確的指令檔 (例如 **ProjectUri**、**LicenseUri** 和 **Tags**)。 只要填上空白，或使用產生的指令檔作為正確格式的範例。

若要確認已正確地填入所有必要中繼資料欄位，請使用 [**Test-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。

若要更新指令碼中繼資料欄位，請使用 [**Update-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet。

## 是否還有其他類型的 PowerShell 模組？

PowerShell 模組這個詞也是指實作實際功能的檔案。 指令碼模組檔案 (.psm1) 包含 PowerShell 程式碼。 二進位模組檔案 (.dll) 包含已編譯的程式碼。

以下是一種考量它的方式：封裝模組的資料夾就是模組資料夾。 模組資料夾可以包含模組資訊清單 (.psd1)，而模組資訊清單描述資料夾的內容。 實際執行工作的檔案是指令碼模組檔案 (.psm1) 和二進位模組檔案 (.dll)。 DSC 資源位於特定子資料夾中，並且實作為指令碼模組檔案或二進位模組檔案。

Gallery 中的所有模組都會包含模組資訊清單，而且其中大部分模組都會包含指令碼模組檔案或二進位模組檔案。 因為這些不同的意義，所以「模組」這個詞很容易混淆。 除非明確指定，否則每次在此頁面上使用「模組」這個詞指的都是包含這些檔案的模組資料夾。

## PackageManagement 與 PowerShellGet 的關聯為何？ (高階回答)

PackageManagement 是處理任何套件管理員的通用介面。 最後，不論處理 PowerShell 模組、MSI、Ruby 寶石、NuGet 套件還是 Perl 模組，您應該可以使用 PackageManagement 的命令 (Find-Package 和 Install-Package) 來進行尋找並安裝。 PackageManagement 的做法是具有插入 PackageManagement 之每個套件管理員的套件提供者。 提供者會執行所有實際工作；他們會從存放庫提取內容，並將內容安裝在本機。 套件提供者通常只需要包裝所指定套件類型的現有套件管理員工具。

PowerShellGet 是 PowerShell 項目的套件管理員。 具有可透過 PackageManagement 公開 PowerShellGet 功能的 PSModule 套件提供者。 因此，您可以執行 [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 或 Install-Package -Provider PSModule 以從 PowerShell Gallery 安裝模組。 無法透過 PackageManagement 命令存取特定 PowerShellGet 功能 (包含 [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 和 [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409))。

總而言之，PowerShellGet 只著重於具有 PowerShell 內容的高階套件管理體驗。 PackageManagement 著重於透過一組通用工作來公開所有套件管理體驗。 如果您不滿意這個回答，則在本文件底端的 **PackageManagement 實際上與 PowerShellGet 的關聯為何？**一節中會有較長的回答。

如需詳細資訊，請瀏覽 [PackageManagement 專案頁面](http://oneget.org/)。

## NuGet 與 PowerShellGet 的關聯為何？

PowerShell Gallery 是修改過的 [NuGet Gallery](http://www.nuget.org/) 版本。 PowerShellGet 使用 NuGet 提供者來處理 NuGet 型存放庫 (例如 PowerShell Gallery)。

您可以對任何有效的 NuGet 存放庫或檔案共用使用 PowerShellGet。 您只需要執行 [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) Cmdlet，即可新增存放庫。

## 是否表示我可以使用 NuGet.exe 來處理 Gallery？

可以。

## PackageManagement 實際上與 PowerShellGet 的關聯為何？ (技術詳細資料)

其實，PowerShellGet 大量採用 PackageManagement 基礎結構。

在 PowerShell Cmdlet 層，[Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) 實際上是 Install-Package -Provider PSModule 的精簡型包裝函式。

在 PackageManagement 套件提供者層，PSModule 套件提供者實際上會呼叫其他 PackageManagement 套件提供者。 例如，當您處理 NuGet 型組件庫 (例如 PowerShell Gallery) 時，PSModule 套件提供者會使用 NuGet 套件提供者來處理存放庫。

![PowerShellGet 架構](Images/powershellgetArchitecture.png)

圖 1：PowerShellGet 架構

## 執行 PowerShellGet 所需的項目為何？

一般建議挑選最新版本的 PowerShellGet 模組 (請注意，需要 .NET 4.5)。

**PowerShellGet** 模組需要 **PowerShell 3.0 或更新版本**。

因此，**PowerShellGet** 需要下列其中一個作業系統：

- Windows 10
- Windows 8.1 專業版
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** 也需要 .NET Framework 4.5 或更新版本。 您可以從[這裡](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。

## 是否可以保留未來發行之項目的名稱？

無法擅自使用項目名稱。 如果您認為現有項目已採用更符合您項目的名稱，請嘗試[連絡項目的擁有者](psgallery_contacting_item_owners.md)。 如果您在幾週內未收到回應，則可以連絡支援人員，PowerShell Gallery 小組會查看該問題。

## 如何宣告項目的擁有權？

如需詳細資訊，請參閱 [PowerShellGallery.com 上的管理項目擁有者](Managing-Item-Owners.md)。

## 如何對待違反我的項目授權的項目擁有者？

建議 PowerShell 社群一起合作，來解決任何可能在項目擁有者與其他項目之擁有者間發生的爭議。  在 PowerShellGallery.com 系統管理員調解之前，您需要遵循我們所建立的[爭端解決程序](psgallery_dispute_resolution.md)。




<!--HONumber=Oct16_HO2-->


