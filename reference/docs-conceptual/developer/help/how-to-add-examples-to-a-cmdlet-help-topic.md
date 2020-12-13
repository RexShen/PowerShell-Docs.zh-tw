---
ms.date: 09/12/2016
ms.topic: reference
title: 如何新增範例至 Cmdlet 說明主題
description: 如何新增範例至 Cmdlet 說明主題
ms.openlocfilehash: 6b72e29c93740b7953d9b68fc8e68c02eb2f4dee
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654721"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="d4219-103">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="d4219-103">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="d4219-104">Cmdlet 說明中的範例須知事項</span><span class="sxs-lookup"><span data-stu-id="d4219-104">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="d4219-105">列出命令中的所有參數名稱，即使參數名稱是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="d4219-105">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="d4219-106">這可協助使用者輕鬆地解讀命令。</span><span class="sxs-lookup"><span data-stu-id="d4219-106">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="d4219-107">請避免使用別名和部分參數名稱，即使它們在 PowerShell 中運作也一樣。</span><span class="sxs-lookup"><span data-stu-id="d4219-107">Avoid aliases and partial parameter names, even though they work in PowerShell.</span></span>

- <span data-ttu-id="d4219-108">在 [範例描述] 中，說明命令的有理數。</span><span class="sxs-lookup"><span data-stu-id="d4219-108">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="d4219-109">說明您為何選擇特定參數和值，以及如何使用變數。</span><span class="sxs-lookup"><span data-stu-id="d4219-109">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="d4219-110">如果命令使用運算式，請詳細說明它們。</span><span class="sxs-lookup"><span data-stu-id="d4219-110">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="d4219-111">如果命令使用物件的屬性和方法，尤其是未出現在預設顯示中的屬性，請使用此範例做為機會告知使用者物件。</span><span class="sxs-lookup"><span data-stu-id="d4219-111">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="d4219-112">協助視圖顯示範例</span><span class="sxs-lookup"><span data-stu-id="d4219-112">Help Views that Display Examples</span></span>

<span data-ttu-id="d4219-113">範例只會顯示在 [Cmdlet 說明] 的詳細和完整視圖中。</span><span class="sxs-lookup"><span data-stu-id="d4219-113">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="d4219-114">新增範例節點</span><span class="sxs-lookup"><span data-stu-id="d4219-114">Adding an Examples Node</span></span>

<span data-ttu-id="d4219-115">下列 XML 說明如何加入包含單一 **範例** 節點的 **範例** 節點。</span><span class="sxs-lookup"><span data-stu-id="d4219-115">The following XML shows how to add an **Examples** node that contains a single **Example** node.</span></span> <span data-ttu-id="d4219-116">針對您想要包含在主題中的每個範例，新增其他範例節點。</span><span class="sxs-lookup"><span data-stu-id="d4219-116">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="d4219-117">新增範例標題</span><span class="sxs-lookup"><span data-stu-id="d4219-117">Adding an Example Title</span></span>

<span data-ttu-id="d4219-118">下列 XML 說明如何加入範例的 **標題** 。</span><span class="sxs-lookup"><span data-stu-id="d4219-118">The following XML shows how to add a **title** for the example.</span></span> <span data-ttu-id="d4219-119">**標題** 可用來將範例與其他範例分開。</span><span class="sxs-lookup"><span data-stu-id="d4219-119">The **title** is used to set the example apart from other examples.</span></span> <span data-ttu-id="d4219-120">PowerShell 會使用包含連續範例編號的標準標頭。</span><span class="sxs-lookup"><span data-stu-id="d4219-120">PowerShell uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="d4219-121">加入前面的字元</span><span class="sxs-lookup"><span data-stu-id="d4219-121">Adding Preceding Characters</span></span>

<span data-ttu-id="d4219-122">下列 XML 會示範如何新增 Windows PowerShell 提示字元，而這些字元會立即顯示在範例命令 (之前，不) 任何中間的空格。</span><span class="sxs-lookup"><span data-stu-id="d4219-122">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="d4219-123">PowerShell 會使用 Windows PowerShell 提示： `C:\PS>` 。</span><span class="sxs-lookup"><span data-stu-id="d4219-123">PowerShell uses the Windows PowerShell prompt: `C:\PS>`.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="d4219-124">新增命令</span><span class="sxs-lookup"><span data-stu-id="d4219-124">Adding the Command</span></span>

<span data-ttu-id="d4219-125">下列 XML 說明如何新增範例的實際命令。</span><span class="sxs-lookup"><span data-stu-id="d4219-125">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="d4219-126">新增命令時，請輸入完整名稱 (不要使用 Cmdlet 和參數的別名) 。</span><span class="sxs-lookup"><span data-stu-id="d4219-126">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="d4219-127">此外，請盡可能使用小寫字元。</span><span class="sxs-lookup"><span data-stu-id="d4219-127">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="d4219-128">新增描述</span><span class="sxs-lookup"><span data-stu-id="d4219-128">Adding a Description</span></span>

<span data-ttu-id="d4219-129">下列 XML 說明如何加入範例的描述。</span><span class="sxs-lookup"><span data-stu-id="d4219-129">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="d4219-130">PowerShell `<maml:para>` 會針對描述使用一組標記，即使可以使用多個標記也是一樣 `<maml:para>` 。</span><span class="sxs-lookup"><span data-stu-id="d4219-130">PowerShell uses a single set of `<maml:para>` tags for the description, even though multiple `<maml:para>` tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="d4219-131">新增範例輸出</span><span class="sxs-lookup"><span data-stu-id="d4219-131">Adding Example Output</span></span>

<span data-ttu-id="d4219-132">下列 XML 說明如何新增命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="d4219-132">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="d4219-133">命令結果資訊是選擇性的，但在某些情況下，示範使用特定參數的效果會很有説明。</span><span class="sxs-lookup"><span data-stu-id="d4219-133">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span>
<span data-ttu-id="d4219-134">PowerShell 會使用兩組空白 `<maml:para>` 標記來分隔命令輸出與命令。</span><span class="sxs-lookup"><span data-stu-id="d4219-134">PowerShell uses two sets of blank `<maml:para>` tags to separate the command output from the command.</span></span>

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
