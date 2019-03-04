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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859874"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="f688b-102">如何新增動態參數至提供者說明主題</span><span class="sxs-lookup"><span data-stu-id="f688b-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="f688b-103">本節說明如何以填入**動態參數**區段的提供者說明主題。</span><span class="sxs-lookup"><span data-stu-id="f688b-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="f688b-104">*動態參數*是 cmdlet 的參數或函式，可只在指定的條件。</span><span class="sxs-lookup"><span data-stu-id="f688b-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="f688b-105">提供者說明主題中所述的動態參數是動態參數提供者磁碟機中使用的 cmdlet 或函式時，提供者新增至 cmdlet 或函式。</span><span class="sxs-lookup"><span data-stu-id="f688b-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="f688b-106">動態參數也有記載在 提供者的自訂 cmdlet 說明。</span><span class="sxs-lookup"><span data-stu-id="f688b-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="f688b-107">當撰寫提供者的提供者說明和自訂的 cmdlet 說明，包含動態參數文件中兩份文件。</span><span class="sxs-lookup"><span data-stu-id="f688b-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="f688b-108">如需有關自訂的 cmdlet 說明的詳細資訊，請參閱 <<c0> [ 撰寫 Windows PowerShell 自訂 Cmdlet 說明的提供者](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)。</span><span class="sxs-lookup"><span data-stu-id="f688b-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="f688b-109">如果提供者未實作任何動態參數，提供者的 [說明] 主題包含空`DynamicParameters`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="f688b-110">若要新增的動態參數</span><span class="sxs-lookup"><span data-stu-id="f688b-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="f688b-111">在  *AssemblyName*.dll help.xml 檔案，內`providerHelp`項目，新增`DynamicParameters`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="f688b-112">`DynamicParameters`後的項目應該會出現`Tasks`項目和前面`RelatedLinks`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="f688b-113">例如：</span><span class="sxs-lookup"><span data-stu-id="f688b-113">For example:</span></span>

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

   <span data-ttu-id="f688b-114">如果提供者未實作任何動態參數，`DynamicParameters`項目可以是空白。</span><span class="sxs-lookup"><span data-stu-id="f688b-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="f688b-115">內`DynamicParameters`項目，每個動態參數，新增`DynamicParameter`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="f688b-116">例如：</span><span class="sxs-lookup"><span data-stu-id="f688b-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="f688b-117">在每個`DynamicParameter`項目，新增`Name`和`CmdletSupported`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="f688b-118">元素名稱</span><span class="sxs-lookup"><span data-stu-id="f688b-118">Element Name</span></span>|<span data-ttu-id="f688b-119">描述</span><span class="sxs-lookup"><span data-stu-id="f688b-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="f688b-120">名稱</span><span class="sxs-lookup"><span data-stu-id="f688b-120">Name</span></span>|<span data-ttu-id="f688b-121">指定參數名稱。</span><span class="sxs-lookup"><span data-stu-id="f688b-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="f688b-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="f688b-122">CmdletSupported</span></span>|<span data-ttu-id="f688b-123">指定的 cmdlet 參數無效。</span><span class="sxs-lookup"><span data-stu-id="f688b-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="f688b-124">輸入 cmdlet 名稱的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="f688b-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="f688b-125">例如，下列的 XML 文件`Encoding`Windows PowerShell FileSystem 提供者新增到的動態參數`Add-Content`， `Get-Content`， `Set-Content` cmdlet。</span><span class="sxs-lookup"><span data-stu-id="f688b-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="f688b-126">在每個`DynamicParameter`項目，新增`Type`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="f688b-127">`Type`項目是容器`Name`所在的.NET 類型的動態參數值的項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="f688b-128">例如，下列 XML 顯示的.NET 類型`Encoding`動態參數是[Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f688b-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="f688b-129">新增`Description`元素，其中包含的動態參數的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="f688b-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="f688b-130">當您在撰寫描述，使用中的所有 cmdlet 參數所都規定的指導方針[如何新增參數資訊](./how-to-add-parameter-information.md)。</span><span class="sxs-lookup"><span data-stu-id="f688b-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="f688b-131">比方說，下列 XML 會包含描述`Encoding`動態參數。</span><span class="sxs-lookup"><span data-stu-id="f688b-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="f688b-132">新增`PossibleValues`項目和其子項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="f688b-133">在一起，這些元素會說明動態參數的值。</span><span class="sxs-lookup"><span data-stu-id="f688b-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="f688b-134">這個項目被設計用於列舉的值。</span><span class="sxs-lookup"><span data-stu-id="f688b-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="f688b-135">如果動態參數不接受的值，這類案例，並切換參數，或無法列舉的值，加入空白`PossibleValues`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="f688b-136">下表列出並描述`PossibleValues`項目和其子項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="f688b-137">元素名稱</span><span class="sxs-lookup"><span data-stu-id="f688b-137">Element Name</span></span>|<span data-ttu-id="f688b-138">描述</span><span class="sxs-lookup"><span data-stu-id="f688b-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="f688b-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="f688b-139">PossibleValues</span></span>|<span data-ttu-id="f688b-140">這個項目是一個容器。</span><span class="sxs-lookup"><span data-stu-id="f688b-140">This element is a container.</span></span> <span data-ttu-id="f688b-141">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="f688b-141">Its child elements are described below.</span></span> <span data-ttu-id="f688b-142">加入一個`PossibleValues`每個提供者說明主題的項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="f688b-143">項目可以是空的。</span><span class="sxs-lookup"><span data-stu-id="f688b-143">The element can be empty.</span></span>|
   |<span data-ttu-id="f688b-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="f688b-144">PossibleValue</span></span>|<span data-ttu-id="f688b-145">這個項目是一個容器。</span><span class="sxs-lookup"><span data-stu-id="f688b-145">This element is a container.</span></span> <span data-ttu-id="f688b-146">其子項目如下所述。</span><span class="sxs-lookup"><span data-stu-id="f688b-146">Its child elements are described below.</span></span> <span data-ttu-id="f688b-147">加入一個`PossibleValue`動態參數的每個值的項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="f688b-148">值</span><span class="sxs-lookup"><span data-stu-id="f688b-148">Value</span></span>|<span data-ttu-id="f688b-149">指定值的名稱。</span><span class="sxs-lookup"><span data-stu-id="f688b-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="f688b-150">描述</span><span class="sxs-lookup"><span data-stu-id="f688b-150">Description</span></span>|<span data-ttu-id="f688b-151">這個項目包含`Para`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-151">This element contains a `Para` element.</span></span> <span data-ttu-id="f688b-152">中的文字`Para`項目會描述出現在值`Value`項目。</span><span class="sxs-lookup"><span data-stu-id="f688b-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="f688b-153">例如，下列 XML 會顯示其中一個`PossibleValue`項目`Encoding`動態參數。</span><span class="sxs-lookup"><span data-stu-id="f688b-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="f688b-154">範例</span><span class="sxs-lookup"><span data-stu-id="f688b-154">Example</span></span>

<span data-ttu-id="f688b-155">下列範例所示`DynamicParameters`項目`Encoding`動態參數。</span><span class="sxs-lookup"><span data-stu-id="f688b-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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