---
title: 寬型檢視 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083734"
---
# <a name="wide-view-basic"></a><span data-ttu-id="75a13-102">寬型檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="75a13-102">Wide View (Basic)</span></span>

<span data-ttu-id="75a13-103">此範例示範如何實作基本的寬型檢視會顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件`Get-Service`cmdlet。</span><span class="sxs-lookup"><span data-stu-id="75a13-103">This example shows how to implement a basic wide view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the `Get-Service` cmdlet.</span></span> <span data-ttu-id="75a13-104">如需詳細的寬型檢視元件的相關資訊，請參閱[建立寬型檢視](./creating-a-wide-view.md)。</span><span class="sxs-lookup"><span data-stu-id="75a13-104">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="75a13-105">若要載入此格式的檔案</span><span class="sxs-lookup"><span data-stu-id="75a13-105">To load this formatting file</span></span>

1. <span data-ttu-id="75a13-106">本主題的範例 > 一節的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="75a13-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="75a13-107">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="75a13-107">Save the text file.</span></span> <span data-ttu-id="75a13-108">請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="75a13-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="75a13-109">開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="75a13-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="75a13-110">此格式檔案會定義顯示的 Windows PowerShell 格式化檔案已經定義的物件。</span><span class="sxs-lookup"><span data-stu-id="75a13-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="75a13-111">您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。</span><span class="sxs-lookup"><span data-stu-id="75a13-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="75a13-112">示範</span><span class="sxs-lookup"><span data-stu-id="75a13-112">Demonstrates</span></span>

<span data-ttu-id="75a13-113">這個格式檔會示範下列的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="75a13-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="75a13-114">[名稱](./name-element-for-view-format.md)檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="75a13-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="75a13-115">[ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="75a13-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="75a13-116">[WideItem](./wideitem-element-for-widecontrol-format.md)定義哪些屬性會顯示由檢視項目。</span><span class="sxs-lookup"><span data-stu-id="75a13-116">The [WideItem](./wideitem-element-for-widecontrol-format.md) element that defines what property is displayed by the view.</span></span>

## <a name="example"></a><span data-ttu-id="75a13-117">範例</span><span class="sxs-lookup"><span data-stu-id="75a13-117">Example</span></span>

<span data-ttu-id="75a13-118">下列 XML 定義顯示值的寬型檢視[System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName)屬性。</span><span class="sxs-lookup"><span data-stu-id="75a13-118">The following XML defines a wide view that displays the value of the [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) property.</span></span>

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

<span data-ttu-id="75a13-119">下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。</span><span class="sxs-lookup"><span data-stu-id="75a13-119">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a><span data-ttu-id="75a13-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75a13-120">See Also</span></span>

[<span data-ttu-id="75a13-121">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="75a13-121">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="75a13-122">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="75a13-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
