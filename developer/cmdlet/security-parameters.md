---
title: 安全性參數 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251297"
---
# <a name="security-parameters"></a>安全性參數

下表列出建議的名稱和參數用來提供作業，例如，參數來指定憑證的金鑰和權限資訊的安全性資訊的功能。

|參數|功能|
|---|---|
|**ACL**<br>資料類型：String|實作這個參數來指定目錄或如統一資源識別元 (URI) 所保護的存取控制層級。|
|**CertFile**<br>資料類型：String|實作此參數，讓使用者可以指定名稱的檔案，其中包含下列其中一項：<br>-Base64 或辨別編碼規則 (DER) 編碼的 x.509 憑證<br>-A 公開金鑰密碼編譯標準 (PKCS) #12 檔案，其中包含至少一個憑證和金鑰|
|**CertIssuerName**<br>資料類型：String|實作此參數，好讓使用者可以指定憑證的簽發者的名稱，或是讓使用者可以指定子字串。|
|**CertRequestFile**<br>資料類型：String|實作此參數可指定包含 Base64 或 DER 編碼 pkcs#10 憑證要求檔案的名稱。|
|**CertSerialNumber**<br>資料類型：String|實作這個參數來指定憑證授權單位所核發的序號。|
|**CertStoreLocation**<br>資料類型：String|實作此參數，讓使用者可以指定憑證存放區的位置。 位置通常是檔案路徑。|
|**CertSubjectName**<br>資料類型：String|實作此參數，好讓使用者可以指定憑證的簽發者，或是讓使用者可以指定子字串。|
|**CertUsage**<br>資料類型：String|實作此參數，以指定的金鑰使用方式或增強金鑰使用方法。 位元遮罩，一下，物件識別碼 (OID)，或字串，則可以表示索引鍵。|
|**認證**<br>資料類型：[System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|實作此參數，cmdlet 將會自動提示使用者輸入使用者名稱或密碼。 如果沒有直接提供完整的認證，則會顯示兩個提示。|
|**CSPName**<br>資料類型：String|實作此參數，讓使用者可以指定憑證的服務提供者 (CSP) 的名稱。|
|**CSPType**<br>資料類型：整數|實作此參數，讓使用者可以指定 CSP 的型別。|
|**群組**<br>資料類型：String|實作此參數，讓使用者可以指定集合的存取權的主體。 如需詳細資訊，請參閱說明**主體**參數。|
|**KeyAlgorithm**<br>資料類型：String|實作此參數，讓使用者可以指定要用於安全性金鑰產生演算法。|
|**KeyContainerName**<br>資料類型：String|實作此參數，讓使用者可以指定金鑰容器的名稱。|
|**KeyLength**<br>資料類型：整數|實作此參數，讓使用者可以指定以位元的金鑰的長度。|
|**Operation**<br>資料類型：String|實作此參數，讓使用者可以指定可以在受保護的物件執行的動作。|
|**主體**<br>資料類型：String|實作此參數，讓使用者可以指定存取的唯一識別實體。|
|**權限**<br>資料類型：String|實作此參數，讓使用者可以指定指令程式必須對特定的實體執行作業的權限。|
|**權限**<br>資料類型：陣列的權限|實作此參數，讓使用者可以指定指令程式必須在執行特定的項目其作業的權限。|
|**Role**<br>資料類型：String|實作此參數，讓使用者可以指定一組實體可以執行的作業。|
|**SaveCred**<br>資料類型：SwitchParameter|實作此參數，指定此參數時，將會使用先前所儲存的使用者的認證。|
|**範圍**<br>資料類型：String|實作此參數，讓使用者可以指定受保護的物件，指令程式的群組。|
|**SID**<br>資料類型：String|實作此參數，讓使用者可以指定表示主體的唯一識別項。|
|**受信任**<br>資料類型：SwitchParameter|實作此參數，參數會指定時，才支援信任層級。|
|**TrustLevel**<br>資料類型：關鍵字|實作此參數，讓使用者可以指定支援的信任層級。 例如，可能值包括網際網路、 內部網路，以及完全信任。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
