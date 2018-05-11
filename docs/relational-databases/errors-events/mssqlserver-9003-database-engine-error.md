---
title: MSSQLSERVER_9003 | Microsoft Docs
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
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2bfbc48941ff3d647e94060b46b451c974d4bba1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|9003|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LOG_INVALID_LSN|  
|Testo del messaggio|Il numero di analisi log %S_LSN passato alla funzione di analisi dei log nel database '%.*ls' non è valido. L'errore può indicare la presenza di dati danneggiati o un problema di mancata corrispondenza tra il file di log (con estensione ldf) e il file di dati (con estensione mdf). Se l'errore si è verificato durante la replica, ricreare la pubblicazione. Se invece il problema provoca un errore all'avvio, eseguire il ripristino da un backup.|  
  
## <a name="explanation"></a>Spiegazione  
Un componente ha passato un numero di sequenza del file di log (LSN) non valido allo strumento di gestione del log per il database. L'errore potrebbe verificarsi durante la replica oppure in presenza di dati danneggiati o di incoerenza tra il file di dati primario e il log.  
  
## <a name="user-action"></a>Azione dell'utente  
Se l'errore si è verificato durante la replica, ricreare la pubblicazione. In caso contrario, eseguire un ripristino dal backup.  
  
