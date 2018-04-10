---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: 資源庫,powershell,cmdlet,psget
title: Save-Script
ms.openlocfilehash: 67697fc0e70fb31cad9ad5ae7ce01debef160b81
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="save-script"></a><span data-ttu-id="58443-103">Save-Script</span><span class="sxs-lookup"><span data-stu-id="58443-103">Save-Script</span></span>

<span data-ttu-id="58443-104">Save-Script Cmdlet 可讓您將指令碼檔案儲存到指定的位置，藉以檢閱指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="58443-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="58443-105">描述</span><span class="sxs-lookup"><span data-stu-id="58443-105">Description</span></span>

<span data-ttu-id="58443-106">Save-Script Cmdlet 會儲存指定的指令碼。</span><span class="sxs-lookup"><span data-stu-id="58443-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="58443-107">Cmdlet 語法</span><span class="sxs-lookup"><span data-stu-id="58443-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="58443-108">Cmdlet 線上說明參考資料</span><span class="sxs-lookup"><span data-stu-id="58443-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="58443-109">Save-Script</span><span class="sxs-lookup"><span data-stu-id="58443-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="58443-110">範例命令</span><span class="sxs-lookup"><span data-stu-id="58443-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="58443-111">範例 1︰儲存存放庫中的指令碼</span><span class="sxs-lookup"><span data-stu-id="58443-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="58443-112">這個命令會將 GalleryINT 存放庫中之指令碼 Fabrikam-ClientScript 的最新版本儲存至本機資料夾 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="58443-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="58443-113">範例 2：從 Find-Script Cmdlet 傳送以儲存指令碼版本</span><span class="sxs-lookup"><span data-stu-id="58443-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="58443-114">第一個命令會尋找 GalleryINT 存放庫中是否有 1.5 版的 Fabrikam-ClientScript，並將它儲存至資料夾 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="58443-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="58443-115">第二個命令會驗證已儲存的指令碼中繼資料。</span><span class="sxs-lookup"><span data-stu-id="58443-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

### <a name="example-3-save-a-prerelease-version-of-a-script-from-a-repository"></a><span data-ttu-id="58443-116">範例 3：儲存存放庫中指令碼的發行前版本</span><span class="sxs-lookup"><span data-stu-id="58443-116">Example 3: Save a prerelease version of a script from a repository</span></span>
<span data-ttu-id="58443-117">這個命令會將 GalleryINT 存放庫中之指令碼 Fabrikam-ClientScript 的最新版本儲存至本機資料夾 C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="58443-117">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Path C:\ScriptSharingDemo -AllowPrerelease
```