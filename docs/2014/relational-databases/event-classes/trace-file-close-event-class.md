---
title: Classe di evento Trace File Close | Microsoft Docs
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
- Trace File Close event class
ms.assetid: 128b7bac-cb64-43e7-ae9b-87b7d2ebb4ef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7992fe56c857baac774cdf8571efd3c1a0181e14
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213631"
---
# <a name="trace-file-close-event-class"></a>Trace File Close - classe di evento
  La classe di evento **Trace File Close** indica che un file di traccia è stato chiuso durante un rollover del file di traccia.  
  
## <a name="trace-file-close-event-class-data-columns"></a>Colonne di dati della classe di evento Trace File Close  
  
|Nome colonna di dati|Tipo di dati|Description|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**EventClass**|**int**|Tipo di evento = 150.|27|no|  
|**EventSequence**|**int**|Timestamp univoco di questo evento generato nella traccia. Si tratta di un valore a incremento progressivo costante per ogni evento generato.|51|no|  
|**FileName**|**nvarchar**|Nome logico del file di traccia chiuso.|36|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, NULL = utente. Il valore è sempre 1 per questa classe di evento.|60|Sì|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente). Il valore è sempre "sa" per questa classe di evento.|11|Sì|  
|**ObjectID**|**int**|ID della traccia assegnato dal sistema.|22|Sì|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
