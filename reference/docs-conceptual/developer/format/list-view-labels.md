---
ms.date: 09/13/2016
ms.topic: reference
title: 清單檢視 (標籤)
description: 清單檢視 (標籤)
ms.openlocfilehash: 2d341ae95d025e0f95b5d88b96afb846b62b092f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666683"
---
# <a name="list-view-labels"></a><span data-ttu-id="71cf9-103">清單檢視 (標籤)</span><span class="sxs-lookup"><span data-stu-id="71cf9-103">List View (Labels)</span></span>

<span data-ttu-id="71cf9-104">此範例示範如何執行清單視圖，以針對清單中的每個資料列顯示自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="71cf9-104">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="71cf9-105">此清單視圖會顯示 System.serviceprocess.dll 的屬性 [。 Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="71cf9-105">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="71cf9-106">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="71cf9-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="71cf9-107">載入此格式化檔案</span><span class="sxs-lookup"><span data-stu-id="71cf9-107">To load this formatting file</span></span>

1. <span data-ttu-id="71cf9-108">將本主題的範例一節中的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="71cf9-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="71cf9-109">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="71cf9-109">Save the text file.</span></span> <span data-ttu-id="71cf9-110">請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="71cf9-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="71cf9-111">開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="71cf9-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="71cf9-112">此格式化檔案會定義已由 Windows PowerShell 格式設定檔案定義之物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="71cf9-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="71cf9-113">`prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="71cf9-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="71cf9-114">示範</span><span class="sxs-lookup"><span data-stu-id="71cf9-114">Demonstrates</span></span>

<span data-ttu-id="71cf9-115">此格式化檔案示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="71cf9-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="71cf9-116">視圖的 [名稱](./name-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="71cf9-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="71cf9-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="71cf9-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="71cf9-118">[ListControl](./listcontrol-element-format.md)元素，定義視圖顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="71cf9-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="71cf9-119">專案 [清單元素，](./listitem-element-for-listitems-for-listcontrol-format.md) 定義清單視圖的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="71cf9-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="71cf9-120">[Label](./label-element-for-listitem-for-listcontrol-format.md)元素，定義清單視圖的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="71cf9-120">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="71cf9-121">定義要顯示之屬性的 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="71cf9-121">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="71cf9-122">範例</span><span class="sxs-lookup"><span data-stu-id="71cf9-122">Example</span></span>

<span data-ttu-id="71cf9-123">下列 XML 定義的清單視圖會在每個資料列中顯示自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="71cf9-123">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="71cf9-124">在此情況下，標籤會包含每個字母大寫的屬性名稱和 "property" 這個字。</span><span class="sxs-lookup"><span data-stu-id="71cf9-124">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="71cf9-125">在每個資料列中，屬性的名稱後面會顯示內容的值。</span><span class="sxs-lookup"><span data-stu-id="71cf9-125">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="71cf9-126">下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="71cf9-126">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="71cf9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71cf9-127">See Also</span></span>

[<span data-ttu-id="71cf9-128">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="71cf9-128">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="71cf9-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="71cf9-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
