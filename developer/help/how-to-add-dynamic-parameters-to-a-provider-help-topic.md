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
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737591"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="15965-102">如何新增動態參數至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="15965-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="15965-103">本節說明如何填入提供者說明主題的**動態參數**一節。</span><span class="sxs-lookup"><span data-stu-id="15965-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="15965-104">*動態參數*是 Cmdlet 或函式的參數，只有在指定的條件下才可使用。</span><span class="sxs-lookup"><span data-stu-id="15965-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="15965-105">提供者說明主題中記載的動態參數是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函式的動態參數。</span><span class="sxs-lookup"><span data-stu-id="15965-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="15965-106">動態參數也可以在提供者的自訂 Cmdlet 說明中記載。</span><span class="sxs-lookup"><span data-stu-id="15965-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="15965-107">為提供者撰寫提供者說明和自訂 Cmdlet 說明時，請在這兩份檔中包含動態參數檔。</span><span class="sxs-lookup"><span data-stu-id="15965-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="15965-108">如需自訂 Cmdlet 說明的詳細資訊，請參閱[撰寫提供者的 Windows PowerShell 自訂 Cmdlet](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)說明。</span><span class="sxs-lookup"><span data-stu-id="15965-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="15965-109">如果提供者未執行任何動態參數，提供者說明主題會包含空`DynamicParameters`的元素。</span><span class="sxs-lookup"><span data-stu-id="15965-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="15965-110">新增動態參數</span><span class="sxs-lookup"><span data-stu-id="15965-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="15965-111">在 dll-help .xml `providerHelp` *檔案的專案*中，新增`DynamicParameters`專案。</span><span class="sxs-lookup"><span data-stu-id="15965-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="15965-112">元素應出現在`Tasks`元素之後和專案之前`RelatedLinks`。 `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="15965-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="15965-113">例如：</span><span class="sxs-lookup"><span data-stu-id="15965-113">For example:</span></span>

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

   <span data-ttu-id="15965-114">如果提供者未執行任何動態參數，元素可以`DynamicParameters`是空的。</span><span class="sxs-lookup"><span data-stu-id="15965-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="15965-115">在專案中，針對每個動態參數`DynamicParameter`加入元素。 `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="15965-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="15965-116">例如：</span><span class="sxs-lookup"><span data-stu-id="15965-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="15965-117">在每`DynamicParameter`個專案中， `Name`加入`CmdletSupported` and 元素。</span><span class="sxs-lookup"><span data-stu-id="15965-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="15965-118">元素名稱</span><span class="sxs-lookup"><span data-stu-id="15965-118">Element Name</span></span>|<span data-ttu-id="15965-119">說明</span><span class="sxs-lookup"><span data-stu-id="15965-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="15965-120">名稱</span><span class="sxs-lookup"><span data-stu-id="15965-120">Name</span></span>|<span data-ttu-id="15965-121">指定參數名稱。</span><span class="sxs-lookup"><span data-stu-id="15965-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="15965-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="15965-122">CmdletSupported</span></span>|<span data-ttu-id="15965-123">指定參數有效的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="15965-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="15965-124">輸入以逗號分隔的 Cmdlet 名稱清單。</span><span class="sxs-lookup"><span data-stu-id="15965-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="15965-125">例如，下列 XML 記載 Windows PowerShell FileSystem `Encoding`提供者新增`Add-Content`至、 `Get-Content`、 `Set-Content` Cmdlet 的動態參數。</span><span class="sxs-lookup"><span data-stu-id="15965-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="15965-126">在每`DynamicParameter`個專案中， `Type`新增元素。</span><span class="sxs-lookup"><span data-stu-id="15965-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="15965-127">元素是`Name`元素的容器，其中包含動態參數值的 .net 類型。 `Type`</span><span class="sxs-lookup"><span data-stu-id="15965-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="15965-128">例如，下列 XML 會顯示`Encoding`動態參數的 .net 型別為[filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉的。</span><span class="sxs-lookup"><span data-stu-id="15965-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="15965-129">`Description`加入元素，其中包含動態參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="15965-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="15965-130">撰寫描述時，請使用[如何新增參數資訊](./how-to-add-parameter-information.md)中的所有 Cmdlet 參數所規定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="15965-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="15965-131">例如，下列 XML 包含`Encoding`動態參數的描述。</span><span class="sxs-lookup"><span data-stu-id="15965-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="15965-132">`PossibleValues`加入元素及其子專案。</span><span class="sxs-lookup"><span data-stu-id="15965-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="15965-133">這些元素一起描述動態參數的值。</span><span class="sxs-lookup"><span data-stu-id="15965-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="15965-134">此元素是針對列舉值所設計。</span><span class="sxs-lookup"><span data-stu-id="15965-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="15965-135">如果動態參數未採用值（例如，如果是具有切換參數的案例），或無法列舉值，請加入空`PossibleValues`的元素。</span><span class="sxs-lookup"><span data-stu-id="15965-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="15965-136">下表列出並描述`PossibleValues`元素及其子項目。</span><span class="sxs-lookup"><span data-stu-id="15965-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="15965-137">元素名稱</span><span class="sxs-lookup"><span data-stu-id="15965-137">Element Name</span></span>|<span data-ttu-id="15965-138">描述</span><span class="sxs-lookup"><span data-stu-id="15965-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="15965-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="15965-139">PossibleValues</span></span>|<span data-ttu-id="15965-140">此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="15965-140">This element is a container.</span></span> <span data-ttu-id="15965-141">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="15965-141">Its child elements are described below.</span></span> <span data-ttu-id="15965-142">將一個`PossibleValues`元素新增至每個提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="15965-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="15965-143">元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="15965-143">The element can be empty.</span></span>|
   |<span data-ttu-id="15965-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="15965-144">PossibleValue</span></span>|<span data-ttu-id="15965-145">此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="15965-145">This element is a container.</span></span> <span data-ttu-id="15965-146">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="15965-146">Its child elements are described below.</span></span> <span data-ttu-id="15965-147">為動態`PossibleValue`參數的每個值新增一個元素。</span><span class="sxs-lookup"><span data-stu-id="15965-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="15965-148">值</span><span class="sxs-lookup"><span data-stu-id="15965-148">Value</span></span>|<span data-ttu-id="15965-149">指定值名稱。</span><span class="sxs-lookup"><span data-stu-id="15965-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="15965-150">描述</span><span class="sxs-lookup"><span data-stu-id="15965-150">Description</span></span>|<span data-ttu-id="15965-151">此元素包含`Para`元素。</span><span class="sxs-lookup"><span data-stu-id="15965-151">This element contains a `Para` element.</span></span> <span data-ttu-id="15965-152">`Para`元素中的文字描述`Value`元素中所命名的值。</span><span class="sxs-lookup"><span data-stu-id="15965-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="15965-153">例如，下列 XML 會顯示`PossibleValue` `Encoding`動態參數的一個元素。</span><span class="sxs-lookup"><span data-stu-id="15965-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="15965-154">範例</span><span class="sxs-lookup"><span data-stu-id="15965-154">Example</span></span>

<span data-ttu-id="15965-155">下列範例顯示`Encoding`動態參數`DynamicParameters`的元素。</span><span class="sxs-lookup"><span data-stu-id="15965-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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