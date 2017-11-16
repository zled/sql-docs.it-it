---
title: Accesso al contesto di Query in Stored procedure | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ea922bed66dbcb625614259346794c9ba7856e9
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="accessing-query-context-in-stored-procedures"></a>Accesso al contesto di query nelle stored procedure
  Il contesto di esecuzione di una stored procedure è disponibile all'interno del codice della stored procedure come il **contesto** oggetto del modello a oggetti server ADOMD.NET. Si tratta di un contesto di sola lettura che non può essere modificato dalla stored procedure. Per questo oggetto sono disponibili le proprietà seguenti.  
  
|Proprietà|Tipo|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cubo per il contesto di query corrente.|  
|**CurrentDatabaseName**|String|Identificatore del database corrente.|  
|**CurrentConnection**|Connessione|Riferimento all'oggetto connessione nel contesto corrente.|  
|**Passare**|Valore intero|Numero della sessione di calcolo per il contesto corrente.|  
  
 Il **contesto** oggetto si verifica quando viene utilizzato il modello a oggetti MDX (Multidimensional Expressions) in una stored procedure. mentre non è disponibile se il modello a oggetti MDX viene utilizzato in un client. Il **contesto** oggetto è passato a o restituito dalla stored procedure in modo non esplicito. ma è disponibile durante l'esecuzione della stored procedure stessa.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

