---
title: 寬視圖（GroupBy） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39388197-4ff9-4889-aa32-526011afa1f6
caps.latest.revision: 6
ms.openlocfilehash: e95ec550a7815a76a8bd7f9526dfa405a9644360
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367947"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="fd0ca-102">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="fd0ca-102">Wide View (GroupBy)</span></span>

<span data-ttu-id="fd0ca-103">這個範例示範如何執行顯示 System.serviceprocess.dll Servicecontroller 群組的寬視圖[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) `Get-Service` Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-103">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="fd0ca-104">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="fd0ca-105">載入此格式檔案</span><span class="sxs-lookup"><span data-stu-id="fd0ca-105">To load this formatting file</span></span>

1. <span data-ttu-id="fd0ca-106">將本主題的範例一節中的 XML 複製到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="fd0ca-107">儲存文字檔。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-107">Save the text file.</span></span> <span data-ttu-id="fd0ca-108">請務必將 `format.ps1xml` 擴充功能新增至檔案，以將其識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="fd0ca-109">開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="fd0ca-110">此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="fd0ca-111">當您執行 Cmdlet 時，必須使用 `prependPath` 參數，而且無法將此格式檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="fd0ca-112">示範</span><span class="sxs-lookup"><span data-stu-id="fd0ca-112">Demonstrates</span></span>

<span data-ttu-id="fd0ca-113">此格式檔案會示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="fd0ca-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="fd0ca-114">View 的[Name](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="fd0ca-115">定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="fd0ca-116">[GroupBy](./groupby-element-for-view-format.md)元素，定義何時顯示新群組。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-116">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="fd0ca-117">定義視圖所要顯示之屬性的[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="fd0ca-118">範例</span><span class="sxs-lookup"><span data-stu-id="fd0ca-118">Example</span></span>

<span data-ttu-id="fd0ca-119">下列 XML 會定義顯示物件群組的寬視圖。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-119">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="fd0ca-120">當[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType)屬性的值變更時，就會啟動每個新群組。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-120">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="fd0ca-121">下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="fd0ca-121">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fd0ca-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd0ca-122">See Also</span></span>

[<span data-ttu-id="fd0ca-123">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="fd0ca-123">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="fd0ca-124">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="fd0ca-124">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
