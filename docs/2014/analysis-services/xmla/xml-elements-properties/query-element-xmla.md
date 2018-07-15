---
title: Eseguire una query elemento (XMLA) | Microsoft Docs
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
api_name:
- Query Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Query
- microsoft.xml.analysis.query
- http://schemas.microsoft.com/analysisservices/2003/engine#Query
helpviewer_keywords:
- Query element
ms.assetid: 5a4544e4-012f-4a47-942c-23596400ea16
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02feb5cb14e6b6acdc6100070495d0c84b89e483
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37293243"
---
# <a name="query-element-xmla"></a>Elemento Query (XMLA)
  Contiene una query all'interno di [query](queries-element-xmla.md) raccolta usata per il [DesignAggregations](../xml-elements-commands/designaggregations-element-xmla.md) comando durante l'ottimizzazione basata sull'utilizzo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Queries>  
   ...  
   <Query>...</Query>  
   ...  
</Queries>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Query](queries-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il comando `DesignAggregations` supporta l'ottimizzazione basata sulle statistiche di utilizzo includendo uno o più elementi `Query` nella raccolta `Queries` del comando. Ogni `Query` elemento rappresenta una query di tipo goal utilizzata dal processo di progettazione per definire le aggregazioni destinate alle query utilizzate più di frequente. È possibile specificare query di tipo goal personalizzate oppure è possibile usare le informazioni archiviate da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] nel log di query per recuperare informazioni su più di frequente query utilizzate.  
  
 Se si siano progettando in modo iterativo le aggregazioni, è sufficiente passato query di tipo goal al primo `DesignAggregations` comando perché la [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza archivia queste query e le utilizza durante le successive `DesignAggregations` comandi. Dopo avere passato query di tipo goal al primo comando `DesignAggregations` di un processo iterativo, qualsiasi comando `DesignAggregations` successivo che contiene query di tipo goal nella proprietà `Queries` genera un errore.  
  
 L'elemento `Query` contiene un valore delimitato da virgole in cui sono presenti gli argomenti seguenti:  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *Frequenza*  
 Fattore di ponderazione corrispondente al numero di volte che la query è stata eseguita in precedenza. Se il `Query` elemento rappresenta una nuova query, il *frequenza* valore rappresenta il fattore del ponderazione utilizzato dal processo di progettazione per valutare la query. Con l'aumentare del valore della frequenza, aumenta il peso associato alla query durante il processo di progettazione.  
  
 *Set di dati*  
 Stringa numerica che specifica gli attributi di una dimensione da includere nella query. Questa stringa deve avere un numero di caratteri uguale al numero di attributi della dimensione. Il valore zero (0) indica che l'attributo nella posizione ordinale specificata non è incluso nella query per la dimensione specificata, mentre il valore uno (1) indica che l'attributo nella posizione ordinale specificata è incluso nella query per la dimensione specificata.  
  
 La stringa "011" fa riferimento ad esempio a una query relativa a una dimensione con tre attributi, di cui il secondo e il terzo sono inclusi nella query.  
  
> [!NOTE]  
>  Alcuni attributi non vengono considerati nel set di dati. Per altre informazioni sugli attributi esclusi, vedere [Properties (XMLA)](query-element-xmla.md).  
  
 Ogni dimensione nel gruppo di misure che contiene la progettazione delle aggregazioni è rappresentata da un *set di dati* valore il `Query` elemento. L'ordine dei valori *Dataset* deve corrispondere all'ordine delle dimensioni incluse nel gruppo di misure.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di aggregazioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/designing-aggregations-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
