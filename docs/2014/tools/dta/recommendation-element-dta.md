---
title: Elemento Recommendation (DTA) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- Recommendation element
ms.assetid: 679ea535-865a-4633-a4d3-5b3090515158
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 58535397a152ff1198cbb4cf713a6d0ec04a7eed
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36064841"
---
# <a name="recommendation-element-dta"></a>Elemento Recommendation (DTA)
  Contiene informazioni sugli indici ipotetici che fanno parte di una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Configuration>  
    ...code removed here...  
    <Table>  
      <Name>...</Name>  
      <Recommendation>  
      ...code removed here...  
      </Recommendation>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Facoltativo. Può utilizzare una sola volta per ogni `Table` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento di tabella per lo Schema &#40;DTA&#41;](table-element-for-schema-dta.md)|  
|**Elementi figlio**|[Creare l'elemento &#40;DTA&#41;](create-element-dta.md)<br /><br /> `Drop` Elemento. Per ulteriori informazioni, vedere l' [XML Schema di Ottimizzazione guidata motore di database](http://go.microsoft.com/fwlink/?linkid=43100).|  
  
## <a name="remarks"></a>Remarks  
 Questo elemento appartiene al nome **RecommendationTypecomplexType** nell'XML Schema dell'Ottimizzazione guidata motore di database. Viene utilizzato per specificare indici per una configurazione ipotetica. Non confondere il `Recommendation` elemento con gli altri tipi che può essere usato per specificare il partizionamento (`RecommendationPType`) o le viste (`RecommendationViewType`). Per informazioni su questi altri `Recommendation` tipi di elemento, vedere la [Engine Tuning Advisor XML schema di Database](http://go.microsoft.com/fwlink/?linkid=43100).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  