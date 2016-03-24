# RefreshMode 和 ConfigurationMode 的頻率不需要是彼此的倍數

在 DSC 先前的版本中，LCM 會將 `RefreshFrequencyMins` 和 `ConfigurationModeFrequencyMins` 視為彼此的倍數，就如部落格中的[這裡](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx)所述。 WMF 5.0 RTM 中這些屬性會彼此獨立的進行處理。 下表將說明此行為︰

**PULL** 模式中的行為︰ 

|                                  |**中繼設定中的值**|**套用中繼設定後的值**|**提取發生的頻率 (以分鐘為單位)**|**套用設定的頻率 (以分鐘為單位)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

**PUSH** 模式中的行為︰

|                                  |**中繼設定中的值**|**套用中繼設定後的值**|**套用設定的頻率 (以分鐘為單位)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
