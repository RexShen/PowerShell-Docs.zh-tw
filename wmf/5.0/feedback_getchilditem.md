---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: cc5d2d799c1292f68de5fb2360fcba220c2c010b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085272"
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="00344-102">Get-ChildItem 具有 -Depth 參數</span><span class="sxs-lookup"><span data-stu-id="00344-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="00344-103">**Get-ChildItem** 現在有 **–Depth** 參數，搭配 **–Recurse** 用來限制遞迴︰</span><span class="sxs-lookup"><span data-stu-id="00344-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="00344-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="00344-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="00344-105">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="00344-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="00344-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="00344-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="00344-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="00344-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="00344-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="00344-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="00344-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="00344-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="00344-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="00344-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="00344-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="00344-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="00344-112">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="00344-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="00344-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="00344-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="00344-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="00344-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="00344-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="00344-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="00344-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="00344-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="00344-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="00344-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="00344-118">目錄：C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="00344-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="00344-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="00344-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="00344-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="00344-120">d----- 4/14/2015 5:33 PM Depth1</span></span>
