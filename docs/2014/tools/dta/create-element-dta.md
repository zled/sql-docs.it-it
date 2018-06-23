---
title: Elemento Create (DTA) | Microsoft Docs
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
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ce464bc186e4e99d14cf17d0bc442abee0fed39a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36157417"
---
# <a name="create-element-dta"></a>Create - elemento (DTA)
  Contiene informazioni su indici, statistiche o strutture heap in una configurazione specificata dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una sola volta per ogni struttura di progettazione fisica, quali indici, statistiche o strutture heap.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Recommendation &#40;DTA&#41;](recommendation-element-dta.md)|  
|**Elementi figlio**|[Elemento di indice &#40;DTA&#41;](index-element-dta.md)<br /><br /> `Statistics` Elemento (vedere [Engine Tuning Advisor XML schema di Database](http://schemas.microsoft.com/sqlserver/) informazioni)<br /><br /> `Heap` Elemento (vedere [Engine Tuning Advisor XML schema di Database](http://schemas.microsoft.com/sqlserver/) informazioni)|  
  
## <a name="remarks"></a>Remarks  
 Questo elemento appartiene al nome **CreateTypecomplexType** nell'XML Schema dell'Ottimizzazione guidata motore di database. Viene utilizzato per creare indici, statistiche e strutture heap per una configurazione specificata dall'utente. Questo elemento `Create` non deve essere confuso con altri tipi che è possibile utilizzare per creare viste (`CreateViewType`) o per il partizionamento (`CreatePType`). Consultare il [Engine Tuning Advisor XML schema di Database](http://schemas.microsoft.com/sqlserver/) per informazioni su questi altri `Create` tipi di elemento.  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  