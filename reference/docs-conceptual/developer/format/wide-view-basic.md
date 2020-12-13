---
ms.date: 09/13/2016
ms.topic: reference
title: 寬型檢視 (基本)
description: 寬型檢視 (基本)
ms.openlocfilehash: bfc647da9b78fcd22aac83cf330e466b6759471c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667686"
---
# <a name="wide-view-basic"></a><span data-ttu-id="7d1da-103">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="7d1da-103">Wide View (Basic)</span></span>

<span data-ttu-id="7d1da-104">這個範例會示範如何執行基本的全形視圖，以顯示 [system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) Cmdlet 所傳回的 Fullname 物件 `Get-Service` 。</span><span class="sxs-lookup"><span data-stu-id="7d1da-104">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="7d1da-105">如需有關廣泛視圖元件的詳細資訊，請參閱 [建立廣泛的視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="7d1da-105">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="7d1da-106">載入此格式化檔案</span><span class="sxs-lookup"><span data-stu-id="7d1da-106">To load this formatting file</span></span>

1. <span data-ttu-id="7d1da-107">將本主題的範例一節中的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="7d1da-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="7d1da-108">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="7d1da-108">Save the text file.</span></span> <span data-ttu-id="7d1da-109">請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="7d1da-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="7d1da-110">開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="7d1da-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="7d1da-111">此格式化檔案會定義已由 Windows PowerShell 格式設定檔案定義之物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="7d1da-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="7d1da-112">`prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="7d1da-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7d1da-113">示範</span><span class="sxs-lookup"><span data-stu-id="7d1da-113">Demonstrates</span></span>

<span data-ttu-id="7d1da-114">此格式化檔案示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="7d1da-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="7d1da-115">視圖的 [名稱](./name-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="7d1da-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="7d1da-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="7d1da-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="7d1da-117">[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素，定義視圖顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="7d1da-117">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="7d1da-118">範例</span><span class="sxs-lookup"><span data-stu-id="7d1da-118">Example</span></span>

<span data-ttu-id="7d1da-119">下列 XML 定義了顯示 [system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) 的值的寬視圖。</span><span class="sxs-lookup"><span data-stu-id="7d1da-119">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
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

<span data-ttu-id="7d1da-120">下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="7d1da-120">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="7d1da-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d1da-121">See Also</span></span>

[<span data-ttu-id="7d1da-122">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="7d1da-122">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="7d1da-123">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="7d1da-123">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
