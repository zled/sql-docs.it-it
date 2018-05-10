---
title: MSSQLSERVER_17130 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17130 (Database Engine error)
ms.assetid: 7ce6afca-221d-402f-89df-da7e74a339a8
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e715843dd8a6bca9a8fad8f5dc6b3b62eef0ae5c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17130"></a>MSSQLSERVER_17130
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
