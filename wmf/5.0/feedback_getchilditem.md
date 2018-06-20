---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: d9f1ca10c948b06b234e17f688b8f899ed41c5d6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221896"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="a17d6-102">Get-ChildItem 具有 -Depth 參數</span><span class="sxs-lookup"><span data-stu-id="a17d6-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="a17d6-103">**Get-ChildItem** 現在有 **–Depth** 參數，搭配 **–Recurse** 用來限制遞迴︰</span><span class="sxs-lookup"><span data-stu-id="a17d6-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="a17d6-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="a17d6-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="a17d6-105">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="a17d6-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a17d6-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a17d6-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a17d6-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a17d6-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a17d6-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a17d6-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a17d6-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a17d6-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="a17d6-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="a17d6-112">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="a17d6-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="a17d6-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a17d6-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a17d6-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="a17d6-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="a17d6-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="a17d6-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="a17d6-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="a17d6-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="a17d6-118">目錄：C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="a17d6-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="a17d6-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="a17d6-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="a17d6-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="a17d6-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
