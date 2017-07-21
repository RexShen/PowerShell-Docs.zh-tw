---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 4185d9395f2f3e5ba1c8daa0c365cb2bf322936b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="get-childitem-has--depth-parameter"></a><span data-ttu-id="0cd11-102">Get-ChildItem 具有 -Depth 參數</span><span class="sxs-lookup"><span data-stu-id="0cd11-102">Get-ChildItem has -Depth parameter</span></span>
<span data-ttu-id="0cd11-103">**Get-ChildItem** 現在有 **–Depth** 參數，搭配 **–Recurse** 用來限制遞迴︰</span><span class="sxs-lookup"><span data-stu-id="0cd11-103">**Get-ChildItem** now has a **–Depth** parameter you use with **–Recurse** to limit the recursion:</span></span>

<span data-ttu-id="0cd11-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span><span class="sxs-lookup"><span data-stu-id="0cd11-104">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 0</span></span>

<span data-ttu-id="0cd11-105">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="0cd11-105">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="0cd11-106">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0cd11-106">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0cd11-107">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="0cd11-107">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="0cd11-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-108">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="0cd11-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-109">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="0cd11-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-110">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="0cd11-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span><span class="sxs-lookup"><span data-stu-id="0cd11-111">PS C:\\Users\\slee\\Downloads\\Example&gt; Get-ChildItem -Recurse -Depth 1</span></span>

<span data-ttu-id="0cd11-112">目錄：C:\\Users\\slee\\Downloads\\Example</span><span class="sxs-lookup"><span data-stu-id="0cd11-112">Directory: C:\\Users\\slee\\Downloads\\Example</span></span>

<span data-ttu-id="0cd11-113">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0cd11-113">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0cd11-114">d----- 4/14/2015 5:36 PM Depth0</span><span class="sxs-lookup"><span data-stu-id="0cd11-114">d----- 4/14/2015 5:36 PM Depth0</span></span>

<span data-ttu-id="0cd11-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-115">-a---- 4/14/2015 1:19 PM 0 File1.txt</span></span>

<span data-ttu-id="0cd11-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-116">-a---- 4/14/2015 1:19 PM 0 File2.txt</span></span>

<span data-ttu-id="0cd11-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span><span class="sxs-lookup"><span data-stu-id="0cd11-117">-a---- 4/14/2015 1:19 PM 0 File3.txt</span></span>

<span data-ttu-id="0cd11-118">目錄：C:\\Users\\slee\\Downloads\\Example\\Depth0</span><span class="sxs-lookup"><span data-stu-id="0cd11-118">Directory: C:\\Users\\slee\\Downloads\\Example\\Depth0</span></span>

<span data-ttu-id="0cd11-119">Mode LastWriteTime Length Name</span><span class="sxs-lookup"><span data-stu-id="0cd11-119">Mode LastWriteTime Length Name</span></span>

---- ------------- ------ ----

<span data-ttu-id="0cd11-120">d----- 4/14/2015 5:33 PM Depth1</span><span class="sxs-lookup"><span data-stu-id="0cd11-120">d----- 4/14/2015 5:33 PM Depth1</span></span>

