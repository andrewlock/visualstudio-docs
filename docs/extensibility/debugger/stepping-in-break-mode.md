---
title: "Stepping in Break Mode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.technology: 
  - "vs-ide-sdk"
ms.topic: "conceptual"
helpviewer_keywords: 
  - "break mode, stepping"
  - "stepping, in break mode"
  - "debugging [Debugging SDK], stepping in break mode"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: "gregvanl"
ms.author: "gregvanl"
manager: douge
ms.workload: 
  - "vssdk"
---
# Stepping in Break Mode
The following describes the process that occurs when the debugger is in break mode and must step through code:  
  
## Stepping Process  
  
1.  Call [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) with [STEPKIND](../../extensibility/debugger/reference/stepkind.md) and [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments to execute a step.  
  
2.  When the step is finished, send an [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) as a stopping event.  
  
## See Also  
 [Calling Debugger Events](../../extensibility/debugger/calling-debugger-events.md)