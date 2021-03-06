---
title: Classe di evento Deadlock Graph | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deadlock Graph event class
ms.assetid: 20f92233-c912-4382-8993-8e2e23d03fbe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d27707fc52c2620d6905cbd23e1b710f927bd58b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105741"
---
# <a name="deadlock-graph-event-class"></a>Deadlock Graph - classe di evento
  La classe di evento **Deadlock Graph** fornisce una descrizione XML di un deadlock. Questa classe viene generata simultaneamente alla classe di evento **Lock:Deadlock** .  
  
## <a name="deadlock-graph-event-class-data-columns"></a>Colonne di dati della classe di evento Deadlock Graph  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Tipo di evento = 148.|27|no|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|no|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente. Il valore è sempre 1 per questo evento.|60|Sì|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di sicurezza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente). Il valore è sempre l'utente di sistema per questo evento.|11|Sì|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server. Il valore è sempre il SID dell'utente di sistema per questo evento.|41|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora in cui è stato rilevato il deadlock.|14|Sì|  
|**TextData**|**ntext**|Descrizione XML del deadlock.|1|Sì|  
|**TransactionID**|**bigint**|Non usato.|4|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Classe di evento Lock:Deadlock](lock-deadlock-event-class.md)  
  
  
