---
ms.date: 09/13/2016
ms.topic: reference
title: 安全性參數
description: 安全性參數
ms.openlocfilehash: 2c73a3372fa719ea436d4a3ae1223d4cbaaf9108
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92650243"
---
# <a name="security-parameters"></a>安全性參數

下表列出用來提供作業安全性資訊的參數的建議名稱和功能，例如指定憑證金鑰和許可權資訊的參數。

|參數|功能|
|---|---|
|**Acl**<br>資料類型：字串|執行此參數來指定目錄的存取控制層級，或 (URI) 的統一資源識別項。|
|**CertFile**<br>資料類型：字串|執行此參數，讓使用者可以指定包含下列其中一個檔案的檔案名：<br>-Base64 或可辨別編碼規則 (DER) 編碼的 x.509 憑證<br>-公開金鑰加密標準 (PKCS) #12 檔案，其中至少包含一個憑證和金鑰|
|**CertIssuerName**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證的簽發者名稱，或讓使用者可以指定子字串。|
|**CertRequestFile**<br>資料類型：字串|執行此參數來指定檔案的名稱，該檔案包含 Base64 或 DER 編碼的 PKCS #10 憑證要求。|
|**CertSerialNumber**<br>資料類型：字串|執行此參數來指定憑證授權單位單位所發出的序號。|
|**CertStoreLocation**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證存放區的位置。 位置通常是檔案路徑。|
|**CertSubjectName**<br>資料類型：字串|執行此參數，讓使用者可以指定憑證的簽發者，或讓使用者可以指定子字串。|
|**CertUsage**<br>資料類型：字串|請執行此參數來指定金鑰使用方式或增強金鑰使用方式。 金鑰可以表示為位元遮罩、位、物件識別碼 (OID) 或字串。|
|**認證**<br>資料類型： [系統管理. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|您可以執行此參數，讓 Cmdlet 自動提示使用者輸入使用者名稱或密碼。 如果未直接提供完整認證，則會顯示這兩者的提示。|
|**CSPName**<br>資料類型：字串|執行此參數，讓使用者可以指定 (CSP) 的憑證服務提供者名稱。|
|**CSPType**<br>資料類型：整數|執行此參數，讓使用者可以指定 CSP 的類型。|
|**群組**<br>資料類型：字串|執行此參數，讓使用者可以指定要存取的主體集合。 如需詳細資訊，請參閱 **主體** 參數的描述。|
|**KeyAlgorithm**<br>資料類型：字串|執行此參數，讓使用者可以指定要用於安全性的金鑰產生演算法。|
|**KeyContainerName**<br>資料類型：字串|執行此參數，讓使用者可以指定金鑰容器的名稱。|
|**KeyLength**<br>資料類型：整數|執行此參數，讓使用者可以指定金鑰的長度（以位為單位）。|
|**運算**<br>資料類型：字串|執行此參數，讓使用者可以指定可在受保護物件上執行的動作。|
|**主體**<br>資料類型：字串|執行此參數，讓使用者可以指定唯一的可存取實體來進行存取。|
|**特權**<br>資料類型：字串|執行此參數，讓使用者可以指定 Cmdlet 對特定實體執行作業所需的許可權。|
|**特權**<br>資料類型：許可權的陣列|執行此參數，讓使用者可以指定 Cmdlet 針對特定專案執行其作業所需的許可權。|
|**角色**<br>資料類型：字串|執行此參數，讓使用者可以指定實體可執行檔一組作業。|
|**SaveCred**<br>資料類型： SwitchParameter|執行此參數，讓使用者先前儲存的認證會在指定參數時使用。|
|**範圍**<br>資料類型：字串|執行此參數，讓使用者可以為 Cmdlet 指定受保護物件的群組。|
|**SID**<br>資料類型：字串|執行此參數，讓使用者可以指定代表主體的唯一識別碼。|
|**信任**<br>資料類型： SwitchParameter|請執行此參數，以在指定參數時支援信任層級。|
|**TrustLevel**<br>資料類型：關鍵字|執行此參數，讓使用者可以指定受支援的信任層級。 例如，可能的值包括網際網路、內部網路和 fulltrust。|

## <a name="see-also"></a>另請參閱

[Cmdlet 參數](./cmdlet-parameters.md)

[撰寫 Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
