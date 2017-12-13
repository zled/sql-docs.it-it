---
title: Elemento Parameters (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Parameters Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Parameters
- urn:schemas-microsoft-com:xml-analysis#Parameters
- microsoft.xml.analysis.parameters
helpviewer_keywords: Parameters element
ms.assetid: d46454a1-a1d1-4aa8-95ea-54be22a53e83
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0948833e2457b0a7af7ec6c4442130fae408926a
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="parameters-element-xmla"></a>Elemento Parameters (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene una raccolta di [parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md) elementi utilizzati per il [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo.  
  
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
|Elementi padre|[Eseguire](../../../analysis-services/xmla/xml-elements-methods-execute.md)|  
|Elementi figlio|[Parametro](../../../analysis-services/xmla/xml-elements-properties/parameter-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 I comandi del codice XML for Analysis (XMLA), come il [processo](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md) comando, possono richiedere informazioni aggiuntive. Il **parametri** elemento fornisce un meccanismo per fornire informazioni aggiuntive, incluse le informazioni in blocchi, per un comando XMLA.  
  
 Se il comando XMLA non utilizza il **parametri** elemento, l'elemento può essere omesso quando si chiama il **Execute** metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
