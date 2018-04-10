---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,安全性
title: Just Enough Administration 概觀
ms.openlocfilehash: fd5b97b7a483908f10cec6460d4e803740f064a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) 是安全性技術，允許將可透過 PowerShell 管理的任何項目委派管理。
使用 JEA，您可以︰

- 利用虛擬帳戶或群組受管理服務帳戶，代表一般使用者執行特殊權限動作，以「減少電腦上的系統管理員數目」。
- 指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。
- 透過文字記錄和記錄檔，顯示使用者在工作階段期間執行的確切命令，以**深入了解使用者正在執行的工作**。

**為何重要？**

用來管理伺服器且具有高度權限的帳戶會造成嚴重的安全性風險。
萬一攻擊者入侵其中一個帳戶，他們便可以對整個組織啟動[橫向攻擊](http://aka.ms/pth)。
他們入侵的每個帳戶都能讓他們存取更多帳戶和資源，讓他們更進一步竊取公司機密、啟動阻絕服務攻擊等等。

移除系統管理員的權限並不一定容易。
請考慮常見的案例：DNS 角色安裝在與 Active Directory 網域控制站相同的電腦上。
您的 DNS 系統管理員必須具有本機系統管理員權限，才能修正 DNS 伺服器的問題，但若要這樣做，您必須將其設為具有高度權限之 "Domain Admins" 安全性群組的成員。
這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。

JEA 有助於解決這個問題，因為它可以協助您採用*最低權限*的原則。
有了 JEA，您就可以設定 DNS 系統管理員的管理端點，並讓他們只存取完成其工作所需的所有 PowerShell 命令。
這表示您可以提供適當的存取權以修復受害的 DNS 快取或重新啟動 DNS 伺服器，卻不會無意中給予他們使用 Active Directory、瀏覽檔案或執行有潛在危險指令碼的權限。
更棒的是，當 JEA 工作階段設定為使用暫時性特殊權限虛擬帳戶時，您的 DNS 系統管理員就可以在使用「非系統管理員」認證連接到伺服器的情況下，仍然能夠執行通常需要系統管理權限的命令。
這項功能可讓您從廣泛權限的本機/網域系統管理員角色移除使用者，並改為小心控制他們能夠在每部電腦上執行的事項。

## <a name="get-started-with-jea"></a>開始使用 JEA

您可以在執行 Windows Server 2016 或 Windows 10 的任何電腦上立即開始使用 JEA。
您也可以在具有 Windows Management Framework 更新的舊版作業系統上執行 JEA。
若要深入了解使用 JEA 的需求，並了解如何建立、使用和稽核 JEA 端點，請參閱下列主題︰

- [必要條件](prerequisites.md) - 說明如何設定環境以使用 JEA。
- [角色功能](role-capabilities.md) - 說明如何建立角色，來判斷使用者允許在 JEA 工作階段中執行的動作。
- [工作階段設定](session-configurations.md) - 說明如何設定 JEA 端點，將使用者對應至角色，並且設定 JEA 識別
- [註冊 JEA](register-jea.md) - 建立 JEA 端點，並使其可供使用者連接。
- [使用 JEA](using-jea.md) - 了解您可以使用 JEA 的各種方式。
- [安全性考量](security-considerations.md) - 檢閱安全性最佳做法和 JEA 設定選項的影響。
- [JEA 上的稽核和報告](audit-and-report.md) - 了解如何在 JEA 端點進行稽核和報告。

## <a name="samples-and-dsc-resource"></a>範例和 DSC 資源

您可以在 [JEA GitHub 存放庫 (英文)](https://github.com/PowerShell/JEA) 中找到範例 JEA 設定和 JEA DSC 資源。