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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856624"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="5a682-102">建立 Management OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="5a682-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="5a682-103">Management ODATA IIS 擴充功能是用於建立 ASP.NET web 服務端點會公開您的管理資料，透過 Windows PowerShell cmdlet 及指令碼，做為 OData Web 服務的實體存取的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="5a682-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="5a682-104">它這麼做，處理 OData 要求，並將它們轉換成 Windows PowerShell 引動過程。</span><span class="sxs-lookup"><span data-stu-id="5a682-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="5a682-105">產品小組可以建置這個基礎結構，以建立端點公開特定的管理資料集的基礎。</span><span class="sxs-lookup"><span data-stu-id="5a682-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="5a682-106">下載並安裝[PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a)範例。</span><span class="sxs-lookup"><span data-stu-id="5a682-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="5a682-107">請依照下列指示來部署 web 服務。</span><span class="sxs-lookup"><span data-stu-id="5a682-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="5a682-108">此 web 服務公開服務和處理序，透過建立、 讀取、 更新和刪除 (CRUD) 作業。</span><span class="sxs-lookup"><span data-stu-id="5a682-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="5a682-109">對 web 服務的 CRUD 要求叫用 Windows PowerShell 命令執行所要求的作業。</span><span class="sxs-lookup"><span data-stu-id="5a682-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="5a682-110">CRUD 作業與基礎的 Windows PowerShell 命令之間的對應是由兩個結構描述檔案、.schema.mof 和 schema.xml 實作。</span><span class="sxs-lookup"><span data-stu-id="5a682-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="5a682-111">Schema.mof 檔案會使用[分散式管理任務推動小組](https://www.dmtf.org/)(小組 DMTF) 受管理物件 」 (MOF) 標準。</span><span class="sxs-lookup"><span data-stu-id="5a682-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="5a682-112">Schema.xml 檔會使用 XML 結構描述中所述[資源對應的結構描述](./resource-mapping-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="5a682-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a682-113">啟用在 Windows Server 2008 R2 SP1 Management ODATA IIS 擴充功能之前，必須啟用下列功能。</span><span class="sxs-lookup"><span data-stu-id="5a682-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="5a682-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="5a682-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="5a682-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="5a682-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="5a682-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="5a682-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="5a682-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="5a682-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="5a682-118">建立管理 OData web 服務的步驟</span><span class="sxs-lookup"><span data-stu-id="5a682-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="5a682-119">下列主題說明如何建立和部署管理 OData web 服務。</span><span class="sxs-lookup"><span data-stu-id="5a682-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="5a682-120">將資源新增至管理 OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="5a682-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-121">Management OData web 服務中實作自訂授權</span><span class="sxs-lookup"><span data-stu-id="5a682-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-122">Management OData web 服務實作 SessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5a682-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-123">撰寫 MOF 結構描述檔案管理 OData web 服務</span><span class="sxs-lookup"><span data-stu-id="5a682-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-124">撰寫管理 OData web 服務的 XML 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="5a682-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-125">撰寫管理 OData web 服務的 Web.config 檔案</span><span class="sxs-lookup"><span data-stu-id="5a682-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-126">部署 Management OData web 服務</span><span class="sxs-lookup"><span data-stu-id="5a682-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="5a682-127">建立管理 OData 實體的關聯</span><span class="sxs-lookup"><span data-stu-id="5a682-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="5a682-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a682-128">See Also</span></span>

[<span data-ttu-id="5a682-129">Management ODATA IIS 擴充功能結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="5a682-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
