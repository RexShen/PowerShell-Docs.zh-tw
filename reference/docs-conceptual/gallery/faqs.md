---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 資源庫常見問題集
ms.openlocfilehash: 29f930cf552abec8acbbf02f5570c6ac0a14066d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87777826"
---
# <a name="frequently-asked-questions"></a>常見問題集

## <a name="what-is-a-powershell-module"></a>什麼是 PowerShell 課程模組？

PowerShell 模組是包含一些 PowerShell 功能的可重複使用套件。 PowerShell 中的所有項目 (函數、變數、DSC 資源等) 都可以封裝成模組。 通常，模組是資料夾，內含特定路徑上所儲存的特定檔案類型。 這裡有數種不同類型的 PowerShell 模組。

## <a name="what-is-a-powershell-script"></a>什麼是 PowerShell 指令碼？

PowerShell 指令碼是儲存在 .ps1 檔案中的一系列命令，可啟用重複使用和共用。 PowerShell 工作流程也是 PowerShell 指令碼，可概述一組工作並提供這些工作的序列。 如需詳細資訊，請參閱[開始使用 PowerShell 工作流程](https://technet.microsoft.com/library/jj134242.aspx)。

## <a name="how-are-powershell-scripts-different-from-powershell-modules"></a>PowerShell 指令碼與 PowerShell 模組的差異為何？

模組一般最適合用於共用，但是我們將啟用指令碼共用，讓您更輕鬆地將工作流程和指令碼提供給社群。 如需詳細資訊，請參閱下列部落格︰

- [不要撰寫指令碼，撰寫 PowerShell 模組](https://blogs.technet.microsoft.com/heyscriptingguy/2011/06/27/dont-write-scripts-write-powershell-modules/)
- [了解 PowerShell 模組](https://blogs.technet.microsoft.com/heyscriptingguy/2015/07/10/understanding-powershell-modules/)

## <a name="how-can-i-publish-to-the-powershell-gallery"></a>如何發行至 PowerShell 資源庫？

您必須在 PowerShell 資源庫中註冊帳戶，才能將套件發行至資源庫。 原因是發行套件需要 NuGetApiKey，而這會於註冊完畢時提供。 若要註冊，請使用您的個人、工作或學校帳戶登入 PowerShell 資源庫。 第一次登入時，需要單次註冊程序。
之後，就可以在設定檔頁面上使用 NuGetApiKey。

您在資源庫中進行註冊之後，請使用 [Publish-Module][] \(英文\) 或 [Publish-Script][] \(英文\) Cmdlet 將您的套件發行至資源庫。 如需如何執行這些 Cmdlet 的詳細資訊，請瀏覽 [發行] 索引標籤，或閱讀 [Publish-Module][] 和 [Publish-Script][] 文件。

**您不需要註冊或登入資源庫，就可以安裝或儲存套件。**

## <a name="i-received-failed-to-process-request-the-specified-api-key-is-invalid-or-does-not-have-permission-to-access-the-specified-package-the-remote-server-returned-an-error-403-forbidden-error-when-i-tried-to-publish-a-package-to-the-powershell-gallery-what-does-that-mean"></a>我收到『無法處理要求。 「指定的 API 金鑰無效，或沒有存取所指定套件的權限。」。 遠端伺服器傳回錯誤：(403) 已禁止。』 錯誤。 這代表什麼？

下列原因會發生此錯誤：

- **指定的 API 金鑰無效。** 請確定您已透過帳戶指定有效的 API 金鑰。 若要取得您的 API 金鑰，請檢視設定檔頁面。
- **指定的套件名稱不屬於您。** 如果您已確認 API 金鑰正確，則可能已存在名稱與您嘗試使用之套件名稱相同的套件。 該套件可能已被其擁有者取消列出，在此情況下，它將不會出現在任何搜尋結果中。 若要判斷是否已存在具有相同名稱的套件，請開啟瀏覽器，並瀏覽至該套件的詳細資料頁面：`https://www.powershellgallery.com/packages/<packageName>`。 例如，直接瀏覽至 `https://www.powershellgallery.com/packages/pester` 會將您帶往 Pester 模組的詳細資料頁面 (不論是否列出)。 如果已存在具有衝突名稱的套件，且該套件已被取消列出，您可以︰
  - 為您的套件選取另一個名稱。
  - 連絡現有套件的擁有者。

## <a name="why-cant-i-sign-in-with-my-personal-account-but-i-could-sign-in-yesterday"></a>為什麼無法使用我的個人帳戶登入，但我昨天還可以登入？

請注意，組件庫帳戶無法容納主要電子郵件別名的變更。
如需詳細資訊，請參閱[管理您 Microsoft 帳戶上的別名](https://windows.microsoft.com/windows/outlook/add-alias-account)。

## <a name="why-dont-i-see-all-the-gallery-packages-when-i-select-all-the-category-checkboxes-on-the-packages-tab"></a>選取 [Packages] \(套件\) 索引標籤上所有的 [Category] \(類別\) 核取方塊時，為什麼看不到所有資源庫套件？

選取一個 [Category] \(類別\) 核取方塊，即表示您「想要看見這個類別中的所有套件」。 系統只會顯示所選取類別中的套件。 同樣地，當您選取所有 [Category] \(類別\) 核取方塊時，即表示您「想要查看所有類別中的所有套件」。 但由於資源庫中有某些項目並不屬於任何已列出的類別，因此它們不會出現在結果中。 若要查看資源庫中所有的套件，請取消選取所有 [Category] \(類別\)，或再次選取 [Packages] \(套件\) 索引標籤。

## <a name="what-are-the-requirements-to-publish-a-module-to-the-powershell-gallery"></a>將模組發行至 PowerShell 資源庫的需求為何？

任何一種 PowerShell 模組 (指令碼模組、二進位模組或資訊清單模組) 都可以發行至組件庫。 若要發行模組，PowerShellGet 需要知道它的一些事項：版本、描述、作者和授權方式。 會從「模組資訊清單」**(.psd1) 檔案或從 [Publish-Module][] Cmdlet 的 **LicenseUri** 參數值中讀取這項資訊，作為發佈程序的一部分。 所有發行至資源庫的模組都必須具有模組資訊清單。 任何在資訊清單中包含下列資訊的模組都可以發行至資源庫：

- 版本
- 描述
- 作者
- 模組授權條款 URI (為資訊清單 **PrivateData** 區段的一部分，或在 [Publish-Module][] Cmdlet 的 **LicenseUri** 參數中)。

## <a name="how-do-i-create-a-correctly-formatted-module-manifest"></a>如何建立格式正確的模組資訊清單？

建立模組資訊清單最簡單的方式是執行 [New-ModuleManifest][] Cmdlet。 在 PowerShell 5.0 或更新版本中，New-ModuleManifest 會使用有用中繼資料的空白欄位來產生格式正確的模組資訊清單 (例如 **ProjectUri**、**LicenseUri** 和 **Tags**)。 只要填上空白，或使用產生的資訊清單作為正確格式的範例。

若要驗證已正確地填入所有必要中繼資料欄位，請使用 [Test-ModuleManifest][] Cmdlet。

若要更新模組資訊清單檔案欄位，請使用 [Update-ModuleManifest][] Cmdlet。

## <a name="what-are-the-requirements-to-publish-a-script-to-the-gallery"></a>將指令碼發行至資源庫的需求為何？

任何一種 PowerShell 指令碼 (指令碼或工作流程) 都可以發行至組件庫。 若要發行指令碼，PowerShellGet 需要知道它的一些事項：版本、描述、作者和授權方式。 會從指令檔的 *PSScriptInfo* 區段，或從 [Publish-Script][] Cmdlet 的 **LicenseUri** 參數值中讀取這項資訊，作為發佈程序的一部分。 所有發行至資源庫的指令碼都必須具有中繼資料資訊。 任何在 PSScriptInfo 區段中包含下列資訊的指令碼都可以發行至資源庫：

- 版本
- 描述
- 作者
- 指令碼授權條款 URI，為指令碼 **PSScriptInfo** 區段的一部分，或在 [Publish-Script][] Cmdlet 的 **LicenseUri** 參數中。

## <a name="how-do-i-search"></a>如何進行搜尋？

在文字方塊中，輸入您要尋找的內容。 例如，如果您想要尋找與 Azure SQL 相關的模組，只需要輸入 "azure sql"。 搜尋引擎會在所有已發行的套件中 (包括在標題、描述和中繼資料中) 尋找那些關鍵字。 然後，根據加權的品質分數，就會顯示最接近的相符項目。 您也可以在下列欄位的搜尋查詢中使用 field:"value" 語法，以依特定欄位進行搜尋：

- Tags
- 函式
- 指令程式
- DscResources
- PowerShellVersion

因此，例如，當您搜尋 PowerShellVersion:"2.0" 時，只會顯示與 PowerShellVersion 2.0 相容的結果 (根據模組/指令碼資訊清單)。

## <a name="how-do-i-create-a-correctly-formatted-script-file"></a>如何建立格式正確的指令檔？

建立格式正確指令檔的簡單方式是執行 [New-ScriptFileInfo][] Cmdlet。 在 PowerShell 5.0 中，New-ScriptFileInfo 會使用有用中繼資料的空白欄位來產生格式正確的指令檔 (例如 **ProjectUri**、**LicenseUri** 和 **Tags**)。 只要填上空白，或使用產生的指令檔作為正確格式的範例。

若要驗證已正確地填入所有必要中繼資料欄位，請使用 [Test-ScriptFileInfo][] Cmdlet。

若要更新指令碼中繼資料欄位，請使用 [Update-ScriptFileInfo][] Cmdlet。

## <a name="what-other-types-of-powershell-modules-exist"></a>是否還有其他類型的 PowerShell 模組？

PowerShell 模組這個詞也是指實作實際功能的檔案。 指令碼模組檔案 (.psm1) 包含 PowerShell 程式碼。 二進位模組檔案 (.dll) 包含已編譯的程式碼。

以下是一種考量它的方式：封裝模組的資料夾就是模組資料夾。 模組資料夾可以包含模組資訊清單 (.psd1)，而模組資訊清單描述資料夾的內容。 實際執行工作的檔案是指令碼模組檔案 (.psm1) 和二進位模組檔案 (.dll)。 DSC 資源位於特定子資料夾中，並且實作為指令碼模組檔案或二進位模組檔案。

資源庫中的所有模組都會包含模組資訊清單，而且其中大部分模組都會包含指令碼模組檔案或二進位模組檔案。 因為這些不同的意義，所以「模組」這個詞很容易混淆。 除非明確指定，否則每次在此頁面上使用「模組」這個詞指的都是包含這些檔案的模組資料夾。

## <a name="how-does-packagemanagement-relate-to-powershellget-high-level-answer"></a>PackageManagement 與 PowerShellGet 的關聯為何？ (高階回答)

PackageManagement 是處理任何套件管理員的通用介面。 最後，不論處理 PowerShell 模組、MSI、Ruby 寶石、NuGet 套件還是 Perl 模組，您應該可以使用 PackageManagement 的命令 (Find-Package 和 Install-Package) 來進行尋找並安裝。 PackageManagement 的做法是具有插入 PackageManagement 之每個套件管理員的套件提供者。 提供者會執行所有實際工作；他們會從存放庫提取內容，並將內容安裝在本機。 套件提供者通常只需要包裝所指定套件類型的現有套件管理員工具。

PowerShellGet 是適用於 PowerShell 套件的套件管理員。 具有可透過 PackageManagement 公開 PowerShellGet 功能的 PSModule 套件提供者。 因此，您可以執行 [Install-Module][] 或 Install-Package -Provider PSModule 以從 PowerShell Gallery 安裝模組。 無法透過 PackageManagement 命令存取特定 PowerShellGet 功能 (包含 [Update-Module][] 和 [Publish-Module][])。

總而言之，PowerShellGet 只著重於具有 PowerShell 內容的高階套件管理體驗。 PackageManagement 著重於透過一組通用工作來公開所有套件管理體驗。 如果您不滿意這個回答，則在本文件底端的 **PackageManagement 實際上與 PowerShellGet 的關聯為何？** 一節中會有較長的回答。

如需詳細資訊，請瀏覽 [PackageManagement 專案頁面](https://oneget.org/)。

## <a name="how-does-nuget-relate-to-powershellget"></a>NuGet 與 PowerShellGet 的關聯為何？

PowerShell 資源庫是修改過的 [NuGet Gallery](https://www.nuget.org/) 版本。
PowerShellGet 使用 NuGet 提供者來處理 NuGet 型存放庫 (例如 PowerShell 資源庫)。

您可以對任何有效的 NuGet 存放庫或檔案共用使用 PowerShellGet。 您只需要執行 [Register-PSRepository][] Cmdlet，即可新增存放庫。

## <a name="does-that-mean-i-can-use-nugetexe-to-work-with-the-gallery"></a>是否表示我可以使用 NuGet.exe 來處理 Gallery？

可以。

## <a name="how-does-packagemanagement-actually-relate-to-powershellget-technical-details"></a>PackageManagement 實際上與 PowerShellGet 的關聯為何？ (技術詳細資料)

其實，PowerShellGet 大量採用 PackageManagement 基礎結構。

在 PowerShell Cmdlet 層，[Install-Module][] 實際上是 `Install-Package -Provider PSModule` 的精簡型包裝函式。

在 PackageManagement 套件提供者層，PSModule 套件提供者實際上會呼叫其他 PackageManagement 套件提供者。 例如，當您處理 NuGet 型組件庫 (例如 PowerShell Gallery) 時，PSModule 套件提供者會使用 NuGet 套件提供者來處理存放庫。

![PowerShellGet 架構圖](media/faqs/powershellgetArchitecture.png)

圖 1：PowerShellGet 架構

## <a name="what-is-required-to-run-powershellget"></a>執行 PowerShellGet 所需的項目為何？

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

**PowerShellGet** 也需要 .NET Framework 4.5 或更新版本。 您可以從[這裡](https://msdn.microsoft.com/library/5a4x27ek.aspx)安裝 .NET Framework 4.5 或更新版本。

## <a name="is-it-possible-to-reserve-names-for-packages-that-will-be-published-in-future"></a>是否可以為預計在未來發行的套件保留名稱？

您無法佔用套件名稱。 如果您認為某個現有套件所採用的名稱更適合您自己的套件使用，請嘗試[連絡該套件的擁有者](./how-to/working-with-packages/contacting-package-owners.md)。
如果您在幾週內未收到回應，則可以連絡支援人員，PowerShell 資源庫小組會查看該問題。

## <a name="how-do-i-claim-ownership-for-packages"></a>如何主張套件的擁有權？

如需詳細資料，請參閱 [PowerShellGallery.com 上的＜管理套件擁有者＞](./how-to/publishing-packages/managing-package-owners.md)。

## <a name="how-do-i-deal-with-a-package-owner-who-is-violating-my-package-license"></a>我應如何處理違反我的套件授權的套件擁有者？

我們建議 PowerShell 社群一起合作，來解決任何可能在套件擁有者與其他套件擁有者之間發生的爭議。 在 PowerShellGallery.com 系統管理員調解之前，您需要遵循我們所建立的[爭端解決程序](./how-to/getting-support/dispute-resolution.md)。

<!-- link references-->
[New-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest
[Test-ModuleManifest]: /powershell/module/Microsoft.PowerShell.Core/Test-ModuleManifest
[Update-ModuleManifest]: /powershell/module/PowerShellGet/Update-ModuleManifest
[Install-Module]: /powershell/module/PowershellGet/Install-Module
[New-ScriptFileInfo]: /powershell/module/PowershellGet/New-ScriptFileInfo
[Publish-Module]: /powershell/module/PowershellGet/Publish-Module
[Publish-Script]: /powershell/module/PowershellGet/Publish-Script
[Register-PSRepository]: /powershell/module/PowershellGet/Register-PSRepository
[Test-ScriptFileInfo]: /powershell/module/PowershellGet/Test-ScriptFileInfo
[Update-Module]: /powershell/module/PowershellGet/Update-Module
[Update-ScriptFileInfo]: /powershell/module/PowershellGet/Update-ScriptFileInfo
