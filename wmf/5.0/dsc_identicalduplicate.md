# 允許在設定中的相同重複資源

DSC 不允許或不處理設定中定義的衝突資源。 它並不會去嘗試解決衝突，而是只會失敗。 當設定重複使用透過複合資源而變得更有用時，衝突發生頻率將會提高。 當衝突資源的定義相同時，DSC 應該進行智慧判斷並允許此情況。 在此版本中，我們支援具有相同定義的多個資源執行個體︰

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

在舊版中，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 執行個體在盡力確保 「網頁伺服器」 角色已安裝時發生衝突，因此會出現編譯失敗的結果。 請注意在這兩種設定中，*所有*正在設定的屬性都是相同的。 由於這兩個資源中的*所有*屬性相同，現在這會讓編譯成功完成。 

如果任何屬性在兩個資源之間的有所差異，它們將不會被視為相同，而且編譯會失敗︰

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

此非常類似的設定將會失敗，因為 WindowsFeature FE_IIS 和 WindowsFeature Worker_IIS 資源不再相同，因此發生衝突。

<!--HONumber=Jun16_HO4-->


