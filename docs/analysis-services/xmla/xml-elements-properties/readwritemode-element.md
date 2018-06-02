---
title: Elemento ReadWriteMode | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0d528567e22c3ba19b49eefff10d886703a0d29a
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576493"
---
# <a name="readwritemode-element"></a>Elemento ReadWriteMode
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Il **ReadWriteMode** proprietà di database consente di specificare se il database è in **ReadWrite** modalità o in **ReadOnly** modalità. Questi sono i due soli valori possibili della proprietà.  
  
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
|Elementi padre|[Database](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 I database vengono creati **ReadWrite** solo in modalità. Non possono essere creati **ReadOnly** modalità.  
  
 Il valore di **ReadWriteMode** elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sola lettura*|Non è possibile applicare modifiche o aggiornamenti al database.|  
|*Lettura/scrittura*|È possibile applicare modifiche e aggiornamenti al database.|  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Attach](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Passare a un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
