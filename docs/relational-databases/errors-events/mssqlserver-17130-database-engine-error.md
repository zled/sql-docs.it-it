---
title: MSSQLSERVER_17130 | Microsoft Docs
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
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bbf8c071d0f64b4fe09322179c7d71c538d9d6e7
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|17130|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|INIT_NOLOCKSPACE|  
|Testo del messaggio|Memoria insufficiente per il numero configurato di blocchi. Verrà tentato l'avvio con una tabella hash di blocchi più piccola, con possibili conseguenze sulle prestazioni. Per configurare più memoria per questa istanza del Motore di database, contattare l'amministratore.|  
  
## <a name="explanation"></a>Spiegazione  
Memoria insufficiente per le dimensioni desiderate della tabella hash di Gestione blocchi.  Verrà eseguito un tentativo di allocare una tabella hash di dimensioni minori.  
  
## <a name="user-action"></a>Azione dell'utente  
Verificare i parametri di configurazione della memoria del server (min server memory/max server memory) e il numero di richieste di memoria e fornire una quantità maggiore di memoria a SQL Server.  
  

