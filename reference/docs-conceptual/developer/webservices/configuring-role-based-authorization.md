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
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="7d3fc-102">設定角色型授權</span><span class="sxs-lookup"><span data-stu-id="7d3fc-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="7d3fc-103">本主題示範如何針對執行管理的自訂授權中所述的[Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)介面，設定以角色為基礎的授權原則[OData IIS 延伸](./implementing-custom-authorization-for-a-management-odata-web-service.md)模組。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="7d3fc-104">在此範例中，您將設定範例管理 OData 應用程式用來定義授權原則的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="7d3fc-105">您將建立兩個角色，並將包含工作流程的不同 Windows PowerShell 模組與這些角色產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="7d3fc-106">定義 XML 檔案的架構會列在以[角色為基礎的授權設定架構](./role-based-authorization-configuration-schema.md)中。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="7d3fc-107">修改 RBacConfiguration .xml 檔案</span><span class="sxs-lookup"><span data-stu-id="7d3fc-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="7d3fc-108">此檔案會定義應用程式的授權原則。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="7d3fc-109">角色是使用 `Group` 節點來定義。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="7d3fc-110">@No__t-0 節點定義指派給該群組的使用者可以執行的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="7d3fc-111">使用者會使用 `User` 節點指派給群組。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="7d3fc-112">在這些範例中，您會將模組新增至 系統管理員 `Group` 節點，並將使用者新增至每個群組。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="7d3fc-113">將模組新增至群組節點</span><span class="sxs-lookup"><span data-stu-id="7d3fc-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="7d3fc-114">在文字編輯器中，建立名為**RBacConfiguration**的檔案。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="7d3fc-115">這個檔案應該儲存至 web 服務的主要應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="7d3fc-116">在檔案中插入下列文字。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="7d3fc-117">檔案包含兩個 @no__t 0 節點。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="7d3fc-118">這代表此範例中使用的兩個角色，`NonAdminGroup` 和 @no__t 1 角色。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="7d3fc-119">在第一個 `Group` 節點的結尾 `Cmdlets` 標記正後方，新增下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7d3fc-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="7d3fc-120">將使用者新增至群組節點</span><span class="sxs-lookup"><span data-stu-id="7d3fc-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="7d3fc-121">在文字編輯器中開啟**RBacConfiguration。**</span><span class="sxs-lookup"><span data-stu-id="7d3fc-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="7d3fc-122">如果您未在安裝前變更端點名稱，此檔案位於 C： \\ \ inetpub\wwwroot\Modata 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="7d3fc-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="7d3fc-123">在 `Users` 節點的結束記號正後方，新增下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7d3fc-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="7d3fc-124">直接在上一個步驟中新增的 XML 之後，新增下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7d3fc-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```