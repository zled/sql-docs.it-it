---
title: MSSQLSERVER_4846 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 4846 (Database Engine error)
ms.assetid: a455e809-1883-4c7d-b3e3-835ee5bfe258
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0b9152072fde4c139602eecef4a182e3e2cd1300
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver4846"></a>MSSQLSERVER_4846
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|4846|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|BULKPROV_MEMORY|  
|Testo del messaggio|Il provider di dati bulk non è in grado di allocare memoria.|  
  
## <a name="explanation"></a>Spiegazione  
L'allocazione di memoria ha avuto esito negativo.  
  
## <a name="user-action"></a>Azione dell'utente  
Per risolvere gli errori di memoria, eseguire la procedura seguente:  
  
1.  Verificare se altre applicazioni o servizi utilizzano la memoria nel server specificato. Riconfigurare le applicazioni o i servizi meno critici per utilizzare una quantità di memoria inferiore.  
  
2.  Iniziare a raccogliere i dati dei contatori di monitoraggio delle prestazioni per **SQL Server: Gestione buffer** e **SQL Server: Gestione memoria**.  
  
3.  Verificare i seguenti parametri di configurazione della memoria di SQL Server:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Valutare eventuali impostazioni non comuni e, se necessario, correggerle. Considerare i requisiti di memoria per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Le impostazioni predefinite sono elencate nell'argomento "Impostazione delle opzioni di configurazione del server" nella documentazione online di SQL Server.  
  
4.  Osservare l'output di DBCC MEMORYSTATUS e il modo in cui viene modificato quando vengono visualizzati questi messaggi di errore.  
  
5.  Verificare il carico di lavoro (ad esempio, numero di sessioni simultanee, query attualmente in esecuzione).  
  
Per aumentare la quantità di memoria disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effettuare le operazioni seguenti:  
  
-   Se le risorse vengono utilizzate da altre applicazioni oltre a SQL Server, provare a interromperne l'esecuzione o a eseguirle in un server distinto. In questo modo sarà possibile eliminare le richieste di memoria esterne.  
  
-   Se è stata configurata l'opzione **max server memory,**, aumentarne il valore impostato.  
  
Eseguire i comandi DBCC seguenti per liberare diverse cache in memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Se il problema persiste, sarà necessario analizzarlo in modo più dettagliato e cercare di ridurre il carico di lavoro.  
  

