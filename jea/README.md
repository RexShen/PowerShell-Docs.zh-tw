# Just Enough Administration
Just Enough Administration (JEA) 是安全性技術，允許將可透過 PowerShell 管理的任何項目委派管理。
使用 JEA，您可以︰
- 利用虛擬帳戶，代表一般使用者執行特殊權限動作，以**減少電腦上的系統管理員數目**。
- 指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。
- 透過 "Over The Shoulder" 文字記錄，顯示使用者在工作階段期間實際執行的命令，以**深入了解使用者正在執行的工作**。

為何重要？
假設在一般情況下，您的 DNS 伺服器會與 Active Directory 網域控制站共置。
您的 DNS 系統管理員必須具有本機系統管理員權限，才能修正 DNS 伺服器的問題，但若要這樣做，您必須將其設為具有高度權限之 "Domain Admins" 安全性群組的成員。
這能有效地讓他們控制您的整個網域，並存取該電腦上的所有資源。

有了 JEA，您就可以設定 DNS 系統管理員的角色，並讓他們只存取完成其工作所需的所有命令。
這表示他們可以輕鬆地修復遭破壞的 DNS 快取而不需要具有 Active Directory 的權限、瀏覽檔案系統，或執行有潛在危險的指令碼。
更棒的是，當 JEA 工作階段設定為使用一次性特殊權限虛擬帳戶時，您的 DNS 系統管理員就可以在使用「非特殊權限」認證連線到伺服器的情況下，仍然能夠執行特殊權限命令。

## 開始使用

### 安裝
JEA 是與即將發行的 Windows Server 2016 版一起開發的功能，舊版 Windows 可透過 Windows Management Framework 更新來使用這項功能。
目前的 JEA 版本適用於下列平台︰

**Windows Server**
- Windows Server 2016 Technical Preview 4 及更新版本
- 安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows Server 2012 R2、2012 和 2008 R2\*

**Windows 用戶端**
- 安裝的 11 月更新 (1511) 的 Windows 10
- 安裝 [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) 的 Windows 8.1、8 和 7\*

\* Windows Server 2008 R2 或 Windows 7 目前不提供 JEA 工作階段中的虛擬帳戶支援。


### 核心概念
**JEA 到底是什麼？**

JEA 是 PowerShell [限制端點](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx)的延伸模組，其新增了角色定義、虛擬帳戶及其他幾項增強功能，讓您更輕鬆地鎖定管理端點。
JEA 端點是由 PowerShell 工作階段設定檔以及一或多個角色功能檔案所組成。

**什麼是工作階段設定檔和角色功能檔案？**

PowerShell 工作階段設定檔 (.pssc) 定義*誰*可以連線到 PowerShell 端點，以及*如何*進行設定。
您可以在此將使用者和安全性群組對應到特定管理角色，並設定虛擬帳戶和文字記錄原則等全域設定。
工作階段設定檔是每部電腦專屬的檔案，可讓您視需要控制每部電腦的存取權。

PowerShell 角色功能檔案 (.psrc) 定義屬於某個角色的使用者能夠在系統上執行*什麼*工作。
您可以在此限制使用者可在其 JEA 工作階段中使用的 Cmdlet、函式、提供者和外部程式。
角色功能檔案通常沒有特定的服務角色 (DNS 管理、初級技術支援、唯讀清查稽核等)，並屬於 PowerShell 模組，因此可讓您輕鬆地在環境中與其他人共用。

**JEA 如何利用虛擬帳戶？**

在 PowerShell 工作階段設定檔中，您可以將 JEA 工作階段設定為使用虛擬「執行身分」帳戶。
虛擬帳戶是專為特定工作階段中的特定連線使用者所設計的一次性特殊權限帳戶，使用者的命令會在該內容中執行。
虛擬帳戶預設屬於本機 "Administrators" 安全性群組，但可以選擇性地設定為只屬於您指定的安全性群組。

### 探索體驗指南
準備好建立您的第一個 JEA 端點嗎？
請參閱 [JEA Experience Guide](jea-uide.md) (JEA 體驗指南)，了解如何撰寫、部署及使用您專屬的 JEA 端點。
該指南可讓您快速地開始使用預先建置的 JEA 端點，以了解使用者體驗，然後逐步引導您從頭開始重新建立端點，以協助說明工作階段設定和角色功能。

### 開始撰寫您自己的 JEA 端點
撰寫 JEA 端點很容易，您只需要啟用 JEA 的系統和文字編輯器 (例如 PowerShell ISE)。
一個實用的入門秘訣是使用 `New-PSRoleCapabilityFile -Path <path>` 和 `New-PSSessionCapabilityFile -Path <Path>`但不提供任何其他引數來建立基本架構檔案。
這些基本架構檔案包含所有適用的設定欄位，以及說明每個欄位可能用途的實用註解。

若要更輕鬆地撰寫 JEA 端點，請參閱 [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx)，其提供可用來撰寫工作階段設定檔和角色功能檔案的 GUI。
甚至支援根據 PowerShell 記錄檔產生角色功能，讓您一開始就有使用者為完成工作所經常執行的命令。


<!--HONumber=Jun16_HO3-->


