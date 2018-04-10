---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,設定
ms.openlocfilehash: ada4fcc0beb3eb74b099f221762341abbf2c3b4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="a1217-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="a1217-102">New-TemporaryFile</span></span>
<span data-ttu-id="a1217-103">有時候在您的指令碼中，您必須建立暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="a1217-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="a1217-104">您可以使用 **New-TemporaryFile**Cmdlet 輕鬆執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="a1217-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="a1217-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="a1217-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="a1217-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="a1217-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="a1217-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="a1217-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>