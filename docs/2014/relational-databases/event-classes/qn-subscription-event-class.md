---
title: Classe di evento QN:Subscription | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Subscription
ms.assetid: 4916167e-8541-43b4-900e-ec8e6adcbc34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7d60680f4c6f286db1c1d0e47961e75b057b14a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192101"
---
# <a name="qnsubscription-event-class"></a>Classe di evento QN:Subscription
  L'evento QN:Subscription fornisce informazioni sulle sottoscrizioni di notifica.  
  
## <a name="qnsubscription-event-class-data-columns"></a>Colonne dati della classe di evento QN:Subscription  
  
|Colonna di dati|Tipo|Description|Numero colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|ClientProcessID|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|DatabaseID|`int`|ID del database specificato dall'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita alcuna istruzione USE *database*. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] viene visualizzato il nome del database se la colonna di dati ServerName viene acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|DatabaseName|`nvarchar`|Nome del database in cui viene eseguita l'istruzione dell'utente.|35|Sì|  
|EventClass|`int`|Tipo di evento = 199.|27|no|  
|EventSequence|`int`|Numero di sequenza dell'evento.|51|no|  
|EventSubClass|`nvarchar`|Tipo di sottoclasse di evento in cui sono disponibili informazioni aggiuntive su ogni classe di evento. Questa colonna può contenere i valori seguenti:<br /><br /> Sottoscrizione registrata: indica quando la sottoscrizione di notifica delle query viene registrata correttamente nel database.<br /><br /> Sottoscrizione riavvolto: indica quando il [!INCLUDE[ssDE](../../includes/ssde-md.md)] riceve una richiesta di sottoscrizione che corrisponde esattamente a una sottoscrizione esistente. In tal caso, [!INCLUDE[ssDE](../../includes/ssde-md.md)] imposta il valore di timeout della sottoscrizione esistente sul timeout specificato nella nuova richiesta di sottoscrizione.<br /><br /> Sottoscrizione è stata attivata: indica quando una sottoscrizione di notifica genera un messaggio di notifica.<br /><br /> Generazione dell'evento non è riuscita con errore di Service broker: indica quando un messaggio di notifica ha esito negativo a causa dell'errore una [!INCLUDE[ssSB](../../includes/sssb-md.md)] errore.<br /><br /> Generazione dell'evento non è riuscita senza errore Service broker: indica quando un messaggio di notifica ha esito negativo, ma non a causa un [!INCLUDE[ssSB](../../includes/sssb-md.md)] errore.<br /><br /> Broker l'errore intercettato: indica che [!INCLUDE[ssSB](../../includes/sssb-md.md)] recapitato un errore nella conversazione usata dalla notifica delle query.<br /><br /> Tentativo di eliminazione sottoscrizione: indica che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha tentato di eliminare una sottoscrizione scaduta per liberare risorse.<br /><br /> L'eliminazione di sottoscrizione non è riuscita: indica che il tentativo di eliminare una sottoscrizione scaduta non è riuscito. [!INCLUDE[ssDE](../../includes/ssde-md.md)] ripianificherà automaticamente la sottoscrizione per l'eliminazione allo scopo di liberare risorse.<br /><br /> Sottoscrizione eliminata: indica che il [!INCLUDE[ssDE](../../includes/ssde-md.md)] eliminato correttamente una sottoscrizione scaduta|21|Sì|  
|GroupID|`int`|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Sì|  
|HostName|`nvarchar`|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|IsSystem|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente.<br /><br /> 0 = utente<br /><br /> 1 = sistema|60|no|  
|LoginName|`nvarchar`|Nome dell'account di accesso dell'utente (account di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di Windows nel formato DOMINIO\nomeutente).|11|no|  
|LoginSID|`image`|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|NTDomainName|`nvarchar`|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|NTUserName|`nvarchar`|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|RequestID|`int`|Identificatore della richiesta contenente l'istruzione.|49|Sì|  
|ServerName|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|SessionLoginName|`nvarchar`|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio un'applicazione si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 ed esegue un'istruzione con l'account di accesso Login2, SessionLoginName indica "Login1" e LoginName indica "Login2". In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|SPID|`int`|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|StartTime|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|TextData|`ntext`|Restituisce un documento XML contenente informazioni specifiche per questo evento. Questo documento è conforme XML Schema disponibile nella pagina [Schema di eventi di SQL Server Profiler correlati alle notifiche delle query](http://go.microsoft.com/fwlink/?LinkId=63331) .|1|Sì|  
  
  
