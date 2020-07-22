---
title: 如何新增動態參數至提供者說明主題
ms.date: 09/13/2016
ms.openlocfilehash: ddf964292ee7bf477767a2ca17c717aef84bad51
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893453"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="f85bc-102">如何新增動態參數至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="f85bc-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="f85bc-103">本節說明如何填入提供者說明主題的**動態參數**一節。</span><span class="sxs-lookup"><span data-stu-id="f85bc-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="f85bc-104">*動態參數*是 Cmdlet 或函式的參數，只有在指定的條件下才可使用。</span><span class="sxs-lookup"><span data-stu-id="f85bc-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="f85bc-105">提供者說明主題中記載的動態參數是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函式的動態參數。</span><span class="sxs-lookup"><span data-stu-id="f85bc-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="f85bc-106">動態參數也可以在提供者的自訂 Cmdlet 說明中記載。</span><span class="sxs-lookup"><span data-stu-id="f85bc-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="f85bc-107">為提供者撰寫提供者說明和自訂 Cmdlet 說明時，請在這兩份檔中包含動態參數檔。</span><span class="sxs-lookup"><span data-stu-id="f85bc-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="f85bc-108">如果提供者未執行任何動態參數，提供者說明主題會包含空的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="f85bc-109">新增動態參數</span><span class="sxs-lookup"><span data-stu-id="f85bc-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="f85bc-110">在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-110">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="f85bc-111">`DynamicParameters`元素應出現在元素之後 `Tasks` 和專案之前 `RelatedLinks` 。</span><span class="sxs-lookup"><span data-stu-id="f85bc-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="f85bc-112">例如：</span><span class="sxs-lookup"><span data-stu-id="f85bc-112">For example:</span></span>

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

   <span data-ttu-id="f85bc-113">如果提供者未執行任何動態參數， `DynamicParameters` 元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="f85bc-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="f85bc-114">在專案中， `DynamicParameters` 針對每個動態參數加入 `DynamicParameter` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="f85bc-115">例如：</span><span class="sxs-lookup"><span data-stu-id="f85bc-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="f85bc-116">在每個專案中 `DynamicParameter` ，加入 `Name` and `CmdletSupported` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="f85bc-117">名稱-指定參數名稱</span><span class="sxs-lookup"><span data-stu-id="f85bc-117">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="f85bc-118">CmdletSupported-指定參數有效的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f85bc-118">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="f85bc-119">輸入以逗號分隔的 Cmdlet 名稱清單。</span><span class="sxs-lookup"><span data-stu-id="f85bc-119">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="f85bc-120">例如，下列 XML 記載 `Encoding` Windows PowerShell FileSystem 提供者新增至 `Add-Content` 、 `Get-Content` 、Cmdlet 的動態參數 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="f85bc-120">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="f85bc-121">在每個專案中 `DynamicParameter` ，新增 `Type` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-121">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="f85bc-122">`Type`元素是元素的容器， `Name` 其中包含動態參數值的 .net 類型。</span><span class="sxs-lookup"><span data-stu-id="f85bc-122">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="f85bc-123">例如，下列 XML 顯示動態參數的 .NET 類型 `Encoding` 為[filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉。</span><span class="sxs-lookup"><span data-stu-id="f85bc-123">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="f85bc-124">加入 `Description` 元素，其中包含動態參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="f85bc-124">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="f85bc-125">撰寫描述時，請使用[如何新增參數資訊](./how-to-add-parameter-information.md)中的所有 Cmdlet 參數所規定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="f85bc-125">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="f85bc-126">例如，下列 XML 包含 `Encoding` 動態參數的描述。</span><span class="sxs-lookup"><span data-stu-id="f85bc-126">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="f85bc-127">加入 `PossibleValues` 元素及其子專案。</span><span class="sxs-lookup"><span data-stu-id="f85bc-127">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="f85bc-128">這些元素一起描述動態參數的值。</span><span class="sxs-lookup"><span data-stu-id="f85bc-128">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="f85bc-129">此元素是針對列舉值所設計。</span><span class="sxs-lookup"><span data-stu-id="f85bc-129">This element is designed for enumerated values.</span></span> <span data-ttu-id="f85bc-130">如果動態參數未採用值（例如，如果是具有切換參數的案例），或無法列舉值，請加入空的 `PossibleValues` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-130">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="f85bc-131">下表列出並描述 `PossibleValues` 元素及其子項目。</span><span class="sxs-lookup"><span data-stu-id="f85bc-131">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="f85bc-132">PossibleValues-此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="f85bc-132">PossibleValues - This element is a container.</span></span> <span data-ttu-id="f85bc-133">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="f85bc-133">Its child elements are described below.</span></span> <span data-ttu-id="f85bc-134">將一個 `PossibleValues` 元素新增至每個提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="f85bc-134">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="f85bc-135">元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="f85bc-135">The element can be empty.</span></span>
   - <span data-ttu-id="f85bc-136">PossibleValue-此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="f85bc-136">PossibleValue - This element is a container.</span></span> <span data-ttu-id="f85bc-137">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="f85bc-137">Its child elements are described below.</span></span> <span data-ttu-id="f85bc-138">`PossibleValue`為動態參數的每個值新增一個元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-138">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="f85bc-139">值-指定值名稱。</span><span class="sxs-lookup"><span data-stu-id="f85bc-139">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="f85bc-140">Description-此元素包含 `Para` 元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-140">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="f85bc-141">元素中的文字 `Para` 描述元素中所命名的值 `Value` 。</span><span class="sxs-lookup"><span data-stu-id="f85bc-141">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="f85bc-142">例如，下列 XML 會顯示 `PossibleValue` 動態參數的一個元素 `Encoding` 。</span><span class="sxs-lookup"><span data-stu-id="f85bc-142">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="f85bc-143">範例</span><span class="sxs-lookup"><span data-stu-id="f85bc-143">Example</span></span>

<span data-ttu-id="f85bc-144">下列範例顯示 `DynamicParameters` `Encoding` 動態參數的元素。</span><span class="sxs-lookup"><span data-stu-id="f85bc-144">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
