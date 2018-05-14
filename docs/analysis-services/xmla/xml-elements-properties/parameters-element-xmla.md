---
title: Elemento Parameters (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 982e589b7337297c84b8909499eba244638a7df3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="parameters-element-xmla"></a>Elemento Parameters (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) elementi utilizzati per il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
 **Namespace:**`urn:schemas-microsoft-com:xml-analysis`  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Execute>  
...  
   <Parameters>  
      <Parameter>...</Parameter>  
   </Parameters>  
...  
</Execute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Elementi figlio|[Parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 I comandi del codice XML for Analysis (XMLA), come il [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comando, possono richiedere informazioni aggiuntive. Il **parametri** elemento fornisce un meccanismo per fornire informazioni aggiuntive, incluse le informazioni in blocchi, per un comando XMLA.  
  
 Se il comando XMLA non utilizza il **parametri** elemento, l'elemento può essere omesso quando si chiama il **Execute** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
