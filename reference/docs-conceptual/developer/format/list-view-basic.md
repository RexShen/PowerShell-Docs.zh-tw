---
ms.date: 09/13/2016
ms.topic: reference
title: 清單檢視 (基本)
description: 清單檢視 (基本)
ms.openlocfilehash: d80ac9c6143b976d8bc13e2b184e4f5a2f8a37ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666632"
---
# <a name="list-view-basic"></a><span data-ttu-id="471ea-103">清單檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="471ea-103">List View (Basic)</span></span>

<span data-ttu-id="471ea-104">這個範例示範如何執行顯示 System.serviceprocess.dll 的基本欄表視圖 [。 Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) [取得服務](/powershell/module/microsoft.powershell.management/get-service) Cmdlet 所傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="471ea-104">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="471ea-105">如需清單視圖元件的詳細資訊，請參閱 [建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="471ea-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="471ea-106">載入此格式化檔案</span><span class="sxs-lookup"><span data-stu-id="471ea-106">To load this formatting file</span></span>

1. <span data-ttu-id="471ea-107">將本主題的範例一節中的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="471ea-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="471ea-108">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="471ea-108">Save the text file.</span></span> <span data-ttu-id="471ea-109">請務必將副檔名新增 `format.ps1xml` 至檔案，以將它識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="471ea-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="471ea-110">開啟 Windows PowerShell，然後執行下列命令，將格式化檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="471ea-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="471ea-111">此格式化檔案會定義已由 Windows PowerShell 格式設定檔案定義之物件的顯示。</span><span class="sxs-lookup"><span data-stu-id="471ea-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="471ea-112">`prependPath`當您執行 Cmdlet 時，您必須使用參數，而且無法將此格式化檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="471ea-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="471ea-113">示範</span><span class="sxs-lookup"><span data-stu-id="471ea-113">Demonstrates</span></span>

<span data-ttu-id="471ea-114">此格式化檔案示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="471ea-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="471ea-115">視圖的 [名稱](./name-element-for-view-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="471ea-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="471ea-116">[ViewSelectedBy](./viewselectedby-element-format.md)元素，定義視圖要顯示的物件。</span><span class="sxs-lookup"><span data-stu-id="471ea-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="471ea-117">[ListControl](./listcontrol-element-format.md)元素，定義視圖顯示的屬性。</span><span class="sxs-lookup"><span data-stu-id="471ea-117">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="471ea-118">專案 [清單元素，](./listitem-element-for-listitems-for-listcontrol-format.md) 定義清單視圖的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="471ea-118">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="471ea-119">定義要顯示之屬性的 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="471ea-119">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="471ea-120">範例</span><span class="sxs-lookup"><span data-stu-id="471ea-120">Example</span></span>

<span data-ttu-id="471ea-121">下列 XML 定義的清單視圖會顯示 System.serviceprocess.dll Servicecontroller 的四個屬性。 [Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 物件。</span><span class="sxs-lookup"><span data-stu-id="471ea-121">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="471ea-122">在每個資料列中，屬性的名稱後面會顯示內容的值。</span><span class="sxs-lookup"><span data-stu-id="471ea-122">In each row, the name of the property is displayed followed by the value of the property.</span></span>

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

<span data-ttu-id="471ea-123">下列範例顯示 Windows PowerShell 如何顯示 [system.serviceprocess.dll. Servicecontroller？](/dotnet/api/System.ServiceProcess.ServiceController) 在載入此格式檔案之後，Displayproperty = Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="471ea-123">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a><span data-ttu-id="471ea-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="471ea-124">See Also</span></span>

[<span data-ttu-id="471ea-125">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="471ea-125">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="471ea-126">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="471ea-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
