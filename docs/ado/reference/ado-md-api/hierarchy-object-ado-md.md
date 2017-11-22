---
title: Oggetto Hierarchy (ADO MD) | Documenti Microsoft
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
f1_keywords: Hierarchy
helpviewer_keywords: Hierarchy object [ADO MD]
ms.assetid: 034af340-ac79-494e-ba5e-2b57da1cb9de
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e02aefb90af923cea7bfd6d33b8b1e97415c6ae8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="hierarchy-object-ado-md"></a>Oggetto Hierarchy (ADO MD)
Rappresenta uno dei modi in cui i membri di un [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md) possono essere aggregati o "rollback". Una dimensione può essere aggregata in una o più gerarchie.  
  
## <a name="remarks"></a>Osservazioni  
 Raccolte e le proprietà di un **gerarchia** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **gerarchia** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive il **gerarchia** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Restituire il [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) gli oggetti che costituiscono il **gerarchia** con il [livelli](../../../ado/reference/ado-md-api/levels-collection-ado-md.md) insieme.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **gerarchia** oggetto.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|Nome|Description|  
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
