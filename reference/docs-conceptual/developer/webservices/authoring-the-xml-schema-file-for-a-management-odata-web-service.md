---
title: 撰寫 Management OData web 服務的 XML 架構檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359797"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="8a37d-102">撰寫 Management OData Web 服務的 XML 結構描述檔案</span><span class="sxs-lookup"><span data-stu-id="8a37d-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="8a37d-103">定義 web 服務將公開的資源之後（請參閱[撰寫 Management OData web 服務的 MOF 架構](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)檔案），您可以將這些資源對應到基礎 Windows PowerShell Cmdlet，藉由建立符合[資源對應架構](./resource-mapping-schema.md)的 XML 檔案，為每個資源執行支援的作業。</span><span class="sxs-lookup"><span data-stu-id="8a37d-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="8a37d-104">XML 檔案也會指定用戶端用來存取資源的 Url。</span><span class="sxs-lookup"><span data-stu-id="8a37d-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="8a37d-105">Mappng 資源至 Url</span><span class="sxs-lookup"><span data-stu-id="8a37d-105">Mappng resources to URLs</span></span>

<span data-ttu-id="8a37d-106">XML 檔案的第一個部分會將 MOF 架構檔案中定義的資源對應到用來存取它們的 Url。</span><span class="sxs-lookup"><span data-stu-id="8a37d-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="8a37d-107">下列範例會顯示該對應。</span><span class="sxs-lookup"><span data-stu-id="8a37d-107">The following example shows that mapping.</span></span>

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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="8a37d-108">將 Cmdlet 對應至 CRUD 作業</span><span class="sxs-lookup"><span data-stu-id="8a37d-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="8a37d-109">接著，您可以指定對應至資源支援之 CRUD （建立、讀取、更新和刪除）作業的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="8a37d-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="8a37d-110">在 Management OData[資源對應架構](./resource-mapping-schema.md)中，CRUD 作業的對應方式如下。</span><span class="sxs-lookup"><span data-stu-id="8a37d-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="8a37d-111">CRUD 命令</span><span class="sxs-lookup"><span data-stu-id="8a37d-111">CRUD command</span></span>|<span data-ttu-id="8a37d-112">XML 元素</span><span class="sxs-lookup"><span data-stu-id="8a37d-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="8a37d-113">建立</span><span class="sxs-lookup"><span data-stu-id="8a37d-113">Create</span></span>|<span data-ttu-id="8a37d-114">建立</span><span class="sxs-lookup"><span data-stu-id="8a37d-114">Create</span></span>|
|<span data-ttu-id="8a37d-115">讀取</span><span class="sxs-lookup"><span data-stu-id="8a37d-115">Read</span></span>|<span data-ttu-id="8a37d-116">查詢</span><span class="sxs-lookup"><span data-stu-id="8a37d-116">Query</span></span>|
|<span data-ttu-id="8a37d-117">更新</span><span class="sxs-lookup"><span data-stu-id="8a37d-117">Update</span></span>|<span data-ttu-id="8a37d-118">更新</span><span class="sxs-lookup"><span data-stu-id="8a37d-118">Update</span></span>|
|<span data-ttu-id="8a37d-119">刪除</span><span class="sxs-lookup"><span data-stu-id="8a37d-119">Delete</span></span>|<span data-ttu-id="8a37d-120">刪除</span><span class="sxs-lookup"><span data-stu-id="8a37d-120">Delete</span></span>|

<span data-ttu-id="8a37d-121">下列範例顯示 `Service` 資源上建立、讀取和更新作業的對應。</span><span class="sxs-lookup"><span data-stu-id="8a37d-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8a37d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a37d-122">See Also</span></span>

[<span data-ttu-id="8a37d-123">撰寫 Management OData web 服務的 MOF 架構檔案</span><span class="sxs-lookup"><span data-stu-id="8a37d-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="8a37d-124">資源對應架構</span><span class="sxs-lookup"><span data-stu-id="8a37d-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="8a37d-125">建立 Management OData Web 服務</span><span class="sxs-lookup"><span data-stu-id="8a37d-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)