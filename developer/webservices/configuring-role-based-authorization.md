---
title: 設定以角色為基礎的授權 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859594"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="b07eb-102">設定角色型授權</span><span class="sxs-lookup"><span data-stu-id="b07eb-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="b07eb-103">本主題示範如何設定以角色為基礎的授權原則的範例實作[Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization)介面中所述[實作自訂Management OData IIS 擴充功能的授權](./implementing-custom-authorization-for-a-management-odata-web-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b07eb-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="b07eb-104">在此範例中，您會設定由範例管理 OData 應用程式用來定義授權原則的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="b07eb-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="b07eb-105">您將建立兩個角色，並將不同的 Windows PowerShell 模組包含與這些角色的工作流程。</span><span class="sxs-lookup"><span data-stu-id="b07eb-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="b07eb-106">定義 XML 檔案的結構描述會列在[角色為基礎的授權組態結構描述](./role-based-authorization-configuration-schema.md)。</span><span class="sxs-lookup"><span data-stu-id="b07eb-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="b07eb-107">修改 RBacConfiguration.xml 檔案</span><span class="sxs-lookup"><span data-stu-id="b07eb-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="b07eb-108">此檔案定義應用程式的授權原則。</span><span class="sxs-lookup"><span data-stu-id="b07eb-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="b07eb-109">角色定義使用`Group`節點。</span><span class="sxs-lookup"><span data-stu-id="b07eb-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="b07eb-110">A`Group`節點定義指派給該群組的使用者可以執行的 Windows PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="b07eb-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="b07eb-111">使用使用者指派給群組`User`節點。</span><span class="sxs-lookup"><span data-stu-id="b07eb-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="b07eb-112">在這些範例中，您會將模組加入系統管理員`Group` 節點，並將使用者新增至每個群組。</span><span class="sxs-lookup"><span data-stu-id="b07eb-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="b07eb-113">將模組加入至群組節點</span><span class="sxs-lookup"><span data-stu-id="b07eb-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="b07eb-114">建立名為**RBacConfiguration.xml**在文字編輯器中。</span><span class="sxs-lookup"><span data-stu-id="b07eb-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="b07eb-115">此檔案應該儲存至您的 web 服務的主要應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="b07eb-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="b07eb-116">在檔案中插入下列文字。</span><span class="sxs-lookup"><span data-stu-id="b07eb-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="b07eb-117">此檔案包含兩個`Group`節點。</span><span class="sxs-lookup"><span data-stu-id="b07eb-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="b07eb-118">這些代表兩個角色在此範例中，使用`NonAdminGroup`而`AdminGroup`角色。</span><span class="sxs-lookup"><span data-stu-id="b07eb-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="b07eb-119">直接在結尾後面`Cmdlets`中第一個標記`Group` 節點，新增下列 XML:</span><span class="sxs-lookup"><span data-stu-id="b07eb-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="b07eb-120">將使用者新增至群組節點</span><span class="sxs-lookup"><span data-stu-id="b07eb-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="b07eb-121">開啟**RBacConfiguration.xml**在文字編輯器中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b07eb-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="b07eb-122">此檔案位於資料夾 c:\\\inetpub\wwwroot\Modata 如果您沒有變更端點名稱，再進行安裝。</span><span class="sxs-lookup"><span data-stu-id="b07eb-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="b07eb-123">直接結尾標記之後在`Users` 節點，新增下列 XML:</span><span class="sxs-lookup"><span data-stu-id="b07eb-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="b07eb-124">直接將 XML 加入上一個步驟之後，新增下列 XML:</span><span class="sxs-lookup"><span data-stu-id="b07eb-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```