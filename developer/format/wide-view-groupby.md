---
title: 寬型檢視 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083649"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="48a24-102">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="48a24-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="48a24-103">此範例示範如何實作顯示群組的寬型檢視[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件`Get-Service`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="48a24-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="48a24-104">如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="48a24-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="48a24-105">若要載入此格式的檔案</span><span class="sxs-lookup"><span data-stu-id="48a24-105">To load this formatting file</span></span>

1. <span data-ttu-id="48a24-106">本主題的範例 > 一節的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="48a24-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="48a24-107">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="48a24-107">Save the text file.</span></span> <span data-ttu-id="48a24-108">請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="48a24-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="48a24-109">開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="48a24-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="48a24-110">此格式的檔案定義 Windows PowerShell 格式化檔案已經定義的物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="48a24-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="48a24-111">您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。</span><span class="sxs-lookup"><span data-stu-id="48a24-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="48a24-112">示範</span><span class="sxs-lookup"><span data-stu-id="48a24-112">Demonstrates</span></span>

<span data-ttu-id="48a24-113">這個格式檔會示範下列的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="48a24-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="48a24-114">[名稱](./name-element-for-view-format.md)檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="48a24-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="48a24-115">[ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="48a24-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="48a24-116">[GroupBy](./groupby-element-for-view-format.md)定義新的群組時顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="48a24-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="48a24-117">[WideItem](./wideitem-element-for-widecontrol-format.md)定義哪些屬性會顯示由檢視項目。</span><span class="sxs-lookup"><span data-stu-id="48a24-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="48a24-118">範例</span><span class="sxs-lookup"><span data-stu-id="48a24-118">Example</span></span>

<span data-ttu-id="48a24-119">下列 XML 定義的寬型檢視，顯示物件的群組。</span><span class="sxs-lookup"><span data-stu-id="48a24-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="48a24-120">在啟動每個新的群組時的值[System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性變更。</span><span class="sxs-lookup"><span data-stu-id="48a24-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <Label>Service Type</Label>
        <PropertyName>ServiceType</PropertyName>
      </GroupBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="48a24-121">下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。</span><span class="sxs-lookup"><span data-stu-id="48a24-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
   Service Type: Win32OwnProcess

Fax                             FCSAM

   Service Type: Win32ShareProcess

fdPHost                         FDResPub
FontCache

   Service Type: Win32OwnProcess

FontCache3.0.0.0                FSysAgent
FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="48a24-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a24-122">See Also</span></span>

[<span data-ttu-id="48a24-123">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="48a24-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="48a24-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="48a24-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
