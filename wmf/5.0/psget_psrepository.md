---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: 269f4112704067f291728e4c1d745d68ec6ccd6f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="1c1c7-102">註冊 PowerShell 存放庫</span><span class="sxs-lookup"><span data-stu-id="1c1c7-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="1c1c7-103">您可以設定 PowerShellGet 操作內部存放庫。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="1c1c7-104">做法是使用新增下列項目︰</span><span class="sxs-lookup"><span data-stu-id="1c1c7-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="1c1c7-105">Register-PSRepository：為目前的使用者註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="1c1c7-106">Unregister-PSRepository：移除目前使用者已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="1c1c7-107">Set-PSRepository：為已註冊的存放庫設定值。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="1c1c7-108">Get-PSRepository：為目前的使用者取得所有已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="1c1c7-109">註冊存放庫後，您可以使用 Find-Module 和 Install-Module 搭配存放庫。</span><span class="sxs-lookup"><span data-stu-id="1c1c7-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

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