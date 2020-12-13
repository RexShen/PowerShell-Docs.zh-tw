---
ms.date: 09/13/2016
ms.topic: reference
title: 寬型檢視 (GroupBy)
description: 寬型檢視 (GroupBy)
ms.openlocfilehash: 807bea2a5d44c38e2c9977f792bea2fb9bca0fc3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667669"
---
# <a name="wide-view-groupby"></a><span data-ttu-id="aadad-103">寬型檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="aadad-103">Wide View (GroupBy)</span></span>

<span data-ttu-id="aadad-104">此範例示範如何執行會顯示 System.serviceprocess.dll Servicecontroller 群組的廣泛視圖 [？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) Cmdlet 所傳回的 Fullname 物件 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="aadad-104">This example shows how to implement a wide view that displays groups of [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="aadad-105">如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="aadad-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="aadad-106">載入此格式化檔案</span><span class="sxs-lookup"><span data-stu-id="aadad-106">To load this formatting file</span></span>

1. <span data-ttu-id="aadad-107">將本主題的範例一節中的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="aadad-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="aadad-108">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="aadad-108">Save the text file.</span></span> <span data-ttu-id="aadad-109">請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="aadad-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="aadad-110">開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="aadad-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="aadad-111">這個格式化檔案會定義已由 Windows PowerShell 格式檔案定義之物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="aadad-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting files.</span></span> <span data-ttu-id="aadad-112">`prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="aadad-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="aadad-113">示範</span><span class="sxs-lookup"><span data-stu-id="aadad-113">Demonstrates</span></span>

<span data-ttu-id="aadad-114">此格式化檔案示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="aadad-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="aadad-115">視圖的 [名稱](./name-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="aadad-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="aadad-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="aadad-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="aadad-117">在顯示新群組時定義的 [GroupBy](./groupby-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="aadad-117">The [GroupBy](./groupby-element-for-view-format.md) element that defines when a new group is displayed.</span></span>

- <span data-ttu-id="aadad-118">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素，定義視圖顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="aadad-118">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="aadad-119">範例</span><span class="sxs-lookup"><span data-stu-id="aadad-119">Example</span></span>

<span data-ttu-id="aadad-120">下列 XML 定義了顯示物件群組的廣泛視圖。</span><span class="sxs-lookup"><span data-stu-id="aadad-120">The following XML defines a wide view that displays groups of objects.</span></span> <span data-ttu-id="aadad-121">當 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 屬性的值變更時，就會啟動每個新群組。</span><span class="sxs-lookup"><span data-stu-id="aadad-121">Each new group is started when the value of the [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) property changes.</span></span>

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

<span data-ttu-id="aadad-122">下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="aadad-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aadad-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aadad-123">See Also</span></span>

[<span data-ttu-id="aadad-124">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="aadad-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="aadad-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="aadad-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
