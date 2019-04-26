---
title: 建立管理 OData Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080691"
---
# <a name="creating-a-management-odata-web-service"></a>建立 Management OData Web 服務

Management ODATA IIS 擴充功能是用於建立 ASP.NET web 服務端點會公開您的管理資料，透過 Windows PowerShell cmdlet 及指令碼，做為 OData Web 服務的實體存取的基礎結構。 它這麼做，處理 OData 要求，並將它們轉換成 Windows PowerShell 引動過程。 產品小組可以建置這個基礎結構，以建立端點公開特定的管理資料集的基礎。

下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例。 請依照下列指示來部署 web 服務。 此 web 服務公開服務和處理序，透過建立、 讀取、 更新和刪除 (CRUD) 作業。 對 web 服務的 CRUD 要求叫用 Windows PowerShell 命令執行所要求的作業。 CRUD 作業與基礎的 Windows PowerShell 命令之間的對應是由兩個結構描述檔案、.schema.mof 和 schema.xml 實作。 Schema.mof 檔案會使用[分散式管理任務推動小組](https://www.dmtf.org/)(小組 DMTF) 受管理物件 」 (MOF) 標準。 Schema.xml 檔會使用 XML 結構描述中所述[資源對應的結構描述](./resource-mapping-schema.md)。

> [!IMPORTANT]
> 啟用在 Windows Server 2008 R2 SP1 Management ODATA IIS 擴充功能之前，必須啟用下列功能。
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>建立管理 OData web 服務的步驟

下列主題說明如何建立和部署管理 OData web 服務。

- [將資源新增至管理 OData Web 服務](./adding-resources-to-a-management-odata-web-service.md)

- [Management OData web 服務中實作自訂授權](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Management OData web 服務實作 SessionConfiguration](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [撰寫 MOF 結構描述檔案管理 OData web 服務](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [撰寫管理 OData web 服務的 XML 結構描述檔案](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [撰寫管理 OData web 服務的 Web.config 檔案](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [部署 Management OData web 服務](./deploying-a-management-odata-web-service.md)

- [建立管理 OData 實體的關聯](./associating-management-odata-entities.md)

## <a name="see-also"></a>另請參閱

[Management ODATA IIS 擴充功能結構描述檔案](./management-odata-iis-extension-schema-files.md)
