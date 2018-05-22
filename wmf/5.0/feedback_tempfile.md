---
ms.date: 06/12/2017
keywords: wmf,powershell,設定
ms.openlocfilehash: 08f431c27cd0ee769518b5246af2fa95aa499d54
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="new-temporaryfile"></a><span data-ttu-id="515a3-102">New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="515a3-102">New-TemporaryFile</span></span>
<span data-ttu-id="515a3-103">有時候在您的指令碼中，您必須建立暫存檔案。</span><span class="sxs-lookup"><span data-stu-id="515a3-103">Sometimes in your scripts, you must create a temporary file.</span></span> <span data-ttu-id="515a3-104">您可以使用 **New-TemporaryFile**Cmdlet 輕鬆執行這項操作︰</span><span class="sxs-lookup"><span data-stu-id="515a3-104">You can easily do this with the **New-TemporaryFile** cmdlet:</span></span>

<span data-ttu-id="515a3-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span><span class="sxs-lookup"><span data-stu-id="515a3-105">PS C:\\&gt; $tempFile = New-TemporaryFile</span></span>

<span data-ttu-id="515a3-106">PS C:\\&gt; $tempFile.FullName</span><span class="sxs-lookup"><span data-stu-id="515a3-106">PS C:\\&gt; $tempFile.FullName</span></span>

<span data-ttu-id="515a3-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span><span class="sxs-lookup"><span data-stu-id="515a3-107">C:\\Users\\slee\\AppData\\Local\\Temp\\tmp375.tmp</span></span>
