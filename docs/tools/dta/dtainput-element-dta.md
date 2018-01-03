---
title: Elemento DTAInput (DTA) | Documenti Microsoft
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
helpviewer_keywords: DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
caps.latest.revision: "15"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0ee58e6b5ec7215353296a1b17151b2354eb5e2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="dtainput-element-dta"></a>Elemento DTAInput (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Contiene la definizione dell'input XML per ottimizzazione guidata motore di Database.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristiche|Description|  
|---------------------|-----------------|  
|**Tipo di dati e lunghezza**|nessuna.|  
|**Valore predefinito**|nessuna.|  
|**Occorrenza**|Facoltativo una volta per ogni elemento **DTAXML** .|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DTAXML &#40;DTA&#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**Elementi figlio**|[Elemento Server &#40;DTA&#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Elemento Workload &#40;DTA&#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [Elemento TuningOptions &#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Elemento Configuration &#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Questo è l'elemento radice della gerarchia dello schema di input di Ottimizzazione guidata motore di database. L'input in Ottimizzazione guidata motore di database può essere costituito da argomenti che specificano i server di cui si desidera ottimizzare i database, i carichi di lavoro, le opzioni di ottimizzazione o una configurazione specificata dall'utente.  
  
## <a name="example"></a>Esempio  
 Per un esempio d'uso dell'elemento **DTAInput**, vedere [Esempio di file di input XML semplice &#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
