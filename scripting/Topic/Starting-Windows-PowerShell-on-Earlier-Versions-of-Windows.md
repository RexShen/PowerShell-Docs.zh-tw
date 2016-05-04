---
title: 在舊版 Windows 上啟動 Windows PowerShell
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
---
# 在舊版 Windows 上啟動 Windows PowerShell
本節說明如何在 [!INCLUDE[win7_client_firstref](../Token/win7_client_firstref_md.md)]、[!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上啟動 [!INCLUDE[wps_2](../Token/wps_2_md.md)] 和 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]。 它也會說明如何在 [!INCLUDE[win7_server_firstref](../Token/win7_server_firstref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上啟用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)] 的選用功能。

若要在支援的系統上安裝 [!INCLUDE[psversion4](../Token/psversion4_md.md)]，請下載並安裝 [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881)。 如需詳細資訊，請參閱[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

若要在支援的系統上安裝 [!INCLUDE[psversion3](../Token/psversion3_md.md)]，請下載並安裝 [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290)。 如需詳細資訊，請參閱[安裝 Windows PowerShell](../Topic/Installing-Windows-PowerShell.md)。

## 如何在舊版 Windows 上啟動 [!INCLUDE[mshshort](../Token/mshshort_md.md)]
使用下列任何方法來啟動已安裝的 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 或 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 版本 (適用時)。

#### 從 [開始] 功能表

-   按一下 **[開始]**，並輸入 **PowerShell**，然後按一下 **[Windows PowerShell]**。

-   從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell]**。

#### 在命令提示字元中

-   在 Cmd.exe、[!INCLUDE[wps_2](../Token/wps_2_md.md)] 或 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE 中，若要啟動 [!INCLUDE[wps_2](../Token/wps_2_md.md)]，請輸入：

    ```
    PowerShell
    ```

    您也可以使用 PowerShell.exe 程式的參數來自訂工作階段。 如需詳細資訊，請參閱 [PowerShell.exe 命令列說明](../Topic/PowerShell.exe-Command-Line-Help.md)。

#### 使用系統管理權限 ([以系統管理員身分執行])

1.  按一下 **[開始]**、輸入 **PowerShell**、以滑鼠右鍵按一下 **[Windows PowerShell]**，然後按一下 **[以系統管理員身分執行]**。

## 如何在舊版 Windows 上啟動 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]
使用下列任何方法來啟動 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。

#### 從 [開始] 功能表

-   按一下 **[開始]**，並輸入 **ISE**，然後按一下 **[Windows PowerShell ISE]**。

-   從 **[開始]** 功能表中，依序按一下 **[開始]**、**[所有程式]**、**[附屬應用程式]**、**[Windows PowerShell]** 資料夾和 **[Windows PowerShell ISE]**。

#### 在命令提示字元中

-   在 Cmd.exe、[!INCLUDE[wps_2](../Token/wps_2_md.md)] 或 [!INCLUDE[wps_2](../Token/wps_2_md.md)] ISE 中，若要啟動 [!INCLUDE[wps_2](../Token/wps_2_md.md)]，請輸入：

    ```
    PowerShell_ISE
    ```

    或

    ```
    ISE
    ```

#### 使用系統管理權限 ([以系統管理員身分執行])

1.  按一下 **[開始]**、輸入 **ISE**、以滑鼠右鍵按一下 **[Windows PowerShell ISE]**，然後按一下 **[以系統管理員身分執行]**。

## 如何在舊版 Windows 上啟用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]
在 [!INCLUDE[psversion4](../Token/psversion4_md.md)] 和 [!INCLUDE[psversion3](../Token/psversion3_md.md)] 中，預設會在 Windows 的所有版本上啟用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。 如果尚未啟用，則 Windows Management Framework 4.0 或 [!INCLUDE[ps_wmf_3.0](../Token/ps_wmf_3.0_md.md)] 會啟用它。

在 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中，預設會在 [!INCLUDE[win7_client_secondref](../Token/win7_client_secondref_md.md)] 上啟用 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]。 不過，在 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 和 [!INCLUDE[lserver](../Token/lserver_md.md)] 上，它是選用功能。

若要在 [!INCLUDE[win7_server_secondref](../Token/win7_server_secondref_md.md)] 或 [!INCLUDE[lserver](../Token/lserver_md.md)] 上啟用 [!INCLUDE[psversion2](../Token/psversion2_md.md)] 中的 [!INCLUDE[mshgraphicalhostshort](../Token/mshgraphicalhostshort_md.md)]，請使用下列程序。

#### 啟用 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]

1.  啟動 [伺服器管理員]。

2.  按一下 **[功能]**，然後按一下 **[新增功能]**。

3.  在 [選取功能] 中，按一下 [!INCLUDE[mshgraphicalhost](../Token/mshgraphicalhost_md.md)]。



<!--HONumber=Apr16_HO1-->


