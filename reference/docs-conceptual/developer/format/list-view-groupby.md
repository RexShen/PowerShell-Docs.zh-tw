---
title: 清單視圖（GroupBy） |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365137"
---
# <a name="list-view-groupby"></a><span data-ttu-id="198ab-102">清單檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="198ab-102">List View (GroupBy)</span></span>

<span data-ttu-id="198ab-103">這個範例示範如何執行清單視圖，將清單中的資料列分割成群組。</span><span class="sxs-lookup"><span data-stu-id="198ab-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="198ab-104">此清單視圖會顯示[system.serviceprocess.dll. Servicecontroller 的屬性？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/Microsoft.PowerShell.Management/Get-Service)Cmdlet 傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="198ab-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="198ab-105">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="198ab-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="198ab-106">載入此格式檔案</span><span class="sxs-lookup"><span data-stu-id="198ab-106">To load this formatting file</span></span>

1. <span data-ttu-id="198ab-107">將本主題的範例一節中的 XML 複製到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="198ab-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="198ab-108">儲存文字檔。</span><span class="sxs-lookup"><span data-stu-id="198ab-108">Save the text file.</span></span> <span data-ttu-id="198ab-109">請務必將 `format.ps1xml` 擴充功能新增至檔案，以將其識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="198ab-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="198ab-110">開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="198ab-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="198ab-111">此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="198ab-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="198ab-112">當您執行 Cmdlet 時，必須使用 `prependPath` 參數，而且無法將此格式檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="198ab-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="198ab-113">示範</span><span class="sxs-lookup"><span data-stu-id="198ab-113">Demonstrates</span></span>

<span data-ttu-id="198ab-114">此格式檔案會示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="198ab-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="198ab-115">View 的[Name](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="198ab-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="198ab-116">定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="198ab-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="198ab-117">[GroupBy](./viewselectedby-element-format.md)元素，定義新群組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="198ab-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="198ab-118">定義視圖所要顯示之屬性的[ListControl](./listcontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="198ab-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="198ab-119">定義要在清單視圖的資料列中顯示之專案[的 [專案](./listitem-element-for-listitems-for-listcontrol-format.md)類型] 元素。</span><span class="sxs-lookup"><span data-stu-id="198ab-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="198ab-120">定義要顯示哪一個屬性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="198ab-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="198ab-121">範例</span><span class="sxs-lookup"><span data-stu-id="198ab-121">Example</span></span>

<span data-ttu-id="198ab-122">下列 XML 定義的清單視圖會在每次[system.serviceprocess.dll. Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.Status)屬性的值變更時啟動新的群組。</span><span class="sxs-lookup"><span data-stu-id="198ab-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="198ab-123">當每個群組啟動時，會顯示包含屬性之新值的自訂標籤。</span><span class="sxs-lookup"><span data-stu-id="198ab-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="198ab-124">下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="198ab-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="198ab-125">Windows PowerShell 會自動新增在群組標籤前後新增的空白行。</span><span class="sxs-lookup"><span data-stu-id="198ab-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="198ab-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="198ab-126">See Also</span></span>

[<span data-ttu-id="198ab-127">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="198ab-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="198ab-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="198ab-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
