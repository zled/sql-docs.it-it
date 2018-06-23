---
title: MSSQLSERVER_2518 | Microsoft Docs
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
- 2518 (Database Engine error)
ms.assetid: 54a13abc-4c33-43f0-b55d-e2e74a1381c8
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f40eb8fe404479f5a2bcd68881aec4b2b2d84613
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067601"
---
# <a name="mssqlserver2518"></a>MSSQLSERVER_2518
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|2518|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DBCC_NO_EXPRESSION_EVAL_CLR_DISABLED|  
|Testo del messaggio|ID oggetto O_ID (oggetto "O_NAME"): impossibile verificare colonne calcolate e tipi definiti dall'utente per questo oggetto perché Common Language Runtime (CLR) è disabilitato.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo messaggio informativo indica che Query Processor non è riuscito a fornire a DBCC un oggetto interno per consentire la restituzione delle colonne calcolate e dei tipi CLR (Common Language Runtime) definiti dall'utente. Il problema si verifica perché CLR è incluso in una delle colonne, ma non è attivato. L'oggetto interno è incluso in tutte le colonne. Pertanto, l'impossibilità di restituire una singola colonna impedisce la creazione dell'oggetto interno. Ciò significa che non verrà controllata la correttezza delle colonne calcolate o che quest'ultime non verranno utilizzate durante il controllo DBCC della consistenza tra indici e tabelle di base.  
  
## <a name="user-action"></a>Azione dell'utente  
 Attivare CLR ed eseguire nuovamente l'istruzione DBCC.  
  
## <a name="see-also"></a>Vedere anche  
 [Abilitazione dell'integrazione con CLR](../clr-integration/clr-integration-enabling.md)  
  
  