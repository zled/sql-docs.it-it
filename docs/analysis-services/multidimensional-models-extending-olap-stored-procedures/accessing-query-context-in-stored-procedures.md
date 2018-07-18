---
title: Accesso al contesto di Query in Stored procedure | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1679b5ddaf2c3abefb6da4e89e97e84193593630
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34027288"
---
# <a name="accessing-query-context-in-stored-procedures"></a>Accesso al contesto di query nelle stored procedure
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Il contesto di esecuzione di una stored procedure è disponibile all'interno del codice della stored procedure come il **contesto** oggetto del modello a oggetti server ADOMD.NET. Si tratta di un contesto di sola lettura che non può essere modificato dalla stored procedure. Per questo oggetto sono disponibili le proprietà seguenti.  
  
|Proprietà|Tipo|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Cubo per il contesto di query corrente.|  
|**CurrentDatabaseName**|String|Identificatore del database corrente.|  
|**CurrentConnection**|Connessione|Riferimento all'oggetto connessione nel contesto corrente.|  
|**Passare**|Integer|Numero della sessione di calcolo per il contesto corrente.|  
  
 Il **contesto** oggetto si verifica quando viene utilizzato il modello a oggetti MDX (Multidimensional Expressions) in una stored procedure. mentre non è disponibile se il modello a oggetti MDX viene utilizzato in un client. Il **contesto** oggetto è passato a o restituito dalla stored procedure in modo non esplicito. ma è disponibile durante l'esecuzione della stored procedure stessa.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di assembly di modelli multidimensionali](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Definizione delle Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
