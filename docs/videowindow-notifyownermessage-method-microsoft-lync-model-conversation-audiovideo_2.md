---
title: VideoWindow.NotifyOwnerMessage method  (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: 'NotifyOwnerMessage method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.AudioVideo.VideoWindow.NotifyOwnerMessage(System.Int64,System.Int32,System.Int64,System.Int64)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.videowindow.notifyownermessage(v=office.15)
ms:contentKeyID: 56370896
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.VideoWindow.NotifyOwnerMessage
dev_langs:
- CSharp
- JScript
- VB
- other
---

# VideoWindow.NotifyOwnerMessage method

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub NotifyOwnerMessage ( _
    hwnd As Long, _
    uMsg As Integer, _
    wParam As Long, _
    lParam As Long _
)
'Usage
Dim instance As VideoWindow
Dim hwnd As Long
Dim uMsg As Integer
Dim wParam As Long
Dim lParam As Long

instance.NotifyOwnerMessage(hwnd, uMsg, _
    wParam, lParam)
```

``` csharp
public void NotifyOwnerMessage(
    long hwnd,
    int uMsg,
    long wParam,
    long lParam
)
```

#### Parameters

  - hwnd  
    Type: [System.Int64](http://msdn2.microsoft.com/en-us/library/6yy583ek)  

<!-- end list -->

  - uMsg  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

<!-- end list -->

  - wParam  
    Type: [System.Int64](http://msdn2.microsoft.com/en-us/library/6yy583ek)  

<!-- end list -->

  - lParam  
    Type: [System.Int64](http://msdn2.microsoft.com/en-us/library/6yy583ek)  

## See also

#### Reference

[VideoWindow class](videowindow-class-microsoft-lync-model-conversation-audiovideo_2.md)

[VideoWindow members](videowindow-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

