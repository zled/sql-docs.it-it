---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1311779c5ff5bc452c92654231aafc3ce543de84
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17884"></a>MSSQLSERVER_17884
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17884|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|SRV_SCHEDULER_DEADLOCK|  
|Testo del messaggio|Nessun thread di lavoro ha prelevato nuove query assegnate al processo nel nodo % negli ultimi %d secondi. La situazione potrebbe essere causata da query bloccate o con esecuzione prolungata che possono peggiorare i tempi di risposta del client. Utilizzare l'opzione di configurazione "max worker thread" per aumentare il numero di thread consentiti oppure ottimizzare le query in esecuzione.  Utilizzo processo SQL: %d%%. Inattività del sistema: %d%%.|  
  
## <a name="explanation"></a>Spiegazione  
Non è presente alcun segnale relativo allo stato di avanzamento in alcuna utilità di pianificazione. Questa situazione potrebbe essere causata da deadlock per cui nessun thread può avanzare e/o nessun lavoro può essere scelto ed elaborato. Se l'utilizzo del processo è basso, gli altri processi presenti nel computer potrebbero provocare l'esaurimento delle risorse della CPU relative ai processi del server.  
  
## <a name="user-action"></a>Azione dell'utente  
Determinare il motivo del blocco e del mancato avanzamento e risolvere di conseguenza la situazione. Se l'utilizzo del processo è basso, controllare il carico nel sistema provocato dagli altri processi.  
  
