---
title: Dimensione oggetto (ADO MD) | Documenti Microsoft
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
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10378c62ec05008529e1d271208f3e5657d6a140
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283910"
---
# <a name="dimension-object-ado-md"></a>Oggetto dimensione (ADO MD)
Rappresenta una delle dimensioni di un cubo multidimensionale, contenente uno o più gerarchie di membri.  
  
## <a name="remarks"></a>Remarks  
 Raccolte e le proprietà di un **dimensione** dell'oggetto, è possibile eseguire le operazioni seguenti:  
  
-   Identificare il **dimensione** con il [nome](../../../ado/reference/ado-md-api/name-property-ado-md.md) e [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md) proprietà.  
  
-   Restituire una stringa significativa che descrive il **dimensione** con il [descrizione](../../../ado/reference/ado-md-api/description-property-ado-md.md) proprietà.  
  
-   Restituire il [gerarchia](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md) gli oggetti che costituiscono il **dimensione** con il [gerarchie](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md) insieme.  
  
-   Utilizzare ADO standard [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) insieme per ottenere informazioni aggiuntive sul **dimensione** oggetto.  
  
 Il **proprietà** insieme contiene le proprietà specifiche del provider. Nella tabella seguente sono elencate le proprietà che potrebbero essere disponibili. L'elenco di proprietà effettivo può variare in base all'implementazione del provider. Vedere la documentazione del provider per un elenco completo delle proprietà disponibili.  
  
|nome|Description|  
|----------|-----------------|  
|CatalogName|Il nome del catalogo a cui appartiene il cubo.|  
|CubeName|Nome del cubo.|  
|Proprietà DefaultHierarchy|Il nome univoco della gerarchia predefinita.|  
|Description|Una descrizione significativa del cubo.|  
|DimensionCaption|Etichetta o didascalia associata alla dimensione.|  
|DimensionCardinality|Il numero di membri nella dimensione.|  
|DimensionGUID|Il GUID della dimensione.|  
|DimensionName|Nome della dimensione.|  
|DimensionOrdinal|Il numero ordinale della dimensione all'interno del gruppo di dimensioni che costituiscono il cubo.|  
|DimensionType|Il tipo di dimensione.|  
|DimensionUniqueName|Nome univoco della dimensione.|  
|SchemaName|Il nome dello schema a cui appartiene il cubo.|  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio CubeDef (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [Raccolta di dimensioni (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [Raccolta hierarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
