---
title: 清單檢視 (Basic) |Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 3c94d8e98f179286112a417230fce659dc0b614c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065303"
---
# <a name="list-view-basic"></a><span data-ttu-id="a44c5-102">清單檢視 (基本)</span><span class="sxs-lookup"><span data-stu-id="a44c5-102">List View (Basic)</span></span>

<span data-ttu-id="a44c5-103">此範例示範如何實作基本的清單檢視會顯示[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)所傳回的物件[Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet。</span><span class="sxs-lookup"><span data-stu-id="a44c5-103">This example shows how to implement a basic list view that displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects returned by the [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet.</span></span> <span data-ttu-id="a44c5-104">清單檢視元件的相關資訊，請參閱[建立清單檢視](./creating-a-list-view.md)。</span><span class="sxs-lookup"><span data-stu-id="a44c5-104">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

### <a name="to-load-this-formatting-file"></a><span data-ttu-id="a44c5-105">若要載入此格式的檔案</span><span class="sxs-lookup"><span data-stu-id="a44c5-105">To load this formatting file</span></span>

1. <span data-ttu-id="a44c5-106">本主題的範例 > 一節的 XML 複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="a44c5-106">Copy the XML from the Example section of this topic into a text file.</span></span>

2. <span data-ttu-id="a44c5-107">儲存文字檔案。</span><span class="sxs-lookup"><span data-stu-id="a44c5-107">Save the text file.</span></span> <span data-ttu-id="a44c5-108">請務必新增`format.ps1xml`至檔案，以將它識別為格式化檔案的副檔名。</span><span class="sxs-lookup"><span data-stu-id="a44c5-108">Be sure to add the `format.ps1xml` extension to the file to identify it as a formatting file.</span></span>

3. <span data-ttu-id="a44c5-109">開啟 Windows PowerShell，然後執行下列命令將目前的工作階段中載入的格式化檔案： `Update-formatdata -prependpath PathToFormattingFile`。</span><span class="sxs-lookup"><span data-stu-id="a44c5-109">Open Windows PowerShell, and run the following command to load the formatting file into the current session: `Update-formatdata -prependpath PathToFormattingFile`.</span></span>

   > [!WARNING]
   > <span data-ttu-id="a44c5-110">此格式檔案會定義顯示的 Windows PowerShell 格式化檔案已經定義的物件。</span><span class="sxs-lookup"><span data-stu-id="a44c5-110">This formatting file defines the display of an object that is already defined by a Windows PowerShell formatting file.</span></span> <span data-ttu-id="a44c5-111">您必須使用`prependPath`參數，當您執行 cmdlet，而且您無法載入此格式檔案為模組。</span><span class="sxs-lookup"><span data-stu-id="a44c5-111">You must use the `prependPath` parameter when you run the cmdlet, and you cannot load this formatting file as a module.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a44c5-112">示範</span><span class="sxs-lookup"><span data-stu-id="a44c5-112">Demonstrates</span></span>

<span data-ttu-id="a44c5-113">這個格式檔會示範下列的 XML 項目：</span><span class="sxs-lookup"><span data-stu-id="a44c5-113">This formatting file demonstrates the following XML elements:</span></span>

- <span data-ttu-id="a44c5-114">[名稱](./name-element-for-view-format.md)檢視的項目。</span><span class="sxs-lookup"><span data-stu-id="a44c5-114">The [Name](./name-element-for-view-format.md) element for the view.</span></span>

- <span data-ttu-id="a44c5-115">[ViewSelectedBy](./viewselectedby-element-format.md)會定義哪些物件檢視所顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="a44c5-115">The [ViewSelectedBy](./viewselectedby-element-format.md) element that defines what objects are displayed by the view.</span></span>

- <span data-ttu-id="a44c5-116">[ListControl](./listcontrol-element-format.md)定義哪些屬性會顯示由檢視項目。</span><span class="sxs-lookup"><span data-stu-id="a44c5-116">The [ListControl](./listcontrol-element-format.md) element that defines what property is displayed by the view.</span></span>

- <span data-ttu-id="a44c5-117">[ListItem](./listitem-element-for-listitems-for-listcontrol-format.md)項目，定義 [清單] 檢視的資料列中顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="a44c5-117">The [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) element that defines what is displayed in a row of the list view.</span></span>

- <span data-ttu-id="a44c5-118">[PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md)定義會顯示哪一個屬性的項目。</span><span class="sxs-lookup"><span data-stu-id="a44c5-118">The [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element that defines which property is displayed.</span></span>

## <a name="example"></a><span data-ttu-id="a44c5-119">範例</span><span class="sxs-lookup"><span data-stu-id="a44c5-119">Example</span></span>

<span data-ttu-id="a44c5-120">下列 XML 定義顯示的四個屬性的清單檢視[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件。</span><span class="sxs-lookup"><span data-stu-id="a44c5-120">The following XML defines a list view that displays four properties of the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="a44c5-121">在每個資料列中，屬性的名稱會顯示後面之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="a44c5-121">In each row, the name of the property is displayed followed by the value of the property.</span></span>

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

<span data-ttu-id="a44c5-122">下列範例會示範 Windows PowerShell 的顯示方式[System.Serviceprocess.Servicecontroller 嗎？Displayproperty = Fullname>](/dotnet/api/System.ServiceProcess.ServiceController)物件載入這個格式檔案之後。</span><span class="sxs-lookup"><span data-stu-id="a44c5-122">The following example shows how Windows PowerShell displays the [System.Serviceprocess.Servicecontroller?Displayproperty=Fullname](/dotnet/api/System.ServiceProcess.ServiceController) objects after this format file is loaded.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a44c5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a44c5-123">See Also</span></span>

[<span data-ttu-id="a44c5-124">格式檔案的範例</span><span class="sxs-lookup"><span data-stu-id="a44c5-124">Examples of Formatting Files</span></span>](./examples-of-formatting-files.md)

[<span data-ttu-id="a44c5-125">撰寫 PowerShell 格式化檔案</span><span class="sxs-lookup"><span data-stu-id="a44c5-125">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
