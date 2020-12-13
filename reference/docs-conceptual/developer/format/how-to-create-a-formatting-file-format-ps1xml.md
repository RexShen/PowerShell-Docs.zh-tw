---
ms.date: 09/13/2016
ms.topic: reference
title: 如何建立格式設定檔案 (.format.ps1xml)
description: 如何建立格式設定檔案 (.format.ps1xml)
ms.openlocfilehash: 5bbc1ba40bfccf13636abc0f0751938aa724b761
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652002"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="8770f-103">如何建立格式設定檔案 (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="8770f-103">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="8770f-104">本主題說明如何建立 ( # B0 xml) 的格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="8770f-104">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="8770f-105">您也可以建立 Windows PowerShell 所提供的其中一個檔案的複本，以建立格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="8770f-105">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="8770f-106">如果您複製現有的檔案，請刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。</span><span class="sxs-lookup"><span data-stu-id="8770f-106">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="8770f-107">建立 .format.ps1的 xml 檔。</span><span class="sxs-lookup"><span data-stu-id="8770f-107">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="8770f-108">使用記事本之類的文字編輯器建立文字檔 ( .txt) 。</span><span class="sxs-lookup"><span data-stu-id="8770f-108">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="8770f-109">將下列幾行複製到格式設定檔中。</span><span class="sxs-lookup"><span data-stu-id="8770f-109">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="8770f-110">這些 `<Configuration></Configuration>` 標記會定義根 `Configuration` 節點。</span><span class="sxs-lookup"><span data-stu-id="8770f-110">The `<Configuration></Configuration>` tags define the root `Configuration` node.</span></span> <span data-ttu-id="8770f-111">所有其他的 XML 標記將會包含在此節點內。</span><span class="sxs-lookup"><span data-stu-id="8770f-111">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="8770f-112">這些 `<ViewDefinitions></ViewDefinitions>` 標記會定義 `ViewDefinitions` 節點。</span><span class="sxs-lookup"><span data-stu-id="8770f-112">The `<ViewDefinitions></ViewDefinitions>` tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="8770f-113">所有視圖都是在此節點中定義。</span><span class="sxs-lookup"><span data-stu-id="8770f-113">All views are defined within this node.</span></span>

3. <span data-ttu-id="8770f-114">將檔案儲存到 Windows PowerShell 安裝資料夾、模組資料夾或模組資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="8770f-114">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="8770f-115">當您儲存檔案時，請使用下列名稱格式：  `MyFile.format.ps1xml` 。</span><span class="sxs-lookup"><span data-stu-id="8770f-115">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="8770f-116">格式化檔案必須使用 `.format.ps1xml` 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="8770f-116">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="8770f-117">您現在已準備好將視圖新增至格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="8770f-117">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="8770f-118">在格式化檔案中可定義的視圖數目沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="8770f-118">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="8770f-119">您可以為每個物件、相同物件的多個視圖，或多個物件使用的單一視圖，新增單一視圖。</span><span class="sxs-lookup"><span data-stu-id="8770f-119">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="8770f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8770f-120">See Also</span></span>

[<span data-ttu-id="8770f-121">寫入 Windows PowerShell 格式和類型檔案</span><span class="sxs-lookup"><span data-stu-id="8770f-121">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
