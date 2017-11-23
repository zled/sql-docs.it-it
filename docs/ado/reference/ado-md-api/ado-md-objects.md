---
title: Oggetti ADO MD | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADO MD, objects
- objects [ADO MD]
ms.assetid: 2a32e873-3282-4520-a7ed-89493f1da80e
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5f2828b7c39ba721401ad35598a3f0c767b9f6d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="ado-md-objects"></a>Oggetti ADO MD
|||  
|-|-|  
|[Axis](../../../ado/reference/ado-md-api/axis-object-ado-md.md)|Rappresenta una posizione o l'asse filtro di un set di celle contenente i membri selezionati di una o più dimensioni.|  
|[Catalogo](../../../ado/reference/ado-md-api/catalog-object-ado-md.md)|Contiene informazioni sullo schema multidimensionale (vale a dire, cubi e sottostante dimensioni, gerarchie, livelli e membri) specifiche per un provider di dati multidimensionali (dati Multidimensionali).|  
|[Cella](../../../ado/reference/ado-md-api/cell-object-ado-md.md)|Rappresenta i dati in corrispondenza dell'intersezione delle coordinate dell'asse, contenuti in un set di celle.|  
|[Set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)|Rappresenta i risultati di una query multidimensionale. È una raccolta di celle selezionate da cubi o altri set di celle.|  
|[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)|Rappresenta un cubo da uno schema multidimensionale, contenente un set di dimensioni correlate.|  
|[Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)|Rappresenta una delle dimensioni di un cubo multidimensionale, contenente uno o più gerarchie di membri.|  
|[Hierarchy](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)|Rappresenta uno dei modi in cui i membri di una dimensione possono essere aggregati o "rollback". Una dimensione può essere aggregata in una o più gerarchie.|  
|[Level](../../../ado/reference/ado-md-api/level-object-ado-md.md)|Contiene un set di membri, ognuno dei quali ha lo stesso rango all'interno di una gerarchia.|  
|[Membro](../../../ado/reference/ado-md-api/member-object-ado-md.md)|Rappresenta un membro di un livello in un cubo, gli elementi figlio di un membro di un livello o un membro di una posizione lungo un asse di un set di celle.|  
|[Posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md)|Rappresenta un set di uno o più membri di dimensioni diverse che definisce un punto lungo un asse.|  
  
 Inoltre, il **catalogo** oggetto connesso a un oggetto ADO **connessione** oggetto, che è incluso nella libreria ADO standard:  
  
|Oggetto|Description|  
|------------|-----------------|  
|[Connessione](../../../ado/reference/ado-api/connection-object-ado.md)|Rappresenta una connessione aperta a un'origine dati.|  
  
 Le relazioni tra questi oggetti sono illustrate nella sezione di [modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md).  
  
 Molti oggetti ADO MD possono essere contenuti in una raccolta corrispondente. Ad esempio, un [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) oggetto può essere contenuto un [CubeDefs](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md) raccolta di un **catalogo**. Per ulteriori informazioni, vedere [insiemi ADO MD](../../../ado/reference/ado-md-api/ado-md-collections.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API di ADO MD](../../../ado/reference/ado-md-api/ado-md-api-reference.md)   
 [Esempi di codice ADO MD](../../../ado/reference/ado-md-api/ado-md-code-examples.md)   
 [Insiemi ADO MD](../../../ado/reference/ado-md-api/ado-md-collections.md)   
 [Costanti enumerate ADO MD](../../../ado/reference/ado-md-api/ado-md-enumerated-constants.md)   
 [Metodi ADO MD](../../../ado/reference/ado-md-api/ado-md-methods.md)   
 [Modello a oggetti ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [Proprietà di ADO MD](../../../ado/reference/ado-md-api/ado-md-properties.md)
