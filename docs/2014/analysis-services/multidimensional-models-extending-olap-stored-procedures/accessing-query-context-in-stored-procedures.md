---
title: Accesso al contesto di Query nelle Stored procedure | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28aafacda2e9880a79201fd07ca41fb15959e87b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37239841"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Accesso al contesto di query nelle stored procedure
  Il contesto di esecuzione di una stored procedure è disponibile all'interno del codice della stored procedure stessa sotto forma di oggetto `Context` del modello a oggetti server ADOMD.NET. Si tratta di un contesto di sola lettura che non può essere modificato dalla stored procedure. Per questo oggetto sono disponibili le proprietà seguenti.  
  
|Proprietà|Tipo|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cubo per il contesto di query corrente.|  
|**CurrentDatabaseName**|String|Identificatore del database corrente.|  
|**CurrentConnection**|Connessione|Riferimento all'oggetto connessione nel contesto corrente.|  
|**Pass**|Valore intero|Numero della sessione di calcolo per il contesto corrente.|  
  
 L'oggetto `Context` è presente se in una stored procedure viene utilizzato un modello a oggetti MDX (Multidimensional Expressions), mentre non è disponibile se il modello a oggetti MDX viene utilizzato in un client. L'oggetto `Context` non viene esplicitamente passato a o restituito dalla stored procedure, ma è disponibile durante l'esecuzione della stored procedure stessa.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle stored procedure](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
