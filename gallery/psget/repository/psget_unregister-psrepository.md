---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Unregister-PSRepository
ms.openlocfilehash: 7847e223ae7edd9ec2417d104e5e8130f92a59cf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="unregister-psrepository"></a><span data-ttu-id="da121-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da121-103">Unregister-PSRepository</span></span>

<span data-ttu-id="da121-104">取消註冊存放庫。</span><span class="sxs-lookup"><span data-stu-id="da121-104">Unregisters a repository.</span></span>

## <a name="description"></a><span data-ttu-id="da121-105">描述</span><span class="sxs-lookup"><span data-stu-id="da121-105">Description</span></span>

<span data-ttu-id="da121-106">Unregister-PSRepository Cmdlet 會取消註冊目前使用者的存放庫。</span><span class="sxs-lookup"><span data-stu-id="da121-106">The Unregister-PSRepository cmdlet unregisters a repository for the current user.</span></span>
- <span data-ttu-id="da121-107">企業和中斷連線的案例允許取消註冊和重新註冊 PSGallery 存放庫。</span><span class="sxs-lookup"><span data-stu-id="da121-107">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
- <span data-ttu-id="da121-108">使用者只要執行 `Register-PSRepository -Default`，就可以重新註冊 PSGallery</span><span class="sxs-lookup"><span data-stu-id="da121-108">Users can re-register the PSGallery by simply running `Register-PSRepository -Default`</span></span>
- <span data-ttu-id="da121-109">因為 PSGallery 是 Publish-Module 和 Publish-Script Cmdlet 中的預設發行存放庫，所以如果已註冊的存放庫清單中沒有 PSGallery，則會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="da121-109">Since PSGallery is the default publish repository in Publish-Module and Publish-Script cmdlets, an error will be thrown if PSGallery is not available in the registered repository list.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="da121-110">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="da121-110">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Unregister-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="da121-111">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="da121-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="da121-112">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="da121-112">Unregister-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517130)

## <a name="example-commands"></a><span data-ttu-id="da121-113">範例命令</span><span class="sxs-lookup"><span data-stu-id="da121-113">Example commands</span></span>

```powershell
Unregister-PSRepository -Name "MyPrivateGallery"

Get-PSRepository exp | Unregister-PSRepository
```

### <a name="unregistration-and-re-registration-of-the-psgallery-repository-is-allowed-for-an-enterprise-and-disconnected-scenarios"></a><span data-ttu-id="da121-114">企業和中斷連線的案例允許取消註冊和重新註冊 PSGallery 存放庫。</span><span class="sxs-lookup"><span data-stu-id="da121-114">Unregistration and re-registration of the PSGallery repository is allowed for an enterprise and disconnected scenarios.</span></span>
```powershell

# Unregister PSGallery repository
Unregister-PSRepository PSGallery

# Publish-Module throws an error when PSGallery is not a registered repository
Publish-Module -Name MyModule
publish-module : Unable to find repository 'PSGallery'. Use Get-PSRepository to see all available repositories. Try again after specifying a valid repository name. You can use 'Register-PSRepository -Default' to register the PSGallery repository.
At line:1 char:1
+ publish-module -name mymodule
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (PSGallery:String) [Publish-Module], ArgumentException
    + FullyQualifiedErrorId : PSGalleryNotFound,Publish-Module

# Re-register PSGallery repository
Register-PSRepository -Default
```