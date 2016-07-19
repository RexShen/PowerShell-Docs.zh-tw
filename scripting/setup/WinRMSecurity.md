---
title: WinRMSecurity
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 67ef350559f9b3d17232f3c93d67634b3e939c60
ms.openlocfilehash: b1addddd50368fadcbb2581673d3ebc7cad8e32a

---

# PowerShell 遠端安全性考量

建議採用 PowerShell 遠端來管理 Windows 系統。 Windows Server 2012 R2 中預設已啟用 PowerShell 遠端。 本文件涵蓋使用 PowerShell 遠端時的安全性考量、建議與最佳做法。

## 什麼是 PowerShell 遠端？

PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx)，這是[管理的 Web 服務 (WS 管理)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf) 通訊協定的 Microsoft 實作，可讓使用者在遠端電腦上執行 PowerShell 命令。 您可以在[執行遠端命令](https://technet.microsoft.com/en-us/library/dd819505.aspx)處找到有關使用 PowerShell 遠端的詳細資訊。

PowerShell 遠端和使用 Cmdlet 的 **ComputerName** 參數在遠端電腦上執行不同，其使用遠端程序呼叫 (RPC) 作為其基礎通訊協定。

##  PowerShell 遠端的預設設定

PowerShell 遠端 (和 WinRM) 會接聽以下連接埠︰

- HTTP：5985
- HTTPS： 5986

PowerShell 遠端預設僅允許連線系統管理員群組的成員。 工作階段會在使用者的內容下啟動，因此透過 PowerShell 遠端連線時，所有套用至個別使用者和群組的作業系統存取控制，都會繼續套用。

在私人網路中，PowerShell 遠端的預設 Windows 防火牆規則，可以接受所有的連線。 在公用網路中，預設的 Windows 防火牆規則只允許來自相同子網路的 PowerShell 遠端連線。 您必須明確地變更該規則，才可開啟 PowerShell 遠端對公用網路上的所有連線。

>**警告︰**公用網路的防火牆規則主要是為了保護電腦免受嘗試進行惡意的外部連線的動作。 移除此規則時，請務必小心。

## 處理程序隔離

PowerShell 遠端使用 [Windows 遠端管理 (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) 進行電腦之間的通訊。 WinRM 以網路服務帳戶的服務方式執行，並會繁衍隔離的處理程序作為使用者帳戶，以主控 PowerShell 執行個體。 PowerShell 的執行個體以一位使用者的身分執行時，無法存取執行為另一位使用者的 PowerShell 執行個體。

## PowerShell 遠端所產生的事件記錄檔

FireEye 提供了一份良好的摘要，其中內含 PowerShell 遠端工作階段所產生之事件記錄檔與其他安全性辨識項，而且可以從  
[調查 PowerShell 攻擊](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf)取得。

## 加密及傳輸通訊協定

最好先從兩個層面考量 PowerShell 遠端連線的安全性：初始驗證，以及進行中的通訊。 

不論所使用的傳輸通訊協定 (HTTP 或 HTTPS) 為何，PowerShell 遠端一律會在初始驗證之後，以每個工作階段 AES-256 對稱金鑰為單位，來加密所有通訊。
    
### 初始驗證

驗證會確認用戶端至伺服器的身分識別，在理想的情況下，也會確認伺服器到用戶端的身分識別。
    
當用戶端使用其電腦名稱 (例如︰server01 或 server01.contoso.com) 連線到網域伺服器時，預設的驗證通訊協定是 [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx)。
Kerberos 可保證使用者識別與伺服器識別，而不會傳送任何種類可重複使用的認證。

當用戶端使用其 IP 位址連線到網域伺服器時，或連線到工作群組伺服器時，便無法進行 Kerberos 驗證。 在此情況下，PowerShell 遠端會仰賴 [NTLM 驗證通訊協定](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx)。 NTLM 驗證通訊協定可保證使用者識別，且不會傳送任何種類可委派的認證。 為了要證明使用者識別，NTLM 通訊協定需要用戶端與伺服器從使用者的密碼來計算工作階段金鑰，而不會交換密碼本身。 伺服器通常不知道使用者的密碼，因此會和知道使用者密碼的網域控制站互相通訊，並為伺服器計算出工作階段金鑰。 
      
但 NTLM 通訊協定並不能保證伺服器識別。 因為所有通訊協定都使用 NTLM 進行驗證，所以可以存取已加入網域之電腦的電腦帳戶之攻擊者，就能叫用網域控制站計算出 NTLM 工作階段金鑰，然後模擬該伺服器。

預設會停用 NTLM 的驗證，但在目標伺服器上設定 SSL 或在用戶端設定 WinRM TrustedHosts 設定時，可能會允許。
    
#### NTLM 連線期間使用 SSL 憑證來驗證伺服器識別

由於 NTLM 驗證通訊協定無法確保目標伺服器 (只有它已經知道您的密碼) 的身分識別，所以您可以將目標伺服器設定為使用 SSL 進行 PowerShell 遠端。 將 SSL 憑證指派至目標伺服器 (如果由用戶端也信任的憑證授權中心發出)，可讓 NTLM 驗證能保證使用者識別與伺服器識別。
    
#### 忽略 NTLM 伺服器識別錯誤
      
如果將 SSL 憑證部署至伺服器進行 NTLM 連線並不可行，可以隱藏所產生的身分識別錯誤，方法是將該伺服器新增至 WinRM **TrustedHosts** 清單。 請注意，將伺服器名稱新增到 TrustedHosts 清單的動作，不應視為任何形式對主機本身信賴的保證，因為 NTLM 驗證通訊協定無法保證實際上連線到的主機是想要連線的主機。
相反地，應考慮讓 TrustedHosts 設定成為想要隱藏錯誤 (因無法驗證伺服器身分識別而產生之錯誤) 的主機清單。
    
    
### 進行中的通訊

完成初始驗證之後，[PowerShell 遠端通訊協定](https://msdn.microsoft.com/en-us/library/dd357801.aspx) 會使用每個工作階段的 AES-256 對稱金鑰，加密所有進行中的通訊。  


## 進行第二次跳躍

PowerShell 遠端預設會使用 (如果提供) Kerberos 或 NTLM 驗證。 這兩種通訊協定驗證遠端電腦時，皆不需要將認證傳送到電腦。
這是最安全的驗證方式，但因為遠端電腦並沒有使用者的認證，所以無法代替使用者存取其他電腦與服務。 這稱為「雙躍點 」問題。

避免這個問題的方法有數種︰

### Kerberos 限制委派

若是高度受信任的伺服器，可以啟用 [Kerberos 限制委派](https://technet.microsoft.com/en-us/library/cc995228.aspx)。 遠端伺服器如此即可對指定的電腦與服務清單，模擬已經過驗證的使用者。

### 遠端電腦之間的信任

如果信任使用者從遠端連線到 *Server1*，取用 *Server2* 的資源，可以明確授與 *Server1* 存取這些資源。

### 存取遠端資源時使用明確認證

您可以使用 Cmdlet 的 **Credential** 參數，明確地將認證傳遞至遠端資源。 例如：

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

您可以使用[認證安全性支援提供者 (CredSSP)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) 進行驗證 (藉由將 "CredSSP"指定為呼叫 [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx) Cmdlet 的 `Authentication` 參數值。 CredSSP 會以純文字將認證傳遞至伺服器，因此加以使用時，可能會讓您暴露在認證遭竊的攻擊風險中。 如果遠端電腦遭到入侵，攻擊者就能存取使用者的認證。 預設會停用 CredSSP (用戶端與伺服器電腦皆是)。 只有在最受信任的環境中才應啟用 CredSSP。 例如，因為網域控制站為高度受信任，所以網域系統管理員會連線到網域控制站。

如需使用 PowerShell 遠端的 CredSSP 時，安全性考量的詳細資訊，請參閱 [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (意外妨害：注意 CredSSP)。

如需認證遭竊攻擊的詳細資訊，請參閱[降低傳遞雜湊 (PtH) 攻擊與竊取其他認證](https://www.microsoft.com/en-us/download/details.aspx?id=36036)。











<!--HONumber=Jul16_HO1-->


