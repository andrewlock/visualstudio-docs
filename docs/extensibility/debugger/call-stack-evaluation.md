---
title: "Call Stack Evaluation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.technology: 
  - "vs-ide-sdk"
ms.topic: "conceptual"
helpviewer_keywords: 
  - "debugging [Debugging SDK], call stack evaluation"
  - "call stacks, evaluation"
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: "gregvanl"
ms.author: "gregvanl"
manager: douge
ms.workload: 
  - "vssdk"
---
# Call Stack Evaluation
In order to view the stack frames of the call stack during break mode , you must implement the [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) method.  
  
## Methods for Evaluation  
 For a simple debug engine (DE), there might be only one stack frame. To examine the stack frame during break mode, you must implement the following methods of [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Method|Description|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Gets the code context for a stack frame. The code context represents the current instruction pointer in a stack frame.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Gets the document context for a stack frame. The document context represents the current location in the source code for a stack frame. Required for viewing the source code when you are stopped in a program.|  
  
 These methods require implementation of several context-related interfaces and methods. Thus, you must implement the [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) method and the following methods of [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Method|Description|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Gets the file statement range of a document context.|  
  
 To enumerate code contexts, you must implement all the methods of [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## See Also  
 [Execution Control and State Evaluation](../../extensibility/debugger/execution-control-and-state-evaluation.md)