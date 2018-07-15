---
title: Classe di evento PreConnect:Starting | Microsoft Docs
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
- PreConnect:Starting Event Class
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b980169a5ade2694d1c35fb77c0b9ffd94d22b0b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316341"
---
# <a name="preconnectstarting-event-class"></a>Classe di evento PreConnect:Starting
  La classe di evento PreConnect:Starting indica l'avvio dell'esecuzione di un trigger LOGON o di una funzione di classificazione di Resource Governor.  
  
## <a name="preconnectstarting-event-class-data-columns"></a>Colonne di dati della classe di evento PreConnect:Starting  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|215|27|no|  
|SPID|`int`|ID del processo del server che genera l'evento.|12|Sì|  
|EventSubClass|`int`|1 per la funzione di classificazione definita dall'utente.|21|Sì|  
|StartTime|`datetime`|Ora di avvio della funzione di classificazione definita dall'utente.|14|Sì|  
|ObjectID|`int`|ID dell'oggetto di classificazione definito dall'utente.|22|Sì|  
|ObjectName|`nvarchar(256)`|Nome in due parti della funzione di classificazione definita dall'utente, ad esempio dbo.classifier.|34|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [classe di evento PreConnect:Completed](preconnect-completed-event-class.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  
