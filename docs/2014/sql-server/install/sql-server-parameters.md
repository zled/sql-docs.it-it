---
title: I parametri del Server SQL | Documenti Microsoft
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
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1a0c7676aa40d78967f6ff97a6ac91cdef4f0844
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36054909"
---
# <a name="sql-server-parameters"></a>Parametri per SQL Server
  In questa pagina impostare i parametri che verranno utilizzati per l'analisi del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. È possibile analizzare uno, alcuni o tutti i database, analizzare i file di traccia che sono stati creati tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]e analizzare i file batch SQL.  
  
> [!NOTE]  
>  Alcuni problemi di aggiornamento possono essere rilevati solo se si inviano file di traccia o file batch SQL per l'analisi.  
  
## <a name="options"></a>Opzioni  
 **Database da analizzare**  
 Per analizzare tutti i database, selezionare il **tutti i database** casella di controllo. Per analizzare una selezione di database, selezionare la casella di controllo accanto a ogni database per includerlo nell'analisi.  
  
 **Analizza file di traccia**  
 Selezionare questa casella di controllo per analizzare i file di traccia nel file system.  
  
 **Percorso dei file di traccia**  
 È possibile analizzare uno o più file. Selezionare più file in un percorso oppure specificare più nomi di file. Utilizzare il percorso completo di ogni file, includere il nome del file e separare le voci con il carattere barra verticale (|).  
  
 Se si abilita **Analizza file di traccia**, **successivo** rimane disabilitato finché non si immette un nome di percorso e un nome di file.  
  
 **Analizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch dei file**  
 Selezionare questa casella di controllo per analizzare i file batch [!INCLUDE[tsql](../../includes/tsql-md.md)] nel file system.  
  
 **Percorso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] batch dei file**  
 È possibile analizzare uno o più file batch. Selezionare più file in un percorso oppure specificare più nomi di file. Utilizzare il percorso completo di ogni file, includere il nome del file e separare le voci con il carattere barra verticale (|).  
  
 Se si abilita **Analizza file batch SQL**, la **successivo** pulsante è disabilitato fino a quando non si immette un nome di percorso e un nome di file.  
  
 **Separatore Batch SQL**  
 Testo utilizzato per separare i batch di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. Il valore predefinito è **GO**.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di preparazione aggiornamento](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Riferimento all'interfaccia utente di preparazione aggiornamento](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  