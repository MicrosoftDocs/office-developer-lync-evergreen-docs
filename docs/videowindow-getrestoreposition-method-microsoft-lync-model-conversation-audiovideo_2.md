---
title: VideoWindow.GetRestorePosition method  (Microsoft.Lync.Model.Conversation.AudioVideo)
TOCTitle: 'GetRestorePosition method '
ms:assetid: M:Microsoft.Lync.Model.Conversation.AudioVideo.VideoWindow.GetRestorePosition(System.Int32@,System.Int32@,System.Int32@,System.Int32@)_DI_3_UC_OCS14MrefLyncWPF
ms:mtpsurl: https://msdn.microsoft.com/en-us/library/microsoft.lync.model.conversation.audiovideo.videowindow.getrestoreposition(v=office.15)
ms:contentKeyID: 48598225
ms.date: 07/28/2014
mtps_version: v=office.15
f1_keywords:
- Microsoft.Lync.Model.Conversation.AudioVideo.VideoWindow.GetRestorePosition
dev_langs:
- CSharp
- JScript
- VB
- other
---

# VideoWindow.GetRestorePosition method

**Namespace:**  [Microsoft.Lync.Model.Conversation.AudioVideo](microsoft-lync-model-conversation-audiovideo-namespace_2.md)  
**Assembly:**  Microsoft.Lync.Model (in Microsoft.Lync.Model.dll)

## Syntax

``` vb
'Declaration
Public Sub GetRestorePosition ( _
    <OutAttribute> ByRef pLeft As Integer, _
    <OutAttribute> ByRef pTop As Integer, _
    <OutAttribute> ByRef pWidth As Integer, _
    <OutAttribute> ByRef pHeight As Integer _
)
'Usage
Dim instance As VideoWindow
Dim pLeft As Integer
Dim pTop As Integer
Dim pWidth As Integer
Dim pHeight As Integer

instance.GetRestorePosition(pLeft, pTop, _
    pWidth, pHeight)
```

``` csharp
public void GetRestorePosition(
    out int pLeft,
    out int pTop,
    out int pWidth,
    out int pHeight
)
```

#### Parameters

  - pLeft  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

<!-- end list -->

  - pTop  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

<!-- end list -->

  - pWidth  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

<!-- end list -->

  - pHeight  
    Type: [System.Int32](http://msdn2.microsoft.com/en-us/library/td2s409d)  

## See also

#### Reference

[VideoWindow class](videowindow-class-microsoft-lync-model-conversation-audiovideo_2.md)

[VideoWindow members](videowindow-members-microsoft-lync-model-conversation-audiovideo_2.md)

[Microsoft.Lync.Model.Conversation.AudioVideo namespace](microsoft-lync-model-conversation-audiovideo-namespace_2.md)

