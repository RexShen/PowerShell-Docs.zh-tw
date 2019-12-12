---
title: 如何建立格式檔案（. 格式. types.ps1xml） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363617"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="9acf6-102">如何建立格式設定檔案 (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="9acf6-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="9acf6-103">本主題說明如何建立格式檔案（. 格式. types.ps1xml）。</span><span class="sxs-lookup"><span data-stu-id="9acf6-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="9acf6-104">您也可以藉由複製 Windows PowerShell 所提供的其中一個檔案，建立格式檔案。</span><span class="sxs-lookup"><span data-stu-id="9acf6-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="9acf6-105">如果您複製現有的檔案，請刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。</span><span class="sxs-lookup"><span data-stu-id="9acf6-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="9acf6-106">建立 types.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="9acf6-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="9acf6-107">使用文字編輯器（如 [記事本]）建立文字檔（.txt）。</span><span class="sxs-lookup"><span data-stu-id="9acf6-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="9acf6-108">將下列幾行複製到格式檔案中。</span><span class="sxs-lookup"><span data-stu-id="9acf6-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="9acf6-109">\<Configuration >\</組態 > 標記會定義根 `Configuration` 節點。</span><span class="sxs-lookup"><span data-stu-id="9acf6-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="9acf6-110">所有其他的 XML 標記都會放在這個節點內。</span><span class="sxs-lookup"><span data-stu-id="9acf6-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="9acf6-111">這些<ViewDefinitions></ViewDefinitions>標記會定義 `ViewDefinitions` 節點。</span><span class="sxs-lookup"><span data-stu-id="9acf6-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="9acf6-112">所有的視圖都會在此節點中定義。</span><span class="sxs-lookup"><span data-stu-id="9acf6-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="9acf6-113">將檔案儲存至 Windows PowerShell 安裝資料夾、模組資料夾或模組資料夾的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="9acf6-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="9acf6-114">當您儲存檔案時，請使用下列名稱格式： `MyFile.format.ps1xml`。</span><span class="sxs-lookup"><span data-stu-id="9acf6-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="9acf6-115">格式化檔案必須使用 `.format.ps1xml` 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9acf6-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="9acf6-116">您現在已準備好將 views 新增至格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9acf6-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="9acf6-117">可以在格式化檔案中定義的視圖數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="9acf6-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="9acf6-118">您可以為每個物件、多個相同物件的視圖，或多個物件所使用的單一視圖加入單一視圖。</span><span class="sxs-lookup"><span data-stu-id="9acf6-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="9acf6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9acf6-119">See Also</span></span>

[<span data-ttu-id="9acf6-120">撰寫 Windows PowerShell 格式化和類型檔案</span><span class="sxs-lookup"><span data-stu-id="9acf6-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
