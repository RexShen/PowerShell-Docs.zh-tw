---
title: 正在設定以角色為基礎的授權 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359767"
---
# <a name="configuring-role-based-authorization"></a>設定角色型授權

本主題示範如何針對[執行 Management ODATA IIS 擴充功能的自訂授權](./implementing-custom-authorization-for-a-management-odata-web-service.md)中所述的[Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)介面的範例執行，設定以角色為基礎的授權原則。

在此範例中，您將設定範例管理 OData 應用程式用來定義授權原則的 XML 檔案。 您將建立兩個角色，並將包含工作流程的不同 Windows PowerShell 模組與這些角色產生關聯。 定義 XML 檔案的架構會列在以[角色為基礎的授權設定架構](./role-based-authorization-configuration-schema.md)中。

## <a name="modifying-the-rbacconfigurationxml-file"></a>修改 RBacConfiguration .xml 檔案

此檔案會定義應用程式的授權原則。 角色是使用 `Group` 節點所定義。 `Group` 節點會定義使用者指派給該群組的 Windows PowerShell 命令。 使用者會使用 `User` 節點指派給群組。

在這些範例中，您會將模組新增至 [系統管理員] `Group` 節點，並將使用者新增至每個群組。

#### <a name="adding-a-module-to-a-group-node"></a>將模組新增至群組節點

1. 在文字編輯器中，建立名為**RBacConfiguration**的檔案。 這個檔案應該儲存至 web 服務的主要應用程式目錄。 在檔案中插入下列文字。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. 檔案包含兩個 `Group` 節點。 這些代表在此範例中使用的兩個角色，`NonAdminGroup` 和 `AdminGroup` 角色。

   在第一個 `Group` 節點的結尾 `Cmdlets` 標記的正後方，新增下列 XML：

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>將使用者新增至群組節點

1. 在文字編輯器中開啟**RBacConfiguration。** 如果您未在安裝前變更端點名稱，此檔案位於 C：\\\inetpub\wwwroot\Modata 資料夾中。

2. 在 `Users` 節點的結束記號正後方，新增下列 XML：

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. 直接在上一個步驟中新增的 XML 之後，新增下列 XML：

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```