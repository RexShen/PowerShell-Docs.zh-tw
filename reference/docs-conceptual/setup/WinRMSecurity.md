---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: WinRMSecurity
ms.openlocfilehash: 0522844fded847a3fd45c1b3890a141357edb2b2
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="powershell-remoting-security-considerations"></a>PowerShell 遠端安全性考量

建議採用 PowerShell 遠端來管理 Windows 系統。 Windows Server 2012 R2 中預設已啟用 PowerShell 遠端。 本文件涵蓋使用 PowerShell 遠端時的安全性考量、建議與最佳做法。

## <a name="what-is-powershell-remoting"></a>什麼是 PowerShell 遠端？

PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx)，這是[管理的 Web 服務 (WS 管理)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 通訊協定的 Microsoft 實作，可讓使用者在遠端電腦上執行 PowerShell 命令。 您可以在[執行遠端命令](https://technet.microsoft.com/library/dd819505.aspx)處找到有關使用 PowerShell 遠端的詳細資訊。

PowerShell 遠端和使用 Cmdlet 的 **ComputerName** 參數在遠端電腦上執行不同，其使用遠端程序呼叫 (RPC) 作為其基礎通訊協定。

## <a name="powershell-remoting-default-settings"></a>PowerShell 遠端的預設設定

PowerShell 遠端 (和 WinRM) 會接聽以下連接埠︰

- HTTP：5985
- HTTPS： 5986

PowerShell 遠端預設僅允許連線系統管理員群組的成員。 工作階段會在使用者的內容下啟動，因此透過 PowerShell 遠端連線時，所有套用至個別使用者和群組的作業系統存取控制，都會繼續套用。

在私人網路中，PowerShell 遠端的預設 Windows 防火牆規則，可以接受所有的連線。 在公用網路中，預設的 Windows 防火牆規則只允許來自相同子網路的 PowerShell 遠端連線。 您必須明確地變更該規則，才可開啟 PowerShell 遠端對公用網路上的所有連線。

>**警告︰**公用網路的防火牆規則主要是為了保護電腦免受嘗試進行惡意的外部連線的動作。 移除此規則時，請務必小心。

## <a name="process-isolation"></a>處理程序隔離

PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) 進行電腦之間的通訊。 WinRM 以網路服務帳戶的服務方式執行，並會繁衍隔離的處理程序作為使用者帳戶，以主控 PowerShell 執行個體。 PowerShell 的執行個體以一位使用者的身分執行時，無法存取執行為另一位使用者的 PowerShell 執行個體。

## <a name="event-logs-generated-by-powershell-remoting"></a>PowerShell 遠端所產生的事件記錄檔

FireEye 提供了一份良好的摘要，其中內含 PowerShell 遠端工作階段所產生之事件記錄檔與其他安全性辨識項，而且可以從  
[調查 PowerShell 攻擊](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)取得。

## <a name="encryption-and-transport-protocols"></a>加密及傳輸通訊協定

最好先從兩個層面考量 PowerShell 遠端連線的安全性：初始驗證，以及進行中的通訊。 

不論所使用的傳輸通訊協定 (HTTP 或 HTTPS) 為何，PowerShell 遠端一律會在初始驗證之後，以每個工作階段 AES-256 對稱金鑰為單位，來加密所有通訊。
    
### <a name="initial-authentication"></a>初始驗證

驗證會確認用戶端至伺服器的身分識別，在理想的情況下，也會確認伺服器到用戶端的身分識別。
    
當用戶端使用其電腦名稱 (例如︰server01 或 server01.contoso.com) 連線到網域伺服器時，預設的驗證通訊協定是 [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx)。
Kerberos 可保證使用者識別與伺服器識別，而不會傳送任何種類可重複使用的認證。

當用戶端使用其 IP 位址連線到網域伺服器時，或連線到工作群組伺服器時，便無法進行 Kerberos 驗證。 在此情況下，PowerShell 遠端會仰賴 [NTLM 驗證通訊協定](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx)。 NTLM 驗證通訊協定可保證使用者識別，且不會傳送任何種類可委派的認證。 為了要證明使用者識別，NTLM 通訊協定需要用戶端與伺服器從使用者的密碼來計算工作階段金鑰，而不會交換密碼本身。 伺服器通常不知道使用者的密碼，因此會和知道使用者密碼的網域控制站互相通訊，並為伺服器計算出工作階段金鑰。 
      
但 NTLM 通訊協定並不能保證伺服器識別。 因為所有通訊協定都使用 NTLM 進行驗證，所以可以存取已加入網域之電腦的電腦帳戶之攻擊者，就能叫用網域控制站計算出 NTLM 工作階段金鑰，然後模擬該伺服器。

預設會停用 NTLM 的驗證，但在目標伺服器上設定 SSL 或在用戶端設定 WinRM TrustedHosts 設定時，可能會允許。
    
#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>NTLM 連線期間使用 SSL 憑證來驗證伺服器識別

由於 NTLM 驗證通訊協定無法確保目標伺服器 (只有它已經知道您的密碼) 的身分識別，所以您可以將目標伺服器設定為使用 SSL 進行 PowerShell 遠端。 將 SSL 憑證指派至目標伺服器 (如果由用戶端也信任的憑證授權中心發出)，可讓 NTLM 驗證能保證使用者識別與伺服器識別。
    
#### <a name="ignoring-ntlm-based-server-identity-errors"></a>忽略 NTLM 伺服器識別錯誤
      
如果將 SSL 憑證部署至伺服器進行 NTLM 連線並不可行，可以隱藏所產生的身分識別錯誤，方法是將該伺服器新增至 WinRM **TrustedHosts** 清單。 請注意，將伺服器名稱新增到 TrustedHosts 清單的動作，不應視為任何形式對主機本身信賴的保證，因為 NTLM 驗證通訊協定無法保證實際上連線到的主機是想要連線的主機。
相反地，應考慮讓 TrustedHosts 設定成為想要隱藏錯誤 (因無法驗證伺服器身分識別而產生之錯誤) 的主機清單。
    
    
### <a name="ongoing-communication"></a>進行中的通訊

完成初始驗證之後，[PowerShell 遠端通訊協定](https://msdn.microsoft.com/en-us/library/dd357801.aspx) 會使用每個工作階段的 AES-256 對稱金鑰，加密所有進行中的通訊。  


## <a name="making-the-second-hop"></a>進行第二次跳躍

PowerShell 遠端預設會使用 (如果提供) Kerberos 或 NTLM 驗證。 這兩種通訊協定驗證遠端電腦時，皆不需要將認證傳送到電腦。
這是最安全的驗證方式，但因為遠端電腦並沒有使用者的認證，所以無法代替使用者存取其他電腦與服務。 這稱為「第二個躍點問題」。

避免這個問題的方法有數種。 如需這些方法的描述，以及每一項的優缺點，請參閱[Making the second hop in PowerShell Remoting](PS-remoting-second-hop.md) (在 PowerShell 遠端中進行第二次跳躍)。










