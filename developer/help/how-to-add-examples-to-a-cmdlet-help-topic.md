---
title: 如何新增 Cmdlet 說明主題的範例 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855120"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="3fe14-102">如何新增範例至 Cmdlet 說明主題</span><span class="sxs-lookup"><span data-stu-id="3fe14-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="3fe14-103">關於指令程式說明中的範例應該知道的事項</span><span class="sxs-lookup"><span data-stu-id="3fe14-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="3fe14-104">即使是選擇性的參數名稱，請列出的參數名稱，在命令中，所有選項。</span><span class="sxs-lookup"><span data-stu-id="3fe14-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="3fe14-105">這可協助使用者輕鬆地解譯命令。</span><span class="sxs-lookup"><span data-stu-id="3fe14-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="3fe14-106">避免別名和部分參數名稱，即使它們在 Windows PowerShell® 中運作。</span><span class="sxs-lookup"><span data-stu-id="3fe14-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="3fe14-107">在範例描述，說明 rational 建構的命令。</span><span class="sxs-lookup"><span data-stu-id="3fe14-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="3fe14-108">說明您為何要選擇特定的參數和值，以及您如何使用變數。</span><span class="sxs-lookup"><span data-stu-id="3fe14-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="3fe14-109">如果此命令會使用運算式，它們會詳細說明。</span><span class="sxs-lookup"><span data-stu-id="3fe14-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="3fe14-110">如果此命令會使用物件的屬性和方法，特別是不會出現在顯示的預設值的屬性會使用範例，因為有機會告訴使用者關於物件。</span><span class="sxs-lookup"><span data-stu-id="3fe14-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="3fe14-111">顯示範例的說明檢視</span><span class="sxs-lookup"><span data-stu-id="3fe14-111">Help Views that Display Examples</span></span>

<span data-ttu-id="3fe14-112">範例只會出現在 cmdlet 說明的詳細資料和完整檢視。</span><span class="sxs-lookup"><span data-stu-id="3fe14-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="3fe14-113">新增範例節點</span><span class="sxs-lookup"><span data-stu-id="3fe14-113">Adding an Examples Node</span></span>

<span data-ttu-id="3fe14-114">下列 XML 示範如何新增的範例節點包含單一的範例節點。</span><span class="sxs-lookup"><span data-stu-id="3fe14-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="3fe14-115">新增您想要包含在本主題中的每個範例的其他範例節點。</span><span class="sxs-lookup"><span data-stu-id="3fe14-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="3fe14-116">新增範例標題</span><span class="sxs-lookup"><span data-stu-id="3fe14-116">Adding an Example Title</span></span>

<span data-ttu-id="3fe14-117">下列 XML 示範如何加入標題的範例。</span><span class="sxs-lookup"><span data-stu-id="3fe14-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="3fe14-118">標題用來設定範例中的，除了其他範例。</span><span class="sxs-lookup"><span data-stu-id="3fe14-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="3fe14-119">Windows PowerShell® 會使用標準的標頭包含循序的範例編號。</span><span class="sxs-lookup"><span data-stu-id="3fe14-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="3fe14-120">新增前置字元</span><span class="sxs-lookup"><span data-stu-id="3fe14-120">Adding Preceding Characters</span></span>

<span data-ttu-id="3fe14-121">下列 XML 示範如何加入字元，例如 Windows PowerShell 提示字元中，顯示之前範例命令 （不含任何中間的空格）。</span><span class="sxs-lookup"><span data-stu-id="3fe14-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="3fe14-122">Windows PowerShell® 會使用 Windows PowerShell 命令提示字元：C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="3fe14-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="3fe14-123">加入命令</span><span class="sxs-lookup"><span data-stu-id="3fe14-123">Adding the Command</span></span>

<span data-ttu-id="3fe14-124">下列 XML 示範如何加入實際範例的命令。</span><span class="sxs-lookup"><span data-stu-id="3fe14-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="3fe14-125">當加入命令，輸入完整名稱 （請勿使用別名） 的 cmdlet 和參數。</span><span class="sxs-lookup"><span data-stu-id="3fe14-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="3fe14-126">此外，使用盡可能的小寫字元。</span><span class="sxs-lookup"><span data-stu-id="3fe14-126">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="3fe14-127">加入描述</span><span class="sxs-lookup"><span data-stu-id="3fe14-127">Adding a Description</span></span>

<span data-ttu-id="3fe14-128">下列 XML 示範如何加入範例的描述。</span><span class="sxs-lookup"><span data-stu-id="3fe14-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="3fe14-129">Windows PowerShell® 會使用一組\<: para><maml: > 標記描述，即使多個\<: para><maml: > 可以使用標記。</span><span class="sxs-lookup"><span data-stu-id="3fe14-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="3fe14-130">新增範例輸出</span><span class="sxs-lookup"><span data-stu-id="3fe14-130">Adding Example Output</span></span>

<span data-ttu-id="3fe14-131">下列 XML 示範如何新增命令的輸出。</span><span class="sxs-lookup"><span data-stu-id="3fe14-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="3fe14-132">命令結果的資訊是選擇性的但在某些情況下很有幫助示範使用特定參數的效果。</span><span class="sxs-lookup"><span data-stu-id="3fe14-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="3fe14-133">Windows PowerShell® 會使用兩組空白\<: para><maml: > 標記來分隔命令的命令輸出。</span><span class="sxs-lookup"><span data-stu-id="3fe14-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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