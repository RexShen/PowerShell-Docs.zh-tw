---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "wmf,powershell,設定"
ms.openlocfilehash: 8d5f8cc8c85d584b195483e464e878857629a78e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2017
---
# <a name="clipboard-cmdlets"></a><span data-ttu-id="dfcf4-102">剪貼簿 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="dfcf4-102">Clipboard cmdlets</span></span>
<span data-ttu-id="dfcf4-103">**Get-Clipboard** 和 **Set-Clipboard** 讓您更輕鬆地與 Windows PowerShell 工作階段來回傳送內容。</span><span class="sxs-lookup"><span data-stu-id="dfcf4-103">**Get-Clipboard** and **Set-Clipboard** make it easier for you to transfer content to and from a Windows PowerShell session.</span></span> <span data-ttu-id="dfcf4-104">例如，如果使用 Windows 檔案總管將這三個檔案複製到剪貼簿 (例如，選取檔案後按下 `ctrl-c`)，即可輕鬆地以檔案清單的方式存取剪貼簿內容︰</span><span class="sxs-lookup"><span data-stu-id="dfcf4-104">For example, if you use Windows Explorer to copy three files to the clipboard (by selecting them and pressing `ctrl-c`, for example), you can then easily access the contents of the clipboard as a list of files:</span></span>

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


<span data-ttu-id="dfcf4-105">剪貼簿 Cmdlet 支援影像、音訊檔、檔案清單和文字。</span><span class="sxs-lookup"><span data-stu-id="dfcf4-105">The Clipboard cmdlets support images, audio files, file lists, and text.</span></span>

