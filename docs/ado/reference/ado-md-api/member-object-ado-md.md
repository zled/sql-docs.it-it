---
title: Oggetto membro (ADO MD) | Documenti Microsoft
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
- Member
helpviewer_keywords:
- Member object [ADO MD], members
ms.assetid: 3dedf755-0741-4c3f-8b4e-bff8ff8809c8
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee79dc5a17ebbce35a8543a0ed2351ca65f03374
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284040"
---
# <a name="member-object-ado-md"></a>Oggetto membro (ADO MD)
Rappresenta un membro di un livello in un cubo, gli elementi figlio di un membro di un livello o un membro di una posizione lungo un asse di un set di celle.  
  
## <a name="remarks"></a>Remarks  
 Le proprietà di un **membro** differiscono a seconda del contesto in cui viene utilizzato. A **membro** di un [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md) in un [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) ha un [figli](../../../ado/reference/ado-md-api/children-property-ado-md.md) proprietà che restituisce il **membri** in il livello inferiore successivo della gerarchia dal corrente **membro**. Per un **membro** di un [posizione](../../../ado/reference/ado-md-api/position-object-ado-md.md), **figli** raccolta è sempre vuota. Inoltre, il [tipo](../../../ado/reference/ado-md-api/type-property-ado-md.md) proprietà si applica solo a **membri** di un **livello**.  
  
 A **membro** di **posizione** ha due proprietà che sono utili quando si visualizzano i [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md): [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) e [ ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md). Si verifica un errore se si accede a queste proprietà su un **membro** di un **livello**.  
  
 Raccolte e le proprietà di un **membro** oggetto di un **livello**, è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **membro** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa da utilizzare per la visualizzazione di **membro** con il [didascalia](../../../ado/reference/ado-md-api/caption-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive una misura o una formula **membro** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Determinare la natura del **membro** con il [tipo](../../../ado/reference/ado-md-api/type-property-ado-md.md) proprietà.  
  
-   Ottenere informazioni sul **livello** del **membro** con il [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) e [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) proprietà.  
  
-   Ottenere correlati **membri** in un [gerarchia](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) con il [padre](../../../ado/reference/ado-md-api/parent-property-ado-md.md) e [figli](../../../ado/reference/ado-md-api/children-property-ado-md.md) proprietà.  
  
-   Contare gli elementi figlio di un **membro** con il [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) proprietà.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **livello** oggetto.  
  
 Raccolte e le proprietà di un **membro** di un **posizione** lungo un [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md), è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **membro** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa da utilizzare per la visualizzazione di **membro** con il [didascalia](../../../ado/reference/ado-md-api/caption-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive una misura o una formula **membro** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Ottenere informazioni sul **livello** del **membro** con il [LevelDepth](../../../ado/reference/ado-md-api/leveldepth-property-ado-md.md) e [LevelName](../../../ado/reference/ado-md-api/levelname-property-ado-md.md) proprietà.  
  
-   Contare gli elementi figlio di un **membro** con il [ChildCount](../../../ado/reference/ado-md-api/childcount-property-ado-md.md) proprietà.  
  
-   Utilizzare il [DrilledDown](../../../ado/reference/ado-md-api/drilleddown-property-ado-md.md) proprietà per determinare se è presente almeno un elemento figlio nel **asse** immediatamente dopo questo **membro**.  
  
-   Utilizzare il [ParentSameAsPrev](../../../ado/reference/ado-md-api/parentsameasprev-property-ado-md.md) proprietà per determinare se l'elemento padre di questo **membro** corrisponde al padre dell'oggetto immediatamente precedente **membro**.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **livello** oggetto.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|nome|Description|  
|----------|-----------------|  
|CatalogName|Il nome del catalogo a cui appartiene il cubo.|  
|ChildrenCardinality|Numero di elementi figlio del membro.|  
|CubeName|Nome del cubo.|  
|Description|Una descrizione significativa del membro.|  
|DimensionUniqueName|Nome univoco del [dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md).|  
|HierarchyUniqueName|Nome univoco della gerarchia.|  
|LevelNumber|La distanza tra il livello e la radice della gerarchia.|  
|LevelUniqueName|Nome univoco del livello.|  
|MemberCaption|Etichetta o didascalia associata al membro.|  
|MemberGUID|GUID del membro.|  
|MemberName|Nome del membro.|  
|MemberOrdinal|Il numero ordinale del membro.|  
|MemberType|Tipo del membro.|  
|MemberUniqueName + + +|Nome univoco del membro.|  
|ParentCount|Il conteggio del numero di elementi padre del membro.|  
|ParentLevel|Il numero del livello del padre del membro.|  
|ParentUniqueName|Nome univoco del padre membro.|  
|SchemaName|Il nome dello schema a cui appartiene il cubo.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/member-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di catalogo (VB)](../../../ado/reference/ado-md-api/catalog-example-vb.md)   
 [Raccolta di membri (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
