---
title: Livello di oggetto (ADO MD) | Documenti Microsoft
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
apitype: COM
f1_keywords: Level
helpviewer_keywords: Level object [ADO MD]
ms.assetid: 37815869-ed30-45fd-9aea-0a986c1b305c
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 540048b6ba889152089b39a77aa926a5c2fd61f8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="level-object-ado-md"></a>Oggetto di livello (ADO MD)
Contiene un set di membri, ognuno dei quali ha lo stesso rango all'interno di una gerarchia.  
  
## <a name="remarks"></a>Osservazioni  
 Raccolte e le proprietà di un **livello** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **livello** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa da utilizzare per la visualizzazione di **livello** con il [didascalia](../../../ado/reference/ado-md-api/caption-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive il **livello** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Restituire il [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md) gli oggetti che costituiscono il **livello** con il [membri](../../../ado/reference/ado-md-api/members-collection-ado-md.md) insieme.  
  
-   Restituire il numero di livelli dalla radice di **livello** con il [profondità](../../../ado/reference/ado-md-api/depth-property-ado-md.md) proprietà.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **livello** oggetto.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|Nome|Description|  
|----------|-----------------|  
|CatalogName|Il nome del catalogo a cui appartiene il cubo.|  
|CubeName|Nome del cubo.|  
|Description|Una descrizione significativa del livello.|  
|DimensionUniqueName|Nome univoco del [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Nome univoco della gerarchia.|  
|LevelCaption|Etichetta o didascalia associata al livello.|  
|LevelCardinality|Numero di membri nel livello.|  
|LevelGUID|Il GUID del livello.|  
|LevelName|Nome del livello.|  
|LevelNumber|La distanza tra il livello e la radice della gerarchia.|  
|LevelType|Il tipo di livello.|  
|LevelUniqueName|Nome univoco del livello.|  
|SchemaName|Il nome dello schema a cui appartiene il cubo.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/level-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Oggetto Hierarchy (ADO MD)](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)   
 [Raccolta di livelli (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Raccolta di membri (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
