---
title: MSSQLSERVER_18264 | Microsoft Docs
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
- 18264 (Database Engine error)
ms.assetid: 3050fc56-2be5-43cf-916b-50a3ac5f89aa
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 06ae22f5e2e7344a5934493bb893a07bdb20383a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver18264"></a>MSSQLSERVER_18264
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|Microsoft SQL Server|  
|ID evento|18264|  
|Origine evento|MSSQLENGINE|  
|Componente|SQLEngine|  
|Nome simbolico|STRMIO_DBDUMP|  
|Testo del messaggio|Backup del database eseguito: database: %s, data (ora) di creazione: %s(%s), pagine copiate: %d, primo LSN: %s, ultimo LSN: %s, numero di dispositivi di dump: %d, informazioni dispositivo: (%s). Questo è un messaggio informativo. Non è richiesta alcuna azione da parte dell'utente.|  
  
## <a name="explanation"></a>Spiegazione  
Per impostazione predefinita, per ogni backup eseguito in modo corretto viene aggiunto questo messaggio informativo al log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e al registro eventi di sistema. Se il backup del log delle transazioni viene eseguito di frequente, questi messaggi possono aumentare rapidamente, provocando la creazione di log degli errori di grandi dimensioni e rendendo difficile l'individuazione di altri messaggi.  
  
## <a name="user-action"></a>Azione dell'utente  
È possibile eliminare queste voci di log mediante il flag di traccia **3226** di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'abilitazione di questo flag di traccia risulta utile se si eseguono backup del log frequenti e se nessuno degli script dipende da tali voci.  
  
Per informazioni sull'utilizzo dei flag di traccia, vedere la documentazione online di SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
[Flag di traccia &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)  
  

