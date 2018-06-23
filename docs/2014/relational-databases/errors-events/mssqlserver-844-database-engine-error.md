---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 1a3f477e809b154c89b9e141739fb49c26e9eb35
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36169219"
---
# <a name="mssqlserver844"></a>MSSQLSERVER_844
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|844|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|BUFLATCH_TIMEOUT_CONTINUE|  
|Testo del messaggio|Timeout durante l'attesa del latch del buffer: tipo %d, bp %p, pagina %d:%d, stat %#x, ID database: %d, ID unità di allocazione:%I64d%ls, attività 0x%p: %d, attesa %d, flag 0x%I64x, attività proprietaria 0x%p.  L'attesa verrà protratta.|  
  
## <a name="explanation"></a>Spiegazione  
 Un processo è in attesa di acquisire un latch. Il problema può essere causato da un'operazione di I/O il cui completamento richiede troppo tempo. Questo tipo di errore in genere è dovuto ad altre attività che bloccano i processi di sistema. In alcuni casi, tuttavia, può essere dovuto a un errore hardware.  
  
## <a name="user-action"></a>Azione dell'utente  
 Per evitare che si verifichi questo errore, provare le soluzioni seguenti:  
  
-   Ridurre il carico di lavoro.  
  
-   Verificare la presenza di errori di I/O associati nel log degli errori o nel log eventi. Gli errori di I/O in genere sono dovuti a un malfunzionamento del disco.  
  
-   Controllare nel log degli errori la presenza di attività che non cedono la precedenza e di altri errori critici.  
  
-   Se si verificano spesso errori critici, ad esempio di asserzione, risolvere tali problemi.  
  
 Se l'errore persiste, contattare il Servizio Supporto Tecnico Clienti Microsoft.  
  
  