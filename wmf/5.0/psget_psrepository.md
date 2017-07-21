---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 81ce13a082ad1d7a13ba5fd76a7595b55708f54e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="88a43-102">註冊 PowerShell 存放庫</span><span class="sxs-lookup"><span data-stu-id="88a43-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="88a43-103">您可以設定 PowerShellGet 操作內部存放庫。</span><span class="sxs-lookup"><span data-stu-id="88a43-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="88a43-104">做法是使用新增下列項目︰</span><span class="sxs-lookup"><span data-stu-id="88a43-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="88a43-105">Register-PSRepository：為目前的使用者註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="88a43-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="88a43-106">Unregister-PSRepository：移除目前使用者已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="88a43-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="88a43-107">Set-PSRepository：為已註冊的存放庫設定值。</span><span class="sxs-lookup"><span data-stu-id="88a43-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="88a43-108">Get-PSRepository：為目前的使用者取得所有已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="88a43-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="88a43-109">註冊存放庫後，您可以使用 Find-Module 和 Install-Module 搭配存放庫。</span><span class="sxs-lookup"><span data-stu-id="88a43-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```

