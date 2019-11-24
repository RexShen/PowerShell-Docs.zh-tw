---
title: 如何將範例新增至 Cmdlet 說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368107"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="7d8c0-102">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="7d8c0-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="7d8c0-103">Cmdlet 說明中的範例須知事項</span><span class="sxs-lookup"><span data-stu-id="7d8c0-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="7d8c0-104">列出命令中的所有參數名稱，即使參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="7d8c0-105">這可協助使用者輕鬆地解讀命令。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="7d8c0-106">請避免使用別名和部分參數名稱，即使它們在 Windows PowerShell®中工作也是一樣。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="7d8c0-107">在範例描述中，為命令的結構說明有理數。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="7d8c0-108">說明為何選擇特定的參數和值，以及如何使用變數。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="7d8c0-109">如果命令使用運算式，請詳細說明它們。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="7d8c0-110">如果命令使用物件的屬性和方法，特別是不會出現在預設顯示中的屬性，請使用此範例做為商機，告訴使用者該物件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="7d8c0-111">顯示範例的說明視圖</span><span class="sxs-lookup"><span data-stu-id="7d8c0-111">Help Views that Display Examples</span></span>

<span data-ttu-id="7d8c0-112">範例只會出現在 Cmdlet 說明的詳細和完整的觀點。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="7d8c0-113">新增範例節點</span><span class="sxs-lookup"><span data-stu-id="7d8c0-113">Adding an Examples Node</span></span>

<span data-ttu-id="7d8c0-114">下列 XML 顯示如何新增包含單一範例節點的範例節點。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="7d8c0-115">針對您想要包含在主題中的每個範例，新增其他範例節點。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="7d8c0-116">加入範例標題</span><span class="sxs-lookup"><span data-stu-id="7d8c0-116">Adding an Example Title</span></span>

<span data-ttu-id="7d8c0-117">下列 XML 示範如何新增範例的標題。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="7d8c0-118">標題是用來設定除了其他範例以外的範例。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="7d8c0-119">Windows PowerShell®使用包含連續範例號碼的標準標頭。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="7d8c0-120">新增前面的字元</span><span class="sxs-lookup"><span data-stu-id="7d8c0-120">Adding Preceding Characters</span></span>

<span data-ttu-id="7d8c0-121">下列 XML 顯示如何新增緊接在範例命令之前顯示的字元（例如 Windows PowerShell 提示）（不含任何空格）。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="7d8c0-122">Windows PowerShell®使用 Windows PowerShell 命令提示字元： C:\PS >。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="7d8c0-123">新增命令</span><span class="sxs-lookup"><span data-stu-id="7d8c0-123">Adding the Command</span></span>

<span data-ttu-id="7d8c0-124">下列 XML 顯示如何新增範例的實際命令。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="7d8c0-125">新增命令時，請輸入 Cmdlet 和參數的完整名稱（請勿使用 alias）。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="7d8c0-126">此外，盡可能使用小寫字元。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="7d8c0-127">新增描述</span><span class="sxs-lookup"><span data-stu-id="7d8c0-127">Adding a Description</span></span>

<span data-ttu-id="7d8c0-128">下列 XML 顯示如何新增範例的描述。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="7d8c0-129">Windows PowerShell®會使用一組 \<maml：段落 > 標記來進行描述，雖然可以使用多個 \<maml：段落 > 標記。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="7d8c0-130">新增範例輸出</span><span class="sxs-lookup"><span data-stu-id="7d8c0-130">Adding Example Output</span></span>

<span data-ttu-id="7d8c0-131">下列 XML 顯示如何新增命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="7d8c0-132">命令結果資訊是選擇性的，但在某些情況下，示範使用特定參數的效果會很有説明。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="7d8c0-133">Windows PowerShell®使用兩組空白 \<maml：段落 > 標記來分隔命令輸出與命令。</span><span class="sxs-lookup"><span data-stu-id="7d8c0-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```