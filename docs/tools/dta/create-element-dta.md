---
title: Elemento create (DTA) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: XML
helpviewer_keywords: Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 02dc029883c6d10ed523e4762b843349cb8f420a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
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
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Obbligatorio una sola volta per ogni struttura di progettazione fisica, quali indici, statistiche o strutture heap.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Recommendation &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Elementi figlio**|[Elemento Index &#40;DTA&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Elemento**Statistics** . Per informazioni, vedere l' [XML Schema dell'Ottimizzazione guidata motore di database](http://schemas.microsoft.com/sqlserver/) <br /><br /> Elemento**Heap** . Per informazioni, vedere l' [XML Schema dell'Ottimizzazione guidata motore di database](http://schemas.microsoft.com/sqlserver/) |  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento appartiene al nome **CreateTypecomplexType** nell'XML Schema dell'Ottimizzazione guidata motore di database. Viene utilizzato per creare indici, statistiche e strutture heap per una configurazione specificata dall'utente. Non confondere l'elemento **Create** con altri tipi che possono essere usati per creare viste (**CreateViewType**) o partizionamenti (**CreatePType**). Per informazioni su questi altri tipi di elemento [Create](http://schemas.microsoft.com/sqlserver/) , vedere l' **XML Schema dell'Ottimizzazione guidata motore di database** .  
  
## <a name="example"></a>Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento ai file di input XML&#40; (Ottimizzazione guidata motore di database)&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
