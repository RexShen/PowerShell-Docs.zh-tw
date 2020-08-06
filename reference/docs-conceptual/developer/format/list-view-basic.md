---
title: " (基本) 的清單視圖 |Microsoft Docs"
ms.date: 09/13/2016
ms.openlocfilehash: 74ff8f6eee0a9358c123455aa00736a11e7f085d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783546"
---
# <a name="list-view-basic"></a><span data-ttu-id="ff775-102">清單檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="ff775-102">List View (Basic)</span></span>

<span data-ttu-id="ff775-103">這個範例示範如何執行會顯示 System.serviceprocess.dll. Servicecontroller 的基本欄表視圖[？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)由[Get-服務](/powershell/module/microsoft.powershell.management/get-service)Cmdlet 傳回的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="ff775-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="ff775-104">如需清單視圖之元件的詳細資訊，請參閱[建立清單視圖](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="ff775-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="ff775-105">載入此格式檔案</span><span class="sxs-lookup"><span data-stu-id="ff775-105">To load this formatting file</span></span>

1. <span data-ttu-id="ff775-106">將本主題的範例一節中的 XML 複製到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="ff775-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="ff775-107">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="ff775-107">Save the text file.</span></span> <span data-ttu-id="ff775-108">請務必將擴充功能新增 `format.ps1xml` 至檔案，以將其識別為格式化檔案。</span><span class="sxs-lookup"><span data-stu-id="ff775-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="ff775-109">開啟 Windows PowerShell，然後執行下列命令，將格式檔案載入目前的會話： `Update-formatdata -prependpath PathToFormattingFile` 。</span><span class="sxs-lookup"><span data-stu-id="ff775-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="ff775-110">此格式檔案會定義已由 Windows PowerShell 格式化檔案所定義的物件顯示。</span><span class="sxs-lookup"><span data-stu-id="ff775-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="ff775-111">`prependPath`當您執行 Cmdlet 時，必須使用參數，而且無法將此格式檔案載入為模組。</span><span class="sxs-lookup"><span data-stu-id="ff775-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ff775-112">示範</span><span class="sxs-lookup"><span data-stu-id="ff775-112">Demonstrates</span></span>

<span data-ttu-id="ff775-113">此格式檔案會示範下列 XML 元素：</span><span class="sxs-lookup"><span data-stu-id="ff775-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="ff775-114">View 的[Name](./name-element-for-view-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ff775-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="ff775-115">定義視圖所要顯示之物件的[ViewSelectedBy](./viewselectedby-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ff775-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="ff775-116">定義視圖所要顯示之屬性的[ListControl](./listcontrol-element-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ff775-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="ff775-117">定義要在清單視圖的資料列中顯示之專案[的 [專案](./listitem-element-for-listitems-for-listcontrol-format.md)類型] 元素。</span><span class="sxs-lookup"><span data-stu-id="ff775-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="ff775-118">定義要顯示哪一個屬性的[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ff775-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="ff775-119">範例</span><span class="sxs-lookup"><span data-stu-id="ff775-119">Example</span></span>

<span data-ttu-id="ff775-120">下列 XML 定義的清單視圖會顯示 System.serviceprocess.dll. Servicecontroller 的四個屬性[？Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="ff775-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ff775-121">在每個資料列中，屬性的名稱後面會顯示內容的值。</span><span class="sxs-lookup"><span data-stu-id="ff775-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="ff775-122">下列範例顯示 Windows PowerShell 如何顯示[system.serviceprocess.dll. Servicecontroller？Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController)載入此格式檔案後的 Fullname 物件。</span><span class="sxs-lookup"><span data-stu-id="ff775-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ff775-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff775-123">See Also</span></span>

[<span data-ttu-id="ff775-124">格式設定檔案的範例</span><span class="sxs-lookup"><span data-stu-id="ff775-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="ff775-125">撰寫 PowerShell 格式設定檔案</span><span class="sxs-lookup"><span data-stu-id="ff775-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
