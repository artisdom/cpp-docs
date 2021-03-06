---
title: "Platform::Delegate Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.technology: "cpp-windows"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "VCCORLIB/Platform::Delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::Delegate Class"
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Platform::Delegate Class
Represents a function object.  
  
## Syntax  
  
```cpp  
public delegate void delegate_name();  
```  
  
### Members  
 The Delegate class has the Equals(), GetHashCode(), and ToString() methods derived from the [Platform::Object Class](../cppcx/platform-object-class.md).  
  
### Remarks  
 Use the [delegate](../windows/delegate-cpp-component-extensions.md) keyword to create delegates; do not use Platform::Delegate explicitly. For more information, see [Delegates](../cppcx/delegates-c-cx.md). For an example of how to create and consume a delegate, see [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md).  
  
### Requirements  
 **Minimum supported client:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Minimum supported server:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Namespace:** Platform  
  
 **Metadata:** platform.winmd  
  
## See Also  
 [Platform namespace](../cppcx/platform-namespace-c-cx.md)