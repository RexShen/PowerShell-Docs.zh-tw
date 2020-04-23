---
ms.date: 07/10/2019
keywords: jea,powershell,安全性
title: Just Enough Administration 概觀
ms.openlocfilehash: 4b74e5be9558810748a8844a325c8213e1b3ebc9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "70017699"
---
# <a name="just-enough-administration"></a>Just Enough Administration

Just Enough Administration (JEA) 是安全性技術，允許委派管理 PowerShell 管理的任何項目。 使用 JEA，您可以︰

- 使用虛擬帳戶或群組受控服務帳戶來代表一般使用者執行特殊權限動作，以**減少電腦上的系統管理員數目**。
- 指定使用者可以執行的 Cmdlet、函式和外部命令，以**限制使用者可以執行的工作**。
- 透過文字記錄和記錄檔，顯示使用者在工作階段期間執行的確切命令，以**深入了解使用者正在執行的工作**。

**JEA 為何如此重要？**

用來管理伺服器且具有高度權限的帳戶會造成嚴重的安全性風險。 萬一攻擊者入侵其中一個帳戶，他們便可以對整個組織啟動[橫向攻擊](https://aka.ms/pth)。 每個遭入侵的帳戶都能讓攻擊者存取更多帳戶和資源，讓他們進一步竊取公司祕密、啟動拒絕服務的攻擊等。

移除系統管理員權限從來不是一件容易的事。 請考慮常見的案例：DNS 角色安裝在與 Active Directory 網域控制站相同的電腦上。 您的 DNS 系統管理員需要本機系統管理員權限，才能修正 DNS 伺服器的問題。 但若要這樣做，您必須讓他們成為具高度權限的 **Domain Admins** 安全性群組成員。 這個方法能有效地讓 DNS 系統管理員控制您的整個網域，並存取該電腦上的所有資源。

JEA 透過**最低權限**原則解決此問題。 有了 JEA，您就可以設定 DNS 系統管理員的管理端點，並讓他們只存取完成其工作所需的 PowerShell 命令。 這表示您可以提供適當的存取權以修復受害的 DNS 快取或重新啟動 DNS 伺服器，卻不會無意中給予他們使用 Active Directory、瀏覽檔案或執行有潛在危險指令碼的權限。 更棒的是，當 JEA 工作階段設定為使用暫時性特殊權限虛擬帳戶時，您的 DNS 系統管理員仍可以在使用**非管理員**認證連線到伺服器的情況下，執行通常需要系統管理權限的命令。 這項功能可讓您從廣泛權限的本機/網域系統管理員角色移除使用者，且小心控制他們能夠在每部電腦上執行的事項。

## <a name="next-steps"></a>後續步驟

若要深入了解使用 JEA 的需求，請參閱[必要條件](prerequisites.md)一文。

## <a name="samples-and-dsc-resource"></a>範例和 DSC 資源

您可以在 [JEA GitHub 存放庫 (英文)](https://github.com/PowerShell/JEA) 中找到範例 JEA 設定和 JEA DSC 資源。
