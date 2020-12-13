---
ms.date: 09/13/2016
ms.topic: reference
title: 清單檢視 (GroupBy)
description: 清單檢視 (GroupBy)
ms.openlocfilehash: e039c38d1e4e93f65a508fe60aaaf35c64ebe2ed
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666615"
---
# <a name="list-view-groupby"></a><span data-ttu-id="95083-103">清單檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="95083-103">List View (GroupBy)</span></span>

<span data-ttu-id="95083-104">這個範例示範如何執行清單視圖，將清單中的資料列分隔成群組。</span><span class="sxs-lookup"><span data-stu-id="95083-104">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="95083-105">此清單視圖會顯示 System.serviceprocess.dll 的屬性 [。 Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service) Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="95083-105">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="95083-106">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="95083-106">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="95083-107">載入此格式化檔案</span><span class="sxs-lookup"><span data-stu-id="95083-107">To load this formatting file</span></span>

1. <span data-ttu-id="95083-108">將本主題的範例一節中的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="95083-108">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="95083-109">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="95083-109">Save the text file.</span></span> <span data-ttu-id="95083-110">請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="95083-110">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="95083-111">開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="95083-111">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="95083-112">此格式化檔案會定義已由 Windows PowerShell 格式設定檔案定義之物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="95083-112">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="95083-113">`prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="95083-113">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="95083-114">示範</span><span class="sxs-lookup"><span data-stu-id="95083-114">Demonstrates</span></span>

<span data-ttu-id="95083-115">此格式化檔案示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="95083-115">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="95083-116">視圖的 [名稱](./name-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="95083-116">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="95083-117">[ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="95083-117">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="95083-118">[GroupBy](./viewselectedby-element-format.md)專案，定義如何顯示新的物件群組。</span><span class="sxs-lookup"><span data-stu-id="95083-118">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="95083-119">[ListControl](./listcontrol-element-format.md)元素，定義視圖顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="95083-119">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="95083-120">專案 [清單元素，](./listitem-element-for-listitems-for-listcontrol-format.md) 定義清單視圖的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="95083-120">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="95083-121">定義要顯示之屬性的 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="95083-121">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="95083-122">範例</span><span class="sxs-lookup"><span data-stu-id="95083-122">Example</span></span>

<span data-ttu-id="95083-123">下列 XML 會定義每次 [System.serviceprocess.dll Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.Status) 的值變更時，會啟動新群組的清單視圖。</span><span class="sxs-lookup"><span data-stu-id="95083-123">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="95083-124">當每個群組都啟動時，會顯示包含屬性新值的自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="95083-124">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.ServiceProcess.ServiceController</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>Status</PropertyName>
        <Label>New Service Status</Label>
      </GroupBy>
      <ListControl>
        <ListEntries>
          <ListEntry>
            <ListItems>
              <ListItem>
                <PropertyName>Name</PropertyName>
              </ListItem>
              <ListItem>
                <PropertyName>DisplayName</PropertyName>
              </ListItem>
              <ListItem>
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

<span data-ttu-id="95083-125">下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="95083-125">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="95083-126">Windows PowerShell 會自動加入群組標籤前後新增的空白行。</span><span class="sxs-lookup"><span data-stu-id="95083-126">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

```powershell
Get-Service f*
```

```output
   New Service Status: Stopped

Name        : Fax
DisplayName : Fax
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
ServiceType : Win32OwnProcess

   New Service Status: Stopped

Name        : fdPHost
DisplayName : Function Discovery Provider Host
ServiceType : Win32ShareProcess

   New Service Status: Running

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
ServiceType : Win32ShareProcess

   New Service Status: Stopped

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
ServiceType : Win32OwnProcess

   New Service Status: Running

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="95083-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95083-127">See Also</span></span>

[<span data-ttu-id="95083-128">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="95083-128">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="95083-129">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="95083-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
