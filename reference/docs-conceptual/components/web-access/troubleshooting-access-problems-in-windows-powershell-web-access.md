---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: 為 Windows PowerShell Web 存取中的存取問題進行疑難排解
ms.openlocfilehash: 818beffaf7df55ae36a154b7b751f9201c5b4299
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870178"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>疑難排解 Windows PowerShell Web 存取中的存取問題

更新日期︰2013 年 6 月 24 日 (修訂日期：2017 年 8 月 23 日)

適用目標︰Windows Server 2012 R2、Windows Server 2012

下列各節識別在嘗試使用 Windows PowerShell Web 存取連線到遠端電腦時的一些常見問題，以及解決這些問題的建議。

## <a name="sign-in-failure"></a>登入失敗

下列各項為可能發生失敗的原因。

- 允許使用者存取電腦的授權規則或遠端電腦上的特定工作階段設定不存在。

  Windows PowerShell Web 存取安全性受到限制；必須使用授權規則明確授與使用者存取遠端電腦的存取權。

  如需建立授權規則的詳細資訊，請參閱 [Windows PowerShell Web 存取的授權規則與安全性功能](authorization-rules-and-security-features-of-windows-powershell-web-access.md)。

- 使用者沒有存取目的地電腦的權限。 這可由存取控制清單 (ACL) 來判斷。

  如需詳細資訊，請參閱[登入 Windows PowerShell Web 存取](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access)或 Windows PowerShell 小組部落格。

- 目的電腦可能沒有啟用 Windows PowerShell 遠端管理。

  確認已在使用者嘗試連線的電腦上啟用遠端管理。

  如需詳細資訊，請參閱 [How to Configure Your Computer for Remoting](/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (如何設定電腦的遠端功能)。

## <a name="internal-server-error"></a>內部伺服器錯誤

當使用者嘗試在 Internet Explorer 視窗登入 Windows PowerShell Web 存取時，會看到 [內部伺服器錯誤]  頁面或 *Internet Explorer* 停止回應。

這是只有 Internet Explorer 會發生的問題。

### <a name="possible-cause"></a>可能的原因

當使用者使用含有中文字元的網域名稱登入，或閘道伺服器名稱含有一或多個中文字元時，會發生這個問題。

#### <a name="workaround"></a>因應措施

1. 安裝並執行 Internet Explorer 10
1. 將 Internet Explorer [文件模式]  設定變更為 [IE10]  標準。
   1. 按 **F12** 開啟開發人員工具主控台
   1. 在 Internet Explorer 10 中，按一下 **[瀏覽器模式]** ，然後選取 *[Internet Explorer 10]* 。
   1. 按一下 [文件模式]  ，然後按一下 [IE10]  標準。
   1. 再按一次 **F12** 關閉開發人員工具主控台。
1. 停用 Internet Explorer 10 中的自動 Proxy 設定。
   1. 按一下 [工具]  ，然後按一下 [網際網路選項]  。
   1. 在 **[網際網路選項]** 對話方塊的 **[連線]** 索引標籤中，按一下 **[區域網路設定]** 。
   1. 清除 [自動偵測設定]  核取方塊。 按一下 [確定]  ，然後再按一次 [確定]  關閉 [網際網路選項]  對話方塊。

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>無法連線到遠端工作群組電腦

如果目的地電腦是工作群組的成員，請使用下列語法提供您的使用者名稱並登入電腦：`<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>即使已安裝角色，仍找不到網頁伺服器 (IIS) 管理工具

如果您使用 `Install-WindowsFeature` Cmdlet 來安裝 Windows PowerShell Web 存取，除非將 **IncludeManagementTools** 參數新增到 Cmdlet，否則不會安裝管理工具。

如需範例，請參閱[使用 Windows PowerShell Cmdlet 安裝 Windows PowerShell Web 存取](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets)。

在以閘道伺服器為目標的 [新增角色及功能精靈]  工作階段選取工具，可以新增 IIS 管理員主控台及您需要的其他 IIS 管理工具。 您可以從 [伺服器管理員] 中開啟 [新增角色及功能精靈]。

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>無法存取 Windows PowerShell Web 存取網站

如果在 Internet Explorer 啟用增強式安全性設定 (IE ESC)，您可以將 Windows PowerShell Web 存取網站新增至信任的網站清單。

較不建議的方法是停用 IE ESC，因為這會有安全性風險。 您可以在 [伺服器管理員] 中 [本機伺服器] 頁面上的 [屬性] 磚中停用 IE ESC。

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>授權失敗。 請確認您已獲授權可連線至目的電腦。

當閘道伺服器為目的地電腦且同時位於工作群組時嘗試連線，會顯示上述錯誤訊息。

當閘道伺服器也是目的地伺服器且位於工作群組時，請指定使用者名稱、電腦名稱和使用者群組名稱。 請勿單獨使用點 (.) 來代表電腦名稱。

### <a name="scenarios-and-proper-values"></a>案例和適當的值

#### <a name="all-cases"></a>所有情況

  參數   |                                        值
------------- | -----------------------------------------------------------------------------------
UserName      | `Server_name\user_name`<br/>`Localhost\user_name`<br/>`.\user_name`
UserGroup     | `Server_name\user_group`<br/>`Localhost\user_group`<br/>`.\user_group`
ComputerGroup | `Server_name\computer_group`<br/>`Localhost\computer_group`<br/>`.\computer_group`

#### <a name="gateway-server-is-in-a-domain"></a>閘道伺服器位於網域

 參數   |                        值
------------ | ----------------------------------------------------
ComputerName | 閘道伺服器的完整名稱，或 Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>閘道伺服器位於工作群組

 參數   |    值
------------ | -----------
ComputerName | 伺服器名稱

### <a name="gateway-credentials"></a>閘道認證

使用下列其中一種格式的認證以目標電腦身分登入閘道伺服器。

- `Server_name\user_name`
- `Localhost\user_name`
- `.\user_name`

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>授權規則顯示安全性識別碼 (SID)

授權規則中會顯示安全性識別碼 (SID)，而非語法 `user_name/computer_name`。

可能是規則不再有效，或者 Active Directory 網域服務查詢失敗。 如果閘道伺服器曾經位於工作群組，但之後加入網域，則授權規則通常無效

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>因為 IPv6 位址包含一個網域，所以無法使用規則登入

在授權規則中將目標電腦指定為含網域的 IPv6 位址時，無法登入該目標電腦。

授權規則不支援網域名稱格式的 IPv6 位址。

若要使用 IPv6 位址指定目的電腦，請在授權規則使用原始 IPv6 位址 (包含冒號)。 在 [Windows PowerShell Web 存取] 登入頁面中，支援以網域及數字 (含冒號) IPv6 位址做為目標電腦名稱，但在授權規則中則不行。

如需 IPv6 位址的詳細資訊，請參閱 [How IPv6 Works](/previous-versions/windows/it-pro/windows-server-2003/cc781672(v=ws.10)) (IPv6 的運作方式)。

## <a name="see-also"></a>另請參閱

- [Windows PowerShell Web 存取的授權規則與安全性功能](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn282394(v=ws.11))
- [使用網頁型 Windows PowerShell 主控台](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11))
- [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)
