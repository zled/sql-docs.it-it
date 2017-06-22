---
title: MSSQLSERVER_30089 | Microsoft Docs
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
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c42bbbb05ba2cb78628433815effb5ef7ce48132
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver30089"></a>MSSQLSERVER_30089
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|30089|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|IFTS_FDHOST_TERMINATEDABNORMAL|  
|Testo del messaggio|Il processo host del daemon di filtri full-text (FDHost) si è arrestato in modo anomalo. Il problema può essere dovuto a un componente linguistico configurato in modo errato o non funzionante, ad esempio un word breaker, uno stemmer o un filtro, che ha causato un errore irreversibile durante l'indicizzazione full-text o l'elaborazione di query. Il processo verrà riavviato automaticamente.|  
  
## <a name="explanation"></a>Spiegazione  
Nell'host del daemon di filtri full-text si è verificato un problema che ha forzato l'arresto anomalo. La causa del problema può essere un documento formattato in modo non corretto, un bug nel filtro o nel word breaker oppure un errore nel daemon di filtri.  
  
## <a name="user-action"></a>Azione dell'utente  
In genere il daemon eseguirà il recupero dall'errore. Se il problema si ripete, è necessario risolverlo. Per isolare il problema, provare le soluzioni seguenti:  
  
1.  Se è stato installato recentemente un nuovo componente linguistico, rimuoverlo dal sistema.  
  
2.  Analizzare il log di tipo ricerca per identificare qualsiasi nuovo documento per cui non è stato possibile eseguire l'indicizzazione full-text, quindi rimuovere il documento.  
  
## <a name="see-also"></a>Vedere anche  
[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
[Configurare e gestire word breaker e stemmer per la ricerca](~/relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
[Configurare e gestire filtri per la ricerca](~/relational-databases/search/configure-and-manage-filters-for-search.md)  
  

