---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "啟動 32 位元版本的 Windows PowerShell"
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="68de5-103">啟動 32 位元版本的 Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="68de5-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="68de5-104">當您在 64 位元電腦上安裝 Windows PowerShell 時，除了 64 位元的版本，還會安裝 32 位元版本的 Windows PowerShell (**Windows PowerShell (x86)**)。</span><span class="sxs-lookup"><span data-stu-id="68de5-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="68de5-105">執行 Windows PowerShell 時，預設會執行 64 位元版本。</span><span class="sxs-lookup"><span data-stu-id="68de5-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="68de5-106">不過，您可能偶而需要執行 **Windows PowerShell (x86)**，例如，使用需要 32 位元版本的模組時，或遠端連線至 32 位元電腦時。</span><span class="sxs-lookup"><span data-stu-id="68de5-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="68de5-107">若要啟動 32 位元版本的 Windows PowerShell，請使用下列任何程序。</span><span class="sxs-lookup"><span data-stu-id="68de5-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="68de5-108">在 Windows Server® 2012 R2 中</span><span class="sxs-lookup"><span data-stu-id="68de5-108">In Windows Server® 2012 R2</span></span>

-   <span data-ttu-id="68de5-109">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="68de5-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="68de5-110">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="68de5-110">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="68de5-111">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-112">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-113">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="68de5-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="68de5-114">在 Windows Server® 2012 中</span><span class="sxs-lookup"><span data-stu-id="68de5-114">In Windows Server® 2012</span></span>

-   <span data-ttu-id="68de5-115">在 **[開始]** 畫面上，輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-116">在 **[伺服器管理員]** 中，從 **[工具]** 功能表中選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-117">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-118">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="68de5-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="68de5-119">在 Windows® 8.1 中</span><span class="sxs-lookup"><span data-stu-id="68de5-119">In Windows® 8.1</span></span>

-   <span data-ttu-id="68de5-120">在 **[開始]** 畫面上，輸入 **Windows PowerShell (x86)**。</span><span class="sxs-lookup"><span data-stu-id="68de5-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="68de5-121">按一下 **[Windows PowerShell x86]** 並排顯示。</span><span class="sxs-lookup"><span data-stu-id="68de5-121">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="68de5-122">如果您正在執行 Windows 8.1 的[遠端伺服器管理工具](http://go.microsoft.com/fwlink/?LinkID=304145)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="68de5-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="68de5-123">選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-123">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-124">在桌面上，將游標移到右上角、按一下 **[搜尋]**、輸入 **PowerShell x86**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
-   <span data-ttu-id="68de5-125">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="68de5-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="68de5-126">在 Windows® 8 中</span><span class="sxs-lookup"><span data-stu-id="68de5-126">In Windows® 8</span></span>

-   <span data-ttu-id="68de5-127">在 **[開始]** 畫面上，將游標移到右上角，並依序按一下 **[設定]** 和 **[並排顯示]**，然後將 **[顯示系統管理工具]** 移到 [是]。</span><span class="sxs-lookup"><span data-stu-id="68de5-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="68de5-128">然後輸入 **PowerShell**，並按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-129">如果您正在執行 Windows 8 的 [遠端伺服器管理工具](http://www.microsoft.com/download/details.aspx?id=28972)，則也可以從 [伺服器管理員工具] 功能表中開啟 Windows PowerShell x86。</span><span class="sxs-lookup"><span data-stu-id="68de5-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="68de5-130">選取 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-130">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-131">在 **[開始]** 畫面或桌面上，輸入 **PowerShell (x86)**，然後按一下 **[Windows PowerShell (x86)]**。</span><span class="sxs-lookup"><span data-stu-id="68de5-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="68de5-132">透過命令列，輸入：`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="68de5-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

