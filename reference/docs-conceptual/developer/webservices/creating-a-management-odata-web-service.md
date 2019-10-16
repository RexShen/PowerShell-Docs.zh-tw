---
title: 建立 Management OData Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359717"
---
# <a name="creating-a-management-odata-web-service"></a>建立 Management OData Web 服務

Management ODATA IIS 擴充功能是建立 ASP.NET web 服務端點的基礎結構，可透過 Windows PowerShell Cmdlet 和腳本（作為 OData Web 服務實體）來公開您的管理資料。 其方式是處理 OData 要求，並將它們轉換成 Windows PowerShell 調用。 產品小組可以在此基礎結構之上建立，以建立可公開特定管理資料集的端點。

下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例。 遵循指示來部署 web 服務。 此 web 服務會透過建立、讀取、更新和刪除（CRUD）作業來公開服務和處理常式。 對 web 服務提出的 CRUD 要求會叫用執行所要求作業的 Windows PowerShell 命令。 CRUD 作業和基礎 Windows PowerShell 命令之間的對應是由兩個架構檔案（架構. mof 和 .xml）所執行。 此架構的 mof 檔案使用[分散式管理工作推動小組](https://www.dmtf.org/)（DMTF）受管理物件（mof）標準。 架構 .xml 檔案會使用[資源對應架構](./resource-mapping-schema.md)中所述的 xml 架構。

> [!IMPORTANT]
> 在 Windows Server 2008 R2 SP1 上啟用 Management ODATA IIS 延伸模組之前，必須先啟用下列功能。
>
> 1.  IIS-Iis-webserverrole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>建立 Management OData web 服務的步驟

下列主題說明如何建立及部署 Management OData web 服務。

- [將資源新增至 Management OData Web 服務](./adding-resources-to-a-management-odata-web-service.md)

- [執行 Management OData web 服務的自訂授權](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [執行 Management OData web 服務的 SessionConfiguration](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [撰寫 Management OData web 服務的 MOF 架構檔案](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [撰寫 Management OData web 服務的 XML 架構檔案](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [撰寫 Management OData web 服務的 web.config 檔案](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [部署 Management OData web 服務](./deploying-a-management-odata-web-service.md)

- [建立管理 OData 實體的關聯](./associating-management-odata-entities.md)

## <a name="see-also"></a>另請參閱

[Management ODATA IIS 擴充功能架構檔案](./management-odata-iis-extension-schema-files.md)
