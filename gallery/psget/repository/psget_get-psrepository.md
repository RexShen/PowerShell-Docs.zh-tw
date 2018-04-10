---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Get-PSRepository
ms.openlocfilehash: 97279a8ed0087c835fb924991484959cd7237016
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="get-psrepository"></a><span data-ttu-id="a137c-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a137c-103">Get-PSRepository</span></span>

<span data-ttu-id="a137c-104">取得電腦上的已註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="a137c-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="a137c-105">描述</span><span class="sxs-lookup"><span data-stu-id="a137c-105">Description</span></span>

<span data-ttu-id="a137c-106">Get-PSRepository Cmdlet 會取得電腦上針對目前使用者所註冊的 PowerShell 模組存放庫。</span><span class="sxs-lookup"><span data-stu-id="a137c-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="a137c-107">針對每個已註冊的存放庫，Get-PSRepository 會傳回 PSRepository 物件，而您可以將這個物件選擇性地傳送至 Unregister-PSRepository 來取消註冊已註冊的存放庫。</span><span class="sxs-lookup"><span data-stu-id="a137c-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a137c-108">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="a137c-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a137c-109">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="a137c-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="a137c-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a137c-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="a137c-111">範例命令</span><span class="sxs-lookup"><span data-stu-id="a137c-111">Example commands</span></span>

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```