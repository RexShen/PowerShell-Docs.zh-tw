---
title: 清單檢視 (GroupBy) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2e66c86-83a7-4148-8575-c28d6d429d4f
caps.latest.revision: 6
ms.openlocfilehash: c178c4a48f9595001bcc249d5f55886fa54bb9f2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794431"
---
# <a name="list-view-groupby"></a><span data-ttu-id="eae16-102">清單檢視 (GroupBy)</span><span class="sxs-lookup"><span data-stu-id="eae16-102">List View (GroupBy)</span></span>

<span data-ttu-id="eae16-103">此範例示範如何實作清單檢視，以分隔清單的資料列分組。</span><span class="sxs-lookup"><span data-stu-id="eae16-103">This example shows how to implement a list view that separates the rows of the list into groups.</span></span> <span data-ttu-id="eae16-104">此清單檢視中顯示的屬性[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="eae16-104">This list view displays the properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) cmdlet.</span></span> <span data-ttu-id="eae16-105">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="eae16-105">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="eae16-106">若要載入此格式的檔案</span><span class="sxs-lookup"><span data-stu-id="eae16-106">To load this formatting file</span></span>

1. <span data-ttu-id="eae16-107">本主題的範例 > 一節的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="eae16-107">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="eae16-108">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="eae16-108">Save the text file.</span></span> <span data-ttu-id="eae16-109">請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="eae16-109">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="eae16-110">開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="eae16-110">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="eae16-111">此格式檔案會定義顯示的 Windows PowerShell 格式化檔案已經定義的物件。</span><span class="sxs-lookup"><span data-stu-id="eae16-111">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="eae16-112">您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。</span><span class="sxs-lookup"><span data-stu-id="eae16-112">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="eae16-113">示範</span><span class="sxs-lookup"><span data-stu-id="eae16-113">Demonstrates</span></span>

<span data-ttu-id="eae16-114">這個格式檔會示範下列的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="eae16-114">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="eae16-115">[名稱](./name-element-for-view-format.md)檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="eae16-115">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="eae16-116">[ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="eae16-116">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="eae16-117">[GroupBy](./viewselectedby-element-format.md)項目，定義新的一整組物件的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="eae16-117">The [GroupBy](./viewselectedby-element-format.md) element that defines how a new group of objects is displayed.</span></span>

- <span data-ttu-id="eae16-118">[ListControl](./listcontrol-element-format.md)定義哪些屬性會顯示由檢視項目。</span><span class="sxs-lookup"><span data-stu-id="eae16-118">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="eae16-119">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目，定義 [清單] 檢視的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="eae16-119">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="eae16-120">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定義會顯示哪一個屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="eae16-120">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="eae16-121">範例</span><span class="sxs-lookup"><span data-stu-id="eae16-121">Example</span></span>

<span data-ttu-id="eae16-122">下列 XML 定義啟動新的清單檢視群組時的值[System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status)屬性變更。</span><span class="sxs-lookup"><span data-stu-id="eae16-122">The following XML defines a list view that starts a new group whenever the value of the [System.Serviceprocess.Servicecontroller.Status](/dotnet/api/System.ServiceProcess.ServiceController.Status) property changes.</span></span> <span data-ttu-id="eae16-123">當啟動每個群組時，自訂標籤會顯示包含新屬性的值。</span><span class="sxs-lookup"><span data-stu-id="eae16-123">When each group is started, a custom label is displayed that includes the new value of the property.</span></span>

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

<span data-ttu-id="eae16-124">下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。</span><span class="sxs-lookup"><span data-stu-id="eae16-124">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span> <span data-ttu-id="eae16-125">Windows PowerShell 會自動加入空白的行加入至之前或之後的群組標籤。</span><span class="sxs-lookup"><span data-stu-id="eae16-125">The blank lines added before and after the group label are automatically added by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="eae16-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eae16-126">See Also</span></span>

[<span data-ttu-id="eae16-127">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="eae16-127">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="eae16-128">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="eae16-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
