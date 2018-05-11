---
title: Elemento ReadWriteMode | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a109db366c2b165ccf466bdeab8b7d3bb9c4d69f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|ReadWrite|  
|Cardinalità|0-1: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 I database vengono creati **ReadWrite** solo in modalità. Non possono essere creati **ReadOnly** modalità.  
  
 Il valore di **ReadWriteMode** elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|*Sola lettura*|Non è possibile applicare modifiche o aggiornamenti al database.|  
|*Lettura/scrittura*|È possibile applicare modifiche e aggiornamenti al database.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Attach](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Passare a un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
