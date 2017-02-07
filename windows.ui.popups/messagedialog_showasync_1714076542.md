---
-api-type: winrt method
---
 **In :** Your app can call [showAsync](messagedialog_showasync.md) from within the **activated** handler (the [onactivated event](http://msdn.microsoft.com/library/8b1cf913-a914-47d1-a690-bc3f0931e9d4) or the [CoreApplicationView.Activated event](../windows.applicationmodel.core/coreapplicationview_activated.md)), and paint operations then occur behind the app's splash screen.
 **Beginning in :**  Windows suppresses painting while the app is behind the splash screen to reduce wasteful operations. Your app should not call [showAsync](messagedialog_showasync.md) from within the **activated** handler, but should instead wait for the **visibility changed** notification (the [visibilitychange event](XREF:TODO:wwa.MSHTMLDocumentExtensions_msvisibilitychanged) or the [CoreWindow.VisibilityChanged event](../windows.ui.core/corewindow_visibilitychanged.md)).