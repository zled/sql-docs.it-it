---
title: Errore del motore di database MSSQLSERVER_802 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 6f77f62eea2dac69a4d9d9b4b0ce3beb78136214
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver802---database-engine-error"></a>Errore del motore di database MSSQLSERVER_802
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|802|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|NO_BUFS|  
|Testo del messaggio|Memoria insufficiente nel pool di buffer.|  
  
## <a name="explanation"></a>Spiegazione  
L'errore è causato dal fatto che il pool di buffer è pieno e non è possibile aumentarne le dimensioni.  
  
## <a name="user-action"></a>Azione dell'utente  
Nell'elenco seguente viene illustrata la procedura generale per la risoluzione degli errori di memoria:  
  
1.  Verificare se altre applicazioni o servizi utilizzano la memoria nel server specificato. Riconfigurare le applicazioni o i servizi meno critici per utilizzare una quantità di memoria inferiore.  
  
2.  Iniziare a raccogliere i dati dei contatori di Performance Monitor per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Gestione buffer** e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**: Gestione memoria**.  
  
3.  Verificare i seguenti parametri di configurazione della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Valutare eventuali impostazioni non comuni e correggerle se necessario. Considerare i requisiti di memoria aggiuntivi per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le impostazioni predefinite sono elencate nell'argomento "Impostazione delle opzioni di configurazione del server" nella documentazione online di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Osservare l'output di DBCC MEMORYSTATUS e il modo in cui viene modificato quando vengono visualizzati questi messaggi di errore.  
  
5.  Verificare il carico di lavoro (numero di sessioni simultanee, query attualmente in esecuzione).  
  
Per aumentare la quantità di memoria disponibile per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], effettuare le operazioni seguenti:  
  
-   Se le risorse vengono utilizzate da altre applicazioni oltre a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], provare ad arrestare tali applicazioni o a eseguirle in un server distinto.  
  
-   Se è stata configurata l'opzione **max server memory,**, aumentarne il valore impostato.  
  
Eseguire i comandi DBCC seguenti per liberare diverse cache in memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Se il problema persiste, sarà necessario analizzarlo in modo più dettagliato e cercare di ridurre il carico di lavoro.  
  
