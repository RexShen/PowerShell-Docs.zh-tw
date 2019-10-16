---
title: 如何將動態參數新增至提供者說明主題 |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361257"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="cd954-102">如何新增動態參數至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="cd954-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="cd954-103">本節說明如何填入提供者說明主題的**動態參數**一節。</span><span class="sxs-lookup"><span data-stu-id="cd954-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="cd954-104">*動態參數*是 Cmdlet 或函式的參數，只有在指定的條件下才可使用。</span><span class="sxs-lookup"><span data-stu-id="cd954-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="cd954-105">提供者說明主題中記載的動態參數是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函式的動態參數。</span><span class="sxs-lookup"><span data-stu-id="cd954-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="cd954-106">動態參數也可以在提供者的自訂 Cmdlet 說明中記載。</span><span class="sxs-lookup"><span data-stu-id="cd954-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="cd954-107">為提供者撰寫提供者說明和自訂 Cmdlet 說明時，請在這兩份檔中包含動態參數檔。</span><span class="sxs-lookup"><span data-stu-id="cd954-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="cd954-108">如果提供者未執行任何動態參數，提供者說明主題會包含空的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="cd954-109">新增動態參數</span><span class="sxs-lookup"><span data-stu-id="cd954-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="cd954-110">在 dll-help .xml 檔案*中的 @no__t*-1 元素內，加入 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="cd954-111">@No__t-0 元素應出現在 `Tasks` 元素之後，以及 `RelatedLinks` 元素之前。</span><span class="sxs-lookup"><span data-stu-id="cd954-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="cd954-112">例如：</span><span class="sxs-lookup"><span data-stu-id="cd954-112">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="cd954-113">如果提供者未執行任何動態參數，則 @no__t 0 元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="cd954-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="cd954-114">在 `DynamicParameters` 元素中，針對每個動態參數新增一個 `DynamicParameter` 個元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="cd954-115">例如：</span><span class="sxs-lookup"><span data-stu-id="cd954-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="cd954-116">在每個 `DynamicParameter` 元素中，加入 `Name` 和 @no__t 2 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="cd954-117">元素名稱</span><span class="sxs-lookup"><span data-stu-id="cd954-117">Element Name</span></span>|<span data-ttu-id="cd954-118">描述</span><span class="sxs-lookup"><span data-stu-id="cd954-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="cd954-119">Name</span><span class="sxs-lookup"><span data-stu-id="cd954-119">Name</span></span>|<span data-ttu-id="cd954-120">指定參數名稱。</span><span class="sxs-lookup"><span data-stu-id="cd954-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="cd954-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="cd954-121">CmdletSupported</span></span>|<span data-ttu-id="cd954-122">指定參數有效的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="cd954-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="cd954-123">輸入以逗號分隔的 Cmdlet 名稱清單。</span><span class="sxs-lookup"><span data-stu-id="cd954-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="cd954-124">例如，下列 XML 記載 Windows PowerShell FileSystem 提供者新增至 `Add-Content`、`Get-Content`、`Set-Content` Cmdlet 的 @no__t 0 動態參數。</span><span class="sxs-lookup"><span data-stu-id="cd954-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="cd954-125">在每個 `DynamicParameter` 元素中，新增一個 `Type` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="cd954-126">@No__t-0 元素是 `Name` 元素的容器，其中包含動態參數值的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="cd954-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="cd954-127">例如，下列 XML 顯示 `Encoding` 動態參數的 .NET 型別為[filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉的。</span><span class="sxs-lookup"><span data-stu-id="cd954-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. <span data-ttu-id="cd954-128">新增 `Description` 元素，其中包含動態參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="cd954-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="cd954-129">撰寫描述時，請使用[如何新增參數資訊](./how-to-add-parameter-information.md)中的所有 Cmdlet 參數所規定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="cd954-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="cd954-130">例如，下列 XML 包含 `Encoding` 動態參數的描述。</span><span class="sxs-lookup"><span data-stu-id="cd954-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. <span data-ttu-id="cd954-131">新增 `PossibleValues` 元素及其子專案。</span><span class="sxs-lookup"><span data-stu-id="cd954-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="cd954-132">這些元素一起描述動態參數的值。</span><span class="sxs-lookup"><span data-stu-id="cd954-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="cd954-133">此元素是針對列舉值所設計。</span><span class="sxs-lookup"><span data-stu-id="cd954-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="cd954-134">如果動態參數未採用值（例如，如果是具有切換參數的案例），或無法列舉值，請加入空的 `PossibleValues` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="cd954-135">下表列出並描述 `PossibleValues` 元素及其子項目。</span><span class="sxs-lookup"><span data-stu-id="cd954-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="cd954-136">元素名稱</span><span class="sxs-lookup"><span data-stu-id="cd954-136">Element Name</span></span>|<span data-ttu-id="cd954-137">描述</span><span class="sxs-lookup"><span data-stu-id="cd954-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="cd954-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="cd954-138">PossibleValues</span></span>|<span data-ttu-id="cd954-139">此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="cd954-139">This element is a container.</span></span> <span data-ttu-id="cd954-140">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="cd954-140">Its child elements are described below.</span></span> <span data-ttu-id="cd954-141">將一個 `PossibleValues` 元素新增至每個提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="cd954-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="cd954-142">元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="cd954-142">The element can be empty.</span></span>|
   |<span data-ttu-id="cd954-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="cd954-143">PossibleValue</span></span>|<span data-ttu-id="cd954-144">此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="cd954-144">This element is a container.</span></span> <span data-ttu-id="cd954-145">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="cd954-145">Its child elements are described below.</span></span> <span data-ttu-id="cd954-146">為動態參數的每個值新增一個 `PossibleValue` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="cd954-147">值</span><span class="sxs-lookup"><span data-stu-id="cd954-147">Value</span></span>|<span data-ttu-id="cd954-148">指定值名稱。</span><span class="sxs-lookup"><span data-stu-id="cd954-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="cd954-149">描述</span><span class="sxs-lookup"><span data-stu-id="cd954-149">Description</span></span>|<span data-ttu-id="cd954-150">此元素包含 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-150">This element contains a `Para` element.</span></span> <span data-ttu-id="cd954-151">@No__t-0 元素中的文字描述在 `Value` 元素中命名的值。</span><span class="sxs-lookup"><span data-stu-id="cd954-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="cd954-152">例如，下列 XML 會顯示 `Encoding` 動態參數的一個 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="cd954-153">範例</span><span class="sxs-lookup"><span data-stu-id="cd954-153">Example</span></span>

<span data-ttu-id="cd954-154">下列範例顯示 `Encoding` 動態參數的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="cd954-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```