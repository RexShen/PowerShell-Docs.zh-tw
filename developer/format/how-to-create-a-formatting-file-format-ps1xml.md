---
title: 如何建立格式檔案 (。 format.ps1xml) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065492"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="4fe47-102">如何建立格式設定檔案 (.format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="4fe47-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="4fe47-103">本主題描述如何建立格式檔案 (。 format.ps1xml)。</span><span class="sxs-lookup"><span data-stu-id="4fe47-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="4fe47-104">您也可以藉由其中一個 Windows PowerShell 所提供的檔案複製建立格式化的檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe47-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="4fe47-105">如果您建立一份現有的檔案時，刪除現有的數位簽章，並將您自己的簽章新增至新的檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe47-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="4fe47-106">若要建立。 format.ps1xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe47-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="4fe47-107">建立文字檔 (.txt) 使用文字編輯器例如記事本。</span><span class="sxs-lookup"><span data-stu-id="4fe47-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="4fe47-108">將下列幾行複製到的格式化檔案中。</span><span class="sxs-lookup"><span data-stu-id="4fe47-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="4fe47-109">\<組態 >\</Configuration > 標籤會定義根`Configuration`節點。</span><span class="sxs-lookup"><span data-stu-id="4fe47-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="4fe47-110">所有其他的 XML 標記會住此節點。</span><span class="sxs-lookup"><span data-stu-id="4fe47-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="4fe47-111"><ViewDefinitions> </ViewDefinitions>標籤會定義`ViewDefinitions`節點。</span><span class="sxs-lookup"><span data-stu-id="4fe47-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="4fe47-112">此節點內定義所有的檢視。</span><span class="sxs-lookup"><span data-stu-id="4fe47-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="4fe47-113">Windows PowerShell 安裝資料夾、 您的模組資料夾，或模組資料夾的子資料夾，請儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe47-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="4fe47-114">當您儲存檔案時，請使用下列名稱格式： `MyFile.format.ps1xml`。</span><span class="sxs-lookup"><span data-stu-id="4fe47-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="4fe47-115">格式檔案必須使用`.format.ps1xml`延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4fe47-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="4fe47-116">您現在已準備好將檢視加入至格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="4fe47-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="4fe47-117">可以格式化檔案中定義的檢視表的數目沒有限制。</span><span class="sxs-lookup"><span data-stu-id="4fe47-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="4fe47-118">您可以新增每個物件、 多個檢視，針對相同的物件或單一檢視，可由多個物件的單一檢視。</span><span class="sxs-lookup"><span data-stu-id="4fe47-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fe47-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fe47-119">See Also</span></span>

[<span data-ttu-id="4fe47-120">撰寫 Windows PowerShell 格式和類型的檔案</span><span class="sxs-lookup"><span data-stu-id="4fe47-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
