---
title: Elemento DataSourceType (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourceType Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#DataSourceType
- microsoft.xml.analysis.datasourcetype
- http://schemas.microsoft.com/analysisservices/2003/engine#DataSourceType
helpviewer_keywords: DataSourceType element
ms.assetid: f5a348b1-911b-4139-832e-4bcb6d80a728
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6542870aac6490512340d029355855c069d29d4e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="datasourcetype-element-xmla"></a>Elemento DataSourceType (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Indica se un [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) elemento specificato per un [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) o [Sincronizza](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md) comando è locale o remoto.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location>  
   ...  
   <DataSourceType>...</DataSourceType>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Remoto*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Il **DataSourceType** elemento determina se l'origine dati definita per il **percorso** elemento include un'origine dati locale o un'origine dati remota. Per ulteriori informazioni sul backup e ripristino di partizioni remote, vedere [backup, ripristino e sincronizzazione di database &#40; XMLA &#41; ](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Locale*|Il **percorso** elemento definisce un'origine dati locale. Se questo valore viene utilizzato, il **ripristinare** e **Sincronizza** comandi usano le informazioni definite nel **percorso** recuperato dall'elemento per aggiornare l'origine dati, il specificato nel file di backup di **File** elemento per il **Backup** comando o il database specificato nella **origine** elemento per il  **Sincronizzare** identificato nel comando di **DataSourceID** elemento del **percorso** elemento.<br /><br /> Questo valore consente a oggetti che utilizzano l’archiviazione relazionale OLAP (ROLAP), dopo il ripristino o la sincronizzazione, di utilizzare un database diverso per i dati e i metadati.<br /><br /> Nota: I dati ROLAP, ad esempio i dati in tabelle delle dimensioni o tabelle writeback, non è ripristinati o sincronizzati. Solo i metadati per gli oggetti ROLAP vengono ripristinati o sincronizzati.|  
|*Remoto*|Il **percorso** elemento definisce un'origine dati remota. Se questo valore viene utilizzato, il **ripristinare** e **Sincronizza** comandi usano le informazioni definite nel **percorso** elemento da ripristinare o sincronizzare partizioni remote, recuperate dal file di backup specificato nella **File** elemento del **Backup** comando o il database specificato nella **origine** elemento per il **Sincronizza** comando, all'istanza remota identificata nel **DataSourceID** del **percorso** elemento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ConnectionString &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/connectionstring-element-xmla.md)   
 [Elemento DataSourceID &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/datasourceid-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
