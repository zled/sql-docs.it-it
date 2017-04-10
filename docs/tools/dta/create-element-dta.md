---
title: "Elemento Create (DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Create - elemento (DTA)"
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# Elemento Create (DTA)
  Contiene informazioni su indici, statistiche o strutture heap in una configurazione specificata dall'utente.  
  
## Sintassi  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|Nessuno|  
|**Valore predefinito**|Nessuno|  
|**Occorrenza**|Obbligatorio una sola volta per ogni struttura di progettazione fisica, quali indici, statistiche o strutture heap.|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento Recommendation &#40;DTA&#41;](../../tools/dta/recommendation-element-dta.md)|  
|**Elementi figlio**|[Elemento Index &#40;DTA&#41;](../../tools/dta/index-element-dta.md)<br /><br /> Elemento **Statistics**. Per informazioni, vedere l'[XML Schema dell'Ottimizzazione guidata motore di database](http://schemas.microsoft.com/sqlserver/)<br /><br /> Elemento **Heap**. Per informazioni, vedere l'[XML Schema dell'Ottimizzazione guidata motore di database](http://schemas.microsoft.com/sqlserver/)|  
  
## Osservazioni  
 Questo elemento appartiene al nome **CreateTypecomplexType** nell'XML Schema dell'Ottimizzazione guidata motore di database. Viene utilizzato per creare indici, statistiche e strutture heap per una configurazione specificata dall'utente. Non confondere l'elemento **Create** con altri tipi che possono essere usati per creare viste (**CreateViewType**) o partizionamenti (**CreatePType**). Per informazioni su questi altri tipi di elemento [Create](http://schemas.microsoft.com/sqlserver/), vedere l'**XML Schema dell'Ottimizzazione guidata motore di database**.  
  
## Esempio  
 Per un esempio di utilizzo di questo elemento, vedere [Esempio di file di input XML con configurazione specificata dall'utente &#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md).  
  
## Vedere anche  
 [Guida di riferimento ai file di input XML &#40;Ottimizzazione guidata motore di database&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  