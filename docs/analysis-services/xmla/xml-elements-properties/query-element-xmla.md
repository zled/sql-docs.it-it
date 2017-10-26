---
title: Eseguire una query elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Query Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b3b6b989932fcb37fba1c137c30658238a0c05df
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="query-element-xmla"></a>Elemento Query (XMLA)
  Contiene una query all'interno di [query](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md) raccolta utilizzata dal [DesignAggregations](../../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) comando durante l'ottimizzazione basata sull'utilizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Query](../../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il comando **DesignAggregations** supporta l'ottimizzazione basata sulle statistiche di utilizzo includendo uno o più elementi **Query** nella raccolta **Queries** del comando. Ogni elemento **Query** rappresenta una query di tipo goal utilizzata dal processo di progettazione per definire le aggregazioni destinate alle query utilizzate più di frequente. È possibile specificare query di tipo goal personalizzate oppure è possibile utilizzare le informazioni archiviate da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nel log di query per recuperare informazioni su più di frequente query utilizzate.  
  
 Se si progettano in modo iterativo le aggregazioni, è necessario solo passare query di tipo goal al primo **DesignAggregations** comando perché la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza archivia queste query e le utilizza durante i successivi  **DesignAggregations** comandi. Dopo avere passato query di tipo goal al primo comando **DesignAggregations** di un processo iterativo, qualsiasi comando **DesignAggregations** successivo che contiene query di tipo goal nella proprietà **Queries** genera un errore.  
  
 L'elemento **Query** contiene un valore delimitato da virgole in cui sono presenti gli argomenti seguenti:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frequenza*  
 Fattore di ponderazione corrispondente al numero di volte che la query è stata eseguita in precedenza. Se l'elemento **Query** rappresenta una nuova query, il valore *Frequency* rappresenta il fattore del ponderazione utilizzato dal processo di progettazione per valutare la query. Con l'aumentare del valore della frequenza, aumenta il peso associato alla query durante il processo di progettazione.  
  
 *Set di dati*  
 Stringa numerica che specifica gli attributi di una dimensione da includere nella query. Questa stringa deve avere un numero di caratteri uguale al numero di attributi della dimensione. Il valore zero (0) indica che l'attributo nella posizione ordinale specificata non è incluso nella query per la dimensione specificata, mentre il valore uno (1) indica che l'attributo nella posizione ordinale specificata è incluso nella query per la dimensione specificata.  
  
 La stringa "011" fa riferimento ad esempio a una query relativa a una dimensione con tre attributi, di cui il secondo e il terzo sono inclusi nella query.  
  
> [!NOTE]  
>  Alcuni attributi non vengono considerati nel set di dati. Per ulteriori informazioni sugli attributi esclusi, vedere [proprietà (XMLA)](../../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 Ogni dimensione nel gruppo di misure che contiene la progettazione delle aggregazioni è rappresentata da un valore *Dataset* nell'elemento **Query** . L'ordine dei valori *Dataset* deve corrispondere all'ordine delle dimensioni incluse nel gruppo di misure.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di aggregazioni &#40; XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  

