---
title: 清單視圖 (標籤) |Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: da45bd8dce7ac2149de6a34c11d5419d6cb4ddb0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773380"
---
# <a name="list-view-labels"></a><span data-ttu-id="d24d4-102">清單檢視 (標籤)</span><span class="sxs-lookup"><span data-stu-id="d24d4-102">List View (Labels)</span></span>

<span data-ttu-id="d24d4-103">這個範例示範如何執行清單視圖，以顯示清單中每個資料列的自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="d24d4-103">This example shows how to implement a list view that displays a custom label for each row of the list.</span></span> <span data-ttu-id="d24d4-104">此清單視圖會顯示[system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service)Cmdlet 傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="d24d4-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object that is returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="d24d4-105">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="d24d4-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="d24d4-106">載入此格式檔案</span><span class="sxs-lookup"><span data-stu-id="d24d4-106">To load this formatting file</span></span>

1. <span data-ttu-id="d24d4-107">將本主題的範例一節中的 XML 複製到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="d24d4-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="d24d4-108">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="d24d4-108">Save the text file.</span></span> <span data-ttu-id="d24d4-109">請務必將擴充功能新增 `format.ps1xml` 至檔案，以將其識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="d24d4-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="d24d4-110">開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="d24d4-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="d24d4-111">此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="d24d4-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="d24d4-112">`prependPath`當您執行 Cmdlet 時，必須使用參數，而且無法將此格式檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="d24d4-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d24d4-113">示範</span><span class="sxs-lookup"><span data-stu-id="d24d4-113">Demonstrates</span></span>

<span data-ttu-id="d24d4-114">此格式檔案會示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="d24d4-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="d24d4-115">View 的[Name](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d24d4-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="d24d4-116">定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d24d4-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="d24d4-117">定義視圖所要顯示之屬性的[ListControl](./listcontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d24d4-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="d24d4-118">定義要在清單視圖的資料列中顯示之專案[的 [專案](./listitem-element-for-listitems-for-listcontrol-format.md)類型] 元素。</span><span class="sxs-lookup"><span data-stu-id="d24d4-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d24d4-119">[Label](./label-element-for-listitem-for-listcontrol-format.md)元素，定義要在清單視圖的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="d24d4-119">The [Label](./label-element-for-listitem-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="d24d4-120">定義要顯示哪一個屬性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="d24d4-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="d24d4-121">範例</span><span class="sxs-lookup"><span data-stu-id="d24d4-121">Example</span></span>

<span data-ttu-id="d24d4-122">下列 XML 會定義清單視圖，以在每個資料列中顯示自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="d24d4-122">The following XML defines a list view that displays a custom label in each row.</span></span> <span data-ttu-id="d24d4-123">在此情況下，標籤會包含屬性名稱，其中每個字母都大寫，而 "property" 一字。</span><span class="sxs-lookup"><span data-stu-id="d24d4-123">In this case, the label includes the property name with each letter capitalized and the word "property".</span></span> <span data-ttu-id="d24d4-124">在每個資料列中，屬性的名稱後面會顯示內容的值。</span><span class="sxs-lookup"><span data-stu-id="d24d4-124">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="d24d4-125">下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="d24d4-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d24d4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d24d4-126">See Also</span></span>

[<span data-ttu-id="d24d4-127">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="d24d4-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="d24d4-128">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="d24d4-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
