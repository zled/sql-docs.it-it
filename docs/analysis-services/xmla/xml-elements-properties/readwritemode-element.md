---
title: Elemento ReadWriteMode | Microsoft Docs
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37994853"
---
# <a name="readwritemode-element"></a>Elemento ReadWriteMode
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Il **ReadWriteMode** proprietà database consente di specificare se il database è in **ReadWrite** modalità o nella **ReadOnly** modalità. Questi sono i due soli valori possibili della proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Database>  
...  
   <ddlns_100_0:ReadWriteMode>...</ddlns_100_0:ReadWriteMode>  
...  
</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|ReadWrite|  
|Cardinalità|0-1: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Database](../../../analysis-services/xmla/xml-elements-properties/database-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 I database vengono creati nella **ReadWrite** solo in modalità. Non possono essere creati nella **ReadOnly** modalità.  
  
 Il valore della **ReadWriteMode** elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sola lettura*|Non è possibile applicare modifiche o aggiornamenti al database.|  
|*Lettura/scrittura*|È possibile applicare modifiche e aggiornamenti al database.|  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Attach](../../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Collegamento e scollegamento di database di Analysis Services](../../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [Spostare un Database di Analysis Services](../../../analysis-services/multidimensional-models/move-an-analysis-services-database.md)   
 [Proprietà readwritemode del database](../../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Passare un database di Analysis Services tra le modalità ReadOnly e ReadWrite](../../../analysis-services/multidimensional-models/switch-an-analysis-services-database-between-readonly-and-readwrite-modes.md)  
  
  
