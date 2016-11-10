---
title: "&#39;Inherits&#39; not valid in Modules"
ms.custom: na
ms.date: "10/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "vbc30230"
  - "bc30230"
helpviewer_keywords: 
  - "BC30230"
ms.assetid: bccd61f7-cb47-4101-9b35-743c97876630
caps.latest.revision: 9
ms.author: "billchi"
manager: "douge"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# &#39;Inherits&#39; not valid in Modules
An `Inherits` statement occurs inside a module. Modules cannot inherit from classes.  
  
 **Error ID:** BC30230  
  
### To correct this error  
  
-   Remove the `Inherits` statement, or retype the module as a class.  
  
## See Also  
 [Inherits Statement](../Topic/Inherits%20Statement.md)   
 [Module Statement](../Topic/Module%20Statement.md)