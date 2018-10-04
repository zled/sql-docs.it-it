---
title: Elemento database per Configuration (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1a3547d10f325e047174f7106267b480084e88df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48062036"
---
# <a name="database-element-for-configuration-dta"></a>Elemento Database per Configuration (DTA)
  Specifica il database sulla quale si desidera Database Ottimizzazione guidata motore di valutazione della configurazione ipotetica (specificato da di `Configuration` elemento).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuna.|  
|**Valore predefinito**|Nessuna.|  
|**Occorrenza**|Obbligatorio una o più volte per ogni `Server` elemento.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento server per la configurazione &#40;DTA&#41;](server-element-for-configuration-dta.md)|  
|**Elementi figlio**|[Nome di elemento per il Database &#40;DTA&#41;](name-element-for-database-dta.md)<br /><br /> [Elemento schema per il Database &#40;DTA&#41;](schema-element-for-database-dta.md)<br /><br /> [Elemento Recommendation &#40;DTA&#41;](recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Note  
 Questo elemento appartiene al nome **DatabaseTypecomplexType** nell'XML Schema di Ottimizzazione guidata motore di database. Questo elemento `Database` non deve essere confuso con l'elemento il cui padre di livello radice è l'elemento `Server` presente all'inizio del file di input XML. Per altre informazioni, vedere [Elemento Database per Server &#40;DTA&#41;](database-element-for-server-dta.md).  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo `Database` elemento, vedere la [esempio di File di Input XML con configurazione specificata dall'utente &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
