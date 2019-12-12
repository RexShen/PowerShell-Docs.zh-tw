---
title: 寬視圖（基本） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367937"
---
# <a name="wide-view-basic"></a><span data-ttu-id="9cf63-102">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="9cf63-102">Wide View (Basic)</span></span>

<span data-ttu-id="9cf63-103">這個範例示範如何執行會顯示 System.serviceprocess.dll. Servicecontroller 的基本寬視圖[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) `Get-Service` Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="9cf63-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="9cf63-104">如需有關寬視圖元件的詳細資訊，請參閱[建立寬視圖](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="9cf63-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="9cf63-105">載入此格式檔案</span><span class="sxs-lookup"><span data-stu-id="9cf63-105">To load this formatting file</span></span>

1. <span data-ttu-id="9cf63-106">將本主題的範例一節中的 XML 複製到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="9cf63-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="9cf63-107">儲存文字檔。</span><span class="sxs-lookup"><span data-stu-id="9cf63-107">Save the text file.</span></span> <span data-ttu-id="9cf63-108">請務必將 `format.ps1xml` 擴充功能新增至檔案，以將其識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="9cf63-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="9cf63-109">開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="9cf63-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="9cf63-110">此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="9cf63-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="9cf63-111">當您執行 Cmdlet 時，必須使用 `prependPath` 參數，而且無法將此格式檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="9cf63-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9cf63-112">示範</span><span class="sxs-lookup"><span data-stu-id="9cf63-112">Demonstrates</span></span>

<span data-ttu-id="9cf63-113">此格式檔案會示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="9cf63-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="9cf63-114">View 的[Name](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9cf63-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="9cf63-115">定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9cf63-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="9cf63-116">定義視圖所要顯示之屬性的[之 wideitem](./wideitem-element-for-widecontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="9cf63-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="9cf63-117">範例</span><span class="sxs-lookup"><span data-stu-id="9cf63-117">Example</span></span>

<span data-ttu-id="9cf63-118">下列 XML 會定義顯示[system.serviceprocess.dll. Servicecontroller. Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)屬性值的寬視圖。</span><span class="sxs-lookup"><span data-stu-id="9cf63-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="9cf63-119">下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="9cf63-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="9cf63-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cf63-120">See Also</span></span>

[<span data-ttu-id="9cf63-121">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="9cf63-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="9cf63-122">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="9cf63-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
