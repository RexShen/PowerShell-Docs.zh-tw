---
title: 撰寫 Management OData web 服務的 web.config 檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359787"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>撰寫 Management OData Web 服務的 Web.config 檔案

在部署 Management OData web 服務之前，您必須先設定 web.config 檔案，使其指向 XML 架構檔案以及[Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)和 enable-pssessionconfiguration 介面的 dll，然後再進行此[作業](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration)。」。

## <a name="sample-config-file"></a>範例設定檔

以下是 web 服務的 web.config 檔案外觀的範例。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>另請參閱

[執行 Management OData web 服務的自訂授權](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[執行 Management OData web 服務的 SessionConfiguration](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[撰寫 Management OData web 服務的 MOF 架構檔案](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[撰寫 Management OData web 服務的 XML 架構檔案](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[建立 Management OData Web 服務](./creating-a-management-odata-web-service.md)