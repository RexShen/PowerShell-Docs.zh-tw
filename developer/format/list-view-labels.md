---
title: 清單檢視 （標籤） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 2bb62ab3e4fa1db9b3af8c82eb9035aa4f3e31c0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860124"
---
# <a name="list-view-labels"></a><span data-ttu-id="da3d7-102">清單檢視 (標籤)</span><span class="sxs-lookup"><span data-stu-id="da3d7-102">List View (Labels)</span></span>

<span data-ttu-id="da3d7-103">此範例示範如何實作會顯示清單的每個資料列的自訂標籤的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="da3d7-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="da3d7-104">此清單檢視中顯示的屬性[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="da3d7-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="da3d7-105">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="da3d7-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>
<span data-ttu-id="da3d7-106">此範例示範如何實作會顯示清單的每個資料列的自訂標籤的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="da3d7-106">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="da3d7-107">此清單檢視中顯示的屬性[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="da3d7-107">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="da3d7-108">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="da3d7-108">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="da3d7-109">若要載入此格式的檔案</span><span class="sxs-lookup"><span data-stu-id="da3d7-109">To load this formatting file</span></span>

1. <span data-ttu-id="da3d7-110">本主題的範例 > 一節的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="da3d7-110">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="da3d7-111">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="da3d7-111">Save the text file.</span></span> <span data-ttu-id="da3d7-112">請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="da3d7-112">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="da3d7-113">開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="da3d7-113">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="da3d7-114">此格式檔案會定義顯示的 Windows PowerShell 格式化檔案已經定義的物件。</span><span class="sxs-lookup"><span data-stu-id="da3d7-114">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="da3d7-115">您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。</span><span class="sxs-lookup"><span data-stu-id="da3d7-115">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="da3d7-116">示範</span><span class="sxs-lookup"><span data-stu-id="da3d7-116">Demonstrates</span></span>

<span data-ttu-id="da3d7-117">這個格式檔會示範下列的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="da3d7-117">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="da3d7-118">[名稱](./name-element-for-view-format.md)檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="da3d7-118">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="da3d7-119">[ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="da3d7-119">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="da3d7-120">[ListControl](./listcontrol-element-format.md)定義哪些屬性會顯示由檢視項目。</span><span class="sxs-lookup"><span data-stu-id="da3d7-120">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="da3d7-121">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目，定義 [清單] 檢視的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="da3d7-121">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="da3d7-122">[標籤](./label-element-for-listitem-for-listcontrol-format.md)項目，定義 [清單] 檢視的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="da3d7-122">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="da3d7-123">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定義會顯示哪一個屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="da3d7-123">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="da3d7-124">範例</span><span class="sxs-lookup"><span data-stu-id="da3d7-124">Example</span></span>

<span data-ttu-id="da3d7-125">下列 XML 程式碼定義在每個資料列中顯示自訂標籤的清單檢視。</span><span class="sxs-lookup"><span data-stu-id="da3d7-125">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="da3d7-126">在此情況下，標籤會包含每個字母大寫的屬性名稱和"property"一字。</span><span class="sxs-lookup"><span data-stu-id="da3d7-126">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="da3d7-127">在每個資料列中，屬性的名稱會顯示後面之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="da3d7-127">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="da3d7-128">下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。</span><span class="sxs-lookup"><span data-stu-id="da3d7-128">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="da3d7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da3d7-129">See Also</span></span>

[<span data-ttu-id="da3d7-130">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="da3d7-130">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="da3d7-131">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="da3d7-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
