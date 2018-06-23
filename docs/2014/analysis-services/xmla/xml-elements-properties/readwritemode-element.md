---
title: Elemento ReadWriteMode | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ReadWriteMode command
ms.assetid: 379bcaca-bb7e-4934-a9e7-21f8ede2fdc7
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 88ebc7e23fc3ec4aad0d8273464636354958217a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36171093"
---
# <a name="readwritemode-element"></a>Elemento ReadWriteMode
  La proprietà di database `ReadWriteMode` specifica se il database è in modalità `ReadWrite` o in modalità `ReadOnly`. Questi sono i due soli valori possibili della proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|ReadWrite|  
|Cardinalità|0-1: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](database-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 I database vengono creati solo in modalità `ReadWrite`. Non possono essere creati in modalità `ReadOnly`.  
  
 Il valore dell'elemento `ReadWriteMode` è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sola lettura*|Non è possibile applicare modifiche o aggiornamenti al database.|  
|*ReadWrite*|È possibile applicare modifiche e aggiornamenti al database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Attach](../xml-elements-commands/attach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../multidimensional-models/database-readwritemodes.md)   
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  