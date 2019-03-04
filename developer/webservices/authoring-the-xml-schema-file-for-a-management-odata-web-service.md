---
title: 撰寫 XML 結構描述檔案管理 OData web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857974"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="d57ec-102">撰寫 Management OData Web 服務的 XML 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="d57ec-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="d57ec-103">定義資源之後，會公開您的 web 服務 (請參閱[撰寫管理 OData web 服務的 MOF 結構描述檔](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md))，您將這些資源對應至實作支援的基礎 Windows PowerShell cmdlet藉由建立 XML 檔案符合每個資源的作業[資源對應的結構描述](./resource-mapping-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="d57ec-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="d57ec-104">XML 檔案也會指定用戶端用來存取資源的 Url。</span><span class="sxs-lookup"><span data-stu-id="d57ec-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="d57ec-105">Mappng 資源 url</span><span class="sxs-lookup"><span data-stu-id="d57ec-105">Mappng resources to URLs</span></span>

<span data-ttu-id="d57ec-106">XML 檔案的第一個部分會對應至用來存取這些 Url 的 MOF 結構描述檔案中定義的資源。</span><span class="sxs-lookup"><span data-stu-id="d57ec-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="d57ec-107">下列範例會顯示該對應。</span><span class="sxs-lookup"><span data-stu-id="d57ec-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="d57ec-108">對應至 CRUD 作業的 cmdlet</span><span class="sxs-lookup"><span data-stu-id="d57ec-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="d57ec-109">然後在您指定之 cmdlet 的對應至 CRUD （建立、 讀取、 更新和刪除） 資源支援的作業。</span><span class="sxs-lookup"><span data-stu-id="d57ec-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="d57ec-110">在 管理 OData[資源對應的結構描述](./resource-mapping-schema.md)，對應的 CRUD 作業，如下所示。</span><span class="sxs-lookup"><span data-stu-id="d57ec-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="d57ec-111">CRUD 命令</span><span class="sxs-lookup"><span data-stu-id="d57ec-111">CRUD command</span></span>|<span data-ttu-id="d57ec-112">XML 項目</span><span class="sxs-lookup"><span data-stu-id="d57ec-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="d57ec-113">建立</span><span class="sxs-lookup"><span data-stu-id="d57ec-113">Create</span></span>|<span data-ttu-id="d57ec-114">建立</span><span class="sxs-lookup"><span data-stu-id="d57ec-114">Create</span></span>|
|<span data-ttu-id="d57ec-115">讀取</span><span class="sxs-lookup"><span data-stu-id="d57ec-115">Read</span></span>|<span data-ttu-id="d57ec-116">查詢</span><span class="sxs-lookup"><span data-stu-id="d57ec-116">Query</span></span>|
|<span data-ttu-id="d57ec-117">更新</span><span class="sxs-lookup"><span data-stu-id="d57ec-117">Update</span></span>|<span data-ttu-id="d57ec-118">更新</span><span class="sxs-lookup"><span data-stu-id="d57ec-118">Update</span></span>|
|<span data-ttu-id="d57ec-119">刪除</span><span class="sxs-lookup"><span data-stu-id="d57ec-119">Delete</span></span>|<span data-ttu-id="d57ec-120">刪除</span><span class="sxs-lookup"><span data-stu-id="d57ec-120">Delete</span></span>|

<span data-ttu-id="d57ec-121">下列範例會示範建立、 讀取和更新作業的對應上`Service`資源。</span><span class="sxs-lookup"><span data-stu-id="d57ec-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="d57ec-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d57ec-122">See Also</span></span>

[<span data-ttu-id="d57ec-123">撰寫 MOF 結構描述檔案管理 OData web 服務</span><span class="sxs-lookup"><span data-stu-id="d57ec-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="d57ec-124">資源對應結構描述</span><span class="sxs-lookup"><span data-stu-id="d57ec-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="d57ec-125">建立管理 OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="d57ec-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)