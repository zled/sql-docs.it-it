---
title: Classe di evento PreConnect:Completed | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a91728174a11ecf1cdd008b5aa1c9829da890ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150692"
---
# <a name="preconnectcompleted-event-class"></a>classe di evento PreConnect:Completed
  La classe di evento PreConnect:Completed indica la fine dell'esecuzione di un trigger LOGON o di una funzione di classificazione di Resource Governor.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Colonne di dati della classe di evento PreConnect:Completed  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|no|  
|SPID|`int`|ID del processo del server che genera l'evento.|12|Sì|  
|EventSubClass|`int`|1 per la funzione di classificazione definita dall'utente.|21|Sì|  
|StartTime|`datetime`|Ora di avvio della funzione di classificazione definita dall'utente.|14|Sì|  
|EndTime|`datetime`|Ora di avvio della funzione di classificazione definita dall'utente.|15|Sì|  
|Duration|`bigint`|Durata della funzione di classificazione in microsecondi.|13|Sì|  
|ObjectID|`int`|ID dell'oggetto di classificazione definito dall'utente.|22|Sì|  
|CPU|`int`|Utilizzo della CPU in millisecondi.|18|Sì|  
|Reads|`int`|Numero di letture logiche.|16|Sì|  
|Writes|`int`|Numero di scritture logiche.|17|Sì|  
|GroupID|`int`|ID del gruppo del carico di lavoro classificato.|66|Sì|  
|Errore|`int`|Ultimo numero di errore se non è possibile eseguire la funzione di classificazione definita dall'utente.|31|Sì|  
|State|`int`|Stato dell'ultimo errore.|30|Sì|  
|TargetUserName|`sysname`|Valore restituito (nome del gruppo del carico di lavoro) per la funzione di classificazione definita dall'utente se non è possibile trovare un gruppo attivo corrispondente. Negli altri casi la colonna è impostata su NULL.|39|Sì|  
|ObjectName|`nvarchar(256)`|Nome in due parti della funzione di classificazione definita dall'utente, ad esempio dbo.classifier.|34|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [Classe di evento PreConnect:Starting](preconnect-starting-event-class.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  
