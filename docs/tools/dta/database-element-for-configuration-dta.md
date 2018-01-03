---
title: Elemento database per Configuration (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: dta
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e65efde942a30cf6e173ad2558c0eb7899723d11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="database-element-for-configuration-dta"></a>Elemento Database per Configuration (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Specifica il database in cui si desidera Database Ottimizzazione guidata motore di valutazione della configurazione ipotetica (specificato da di **configurazione** elemento).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|nessuna.|  
|**Valore predefinito**|nessuna.|  
|**Occorrenza**|Obbligatorio una o più volte in base all'elemento **Server** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Server per Configuration &#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)|  
|**Elementi figlio**|[Elemento Name per Database &#40;DTA&#41;](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [Elemento Schema per Database &#40;DTA&#41;](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [Elemento Recommendation &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento appartiene al nome **DatabaseTypecomplexType** nell'XML Schema di Ottimizzazione guidata motore di database. Questo elemento **Database** non deve essere confuso con l'elemento il cui padre di livello radice è l'elemento **Server** presente all'inizio del file di input XML. Per altre informazioni, vedere [Elemento Database per Server &#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo dell'elemento **Database**, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
