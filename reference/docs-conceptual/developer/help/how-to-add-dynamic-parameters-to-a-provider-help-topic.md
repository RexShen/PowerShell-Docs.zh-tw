---
ms.date: 09/13/2016
ms.topic: reference
title: 如何新增動態參數至提供者說明主題
description: 如何新增動態參數至提供者說明主題
ms.openlocfilehash: 9542538cfacf5fb293ca8d1350b80fb250c71ac6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649631"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="40ef9-103">如何新增動態參數至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="40ef9-103">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="40ef9-104">本節說明如何填入「提供者」說明主題的 **動態參數** 區段。</span><span class="sxs-lookup"><span data-stu-id="40ef9-104">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="40ef9-105">*動態參數* 是 Cmdlet 或函式的參數，只有在指定的條件下才能使用。</span><span class="sxs-lookup"><span data-stu-id="40ef9-105">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="40ef9-106">提供者說明主題中記載的動態參數，是在提供者磁片磁碟機中使用 Cmdlet 或函式時，提供者新增至 Cmdlet 或函數的動態參數。</span><span class="sxs-lookup"><span data-stu-id="40ef9-106">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="40ef9-107">動態參數也可以記錄在提供者的自訂 Cmdlet 說明中。</span><span class="sxs-lookup"><span data-stu-id="40ef9-107">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="40ef9-108">撰寫提供者的提供者說明和自訂 Cmdlet 說明時，請將動態參數檔包含在這兩份檔中。</span><span class="sxs-lookup"><span data-stu-id="40ef9-108">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="40ef9-109">如果提供者不會執行任何動態參數，則提供者說明主題會包含空的 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="40ef9-110">新增動態參數</span><span class="sxs-lookup"><span data-stu-id="40ef9-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="40ef9-111">在檔案中 `<AssemblyName>.dll-help.xml` 的專案內 `providerHelp` ，加入 `DynamicParameters` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-111">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="40ef9-112">`DynamicParameters`元素應該會出現在專案 `Tasks` 之後和元素之前 `RelatedLinks` 。</span><span class="sxs-lookup"><span data-stu-id="40ef9-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="40ef9-113">例如：</span><span class="sxs-lookup"><span data-stu-id="40ef9-113">For example:</span></span>

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

   <span data-ttu-id="40ef9-114">如果提供者不會執行任何動態參數， `DynamicParameters` 元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="40ef9-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="40ef9-115">在 `DynamicParameters` 元素中，針對每個動態參數，加入專案 `DynamicParameter` 。</span><span class="sxs-lookup"><span data-stu-id="40ef9-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="40ef9-116">例如：</span><span class="sxs-lookup"><span data-stu-id="40ef9-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="40ef9-117">在每個專案中 `DynamicParameter` ，加入 `Name` 和 `CmdletSupported` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="40ef9-118">名稱-指定參數名稱</span><span class="sxs-lookup"><span data-stu-id="40ef9-118">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="40ef9-119">CmdletSupported-指定參數有效的 Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="40ef9-119">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="40ef9-120">輸入以逗號分隔的 Cmdlet 名稱清單。</span><span class="sxs-lookup"><span data-stu-id="40ef9-120">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="40ef9-121">例如，下列 XML 記載了 `Encoding` Windows PowerShell FileSystem 提供者加入至 `Add-Content` 、 `Get-Content` 、Cmdlet 的動態參數 `Set-Content` 。</span><span class="sxs-lookup"><span data-stu-id="40ef9-121">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="40ef9-122">在每個專案中 `DynamicParameter` ，加入一個 `Type` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-122">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="40ef9-123">`Type`元素是元素的容器， `Name` 其中包含動態參數值的 .net 型別。</span><span class="sxs-lookup"><span data-stu-id="40ef9-123">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="40ef9-124">例如，下列 XML 會顯示動態參數的 .NET 型別 `Encoding` 是 [filesystemCmdletproviderencoding parameter sets](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 列舉。</span><span class="sxs-lookup"><span data-stu-id="40ef9-124">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

1. <span data-ttu-id="40ef9-125">新增 `Description` 元素，其中包含動態參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="40ef9-125">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="40ef9-126">撰寫描述時，請使用 [如何新增參數資訊](./how-to-add-parameter-information.md)中所有 Cmdlet 參數所指定的指導方針。</span><span class="sxs-lookup"><span data-stu-id="40ef9-126">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="40ef9-127">例如，下列 XML 包含 `Encoding` 動態參數的描述。</span><span class="sxs-lookup"><span data-stu-id="40ef9-127">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

1. <span data-ttu-id="40ef9-128">加入專案 `PossibleValues` 和其子項目。</span><span class="sxs-lookup"><span data-stu-id="40ef9-128">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="40ef9-129">這些元素一起描述動態參數的值。</span><span class="sxs-lookup"><span data-stu-id="40ef9-129">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="40ef9-130">這個元素是針對列舉值所設計。</span><span class="sxs-lookup"><span data-stu-id="40ef9-130">This element is designed for enumerated values.</span></span> <span data-ttu-id="40ef9-131">如果動態參數未採用值（例如使用 switch 參數的案例），或無法列舉值，請加入空的 `PossibleValues` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-131">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="40ef9-132">下表列出並描述 `PossibleValues` 元素和其子項目。</span><span class="sxs-lookup"><span data-stu-id="40ef9-132">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="40ef9-133">PossibleValues-此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="40ef9-133">PossibleValues - This element is a container.</span></span> <span data-ttu-id="40ef9-134">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="40ef9-134">Its child elements are described below.</span></span> <span data-ttu-id="40ef9-135">將一個 `PossibleValues` 元素加入至每個提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="40ef9-135">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="40ef9-136">元素可以是空的。</span><span class="sxs-lookup"><span data-stu-id="40ef9-136">The element can be empty.</span></span>
   - <span data-ttu-id="40ef9-137">PossibleValue-此元素是容器。</span><span class="sxs-lookup"><span data-stu-id="40ef9-137">PossibleValue - This element is a container.</span></span> <span data-ttu-id="40ef9-138">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="40ef9-138">Its child elements are described below.</span></span> <span data-ttu-id="40ef9-139">`PossibleValue`針對動態參數的每個值新增一個元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-139">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="40ef9-140">值-指定值名稱。</span><span class="sxs-lookup"><span data-stu-id="40ef9-140">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="40ef9-141">描述-此元素包含 `Para` 元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-141">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="40ef9-142">專案中的文字 `Para` 描述元素中所命名的值 `Value` 。</span><span class="sxs-lookup"><span data-stu-id="40ef9-142">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="40ef9-143">例如，下列 XML 會顯示 `PossibleValue` 動態參數的一個元素 `Encoding` 。</span><span class="sxs-lookup"><span data-stu-id="40ef9-143">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="40ef9-144">範例</span><span class="sxs-lookup"><span data-stu-id="40ef9-144">Example</span></span>

<span data-ttu-id="40ef9-145">下列範例顯示 `DynamicParameters` `Encoding` 動態參數的元素。</span><span class="sxs-lookup"><span data-stu-id="40ef9-145">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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
