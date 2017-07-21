---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: "資源庫,powershell,cmdlet,psget"
title: Set-PSRepository
ms.openlocfilehash: 2e850947b67d43254ee9d1b3c1c571167435234c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="set-psrepository"></a><span data-ttu-id="c2d58-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c2d58-103">Set-PSRepository</span></span>

<span data-ttu-id="c2d58-104">Set-PSRepository 會設定已註冊存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="c2d58-104">Set-PSRepository sets values for a registered repository.</span></span>

## <a name="description"></a><span data-ttu-id="c2d58-105">描述</span><span class="sxs-lookup"><span data-stu-id="c2d58-105">Description</span></span>

<span data-ttu-id="c2d58-106">Set-PSRepository Cmdlet 會設定已註冊模組存放庫的值。</span><span class="sxs-lookup"><span data-stu-id="c2d58-106">The Set-PSRepository cmdlet sets values for a registered module repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="c2d58-107">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="c2d58-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Set-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c2d58-108">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="c2d58-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="c2d58-109">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c2d58-109">Set-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517128)

## <a name="example-commands"></a><span data-ttu-id="c2d58-110">範例命令</span><span class="sxs-lookup"><span data-stu-id="c2d58-110">Example commands</span></span>

```powershell
PS C:\> Register-PSRepository -Name myRepository -SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" -InstallationPolicy Trusted
PS C:\> Get-PSRepository
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Trusted              https://www.myget.org/F/powershellgetdemo/api/v2

# Set installation Policy for a repository
PS C:\> Set-PSRepository -Name myRepository -InstallationPolicy Untrusted
PS C:\> Get-PSRepository

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
myRepository              Untrusted            https://www.myget.org/F/powershellgetdemo/api/v2
```


### <a name="set-psrepository-cmdlet-with-script-sharing-support"></a><span data-ttu-id="c2d58-111">具有指令碼共用支援的 Set-PSRepository Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c2d58-111">Set-PSRepository cmdlet with script sharing support</span></span>

<span data-ttu-id="c2d58-112">使用 Set-PSRepository Cmdlet 將 **ScriptSourceLocation** 和 **ScriptPublishLocation** 新增至 PSRepository。</span><span class="sxs-lookup"><span data-stu-id="c2d58-112">Use Set-PSRepository cmdlets to add the **ScriptSourceLocation** and **ScriptPublishLocation** to the PSRepository.</span></span>
```powershell
# Add script sharing locations to an existing PSRepository using Set-PSRepository object.
Set-PSRepository -Name MyGallery `
                 -ScriptSourceLocation https://MyGallery.com/api/v2/items/psscript/ `
                 -ScriptPublishLocation https://MyGallery.com/api/v2/package/

Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://MyGallery.com/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://MyGallery.com/api/v2/package/
ScriptSourceLocation : https://MyGallery.com/api/v2/items/psscript/
ScriptPublishLocation : https://MyGallery.com/api/v2/package/
ProviderOptions : {}

```

