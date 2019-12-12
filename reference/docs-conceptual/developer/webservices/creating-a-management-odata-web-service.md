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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359717"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="0d586-102">建立 Management OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="0d586-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="0d586-103">Management ODATA IIS 擴充功能是建立 ASP.NET web 服務端點的基礎結構，可透過 Windows PowerShell Cmdlet 和腳本（作為 OData Web 服務實體）來公開您的管理資料。</span><span class="sxs-lookup"><span data-stu-id="0d586-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="0d586-104">其方式是處理 OData 要求，並將它們轉換成 Windows PowerShell 調用。</span><span class="sxs-lookup"><span data-stu-id="0d586-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="0d586-105">產品小組可以在此基礎結構之上建立，以建立可公開特定管理資料集的端點。</span><span class="sxs-lookup"><span data-stu-id="0d586-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="0d586-106">下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例。</span><span class="sxs-lookup"><span data-stu-id="0d586-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="0d586-107">遵循指示來部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="0d586-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="0d586-108">此 web 服務會透過建立、讀取、更新和刪除（CRUD）作業來公開服務和處理常式。</span><span class="sxs-lookup"><span data-stu-id="0d586-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="0d586-109">對 web 服務提出的 CRUD 要求會叫用執行所要求作業的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="0d586-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="0d586-110">CRUD 作業和基礎 Windows PowerShell 命令之間的對應是由兩個架構檔案（架構. mof 和 .xml）所執行。</span><span class="sxs-lookup"><span data-stu-id="0d586-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="0d586-111">此架構的 mof 檔案使用[分散式管理工作推動小組](https://www.dmtf.org/)（DMTF）受管理物件（mof）標準。</span><span class="sxs-lookup"><span data-stu-id="0d586-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="0d586-112">架構 .xml 檔案會使用[資源對應架構](./resource-mapping-schema.md)中所述的 xml 架構。</span><span class="sxs-lookup"><span data-stu-id="0d586-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0d586-113">在 Windows Server 2008 R2 SP1 上啟用 Management ODATA IIS 延伸模組之前，必須先啟用下列功能。</span><span class="sxs-lookup"><span data-stu-id="0d586-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="0d586-114">IIS-Iis-webserverrole</span><span class="sxs-lookup"><span data-stu-id="0d586-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="0d586-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="0d586-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="0d586-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="0d586-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="0d586-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="0d586-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="0d586-118">建立 Management OData web 服務的步驟</span><span class="sxs-lookup"><span data-stu-id="0d586-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="0d586-119">下列主題說明如何建立及部署 Management OData web 服務。</span><span class="sxs-lookup"><span data-stu-id="0d586-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="0d586-120">將資源新增至 Management OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="0d586-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-121">執行 Management OData web 服務的自訂授權</span><span class="sxs-lookup"><span data-stu-id="0d586-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-122">執行 Management OData web 服務的 SessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="0d586-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-123">撰寫 Management OData web 服務的 MOF 架構檔案</span><span class="sxs-lookup"><span data-stu-id="0d586-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-124">撰寫 Management OData web 服務的 XML 架構檔案</span><span class="sxs-lookup"><span data-stu-id="0d586-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-125">撰寫 Management OData web 服務的 web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="0d586-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-126">部署 Management OData web 服務</span><span class="sxs-lookup"><span data-stu-id="0d586-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="0d586-127">建立管理 OData 實體的關聯</span><span class="sxs-lookup"><span data-stu-id="0d586-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="0d586-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d586-128">See Also</span></span>

[<span data-ttu-id="0d586-129">Management ODATA IIS 擴充功能架構檔案</span><span class="sxs-lookup"><span data-stu-id="0d586-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
