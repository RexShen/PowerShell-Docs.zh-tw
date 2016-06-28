---
title: "Windows PowerShell 50 的新功能"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 1476722e-947e-425d-a86c-50037488dc6e
translationtype: Human Translation
ms.sourcegitcommit: ca7ab17f7ba2615c7a39d1e3dd944501bab4e72c
ms.openlocfilehash: 87e4a23f93d19219a8d00671f319ef93a96fbbf6

---

# Windows PowerShell 的新功能
Windows PowerShell® 5.0 包括一些重要的新功能，能夠擴充用途、改善可用性，並讓您更輕鬆且全面地控制及管理 Windows 環境。

Windows PowerShell 5.0 與舊版相容。 針對 Windows PowerShell 4.0、Windows PowerShell 3.0 及 Windows PowerShell 2.0 所設計的 Cmdlet、提供者、模組、嵌入式管理單元、指令碼、函式及設定檔，通常可在不進行變更的情況下於 Windows PowerShell 5.0 中運作。

Windows Server® 2016 Technical Preview 和 Windows 10® 預設會安裝 Windows PowerShell 5.0。 若要在 Windows Server 2012 R2、Windows 8.1 企業版或 Windows 8.1 專業版上安裝 Windows PowerShell 5.0，請下載並安裝 [Windows Management Framework 5.0](http://aka.ms/wmf5download)。 請務必先閱讀下載詳細資料，並確認符合所有系統需求，然後再安裝 Windows Management Framework 5.0。

## 本主題內容

-   [KB 3000850 中的 Windows PowerShell 4.0 DSC 更新](#BKMK_3000850)

-   [Windows PowerShell 5.0 的新功能](#BKMK_new50)

-   [Windows PowerShell 4.0 的新功能](#BKMK_wps4)

-   [Windows PowerShell 3.0 的新功能](#BKMK_wps3)

## <a name="BKMK_3000850"></a>2014 年 11 月的 Windows PowerShell 4.0 更新彙總套件 (KB 3000850)
[2014 年 11 月的 Windows RT 8.1、Windows 8.1 和 Windows Server 2012 R2 更新彙總套件](https://support.microsoft.com/kb/3000850/) (KB 3000850) 針對 Windows PowerShell 4.0 中的 Windows PowerShell 預期狀態設定 (DSC) 提供了許多更新與改善。 您可以在 Windows PowerShell 中執行 `Get-Hotfix -Id KB3000850`，以判斷系統是否已安裝 KB 3000850。

-   更新 [PSDesiredStateConfiguration](https://technet.microsoft.com/library/dn391651(v=wps.640).aspx) 模組中現有的 Cmdlet。

    -   [Get-DscResource](http://technet.microsoft.com/library/dn521625.aspx) 較快 (尤其是在 ISE 中)。

    -   [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) 有新的參數 –UseExisting，其會重新套用上次套用的設定。

    -   已修正 [Start-DscConfiguration](http://technet.microsoft.com/library/dn521623.aspx) \-Force。

    -   [Get-DscLocalConfigurationManager](http://technet.microsoft.com/library/dn407378.aspx) 可顯示更實用的引擎狀態資訊。

    -   [Test-DscConfiguration](http://technet.microsoft.com/library/dn407382.aspx) 現可將電腦名稱與 True 或 False 一起傳回。

    -   [New-DscChecksum](http://technet.microsoft.com/library/dn521622.aspx) 現可支援 UNC 路徑。

-   [PSDesiredStateConfiguration](http://technet.microsoft.com/library/dn391651(v=wps.640).aspx) 模組中有新的 Cmdlet。

    -   [Update-DscConfiguration](http://technet.microsoft.com/library/mt143541(v=wps.630).aspx)：可依需求執行提取伺服器檢查。

    -   [Stop-DscConfiguration](http://technet.microsoft.com/library/mt143542(v=wps.630).aspx)：可停止已在執行中的設定。

    -   [Remove-DscConfigurationDocument](http://technet.microsoft.com/library/mt143544(v=wps.630).aspx)：可讓您移除各種階段 (擱置、上一個或目前) 的設定文件。

-   語言增強功能

    -   DependsOn 現可支援複合的資源。

    -   DependsOn 現可支援在資源執行個體名稱中使用數字。

    -   評估為空的節點運算式不會再擲回錯誤。

    -   已修正節點運算式評估為空時會發生錯誤的問題。

    -   Windows PowerShell 主控台現可進行設定間的彼此呼叫。

-   提取模式的增強功能

    -   提取模式現可支援所有 ZIP 檔案。

    -   **AllowModuleOverwrite** 現可正常運作。

-   復原改善

    -   新的 **DebugMode** 可讓您重新載入資源模組。

    -   如果設定失敗，不會將 pending.mof 檔案刪除。

    -   當中繼設定已損毀時，本機設定管理員 (LCM) 現可確保較佳的復原性。

-   診斷改善

    -   當 LCM 所設的計時器設定與您指定的不同時，會顯示警告。

    -   錯誤記錄檔現會包含 Windows PowerShell 資源的呼叫堆疊。

-   彈性改善

    -   LocalConfigurationManager 資源有提供新的屬性 **ActionAfterReboot**。

        -   ContinueConfiguration (預設值)︰目標節點重新啟動之後，就會自動繼續設定。

        -   StopConfiguration︰目標節點重新啟動之後，不會自動繼續設定。

    -   一致性執行現在可能比提取作業更常發生 (或提取作業比前者更常發生)。

    -   版本管理支援：DSC 現可辨識在較新版用戶端上所產生的文件 (隨附於 [WMF 5.0](http://aka.ms/wmf5download))。

-   錯誤防範改善

    -   現在，會先強制執行模組版本再套用設定。

    -   現已正確設定 Get\-、Set\- 或 Test\-TargetResource 呼叫的 **DebugPreference**。

-   認證處理改善

    -   現在，如果 **Certificate** 和 **PSDscAllowPlainTextPassword** 兩者皆有指定，則會使用憑證。

    -   系統會解密認證，即使 Get\-TargetResource 亦然。

    -   中繼設定認證會經過加密及解密。

    -   現在，若 PSCredentials 在內嵌物件中，則會將其解密。

-   內建資源改善

    -   套件資源

        -   不會再安裝錯誤的套件 (不論從本機或 Web 來源)。

        -   現可支援 HTTPS。

    -   [套件資源](http://technet.microsoft.com/library/dn282132.aspx)中現可支援使用 HTTPS。

    -   [封存資源](http://technet.microsoft.com/library/dn249917.aspx)現可支援認證。

## <a name="BKMK_new50"></a>Windows PowerShell 5.0 的新功能

-   [Windows PowerShell 的新功能](#BKMK_newcore)

-   [Windows PowerShell 預期狀態設定的新功能](#BKMK_newDSC)

-   [Windows PowerShell ISE 的新功能](#BKMK_newISE)

-   [Windows PowerShell Web 服務的新功能](#BKMK_newOData)

-   [Windows PowerShell 5.0 的重大錯誤修正](#BKMK_5bugfix)

### <a name="BKMK_newcore"></a>Windows PowerShell 的新功能

-   自 Windows PowerShell 5.0 版開始，您可以透過使用類似其他物件導向之程式設計語言的正式語法和語意，來使用類別進行開發。 **Class**、**Enum** 與其他關鍵字已新增至 Windows PowerShell 語言以支援新功能。 如需使用類別的詳細資訊，請參閱＜about\_Classes＞。

-   Windows PowerShell 5.0 引進新的結構化資訊串流，供您在指令碼與呼叫端 (或主機環境) 之間傳送結構化的資料。 現在，您可以使用 Write\-Host 將輸出發出至資訊串流。 資訊串流也可用於 PowerShell.Streams、工作、已排定的工作和工作流程。 下列功能支援資訊串流。

    -   新的 Write\-Information Cmdlet 可讓您指定 Windows PowerShell 如何處理命令的資訊串流資料。 Write\-Host 是 Write\-Information 的包裝函式。 Write\-Information 也是支援的工作流程活動。

    -   InformationVariable 和 InformationAction 這兩個是新的一般參數 ，可讓您決定如何顯示來自命令的資訊串流。 InformationAction 的有效值為 SilentlyContinue、Stop、Continue、Inquire、Ignore 或 Suspend，預設值為 SilentlyContinue。 針對來自命令的 Write\-Host 資料，您可使用 InformationVariable 將字串指定為要儲存的變數名稱。

    -   InformationPreference (新的喜好設定變數) 能指定您在 Windows PowerShell 工作階段中針對資訊串流資料的預設喜好設定。 預設值為 SilentlyContinue。

    -   已新增 PSInformation 和 InformationAction 這兩個新的工作流程一般參數。

    -   現在，當您使用 Format\-Table 命令時，系統會評估通過串流的前 300 毫秒資料，以自動格式化資料表資料行。

-   在與 [Microsoft Research](http://research.microsoft.com/) 合作之下，已新增 ConvertFrom\-String Cmdlet。 ConvertFrom\-String 可讓您擷取及剖析文字字串內容的結構化物件。 如需詳細資訊，請參閱＜ConvertFrom\-String＞。

-   新的 Convert\-String Cmdlet 會自動根據您在 \-Example 參數中提供的範例來格式化文字。

-   新的模組 Microsoft.PowerShell.Archive 包括的 Cmdlet，可讓您將檔案和資料夾壓縮為封存 (也稱為 ZIP) 檔案、從現有的 ZIP 檔案解壓縮檔案，並將 ZIP 檔案更新為已壓縮檔案的較新版本。

-   新的模組 PackageManagement 可讓您在網際網路上探索並安裝軟體套件。 PackageManagement (前稱為 OneGet) 是現有封裝管理員 (也稱為封裝提供者) 的管理員或多工器，可統一 Windows 封裝管理與單一的 Windows PowerShell 介面。

-   針對 [PowerShell Gallery](http://www.powershellgallery.com/) (PowerShell 資源庫) 或透過執行 Register\-PSRepository Cmdlet 設定的內部模組存放庫，新的模組 PowerShellGet 可讓您尋找、安裝、發佈及更新其上的模組和 DSC 資源。

-   已新增語言關鍵字 **Hidden**，其可將 Get\-Member 結果指定為預設不顯示成員 (屬性或方法)，除非您新增 \-Force 參數。 此外，IntelliSense 結果中也不會顯示已標示為隱藏的屬性或方法，除非您所在內容中的成員應該是可見的；例如，自動變數 $This 在類別方法中應會顯示隱藏的成員。

-   已增強 New\-Item、Remove\-Item 和 Get\-ChildItem 支援 [Symbolic link](http://en.wikipedia.org/wiki/Symbolic_link) (符號連結) 的建立與管理。 New\-Item 的 **ItemType** 參數可接受 **SymbolicLink** 這個新值。 現在您可以執行 New\-Item Cmdlet，在單一行中建立符號連結。

-   Get\-ChildItem 也有新的 –Depth 參數，可以搭配 –Recurse 參數來限制遞迴。 例如，Get\-ChildItem –Recurse –Depth 2 傳回的結果包括：來自目前資料夾、目前資料夾中所有子資料夾，以及所有子資料夾內之資料夾的項目。

-   Copy\-Item 現可讓您將檔案或資料夾從某個 Windows PowerShell 工作階段複製到另一個 Windows PowerShell 工作階段，這表示您可以將檔案複製到已連線至遠端電腦的工作階段 (包括執行 [Windows Nano Server](http://blogs.technet.com/b/windowsserver/archive/2015/04/08/microsoft-announces-nano-server-for-modern-apps-and-cloud.aspx) 的電腦 ，因此不會有其他介面)。 若要複製檔案，請將新的 \-FromSession 和 \-ToSession 參數值指定為 PSSession ID，並加入 –Path 和 –Destination 以分別指定原始路徑和目的地。 例如，Copy\-Item \-Path c:\\myFile.txt \-ToSession $s \-Destination d:\\destinationFolder。

-   Windows PowerShell 轉譯已經過改良，因此它不僅能套用至主控台主機 (**powershell.exe**)，也可以套用至所有的裝載應用程式 (例如 Windows PowerShell ISE)。 轉譯選項 (包括啟用全系統轉譯) 可以透過啟用 **[打開 PowerShell 轉譯]** 群組原則設定 (位於 [系統管理範本\/Windows 元件\/Windows PowerShell]) 來設定。

-   新的詳細指令碼追蹤功能可讓您在系統上啟用對 Windows PowerShell 指令碼之使用情況的詳細追蹤和分析。 啟用詳細指令碼追蹤後，Windows PowerShell 會將所有指令碼區塊記錄在 Windows 事件追蹤 (ETW) 事件記錄檔中：**Microsoft\-Windows\-PowerShell\/Operational**。

-   從 Windows PowerShell 5.0 開始，新的密碼編譯訊息語法 Cmdlet 支援針對受密碼編譯保護之訊息，使用 IETF 標準格式來加密和解密內容，如 [RFC5652](http://tools.ietf.org/html/rfc5652) 所述。 Get\-CmsMessage、Protect\-CmsMessage 和 Unprotect\-CmsMessage Cmdlet 已加入 [Microsoft.PowerShell.Security](http://technet.microsoft.com/library/hh849807.aspx) 模組中。

-   [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) 模組的新 Cmdlet：Get\-Runspace、Debug\-Runspace、Get\-RunspaceDebug、Enable\-RunspaceDebug 和 Disable\-RunspaceDebug，可讓您設定 Runspace 偵錯選項，並啟動和停止 Runspace 偵錯。 若要偵錯任意 Runspace (即不屬於 Windows PowerShell 主控台或 Windows PowerShell ISE 工作階段預設 Runspace 的 Runspace)，Windows PowerShell 可讓您在指令碼中設定中斷點，並已新增可停止指令碼執行的中斷點，直到您可以附加偵錯 Runspace 指令碼的偵錯工具為止。 Windows PowerShell 針對 Runspace 的指令碼偵錯工具，已新增支援任意 Runspace 的巢狀偵錯。

-   新的 Format\-Hex Cmdlet 已加入[Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) 模組中。 Format\-Hex 可讓您以十六進位格式檢視文字或二進位資料。

-   Get\-Clipboard 和 Set\-Clipboard Cmdlet 已加入 [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) 模組中，它們可簡化對 Windows PowerShell 工作階段進行傳送，以及自 Windows PowerShell 工作階段進行接收的內容傳輸作業。 剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。

-   新的 Clear\-RecycleBin Cmdlet 已加入 [Microsoft.PowerShell.Management](http://technet.microsoft.com/library/hh849827(v=wps.640).aspx) 模組中，該 Cmdlet 可清空固定磁碟機的資源回收筒，包含外部磁碟機。 由於這個 Cmdlet 的 ConfirmImpact 屬性設定為 ConfirmImpact.High，因此預設會提示您確認 Clear\-RecycleBin 命令。

-   新的 New\-TemporaryFile Cmdlet 可讓您在進行指令碼處理時建立暫存檔案。 新的暫存檔案預設建立在 C:\\Users\\<user name>\\AppData\\Local\\Temp 中。

-   Out\-File、Add\-Content 和 Set\-Content Cmdlet 現在有新的 –NoNewline 參數，會省略輸出之後的新行。

-   New\-Guid Cmdlet 會利用 .NET Framework GUID類別來產生 GUID；在您撰寫指令碼或 DSC 資源時非常實用。

-   由於檔案版本資訊可能會產生誤導，尤其是在已修補檔案的情況下，因此針對 FileInfo 物件提供新的 FileVersionRaw 和 ProductVersionRaw 指令碼屬性。 例如，您可以執行下列命令，以顯示 PowerShell.exe 的上述屬性值，其中 $pid 包含 Windows Powershell 執行工作階段的處理程序識別碼：Get\-Process \-Id $pid \-FileVersionInfo | Format\-List \*版本\* \-Force。

-   新的 Enter\-PSHostProcess 和 Exit\-PSHostProcess Cmdlet 可讓您將處理程序中的 Windows PowerShell 指令碼與目前正在 Windows PowerShell 主控台中執行的處理程序分開，以進行個別偵錯。 您可執行 Enter\-PSHostProcess 來輸入或附加特定處理程序識別碼，然後執行 Get\-Runspace 以傳回處理程序內的使用中 Runspace。 完成處理程序內的指令碼偵錯時，可執行 Exit\-PSHostProcess 以中斷處理程序的連結。

-   新的 Wait\-Debugger Cmdlet 已加入 [Microsoft.PowerShell.Utility](http://technet.microsoft.com/library/hh849958.aspx) 模組中。 您可以先執行 Wait\-Debugger 來停止偵錯工具中的指令碼，然後執行指令碼中的下一個陳述式。

-   Windows PowerShell 工作流程偵錯工具現已支援命令或 TAB 鍵自動完成，您也可以偵錯巢狀工作流程函式。 現在，您只要按 **Ctrl\+Break**，即可進入執行指令碼、本機和遠端工作階段，以及工作流程指令碼中的偵錯工具。

-   Debug\-Job Cmdlet 已加人 [Microsoft.PowerShell.Core](http://technet.microsoft.com/library/hh849695.aspx) 模組中 ，以針對 Windows PowerShell 工作流程、背景，以及正在遠端工作階段中執行之工作的執行工作指令碼進行偵錯。

-   Windows PowerShell 工作已新增 AtBreakpoint 狀態。 當工作正在執行的指令碼包含所設的中斷點，且該指令碼已達中斷點時，即會套用 AtBreakpoint 狀態。 當工作在偵錯中斷點停止時，您必須執行 Debug\-Job Cmdlet 以進行工作偵錯。

-   Windows PowerShell 5.0 實作針對 $PSModulePath 中相同資料夾之單一 Windows PowerShell 模組的多個版本支援。 RequiredVersion 屬性已加入 ModuleSpecification 類別中，其有助您取得所需版本的模組；這個屬性和 ModuleVersion 屬性不可以同時存在。 現在，您可將 RequiredVersion 與 Get\-Module、Import\-Module 和 Remove\-Module Cmdlet 的 FullyQualifiedName 參數值一起使用。

-   您現在可以執行 Test\-ModuleManifest Cmdlet 來驗證模組版本。

-   Get\-Command Cmdlet 的結果現在會顯示 Version 欄；CommandInfo 已新增 Version 屬性。 Get\-Command 會顯示來自多個版本之相同模組的命令。 Version 屬性也屬於 CmdletInfo 和 ApplicationInfo 的一部分，這兩者為 CmdletInfo 的衍生類別。

-   Get\-Command 的新參數 \-ShowCommandInfo 會以 PSObjects 形式傳回 ShowCommand 資訊。 當使用 Windows PowerShell 遠端在 Windows PowerShell ISE 中執行 Show\-Command 時，這個功能特別實用。 –ShowCommandInfo 參數已取代 Microsoft.PowerShell.Utility 模組中現有的 Get\-SerializedCommand 函式，但 Get\-SerializedCommand 指令碼仍可支援舊版指令碼。

-   新的 Get\-ItemPropertyValue Cmdlet 讓您不需使用點標記法，即可取得屬性值。 例如，在舊版的 Windows PowerShell 中，您可以執行下列命令，以取得 PowerShellEngine 登錄機碼之 Application Base 屬性的值：**(Get\-ItemProperty \-Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine \-Name ApplicationBase).ApplicationBase**。 從 Windows PowerShell 5.0 開始，您可以執行 **Get\-ItemPropertyValue \-Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine \-Name ApplicationBase**。

-   Windows PowerShell 主控台現在和 Windows PowerShell ISE 相同，都是使用語法著色。

-   新的 NetworkSwitch 模組所包含的 Cmdlet 可讓您將交換器、虛擬 LAN (VLAN) 和基本層級 2 網路交換器連接埠設定套用至 Windows Server 2012 R2 標誌認證的網路交換器。

-   FullyQualifiedName 參數已加入 Import\-Module 和 Remove\-Module Cmdlet 中 ，以支援儲存單一模組的多個版本。

-   Save\-Help、Update\-Help、Import\-PSSession、Export\-PSSession 和 Get\-Command 皆有 ModuleSpecification 類型的新參數 FullyQualifiedModule。 您可新增這個參數來指定模組的完整名稱。

-   **$PSVersionTable.PSVersion** 的值已經更新至 5.0。

### <a name="BKMK_newDSC"></a>Windows PowerShell 預期狀態設定的新功能

-   Windows PowerShell 語言增強功能可讓您使用類別來定義 Windows PowerShell 預期狀態設定 (DSC) 資源。 Import\-DscResource 現為真實動態關鍵字；Windows PowerShell 會剖析指定模組的根模組，搜尋包含 DscResource 屬性的類別。 現在，您可以使用類別來定義 DSC 資源；在這種情況下，模組資料夾中不需具備 MOF 檔案，也不需要 DSCResource 子資料夾。 Windows PowerShell 模組檔案可以包含多個 DSC 資源類別。

-   PSDesiredStateConfiguration 模組中的下列 Cmdlet 已新增 ThrottleLimit 參數： 您可新增 ThrottleLimit 參數來指定要在目標電腦或裝置上同時運作的命令數。

    -   Get\-DscConfiguration

    -   Get\-DscConfigurationStatus

    -   Get\-DscLocalConfigurationManager

    -   Restore\-DscConfiguration

    -   Test\-DscConfiguration

    -   Compare\-DscConfiguration

    -   Publish\-DscConfiguration

    -   Set\-DscLocalConfigurationManager

    -   Start\-DscConfiguration

    -   Update\-DscConfiguration

-   使用集中式 DSC 錯誤報告時，不只會將豐富的錯誤資訊記錄到事件記錄檔中，還可將其傳送到中央位置以便稍後進行分析。 您可以使用這個中央位置，來儲存任何伺服器在其環境中所發生的 DSC 設定錯誤。 於中繼設定中定義報表伺服器之後，會將所有錯誤傳送到報表伺服器，然後儲存在資料庫中。 不論是否有設定要從提取伺服器提取設定的目標節點，您都可以設定這項功能。

-   針對 Windows PowerShell ISE 的改善能簡化 DSC 資源的撰寫。 您現在可以執行下列操作：

    -   在區塊的空白行輸入 **Ctrl\+空格鍵**，列出 **設定** 或**節點**區塊中的所有 DSC 資源。

    -   **列舉**類型資源屬性的自動完成功能。

    -   DSC 資源 **DependsOn** 屬性的自動完成功能，以設定的其他資源執行個體為基礎。

    -   增強的資源屬性值 TAB 鍵自動完成。

-   使用者現在可以將 **PSDscRunAsCredential** 屬性新增至節點區塊，以執行指定之認證集合下的資源。 例如，PSDscRunAsCredential \= Get\-Credential Contoso\\DscUser。 這項功能非常適合用來建立設定，以執行 Windows Installer 和可執行的安裝程式、存取每位使用者的登錄區，或執行目前使用者內容以外的其他工作。

-   針對 **Configuration** 關鍵字，已可支援 32 位元 (x86 為基礎)。

-   Windows PowerShell 現已支援 DSC 設定的自訂說明，您可透過將 \[CmdletBinding()] 加入產生的設定函式中來進行定義。

-   新的 **DscLocalConfigurationManager** 屬性可將設定區塊指定為中繼設定，用於設定 DSC 本機設定管理員。 此屬性會限制住設定，讓它只包含設定 DSC 本機設定管理員的項目。 在處理期間，此設定會產生 \*.meta.mof 檔案，然後會執行 Set\-DscLocalConfigurationManager Cmdlet 以將此檔案傳送至適當的目標節點。

-   Windows PowerShell 5.0 現已允許部分設定。 您可將設定文件以片段形式傳遞到節點。 若要讓節點接收設定文件的多個片段，您必須先設好該節點的本機設定管理員，以指定預期的片段。

-   Windows PowerShell 5.0 的 DSC 中提供跨電腦同步處理的新功能。 使用內建的 WaitFor\* 資源 (**WaitForAll**、**WaitForAny** 和 **WaitForSome**)，您現在可以於設定執行期間在電腦之間指定相依性，而不需要外部協調流程。 這些資源會透過使用 WS\-Man 通訊協定的 CIM 連線提供節點對節點同步處理。 設定可以等候另一部電腦的特定資源狀態變更。

-   Just Enough Administration (JEA) 是一種新的委派安全性功能，它可利用 DSC 和 Windows PowerShell 受限 Runspace 來協助保障企業安全，避免資料遺失或遭到員工洩漏，無論是有意還是無意。 如需 JEA 的詳細資訊，包括可以下載 xJEA DSC 資源的位置，請參閱 [Just Enough Administration, Step by Step (Just Enough Administration 逐步解說)](http://blogs.technet.com/b/privatecloud/archive/2014/05/14/just-enough-administration-step-by-step.aspx)。

-   PSDesiredStateConfiguration 模組已新增下列新的 Cmdlet。

    -   新的 Get\-DscConfigurationStatus Cmdlet 會從目標節點取得設定狀態的高層級資訊。 您可以取得上一次設定或所有設定的狀態。

    -   新的 Compare\-DscConfiguration Cmdlet 會針對指定的設定與一或多個目標節點的實際狀態進行比較。

    -   新的 Publish\-DscConfiguration Cmdlet 會將設定 MOF 檔案複製到目標節點，但不會套用設定。 直到下個一致性階段，或當您執行 Update\-DscConfiguration Cmdlet 時才會套用設定。

    -   新的 Test\-DscConfiguration Cmdlet 可讓您驗證產生的設定與所需的設定是否相符：如果設定與所需的設定相符，會傳回 True；如果實際設定與所需的設定不相符會傳回 False。

    -   新的 Update\-DscConfiguration Cmdlet 會強制處理設定。 如果本機設定管理員處於提取模式，此 Cmdlet 會從提取伺服器取得設定之後才套用。

### <a name="BKMK_newISE"></a>Windows PowerShell ISE 的新功能

-   現在，您可透過執行 Enter\-PSSession 來在存有您要編輯之檔案的電腦上啟動遠端工作階段，然後執行 **PSEdit <path and file name on the remote computer>**，以在 Windows PowerShell ISE 本機複本中編輯遠端 Windows PowerShell 指令碼和檔案。 這項功能可減輕 Windows PowerShell 檔案的編輯工作，這些檔案是儲存在 Windows Server 的 Server Core 安裝選項上，該位置並無法執行 Windows PowerShell ISE。

-   Windows PowerShell ISE 現可支援 Start\-Transcript Cmdlet。

-   現在，您可以在 Windows PowerShell ISE 中偵錯遠端指令碼。

-   新的功能表命令 **[全部中斷]** (Ctrl\+B) 可中斷在本機和遠端執行指令碼的偵錯工具。

### <a name="BKMK_newOData"></a>Windows PowerShell Web 服務的新功能 (Management OData IIS 擴充功能)

-   從 Windows PowerShell 5.0 版開始，您可以執行新 [Microsoft.PowerShell.OdataUtils](http://technet.microsoft.com/library/dn818507(v=wps.640).aspx) 模組中的 Export\-ODataEndpointProxy Cmdlet，依據特定 OData 端點公開的功能，產生一組 Windows PowerShell Cmdlet。

### <a name="BKMK_5bugfix"></a>Windows PowerShell 5.0 的重大錯誤修正

-   Windows PowerShell 5.0 包含新的 COM 實作，它在您使用 COM 物件時可提供大幅的效能改善。 如需效果的示範影片，請參閱 [Com_Perf_Improvements](http://1drv.ms/1qu3UPZ)。

-   Windows PowerShell 工作階段中第一次 Tab 鍵自動完成的效能獲得了顯著的改善，Tab 鍵自動完成時間幾乎縮短 500 毫秒。

## <a name="BKMK_wps4"></a>Windows PowerShell 4.0 的新功能
Windows PowerShell 4.0 與舊版相容。 針對 Windows PowerShell 3.0 及 Windows PowerShell 2.0 所設計的 Cmdlet、提供者、模組、嵌入式管理單元、指令碼、函式及設定檔，可在不進行變更的情況下於 Windows PowerShell 4.0 中運作。

Windows PowerShell 4.0 預設已安裝於 Windows® 8.1 和 Windows Server 2012 R2 之上。 若要在 Windows 7 SP1 或 Windows Server 2008 R2 上安裝 Windows PowerShell 4.0，請下載並安裝 [Windows Management Framework 4.0](http://www.microsoft.com/download/details.aspx?id=40855)。 請務必先閱讀下載詳細資料，並確認符合所有系統需求，然後再安裝 Windows Management Framework 4.0。

-   [Windows PowerShell 的新功能](#BKMK_core)

-   [Windows PowerShell 整合式指令碼環境 (ISE) 的新功能](#BKMK_ise)

-   [Windows PowerShell 工作流程的新功能](#BKMK_workflow)

-   [Windows PowerShell Web 服務的新功能](#BKMK_psws)

-   [Windows PowerShell Web 存取的新功能](#BKMK_powwa)

-   [Windows PowerShell 4.0 的重大錯誤修正](#BKMK_bugs)

Windows PowerShell 4.0 包括下列新功能。

### <a name="BKMK_core"></a>Windows PowerShell 的新功能

-   **Windows PowerShell 預期狀態設定** (DSC) 是 Windows PowerShell 4.0 中的新管理系統，可用來部署及管理軟體服務與這些服務執行所在之環境的設定資料。 如需 DSC 的詳細資訊，請參閱[開始使用 Windows PowerShell 預期狀態設定](https://technet.microsoft.com/en-us/library/c134aa32-b085-4656-9a89-955d8ff768d0)。

-   **Save\-Help** 現可讓您儲存遠端電腦上安裝的模組說明。 您可以使用 Save\-Help 從連線至網際網路的用戶端 (該用戶端上不需要安裝您想要取得說明的所有模組) 下載模組說明，然後將儲存的說明複製到遠端共用資料夾或無法存取網際網路的遠端電腦。

-   Windows PowerShell 偵錯工具已經增強，以針對 Windows PowerShell 工作流程及在遠端電腦上執行的指令碼進行偵錯。 Windows PowerShell 工作流程現已可以透過 Windows PowerShell 命令列或 Windows PowerShell ISE 於指令碼層級進行偵錯。 您現可透過遠端工作階段對 Windows PowerShell 指令碼 (包括指令碼工作流程) 進行偵錯。 對於中斷連線並於稍後重新連線的 Windows PowerShell 遠端工作階段，系統會保留遠端偵錯工作階段。

-   **Register\-ScheduledJob** 和 **Set\-ScheduledJob** 的 **RunNow** 參數讓您不需要再使用 **Trigger** 參數為工作設定立即開始的日期和時間。

-   **Invoke\-RestMethod** 和 **Invoke\-WebRequest** 現在可讓您使用 Headers 參數設定所有標頭。 雖然此參數一直都存在，但是它是會導致產生例外狀況或錯誤之 Web Cmdlet 的幾個參數之一。

-   **Get\-Module** 有新的參數 **FullyQualifiedName**，其類型為 **ModuleSpecification\[]**。 Get\-Module 的 **FullyQualifiedName** 參數現可讓您使用模組的名稱、版本與 (選擇性) 其 GUID 來指定模組。

-   Windows Server 2012 R2 上的預設執行原則設定是 **RemoteSigned**。 在 Windows 8.1 上，預設設定沒有任何變更。

-   Windows PowerShell 4.0 開始支援使用動態方法名稱來叫用方法。 您可以使用變數來儲存方法名稱，然後透過呼叫變數來動態叫用方法。

-   當 **PSElapsedTimeoutSec** 工作流程一般參數所指定的逾時期間過去之後，即不會刪除非同步工作流程工作。

-   新的參數 **RepeatIndefinitely** 已加入 **New\-JobTrigger** 和 **Set\-JobTrigger** Cmdlet 中。 這讓您不再需要指定 **RepetitionDuration** 參數的 **TimeSpan.MaxValue** 值來重複執行不限期間的排程工作。

-   **Passthru** 參數已加入 **Enable\-JobTrigger** 和 **Disable\-JobTrigger** Cmdlet 中。 Passthru 參數會顯示您的命令所建立或修改的任何物件。

-   **Add\-Computer** 和 **Remove\-Computer** Cmdlet 中用於指定工作群組的參數名稱現在是一致的。 這兩個 Cmdlet 現在都是使用 **WorkgroupName** 參數。

-   已經新增一般參數 **PipelineVariable**。 PipelineVariable 可讓您將管線命令 (或管線命令的一部分) 的結果儲存為可在管線的其餘部分傳遞的變數。

-   現在支援使用方法語法篩選集合。 這表示您現在可以使用簡化的語法 (類似於 Where() 或 Where\-Object 的語法，且格式為方法呼叫) 來篩選物件的集合。 範例如下：(Get\-Process).where({$\_.Name \-match 'powershell'})

-   **Get\-Process** Cmdlet 有一個新的切換參數：**IncludeUserName**。

-   已加入新的 **Get\-FileHash** Cmdlet，它會以其中一種指定的檔案格式傳回檔案雜湊。

-   在 Windows PowerShell 4.0 中，如果模組在其資訊清單中使用 **DefaultCommandPrefix** 機碼，或如果使用者使用 **Prefix** 參數匯入模組，模組的 **ExportedCommands** 屬性就會顯示模組中具有該前置詞的命令。 當您使用模組完整語法 ModuleName\\CommandName 執行命令時，命令名稱必須包含前置詞。

-   **$PSVersionTable.PSVersion** 的值已經更新至 4.0。

-   **Where()** 運算子行為已經改變。 `Collection.Where('property –match name')` 已不再接受 `"Property –CompareOperator Value"` 格式的字串運算式。 但是，**Where()** 運算子還是可以接受 Scriptblock 格式的字串運算式。

### <a name="BKMK_ise"></a>Windows PowerShell 整合式指令碼環境 (ISE) 的新功能

-   Windows PowerShell ISE 同時支援 Windows PowerShell 工作流程偵錯和遠端指令碼偵錯。

-   已新增對 Windows PowerShell 預期狀態設定之提供者與設定的 IntelliSense 支援。

### <a name="BKMK_workflow"></a>Windows PowerShell 工作流程的新功能

-   已在反覆運算管線環境中新增對新的 **PipelineVariable** 一般參數的支援，例如 System Center Orchestrator 所使用的一般參數；也就是單純地從左至右執行命令的管線，與使用資料流執行時的方向相反。

-   已經大幅增強參數繫結在 Tab 鍵自動完成案例之外的運作效能，例如使用目前 Runspace 中不存在的命令。

-   已新增對自訂容器活動的支援至 Windows PowerShell 工作階段。 如果活動參數的類型為 **Activity**、**Activity\[]** (或如果活動參數為活動的泛型集合)，且使用者已經提供指令碼區塊作為引數，則 Windows PowerShell 工作流程將會把指令碼區塊轉換成 XAML，和一般 Windows PowerShell 指令碼轉工作流程的編譯相同。

-   在當機之後，Windows PowerShell 工作流程會自動重新連線到受管理的節點。

-   您現在可以使用 **ThrottleLimit** 屬性對 **Foreach \-Parallel** 活動陳述式進行節流處理。

-   **ErrorAction** 一般參數有一個新的有效值 **Suspend**，這是工作流程專用的值。

-   現在如果沒有作用中工作階段、沒有進行中的工作，以及沒有擱置中的工作，工作流程端點就會自動關閉。 在達到自動關閉條件時，此功能可以節省做為工作流程伺服器使用之電腦上的資源。

### <a name="BKMK_psws"></a>Windows PowerShell Web 服務的新功能

-   當 Cmdlet 執行時，若 Windows PowerShell Web 服務 (PSWS，亦稱為「管理 OData IIS 擴充功能」) 發生錯誤，將會傳回更多詳細的錯誤訊息給呼叫者。 此外，錯誤碼會以 [Windows Azure REST API 錯誤碼指導方針](http://msdn.microsoft.com/library/windowsazure/dd179357.aspx)為依據。

-   端點現在可以定義 API 版本，以及強制使用特定的 API 版本。 只要用戶端與伺服器之間版本不符，就會對用戶端與伺服器顯示錯誤。

-   分派結構描述的管理作業，已經透過為結構描述中遺漏的任何欄位自動產生值的方式來簡化。 即使分派結構描述不存在，也會自動產生 (這是一個很有幫助的起點)。

-   PSWS 中的類型處理已獲得改善，以透過與 Windows PowerShell 中之 **PSTypeConverter** 類似的行為，來支援使用與預設建構函式不同之建構函式的類型。 這可以讓您搭配 PSWS 使用複雜類型。

-   PSWS 現在允許在執行查詢時展開關聯的執行個體。 對於更大的二進位內容 (例如影像、音訊或視訊) 而言，傳輸成本會很可觀，而且二進位資料最好是在沒有編碼的情況下傳輸。 PSWS 會使用具名資源資料流，在不編碼的情況下傳輸。 具名資源資料流是 **Edm.Stream** 類型實體的屬性。 每個具名資源資料流都有個別的 GET 或 UPDATE 作業的 URI。

-   OData 動作現在提供在資源上叫用非 CRUD (Create、Read、Update 及 Delete) 方法的機制。 您可以傳送 HTTP POST 要求到為動作定義的 URI 來叫用動作。 動作的參數是在 POST 要求的主體中定義。

-   若要與 Microsoft Azure 指導方針一致，應簡化所有 URL。 **Key As Segment** 中包含的變更可以讓單一機碼以區段方式表示。 請注意，使用多個機碼值的參照需要像以前一樣，以逗點分隔值並使用括弧括住。

-   在這一版的 PSWS 之前，執行 Create、Update 或 Delete 作業的唯一方式是叫用位於最上層資源的 Post、Put 或 Delete。 這一版 PSWS 的新功能是，Contained Resource 作業可讓使用者在以不那麼直接的方式 (就像原本就包含這些資源一樣) 連線相同的資源時達到相同的結果。

### <a name="BKMK_powwa"></a>Windows PowerShell Web 存取的新功能

-   您可以在網頁導向式的 Windows PowerShell Web 存取主控台中，中斷並重新連接到現有的工作階段。 網頁導向式主控台有一個 **[儲存]** 按鈕，供您在不刪除工作階段的情況下與工作階段中斷連線，然後在其他時間重新連線。

-   登入頁面會顯示預設參數。 若要顯示預設參數，請在名為 **web.config** 的檔案中，設定登入頁面的 **[選用連線設定]** 區域中顯示之所有設定的值。 您可以使用 **web.config** 檔案來設定除了第二或備用的認證集以外的所有選用連線設定。

-   在 Windows Server 2012 R2 中，您可以針對 Windows PowerShell Web 存取的授權規則進行遠端管理。 **Add\-PswaAuthorizationRule** 和 **Test\-PswaAuthorizationRule** Cmdlet 現在包含一個 Credential 參數，這個參數可以讓系統管理員從遠端電腦或在 Windows PowerShell Web 存取工作階段中管理授權規則。

-   您現在可以透過針對每個工作階段使用一個新的瀏覽器索引標籤，來於單一瀏覽器工作階段中處理多個 Windows PowerShell Web 存取工作階段。 您不需要再開啟新的瀏覽器工作階段來連接至網頁導向式之 Windows PowerShell 主控台的新工作階段。

### <a name="BKMK_bugs"></a>Windows PowerShell 4.0 的重大錯誤修正

-   **Get\-Counter** 現可傳回包含法文版 Windows 中單引號字元的計數器。

-   您現在可以檢視已還原序列化之物件上的 **GetType** 方法。

-   **\#Requires** 陳述式現在可以讓使用者要求系統管理員存取權限 (如有需要的話)。

-   **Import\-Csv** Cmdlet 現在會忽略空白行。

-   已經修正當您在執行 **Invoke\-WebRequest** 命令時，Windows PowerShell ISE 會使用太多記憶體的問題。

-   **Get\-Module** 現在會在 **Version** 欄中顯示模組版本。

-   Remove\-Item –Recurse 現在可以如預期般移除子資料夾中的項目。

-   **UserName** 屬性已加入 **Get\-Process** 輸出物件中。

-   **Invoke\-RestMethod** Cmdlet 現在會傳回所有可用結果。

-   **Add\-Member** 現在可以在雜湊表上生效，即使尚未存取雜湊表也一樣。

-   **Select\-Object –Expand** 不會再於屬性值是 Null 或空白時失敗或產生例外狀況。

-   現在，**Get\-Process** 可以在管線中搭配使用可從物件取得 **ComputerName** 屬性的其他命令。

-   **ConvertTo\-Json** 和 **ConvertFrom\-Json** 現在可以接受以雙引號括住的詞彙，而且其錯誤訊息已經當地語系化。

-   **Get\-Job** 現在會傳回任何已完成的排程工作，即使是新工作階段中的工作也一樣。

-   已經修正使用 Windows PowerShell 4.0 中的 **FileSystem** 提供者所導致的裝載及卸載 VHD 問題。 現在，於相同工作階段中掛接新的磁碟機時，Windows PowerShell 將可以偵測新的磁碟機。

-   您不需要再明確載入 **ScheduledJob** 或 **Workflow** 模組來與它們的工作類型搭配使用。

-   已經改善匯入定義巢狀工作流程之工作流程的處理效能；現在執行此程序的速度比以前更快。

## <a name="BKMK_wps3"></a>Windows PowerShell 3.0 的新功能
Windows PowerShell 3.0 包括下列新功能。

-   [Windows PowerShell 工作流程](#BKMK_Workflow)

-   [Windows PowerShell Web 存取](#BKMK_WebAccess)

-   [新的 Windows PowerShell ISE 功能](#BKMK_ISE)

-   [支援 Microsoft .NET Framework 4.0](#BKMK_NET4)

-   [支援 Windows 預先安裝環境](#BKMK_WinPE)

-   [已中斷連線的工作階段](#BKMK_Disconnected)

-   [健全的工作階段連線](#BKMK_Robust)

-   [可更新的說明系統](#BKMK_UpHelp)

-   [增強的線上說明](#BKMK_Online)

-   [CIM 整合](#BKMK_CIM)

-   [工作階段設定檔案](#BKMK_ConfigFile)

-   [排程工作與工作排程器整合](#BKMK_ScheduledJob)

-   [Windows PowerShell 語言增強功能](#BKMK_Lang)

-   [新的核心 Cmdlet](#BKMK_Core)

-   [對現有核心 Cmdlet 與提供者的改善](#BKMK_Prov)

-   [遠端模組匯入及探索](#BKMK_REM)

-   [增強的 Tab 鍵自動完成](#BKMK_TAB)

-   [模組自動載入](#BKMK_AutoLoad)

-   [模組體驗改善](#BKMK_MOD)

-   [簡化的命令探索](#BKMK_SIMPLE)

-   [改善的記錄、診斷與群組原則支援](#BKMK_LOG)

-   [格式設定與輸出改善](#BKMK_OUT)

-   [增強的主控台主機體驗](#BKMK_HOST)

-   [新的 Cmdlet 與裝載 API](#BKMK_API)

-   [效能改善](#BKMK_PERF)

-   [RunAs 與共用主機支援](#BKMK_RUNAS)

-   [特殊字元處理改善](#BKMK_CHAR)

### <a name="BKMK_Workflow"></a>Windows PowerShell 工作流程
Windows PowerShell® 工作階段將 Windows Workflow Foundation 的功能帶給 Windows PowerShell。 您現在可以使用 XAML 或使用 Windows PowerShell 語言來撰寫工作流程，以及透過與 Cmdlet 相同的執行方式來執行工作流程。 [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) Cmdlet 可取得工作流程命令，而 [Get-help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) Cmdlet 可取得工作流程的說明。

工作流程是一系列長時間執行、可重複、經常性、平行式、可中斷、可暫停，以及可重新啟動的多部電腦管理活動。 工作流程可以從蓄意或意外中斷 (例如網路中斷、Windows 重新啟動，或電源中斷) 中恢復繼續運作。

工作流程也是可攜式的；您可以將它們匯出為 XAML 檔案，或從 XAML 檔案匯入它們。 您可以撰寫自訂工作階段設定，來允許工作流程或工作流程中的活動能夠由委派或下屬使用者執行。

下列為 Windows PowerShell 工作流程的好處

-   **自動化長時間執行的連續性工作。**

-   **遠端監視長時間執行的工作**。 隨時可觀看活動的狀態與進度。

-   **多部電腦管理。** 在數百個受管理節點上以工作流程形式同時執行工作。 Windows PowerShell 工作流程包括一個一般管理參數的內建程式庫，例如 **PSComputerName**，它可以支援多部電腦管理案例。

-   **以單一工作執行方式執行複雜的處理程序。** 您可以將實作整個端對端案例的相關指令碼結合成單一工作流程。

-   **持續性**：工作流程會在其作者定義的特定時間點儲存 (或建立檢查點)，因此您可以從上一個持續工作 (或檢查點) 繼續工作流程，而不需要從頭開始重新啟動工作流程。

-   **健全性。** 自動化失敗修復。 工作流程可在計劃性與非計劃性重新啟動之後繼續執行。 您可以暫停工作流程執行，然後從上一個持續時間點繼續工作流程。 工作流程作者可以指定在一或多個受管理節點失敗時，要重新執行的特定活動。

-   **可以在已中斷連線的工作階段中中斷連線、重新連線，以及執行的能力。** 使用者可以與工作流程伺服器連線及中斷連線，但是工作流程會繼續執行。 您可以登出用戶端電腦或重新啟動用戶端電腦，以及在不中斷工作流程的情況下從另一部電腦監視工作流程執行。

-   **排程。** 工作流程工作的排定方式和任何 Windows PowerShell Cmdlet 或指令碼一樣。

-   **工作流程與連線節流處理。** 針對工作流程的執行與節點的連線，您可以進行節流處理，以確保延展性與高可用性。

### <a name="BKMK_WebAccess"></a>Windows PowerShell Web 存取
Windows PowerShell® Web 存取是一項 Windows Server 2012 功能，可以讓使用者在網頁導向式主控台中執行 Windows PowerShell 命令與指令碼。 使用網頁導向式主控台的裝置不需要 Windows PowerShell、遠端管理軟體，或瀏覽器外掛程式安裝。 它們只需要正確設定的 Windows PowerShell Web 存取閘道，以及支援 JavaScript® 並接受 Cookie 的用戶端裝置瀏覽器。

如需詳細資訊，請參閱[部署 Windows PowerShell Web 存取](http://go.microsoft.com/fwlink/p/?LinkID=221050)。

### <a name="BKMK_ISE"></a>新的 Windows PowerShell ISE 功能
Windows PowerShell® 整合式指令碼環境 (ISE) 針對 Windows PowerShell 3.0 有許多新功能，包括 IntelliSense、顯示命令視窗、統一的主控台窗格、程式碼片段、括號對稱、展開折疊區段、自動儲存、最近使用的項目清單、多種內容複製、區塊複製，以及針對撰寫 Windows PowerShell 指令碼工作流程的完整支援。 如需詳細資訊，請參閱 [about_Windows_PowerShell_ISE [v3]](https://technet.microsoft.com/en-us/library/dfa54d47-60c6-4fff-8197-c747e8d411bb)。

### <a name="BKMK_NET4"></a>支援 Microsoft .NET Framework 4
Windows PowerShell 是針對 Common Language Runtime 4.0 所建立。 Cmdlet、指令碼與工作流程作者可以使用 Windows PowerShell 中新的 Microsoft .NET Framework 4 類別，其功能包括應用程式相容性與部署、Managed Extensibility Framework、平行運算、網路、Windows Communication Foundation 及 Windows Workflow Foundation。

### <a name="BKMK_WinPE"></a>支援 Windows 預先安裝環境
Windows PowerShell 3.0 是適用於 Windows 8 之 Windows 預先安裝環境 (Windows PE) 4.0 的選用元件。 Windows PE 是啟動尚未安裝作業系統之電腦的最小作業系統，並且可以讓電腦準備好以安裝 Windows。 Windows PE 可以用來分割及格式化硬碟、複製磁碟映像至電腦，以及從網路共用位置起始 Windows 安裝程式。 Windows PowerShell 3.0 可以在 Windows PE 上使用，以管理部署、診斷與修復案例。

### <a name="BKMK_Disconnected"></a>已中斷連線的工作階段
從 Windows PowerShell 3.0 開始，您使用 New\-PSSession Cmdlet 建立之持續性使用者管理的工作階段 ("PSSessions") 會儲存在遠端電腦上。 它們已經不再與它們建立所在的工作階段相依。

您現在可以與工作階段中斷連線，而不會中斷工作階段中正在執行的命令。 您可以關閉工作階段並關閉您的電腦。 稍後您可以在相同或不同的電腦上，從不同的工作階段重新連線至工作階段。

[Get-PSSession](https://technet.microsoft.com/en-us/library/b2b10531-d0df-4746-b877-e75c09955cb6) Cmdlet 的 **ComputerName** 參數現在可以取得已連線到電腦的所有使用者工作階段，即使它們是在其他電腦上不同的工作階段中啟動。 您可以連線至工作階段、取得命令的結果、啟動新的命令，然後與工作階段中斷連線。

新增可支援「已中斷連線的工作階段」功能的 Cmdlet，包括 [Disconnect-PSSession](https://technet.microsoft.com/en-us/library/f8f95111-612f-4cba-9098-77904b0473d8)、[Connect-PSSession](https://technet.microsoft.com/en-us/library/b803dd29-f208-4079-80d4-db04d778f060) 與 Receive\-PSSession，亦已新增參數至管理 PSSessions 的 Cmdlet，例如 [Invoke-Command](https://technet.microsoft.com/en-us/library/906b4b41-7da8-4330-9363-e7164e5e6970) Cmdlet 的 **InDisconnectedSession** 參數。

只有在位於連線起始端 (用戶端) 與終止端 (伺服器) 的電腦是執行 Windows PowerShell 3.0 時，才支援「已中斷連線的工作階段」功能。

### <a name="BKMK_Robust"></a>健全的工作階段連線
Windows PowerShell 3.0 會偵測用戶端與伺服器之間是否發生未預期的連線中斷，並嘗試自動重新建立連線及繼續執行。 如果無法在配置的時間內重新建立用戶端伺服器連線，就會通知使用者並中斷連線工作階段。 嘗試重新連線期間，Windows PowerShell 會持續向使用者提供回饋。

如果是使用 InvokeCommand 啟動中斷連線的工作階段，Windows PowerShell 會為中斷連線的工作階段建立一個工作，使其更容易重新連線及繼續執行。

這些功能可提供更可靠且更容易修復的遠端體驗，並可讓使用者執行需要健全工作階段的長時間執行工作，例如工作流程。

### <a name="BKMK_UpHelp"></a>可更新的說明系統
您現在可以為您模組中的 Cmdlet 下載已更新的說明檔案。 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Cmdlet 可識別最新的說明檔案，將其從網際網路下載、解壓縮、驗證，然後安裝在模組的正確語言特定目錄中。

若要使用已更新的說明檔案，只要輸入 `Get-Help` 即可。 您不需要重新啟動 Windows 或 Windows PowerShell。 若要為 $pshome 目錄中的模組更新說明檔案，請使用 [以系統管理員身分執行] 選項啟動 Windows PowerShell。

為支援沒有連線網際網路的使用者以及位於防火牆後方的使用者，新的 [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) Cmdlet 會將說明檔案下載到檔案系統目錄，例如檔案共用。 使用者即可使用 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Cmdlet 從檔案共用取得已更新的說明檔案。

您可以使用 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Cmdlet，針對所有支援的 UI 文化特性中的所有或特定模組，更新其說明檔案。 您甚至可以在 Windows PowerShell 設定檔中放入 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) 命令。 依照預設，Windows PowerShell 一天只會為一個模組下載說明檔案一次。

Windows 8 與 Windows Server 2012 模組並沒有包含說明檔案。 若要下載最新的說明檔案，請輸入 `Update-Help`。 如需詳細資訊，請輸入 `Get-Help` (不含參數) 或請參閱 [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe)。

當電腦上沒有安裝 Cmdlet 的說明檔案時，[Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) Cmdlet 現在會顯示自動產生的說明。 自動產生的說明包括使用 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) Cmdlet 下載說明檔案的命令語法與指示。

任何模組作者都可以為其模組的可更新的說明提供支援。 您可以在模組中包括說明檔案並使用「可更新的說明」來更新說明檔案，或在模組中省略說明檔案並使用「可更新的說明」來安裝說明檔案。 如需支援「可更新的說明」的詳細資訊，請參閱 MSDN 中的[支援可更新的說明](http://go.microsoft.com/FWLink/?LinkID=242129)。

### <a name="BKMK_Online"></a>增強的線上說明
Windows PowerShell 線上說明對所有使用者來說都是很寶貴的資源，但是對於沒有或無法安裝更新的說明檔案的使用者而言，更是特別重要。

若要針對任何 Windows PowerShell Cmdlet 取得線上說明，請輸入：

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell 會在您的預設網際網路瀏覽器中開啟說明主題的線上版本。

Windows PowerShell 3.0 中的 **Get\-Help \-Online** 功能現在更強大了，因為即使電腦上沒有安裝 Cmdlet 的說明檔案，它也可以運作。 **Get\-Help \-Online** 功能會從 Cmdlet 與進階函式的 HelpUri 屬性取得線上說明主題的 URI。

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
http://go.microsoft.com/fwlink/?LinkID=223923
```

從 Windows PowerShell 3.0 開始，C\# Cmdlet 的作者可以透過在 Cmdlet 類別上建立 **HelpUri** 屬性來填入 **HelpUri** 內容。 進階函式的作者可以在 **CmdletBinding** 屬性上定義 **HelpUri** 屬性。 **HelpUri** 屬性的值必須以 "http" 或 "https" 作為開頭。

您也可以在以 XML 為基礎之 Cmdlet 說明檔案的第一個相關連結中包含 **HelpUri** 值，或在函式中包含以註解為基礎之說明的 .Link 指示詞。

如需支援「可更新的說明」的詳細資訊，請參閱 MSDN 中的[支援線上說明](http://go.microsoft.com/fwlink/?LinkId=242132)。

### <a name="BKMK_CIM"></a>CIM 整合
Windows PowerShell 3.0 支援通用訊息模型 (CIM)，它可為系統、網路、應用程式及服務提供管理資訊的一般定義，讓它們能夠在異質系統之間交換管理資訊。 Windows PowerShell 3.0 中對 CIM 的支援，包括依據新的或現有的 CIM 類別編寫 Windows PowerShell Cmdlet 的能力、依據 Cmdlet 定義 XML 檔案編寫命令的能力，以及針對 CIM .NET Framework 的支援。 API、CIM 管理 Cmdlet 與 WMI 2.0 提供者。

### <a name="BKMK_ConfigFile"></a>工作階段設定檔案
從 Windows PowerShell 3.0 開始，您可以使用檔案來設計自訂工作階段設定。 新的工作階段設定檔案可讓您決定使用工作階段設定之工作階段的環境，包括要在工作階段中載入哪些模組、指令碼及格式檔案、使用者可以使用哪些 Cmdlet 和語言元素、使用者可以執行哪些模組和指令碼，以及使用者可以看見哪些變數。

您可以設計一個工作階段，讓使用者只能在裡面執行來自某個特定模組的 Cmdlet，或設計一個工作階段，讓使用者在裡面擁有完整語言、所有模組的完整存取權，以及可執行進階工作之指令碼的完整存取權。

在舊版的 Windows PowerShell 中，只有能夠撰寫 C\# 程式或複雜啟動指令碼的人員才能執行此層級的控制。 現在電腦上 Administrators 群組的任何成員都可以使用設定檔案來自訂工作階段設定。

若要建立工作階段設定檔案，請使用 [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866) Cmdlet。 若要將工作階段設定檔案套用到工作階段設定，請使用 [Register-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/e9152ae2-bd6d-4056-9bc7-dc1893aa29ea) 或 [Set-PSSessionConfiguration](https://technet.microsoft.com/en-us/library/b21fbad3-1759-4260-b206-dcb8431cd6ea) Cmdlet。

如需詳細資訊，請參閱 [about_Session_Configuration_Files](https://technet.microsoft.com/en-us/library/c7217447-1ebf-477b-a8ef-4dbe9a1473b8) 與 [New-PSSessionConfigurationFile](https://technet.microsoft.com/en-us/library/5f3e3633-6e90-479c-aea9-ba45a1954866)。

### <a name="BKMK_ScheduledJob"></a>排程工作與工作排程器整合
您現在可以排程 Windows PowerShell 背景工作，並在 Windows PowerShell 和工作排程器中管理它們。

Windows PowerShell 排程工作為 Windows PowerShell 背景工作及工作排程器工作的有用混合體。

排程工作就像 Windows PowerShell 背景工作一樣，會在背景中以非同步方式執行。 您可使用 Job Cmdlet 來管理已完成之排程工作的執行個體，例如 [Start-Job](https://technet.microsoft.com/en-us/library/2bc04935-0deb-4ec0-b856-d7290cca6442) 與 [Get-Job](https://technet.microsoft.com/en-us/library/1352c534-7193-46ca-9ab1-0c5219a661ad)。

就像 [工作排程器] 工作一樣，您可以在單次或週期性排程中執行排程工作，或在偵測到某個動作或事件時執行排程工作。 您可以在工作排程器中檢視及管理排程工作、視需要啟用及停用排程工作、將排程工作做為範例來執行或使用，以及設定工作啟動時所依據的條件。

此外，排程工作也隨附一組自訂的 Cmdlet 以用於管理排程工作。 這些 Cmdlet 可讓您建立、編輯、管理、停用及重新啟用排程工作、建立排程工作觸發程序，以及設定排程工作選項。

如需排程工作的詳細資訊，請參閱 [about_Scheduled_Jobs](https://technet.microsoft.com/en-us/library/3b546629-703c-4939-b44f-52dd567bce92)。

### <a name="BKMK_Lang"></a>Windows PowerShell 語言增強功能
Windows PowerShell 3.0 包括許多為了使其語言更簡單、更容易使用，以及避免發生一般錯誤所設計的功能。 這些改善項目包括屬性列舉、純量物件的計數和長度屬性、新的重新導向運算子、$Using 範圍修飾詞、PSItem 自動變數、彈性指令碼格式設定、變數屬性、簡化的屬性引數、數字命令名稱、Stop-Parsing 運算子、改善的陣列展開、全新位元運算子、排序的字典、PSCustomObject 轉換，以及改善的註解型說明。

### <a name="BKMK_Core"></a>新的核心 Cmdlet
新的 Cmdlet 已經新增至 Windows PowerShell 核心安裝，包括用來管理排程工作、已中斷連線的工作階段、CIM 整合，以及可更新的說明系統的 Cmdlet。

|||
|-|-|
|Add\-JobTrigger|New\-JobTrigger|
|Connect\-PSSession|New\-PSSessionConfigurationFile|
|ConvertFrom\-Json|New\-PSTransportOption|
|ConvertTo\-Json|New\-PSWorkflowExecutionOption|
|Disable\-JobTrigger|New\-PSWorkflowSession|
|Disable\-ScheduledJob|New\-ScheduledJobOption|
|Disconnect\-PSSession|New\-WinEvent|
|Enable\-JobTrigger|Receive\-PSSession|
|Enable\-ScheduledJob|Register\-CimIndicationEvent|
|Get\-CimAssociatedInstance|Register\-ScheduledJob|
|Get\-CimClass|Remove\-CimInstance|
|Get\-CimInstance|Remove\-CimSession|
|Get\-CimSession|Remove\-TypeData|
|Get\-ControlPanelItem|Rename\-Computer|
|Get\-IseSnippet|Resume\-Job|
|Get\-JobTrigger|Save\-Help|
|Get\-ScheduledJob|Set\-CimInstance|
|Get\-ScheduledJobOption|Set\-JobTrigger|
|Get\-TypeData|Set\-ScheduledJob|
|Import\-IseSnippet|Set\-ScheduledJobOption|
|Invoke\-AsWorkflow|Show\-Command|
|Invoke\-CimMethod|Show\-ControlPanelItem|
|Invoke\-RestMethod|Suspend\-Job|
|Invoke\-WebRequest|Test\-PSSessionConfigurationFile|
|New\-CimInstance|Unblock\-File|
|New\-CimSession|Unregister\-ScheduledJob|
|New\-CimSessionOption|Update\-Help|
|New\-IseSnippet||

### <a name="BKMK_Prov"></a>對現有核心 Cmdlet 與提供者的改善
Windows PowerShell 3.0 包含針對現有 Cmdlet 的新功能，包括簡化的語法，以及下列 Cmdlet 的新參數：Computer Cmdlet、CSV Cmdlet、Get\-ChildItem、Get\-Command、Get\-Content、Get\-History、Measure\-Object、Security Cmdlet、Select\-Object、Select\-String、Split\-Path、Start\-Process、Tee\-Object、Test\-Connection、Add\-Member 和 WMI Cmdlet。

Windows PowerShell 提供者也已經大幅改善，包括用於管理虛擬主機之安全通訊端層 (SSL) 憑證的憑證提供者支援，認證支援、持續性網路磁碟機，以及檔案系統磁碟機中的替代資料流。

### <a name="BKMK_REM"></a>遠端模組匯入及探索
Windows PowerShell 3.0 可延伸遠端電腦上的模組探索、匯入及隱含遠端執行功能。 Module Cmdlet 可使用 Windows PowerShell 遠端執行功能取得遠端電腦上的模組，並且將模組匯入到遠端或本機電腦。 新的 CIM 工作階段支援讓您可將在遠端電腦上以隱含方式執行的命令匯入本機電腦，以使用 CIM 和 WMI 來管理非 Windows 電腦。

如需詳細資訊，請參閱 [Get-Module](https://technet.microsoft.com/en-us/library/2cccd4c4-9a21-4c77-b691-984ee57242e1) 與 [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) Cmdlet 的說明主題。

### <a name="BKMK_TAB"></a>增強的 Tab 鍵自動完成
Windows PowerShell 主控台中的 Tab 鍵自動完成現在可以完成 Cmdlet、參數、參數值、列舉、.NET Frameworks 類型、COM 物件、隱藏目錄及其他項目的名稱。 TAB 鍵自動完成功能可以依據新的剖析器與抽象語法樹來重新撰寫，以支援更多案例，包括記憶體內部剖析樹狀結構和中線 Tab 鍵自動完成。

### <a name="BKMK_AutoLoad"></a>模組自動載入
[Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) Cmdlet 現在可取得電腦上安裝之全部模組的所有 Cmdlet 和函式，即使模組沒有匯入目前的工作階段中也一樣。

當您取得您需要的 Cmdlet 時，您可以立即使用，不需要匯入任何模組。 Windows PowerShell 模組現在會在您使用模組中的任何 Cmdlet 時自動匯入。 您不需要再搜尋及匯入模組，就可以使用模組的 Cmdlet。

觸發自動匯入模組的方式是，在命令中使用 Cmdlet、執行不含萬用字元之 Cmdlet 的 **Get\-Command**，或執行不含萬用字元之 Cmdlet 的 [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a)。

您可以使用 **$PSModuleAutoLoadingPreference** 喜好設定變數來啟用、停用及設定自動匯入模組。

如需詳細資訊，請參閱 [about_Modules [v4]](https://technet.microsoft.com/en-us/library/94f57429-a539-4aee-bb0d-205cd7e801f9)、[about_Preference_Variables [v4]](https://technet.microsoft.com/en-us/library/31344314-be29-4286-b039-afa5460cbe8b) 及 [Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) 與 [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) Cmdlet 的說明主題。

### <a name="BKMK_MOD"></a>模組體驗改善
Windows PowerShell 3.0 帶來了對模組的進階功能支援，包括下列新功能。

1.  個別模組的模組記錄 (LogPipelineExecutionDetails) 和新的「開啟模組記錄」群組原則設定。

2.  可公開模組資訊清單中的值的延伸模組物件

3.  模組 (包括巢狀模組) 的新 **ExportedCommands** 屬性，結合了所有類型的命令

4.  改善的可用 (未匯入) 模組探索功能，包括在同一命令中允許使用 **Path** 和 **ListAvailable** 參數。

5.  模組資訊清單中新的 **DefaultCommandPrefix** 索引鍵，可在不變更模組程式碼的情況下避免名稱衝突

6.  改善的模組需求，包括完整的必要模組 (包含版本與 GUID)，以及自動匯入必要模組。

7.  更安靜、更簡化的 [New-ModuleManifest](https://technet.microsoft.com/en-us/library/512adced-f42f-4e88-ba7c-834fc9e5d047) Cmdlet 運作。

8.  \#Requires 的新 **Module** 參數

9. 改善的 [Import-Module](https://technet.microsoft.com/en-us/library/af616c24-e122-4098-930e-1e3ea2080ade) Cmdlet (包含 **MinimumVersion** 與 **RequiredVersion** 參數)

### <a name="BKMK_SIMPLE"></a>簡化的命令探索
您不需要再匯入所有模組即可探索您的工作階段中可用的命令。 在 Windows PowerShell 3.0 中，[Get-Command](https://technet.microsoft.com/en-us/library/59c6d302-6e8c-48b7-a6f6-f0172df936ad) Cmdlet 會從所有已安裝的模組中取得所有命令。 而且，當您使用命令時，匯出命令的模組就會自動匯入到您的工作階段。

新的 [Show-Command](https://technet.microsoft.com/en-us/library/65bba50b-91a8-49d5-80a2-a30fc684ba41) Cmdlet 是特別為初學者所設計。 您可以在視窗中搜尋命令。 您可以直接在視窗中檢視所有命令或依模組篩選命令、按一下按鈕來匯入模組、使用文字方塊與下拉式清單建構有效的命令，然後複製或執行命令。

### <a name="BKMK_LOG"></a>改善的記錄、診斷與群組原則支援
Windows PowerShell 3.0 透過支援 Windows 事件追蹤 (ETW) 記錄檔、模組的可編輯 **LogPipelineExecutionDetails** 屬性，以及「開啟模組記錄」群組原則設定，改善了命令與模組的記錄與追蹤支援。 您現在可以透過顯示記錄內容，來從記錄詳細資料中取得參數值。

### <a name="BKMK_OUT"></a>格式設定與輸出改善
新的格式設定與輸出改善項目改善了所有 Windows PowerShell 使用者的效率。 改善項目包括所有資料流的輸出重新導向、在沒有 Format.ps1xml 檔案的情況下動態新增類型的已增強 Update\-Type Cmdlet、在輸出中自動換行、自訂物件的預設格式設定屬性、**PSCustomObject** 類型、改善的 WMI 物件與異質物件格式設定，以及支援探索方法多載。

### <a name="BKMK_HOST"></a>增強的主控台主機體驗
Windows PowerShell 主控台主機程式在 Windows PowerShell 3.0 中擁有新的功能，包括預設的單一執行緒 Apartment。 檔案總管中新的 [用 PowerShell 執行] 選項，讓您只要以滑鼠右鍵按一下，就可在不受限制的工作階段中執行指令碼。 新的主控台主機啟動邏輯可以更快速地啟動 Windows PowerShell，而新字型則可以讓您將熟悉的主控台視窗體驗個人化。

如需詳細資訊，請參閱 [about_Run_With_PowerShell](https://technet.microsoft.com/en-us/library/c9d9ca5f-eff9-4409-be9d-e43b5b4087eb)。

### <a name="BKMK_API"></a>新的 Cmdlet 與裝載 API
新的 Cmdlet API 與裝載 API 包括公用進階語法樹 (AST) API，以及用於管線分頁、巢狀管線、Runspace 集區 Tab 鍵自動完成、Windows RT、過時 Cmdlet 屬性，以及 FunctionInfo 物件之 Verb 與 Noun 屬性的 API。

### <a name="BKMK_PERF"></a>效能改善
Windows PowerShell 中效能大幅改善的原因是來自全新的語言剖析器 (以 .NET Framework 4 中的動態執行階段語言 (DLR) 為基礎所建立) 以及改善的執行階段指令碼編譯、引擎可靠性，而 [Get-ChildItem](https://technet.microsoft.com/en-us/library/75cf79bb-4db6-4a67-8c36-3d20754e2190) 的演算法變更改善了它的效能，特別是在搜尋網路共用時。

### <a name="BKMK_RUNAS"></a>RunAs 與共用主機支援
Windows PowerShell 3.0 支援 RunAs 與共用主機功能。

*RunAs* 功能是針對 Windows PowerShell 工作流程所設計，可讓工作階段設定的使用者建立使用共用使用者帳戶之權限執行的工作階段。 這可以讓權限較少的使用者以系統管理員權限執行特定命令與指令碼，以及減少新增較初階使用者至 Administrators 群組的需求。

**SharedHost** 功能可允許多部電腦上的多名使用者同時連線至工作流程工作階段，並監視工作流程的進度。 使用者可以在某一部電腦上啟動工作流程，然後連線至另一部電腦上的工作流程工作階段，不需要與原始電腦中的工作階段中斷連線。 使用者必須具備相同權限，並使用相同的工作階段設定。 如需詳細資訊，請參閱＜開始使用 Windows PowerShell 工作流程＞中的＜執行 Windows PowerShell 工作流程＞。

### <a name="BKMK_CHAR"></a>特殊字元處理改善
為改善 Windows PowerShell 3.0 解譯及正確處理特殊字元的能力，用來處理路徑中特殊字元的 **LiteralPath** 參數在所有擁有 **Path** 參數的 Cmdlet (包括新的 [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) 與 [Save-Help](https://technet.microsoft.com/en-us/library/aed94f90-b73f-4e25-a25d-7c18d9f161fa) Cmdlet) 上幾乎都是有效的。 剖析器也包含特殊邏輯，可改善對檔案名稱與路徑中的倒引號字元 (\`) 及方括弧的處理能力。

## 另請參閱
[about_Windows_PowerShell_4.0](http://technet.microsoft.com/en-us/library/hh847833(v=wps.630).aspx)
[about_Windows_PowerShell_5.0](https://technet.microsoft.com/en-us/library/6d56fa88-371e-40c9-b2de-64a2a0cd49da)
[Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116)




<!--HONumber=Jun16_HO4-->


