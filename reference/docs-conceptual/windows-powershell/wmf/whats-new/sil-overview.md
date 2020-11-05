---
ms.date: 06/12/2017
title: 軟體清查記錄 (SIL)
description: WMF 5.x 新增軟體清查記錄功能，可讓您在中央位置收集已安裝軟體的相關資訊，以便更輕鬆地進行管理及稽核。
ms.openlocfilehash: 85e261782a3df5fe5561a80529ba699d686a8779
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646613"
---
# <a name="software-inventory-logging-sil"></a><span data-ttu-id="56f0b-103">軟體清查記錄 (SIL)</span><span class="sxs-lookup"><span data-stu-id="56f0b-103">Software Inventory Logging (SIL)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56f0b-104">在已執行 SIL 的 Windows Server 2012 R2 伺服器上安裝 WMF 5.x 時，在 WMF 安裝之後，必須執行一次 Start-SilLogging Cmdlet，因為安裝程序將會不當停止軟體清查記錄功能。</span><span class="sxs-lookup"><span data-stu-id="56f0b-104">When installing WMF 5.x on a Windows Server 2012 R2 Server that is already running SIL, it is necessary to run the Start-SilLogging cmdlet once after the WMF install, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<span data-ttu-id="56f0b-105">軟體清查記錄是為了在取得安裝在伺服器本機上的 Microsoft 軟體正確資料時，能夠減少運作成本，尤其是在 IT 環境中的許多伺服器上 (假設已在 IT 環境中安裝並執行軟體)。</span><span class="sxs-lookup"><span data-stu-id="56f0b-105">Software Inventory Logging helps reduce the operational costs of getting accurate information about the Microsoft software installed locally on a server, but especially across many servers in an IT environment (assuming the software is installed and running across the IT environment).</span></span> <span data-ttu-id="56f0b-106">假設一個已設定，您可以將這份資料轉送到彙總伺服器，並使用統一的自動程序將記錄資料收集在一個地方。</span><span class="sxs-lookup"><span data-stu-id="56f0b-106">Provided one is set up, you can forward this data to an aggregation server, and collect the log data in one place by using a uniform, automatic process.</span></span>

<span data-ttu-id="56f0b-107">雖然您也能透過直接查詢每部電腦來記錄軟體清查資料，但是軟體清查記錄能使用由每部伺服器啟動的轉送 (經由網路) 架構，這樣可以克服一般會在許多軟體清查和資產管理案例中遇到的伺服器探索難題。</span><span class="sxs-lookup"><span data-stu-id="56f0b-107">While you can also log software inventory data by querying each computer directly, Software Inventory Logging, by employing a forwarding (over the network) architecture initiated by each server, can overcome server discovery challenges that are typical for many software inventory and asset management scenarios.</span></span> <span data-ttu-id="56f0b-108">軟體清查記錄使用 SSL 保護透過 HTTPS 轉送到彙總伺服器的資料。</span><span class="sxs-lookup"><span data-stu-id="56f0b-108">Software Inventory Logging uses SSL to secure data that is forwarded over HTTPS to an aggregation server.</span></span> <span data-ttu-id="56f0b-109">將資料存放在一個地方可以在有需要時更輕鬆地分析、操控及共用資料。</span><span class="sxs-lookup"><span data-stu-id="56f0b-109">Storing the data in one place makes the data easier to analyze, manipulate, and share when necessary.</span></span>

<span data-ttu-id="56f0b-110">此功能不會將這份資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="56f0b-110">None of this data is sent to Microsoft as part of the feature functionality.</span></span> <span data-ttu-id="56f0b-111">軟體清查記錄資料與功能僅供伺服器軟體授權的擁有者與管理員使用。</span><span class="sxs-lookup"><span data-stu-id="56f0b-111">Software Inventory Logging data and functionality is meant for the sole use of the server software's licensed owner and administrators.</span></span>

<span data-ttu-id="56f0b-112">如需軟體清查記錄 Cmdlet 的詳細資訊和相關文件，請參閱[在 Windows Server 2012 R2 中管理軟體清查記錄](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11))。</span><span class="sxs-lookup"><span data-stu-id="56f0b-112">For more information and documentation about Software Inventory Logging cmdlets, see [Manage Software Inventory Logging in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).</span></span>
