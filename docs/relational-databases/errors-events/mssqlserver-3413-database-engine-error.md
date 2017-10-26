---
title: MSSQLSERVER_3413 | Microsoft Docs
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
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 38900b11bc5e2892ea85f22db2a6c1490d6399fb
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3413|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MARKDB|  
|Testo del messaggio|ID di database %d. Impossibile contrassegnare il database come sospetto. Analisi Getnext per NC su sys.databases.database_id non riuscita. Per identificare la causa e correggere gli eventuali problemi associati, fare riferimento agli errori precedenti nel log degli errori.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore imprevisto durante il tentativo di contrassegnare un database utente come SUSPECT nel catalogo. Lo stato SUSPECT non sarà persistente.  
  
## <a name="user-action"></a>Azione dell'utente  
Vedere gli errori precedenti e risolvere il problema.  
  

