---
title: Classe di evento Broker:Message Drop | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Broker:Message Drop event class
ms.assetid: f532b7c9-ca34-4bac-8dc3-53f9895fd6af
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 47fd82b02e3d808d2609e5c9830099d11627795f
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="brokermessage-drop-event-class"></a>Broker:Message Drop - classe di evento
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] genera un evento **Broker:Message Drop** quando Service Broker non è in grado di trattenere un messaggio ricevuto che avrebbe dovuto essere recapitato a un servizio dell'istanza. Per i messaggi che avrebbero dovuto essere inoltrati, vedere [Classe di evento Broker:Forwarded Message Dropped](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md).  
  
## <a name="brokermessage-drop-event-class-data-columns"></a>Colonne di dati della classe di evento Broker:Message Drop  
  
|Colonna di dati|Tipo|Descrizione|Numero colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**Application Name**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**BigintData1**|**bigint**|Numero di sequenza del messaggio eliminato.|52|No|  
|**BigintData2**|**bigint**|Numero di sequenza dell'ultimo messaggio riconosciuto correttamente.|53|No|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita un'istruzione USE *database* . [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**Errore**|**int**|Numero di ID del messaggio in **sys.messages** relativo al testo dell'evento.|31|No|  
|**EventClass**|**int**|Tipo di classe di evento acquisita. Per **Broker:MessageDrop** , corrisponde sempre a **160**.|27|No|  
|**EventSequence**|**int**|Numero di sequenza dell'evento.|51|No|  
|**EventSubClass**|**nvarchar**|Indica se il messaggio eliminato è un messaggio in sequenza. È possibile specificare uno dei due valori seguenti:<br /><br /> **Messaggio in sequenza**. Il messaggio eliminato è un messaggio in sequenza.<br /><br /> **Messaggio non in sequenza**. Il messaggio eliminato non è un messaggio in sequenza.|21|Sì|  
|**GUID**|**uniqueidentifier**|ID della conversazione a cui appartiene il messaggio eliminato. Questo identificatore viene trasmesso come parte del messaggio e viene condiviso da entrambi i lati della conversazione.|54|No|  
|**HostName**|**nvarchar**|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IntegerData**|**int**|Numero di frammento del messaggio eliminato.|25|No|  
|**IntegerData2**|**int**|Numero di frammento riconosciuto dal messaggio eliminato.|55|No|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|No|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di Windows nel formato DOMINIO\nomeutente).|11|No|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|**nvarchar**|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|**NTUserName**|**nvarchar**|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|**ObjectName**|**nvarchar**|Handle di conversazione del dialogo.|34|No|  
|**RoleName**|**nvarchar**|Ruolo dell'handle di conversazione. I valori possibili sono **initiator** o **target**.|38|No|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**Severity**|**int**|Numero di gravità per il testo dell'evento.|29|No|  
|**SPID**|**int**|ID del processo server assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al processo associato al client.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**State**|**int**|Indica la posizione che ha generato l'evento all'interno del codice sorgente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ogni punto che può generare questo evento è contraddistinto da un codice di stato diverso. Questo codice di stato consente al supporto tecnico Microsoft di individuare la posizione in cui è stato generato l'evento.|30|No|  
|**TextData**|**ntext**|Motivo per cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ha eliminato il messaggio.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|No|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)  
  
  
