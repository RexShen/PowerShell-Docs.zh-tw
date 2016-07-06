# [WMF 版本資訊概觀](releasenotes.md)

# [安裝詳細資料](requirements.md)

# [產品的相容性狀態](productincompat.md)

# [意見](feedback.md)

# [WMF 5.0 啟用的案例]()
## [Just Enough Administration (JEA)](jea_overview.md)
### [建立及連接到 JEA 端點](jea_endpoint.md)
### [JEA 上的報告](jea_report.md)

## [使用 PowerShell 類別建立自訂類型](class_overview.md)
### [定義自訂類型](class_newtype.md)
### [宣告基底類別](class_base.md)
### [宣告實作的介面](class_interface.md)
### [呼叫基底類別建構函式](class_baseconstructor.md)
### [呼叫基底類別方法](class_basemethod.md)

## [PowerShell 指令碼偵錯的增強功能](debug_overview.md)

## [預期狀態設定 (DSC) 中的增強功能](dsc_improvements.md)
### [設定]()
#### [指定跨節點相依性](dsc_waitfor.md)
#### [加密的 MOF](dsc_encryptedmof.md)
#### [DSC 設定的說明支援](dsc_confighelp.md)
#### [使用 PowerShell ISE 撰寫增強功能](dsc_authoring.md)
#### [允許設定中有相同的重複資源](dsc_identicalduplicate.md)
#### [Import-DscResource 關鍵字支援 -moduleversion 參數](dsc_importdscresource.md)
#### [WOW64 支援設定關鍵字](dsc_wow64.md)
### [資源]()
#### [以類別為基礎的 DSC 資源](dsc_classbasedresource.md)
#### [DSC 資源指令碼偵錯](dsc_resourcedebugging.md)
#### [DSC 資源的自動 RunAs 支援](dsc_runas.md)
#### [DSC 資源的並存版本控制支援](dsc_sxsresource.md)
#### [新的內建資源](dsc_newresources.md)
### [本機設定管理員]()
#### [以多個設定片段設定節點](dsc_partialconfig.md)
##### [支援混合的 RefreshMode](dsc_partialconfig_mixedmode.md)
#### [以新屬性設定 DSC 引擎](dsc_metaconfiguration.md)
#### [LCM 狀態的詳細資訊](dsc_lcmstate.md)
#### [RefreshMode 和 ConfigurationMode 的頻率不需要相乘](dsc_freqnomultiple.md)
#### [RefreshMode 屬性的額外值](dsc_refreshmode.md)
### [Cmdlet]()
#### [設定狀態的詳細資料](dsc_getconfigurationstatus.md)
#### [Test-DscConfiguration Cmdlet 支援參考設定](dsc_testconfiguration.md)
#### [直接存取 DSC 資源方法](dsc_directaccess.md)
#### [傳遞設定文件，但不套用它](dsc_publishconfig.md)
#### [移除 DSC 文件](dsc_removeconfigdoc.md)
#### [統一且一致的狀態和狀態表示法](dsc_statestatus.md)
#### [Set-dsclocalconfigurationmanager Cmdlet 支援 -force 參數](dsc_setdsclcm.md)
### [Pull 模式]()
#### [DSC 設定的依需求 PULL](dsc_updateconfig.md)
#### [隔離節點和設定識別碼](dsc_nodeid.md)
#### [隔離設定、資源及報表的存放庫](dsc_repository.md)
#### [將設定狀態回報到中央位置](dsc_reporting.md)

## [使用轉譯和記錄稽核 PowerShell 使用狀況](audit_overview.md)
### [增強的轉譯選項](audit_transcript.md)
### [指令碼追蹤和記錄](audit_script.md)
### [密碼編譯訊息語法 (CMS) Cmdlet](audit_cms.md)

## [使用 PackageManagement 探索、安裝及清查軟體](oneget_overview.md)
### [PackageManagement Cmdlet](oneget_cmdlets.md)

## [使用 PowerShellGet 探索、安裝及清查 PowerShell 模組](psget_module_overview.md)
### [註冊 PowerShell 存放庫](psget_psrepository.md)
### [PowerShell 5.0 或更新版本的並存版本支援](psget_modulesxsinstall.md)
### [安裝模組相依性](psget_moduledependency.md)
### [適用於模組管理的 PowerShellGet Cmdlet](psget_modulecmdlets.md)

## [使用 PowerShellGet 探索、安裝和管理 PowerShell 指令碼](psget_script_overview.md)
### [適用於指令碼管理的 PowerShellGet Cmdlet](psget_scriptcmdlets.md)

## [根據社群意見反應增加了全新且更新過的 Cmdlet ](feedback_cmdlets.md)
### [使用 Item Cmdlet 的符號連結](feedback_symbolic.md)
### [封存 Cmdlet](feedback_archive.md)
### [剪貼簿 Cmdlet](feedback_clipboard.md)
### [Convert-String](feedback_convertstring.md)
### [從字串擷取和剖析結構化物件](feedback_convertfromString.md)
### [Format-Hex](feedback_formathex.md)
### [NoNewLine 參數](feedback_nonewline.md)
### [New-TemporaryFile](feedback_tempfile.md)
### [New-Guid](feedback_newguid.md)
### [Get-ChildItem 具有 -Depth 參數](feedback_getchilditem.md)
### [FileInfo 物件的更新](feedback_fileinfo.md)
### [宣告版本範圍 (1.* 等等) 的模組支援](feedback_moduleversionranges.md)

## [資訊串流](informationstream_overview.md)

## [根據 OData 端點產生 PowerShell Cmdlet](odata_overview.md)

## [使用 PowerShell 管理網路交換器](networkswitch_overview.md)

## [軟體清查記錄 (SIL)](sil_overview.md)

# [已知的問題和限制](limitation_overview.md)
## [預期狀態設定 (DSC) 的已知問題](limitation_dsc.md)


<!--HONumber=May16_HO4-->


