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
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369497"
---
# <a name="security-parameters"></a>安全性參數

下表列出用來提供作業安全性資訊之參數的建議名稱和功能，例如指定憑證金鑰和許可權資訊的參數。

|參數|功能|
|---|---|
|**ACL**<br>資料類型：字串|執行此參數來指定目錄或統一資源識別元（URI）的存取控制層級。|
|**CertFile**<br>資料類型：字串|執行此參數，讓使用者可以指定包含下列其中一項的檔案名：<br>-Base64 或可辨別編碼規則（DER）編碼的 x.509 憑證<br>-至少包含一個憑證和金鑰的公開金鑰加密標準（PKCS） #12 檔案|
|**CertIssuerName**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證的簽發者名稱，或讓使用者可以指定子字串。|
|**CertRequestFile**<br>資料類型：字串|執行此參數來指定包含 Base64 或 DER 編碼 PKCS #10 憑證要求的檔案名。|
|**CertSerialNumber**<br>資料類型：字串|執行此參數來指定憑證授權單位單位所發出的序號。|
|**CertStoreLocation**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證存放區的位置。 位置通常是檔案路徑。|
|**CertSubjectName**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證的簽發者，或讓使用者可以指定子字串。|
|**CertUsage**<br>資料類型：字串|執行此參數來指定金鑰使用方式或增強金鑰使用方法。 索引鍵可以用位元遮罩、位、物件識別碼（OID）或字串來表示。|
|**證書**<br>資料類型： [system.object](/dotnet/api/System.Management.Automation.PSCredential)|執行此參數，讓 Cmdlet 會自動提示使用者輸入使用者名稱或密碼。 如果未直接提供完整認證，則會顯示 [兩者的提示]。|
|**CSPName**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證服務提供者（CSP）的名稱。|
|**CSPType**<br>資料類型：整數|執行此參數，讓使用者可以指定 CSP 的類型。|
|**群組**<br>資料類型：字串|執行此參數，讓使用者可以指定要存取的主體集合。 如需詳細資訊，請參閱**主體**參數的描述。|
|**KeyAlgorithm**<br>資料類型：字串|執行此參數，讓使用者可以指定要用於安全性的金鑰產生演算法。|
|**Cspparameters.keycontainername**<br>資料類型：字串|執行此參數，讓使用者可以指定金鑰容器的名稱。|
|**KeyLength**<br>資料類型：整數|執行此參數，讓使用者可以指定金鑰的長度（以位為單位）。|
|**運營**<br>資料類型：字串|執行此參數，讓使用者可以指定可在受保護物件上執行的動作。|
|**委託人**<br>資料類型：字串|執行此參數，讓使用者可以指定唯一可識別的實體來進行存取。|
|**特權**<br>資料類型：字串|執行此參數，讓使用者可以指定 Cmdlet 對特定實體執行作業所需的許可權。|
|**權限**<br>資料類型：許可權陣列|執行此參數，讓使用者可以指定 Cmdlet 針對特定專案執行其作業所需的許可權。|
|**角色**<br>資料類型：字串|執行此參數，讓使用者可以指定實體可執行檔一組作業。|
|**SaveCred**<br>資料類型： SwitchParameter|執行此參數，以便在指定參數時，使用先前儲存的認證。|
|**範圍**<br>資料類型：字串|執行此參數，讓使用者可以為該 Cmdlet 指定受保護物件的群組。|
|**SID**<br>資料類型：字串|執行此參數，讓使用者可以指定代表主體的唯一識別碼。|
|**Trusted**<br>資料類型： SwitchParameter|請執行此參數，以便在指定參數時支援信任層級。|
|**TrustLevel**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定支援的信任層級。 例如，可能的值包括網際網路、內部網路和 fulltrust。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
