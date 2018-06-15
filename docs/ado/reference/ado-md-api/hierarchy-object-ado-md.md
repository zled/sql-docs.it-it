---
title: Oggetto Hierarchy (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Hierarchy
helpviewer_keywords:
- Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6853d2a3fcc0540f23a914e3e39c8720ce3a317
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284060"
---
# <a name="hierarchy-object-ado-md"></a>Oggetto Hierarchy (ADO MD)
Rappresenta uno dei modi in cui i membri di un [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) possono essere aggregati o "rollback". Una dimensione può essere aggregata in una o più gerarchie.  
  
## <a name="remarks"></a>Remarks  
 Raccolte e le proprietà di un **gerarchia** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **gerarchia** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive il **gerarchia** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Restituire il [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) gli oggetti che costituiscono il **gerarchia** con il [livelli](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) insieme.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **gerarchia** oggetto.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|nome|Description|  
|----------|-----------------|  
|AllMember|Il membro al livello massimo di rollup della gerarchia.|  
|CatalogName|Il nome del catalogo a cui appartiene il cubo.|  
|CubeName|Nome del cubo.|  
|DefaultMember|Nome univoco del membro predefinito per questa gerarchia.|  
|Description|Una descrizione significativa della gerarchia.|  
|DimensionType|Il tipo di dimensione a cui appartiene questa gerarchia.|  
|DimensionUniqueName|Nome univoco della dimensione.|  
|HierarchyCaption|Etichetta o didascalia associata alla gerarchia.|  
|HierarchyCardinality|Numero di membri nella gerarchia.|  
|HierarchyGUID|Il GUID della gerarchia.|  
|HierarchyName|Il nome della gerarchia.|  
|HierarchyUniqueName|Nome univoco della gerarchia.|  
|SchemaName|Il nome dello schema a cui appartiene il cubo.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/hierarchy-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Oggetto dimensione (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Raccolta hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Raccolta di livelli (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
