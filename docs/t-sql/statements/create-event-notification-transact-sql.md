---
title: CREARE la notifica degli eventi (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_EVENT_NOTIFICATION_TSQL
- NOTIFICATION_TSQL
- EVENT
- NOTIFICATION
- CREATE EVENT NOTIFICATION
- EVENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EVENT NOTIFICATION statement
- events [SQL Server], notifications
- event notifications [SQL Server], creating
ms.assetid: dbbff0e8-9e25-4f12-a1ba-e12221d16ac2
caps.latest.revision: 64
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 82d4f844c44f92232c8ac9bebd5841460f93051c
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-event-notification-transact-sql"></a>CREATE EVENT NOTIFICATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un oggetto che invia a un servizio di Service Broker informazioni relative a un evento di un database o un server. Le notifiche degli eventi possono essere create solo mediante istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE EVENT NOTIFICATION event_notification_name   
ON { SERVER | DATABASE | QUEUE queue_name }   
[ WITH FAN_IN ]  
FOR { event_type | event_group } [ ,...n ]  
TO SERVICE 'broker_service' , { 'broker_instance_specifier' | 'current database' }  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *event_notification_name*  
 Nome della notifica degli eventi. Un nome di notifica dell'evento deve essere conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md) e deve essere univoco all'interno dell'ambito in cui sono stati creati: SERVER, DATABASE o *object_name*.  
  
 SERVER  
 Indica che l'ambito della notifica degli eventi corrisponde all'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se viene specificato questo parametro, la notifica viene attivata ogni volta che l'evento specificato nella clausola FOR si verifica nell'ambito dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 DATABASE  
 Indica che l'ambito della notifica degli eventi corrisponde al database corrente. Se viene specificato questo parametro, la notifica viene attivata ogni volta che l'evento specificato nella clausola FOR si verifica nel database corrente.  
  
 QUEUE  
 Indica che l'ambito della notifica corrisponde a una coda specifica nel database corrente. QUEUE può essere utilizzato solo se viene specificato anche FOR QUEUE_ACTIVATION o FOR BROKER_QUEUE_DISABLED.  
  
 *nome_coda*  
 Nome della coda a cui applicare la notifica degli eventi. *nome_coda* può essere specificato solo se viene specificata una coda.  
  
 WITH FAN_IN  
 Indica a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di inviare un solo messaggio per evento a qualsiasi servizio specificato per tutte le notifiche degli eventi che:  
  
-   Vengono create per lo stesso evento.  
  
-   Vengono create dalla stessa entità, ovvero sono identificate dallo stesso SID.  
  
-   Specificare lo stesso servizio e *broker_instance_specifier*.  
  
-   Specificano WITH FAN_IN.  
  
 Se ad esempio vengono create tre notifiche degli eventi con FOR ALTER_TABLE, WITH FAN_IN, la stessa clausola TO SERVICE e lo stesso SID, quando viene eseguita un'istruzione ALTER TABLE i messaggi creati da queste tre notifiche degli eventi vengono uniti in un unico messaggio. Il servizio di destinazione riceve pertanto un solo messaggio dell'evento.  
  
 *event_type*  
 Nome di un tipo di evento mediante il quale è stata causata l'esecuzione della notifica degli eventi. *event_type* può essere un [!INCLUDE[tsql](../../includes/tsql-md.md)] tipo di evento DDL, un tipo di evento di traccia SQL o un [!INCLUDE[ssSB](../../includes/sssb-md.md)] tipo di evento. Per un elenco di qualificazione [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di evento DDL, vedere [eventi DDL](../../relational-databases/triggers/ddl-events.md). I tipi di evento di [!INCLUDE[ssSB](../../includes/sssb-md.md)] sono QUEUE_ACTIVATION e BROKER_QUEUE_DISABLED. Per altre informazioni, vedere [Event Notifications](../../relational-databases/service-broker/event-notifications.md).  
  
 *event_group*  
 Nome di un gruppo predefinito di tipi di evento [!INCLUDE[tsql](../../includes/tsql-md.md)] o di Traccia SQL. Una notifica degli eventi può essere attivata dopo l'esecuzione di un qualsiasi evento appartenente a un gruppo di eventi. Per un elenco dei gruppi di eventi DDL, il [!INCLUDE[tsql](../../includes/tsql-md.md)] coprono eventi e l'ambito in cui possono essere definiti, vedere [gruppi di eventi DDL](../../relational-databases/triggers/ddl-event-groups.md).  
  
 *event_group* inoltre utilizzato come macro, al termine dell'esecuzione dell'istruzione CREATE EVENT NOTIFICATION, aggiungendo i tipi di evento inclusi il **Sys. Events** vista del catalogo.  
  
 **'** *broker_service* **'**  
 Viene specificato il servizio di destinazione tramite cui vengono ricevuti i dati dell'istanza dell'evento. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono avviate una o più conversazioni con il servizio di destinazione per la notifica degli eventi. Questo servizio deve utilizzare lo stesso tipo di messaggio e lo stesso contratto per gli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicati per l'invio del messaggio.  
  
 Le conversazioni rimangono aperte fino a quando la notifica degli eventi non viene eliminata. Alcuni errori possono causare una terminazione anticipata delle conversazioni. Una terminazione esplicita di una parte delle conversazioni o di tutte le conversazioni può impedire al servizio di destinazione di ricevere ulteriori messaggi.  
  
 { **'***broker_instance_specifier***'** | **'current database'** }  
 Specifica un'istanza di service broker in cui *broker_service* viene risolto. Il valore per un'istanza specifica di service broker può essere acquisite mediante l'esecuzione di query di **service_broker_guid** colonna del **Sys. Databases** vista del catalogo. Utilizzare **'current database'** per specificare l'istanza di service broker nel database corrente. **'current database'** è un valore letterale stringa tra maiuscole e minuscole.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] prevede un tipo di messaggio e un contratto specifici per le notifiche degli eventi. Pertanto, essendo già disponibile un servizio di inizializzazione di Service Broker che specifica il nome di contratto `http://schemas.microsoft.com/SQL/Notifications/PostEventNotification`, non è necessario crearne uno.  
  
 Il servizio di destinazione che riceve le notifiche degli eventi deve rispettare il contratto esistente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] per le notifiche degli eventi che prevedono l'invio di messaggi a Service Broker su un server remoto. La sicurezza del dialogo deve essere configurata manualmente in base al modello di sicurezza avanzata. Per ulteriori informazioni, vedere [configurare la sicurezza del dialogo per le notifiche degli eventi](../../relational-databases/service-broker/configure-dialog-security-for-event-notifications.md).  
  
 Se viene eseguito il rollback di una transazione di evento che attiva una notifica, verrà annullato anche l'invio della notifica degli eventi. Le notifiche degli eventi non vengono attivate da un'azione definita in un trigger quando viene eseguito il commit o il rollback della transazione all'interno del trigger. Poiché gli eventi di traccia non sono associati a transazioni, le notifiche degli eventi basate su eventi di traccia vengono inviate anche se viene eseguito il rollback della transazione da cui sono attivate.  
  
 Se la conversazione tra il server e il servizio di destinazione viene interrotta dopo l'attivazione di una notifica degli eventi, viene segnalata la presenza di un errore e la notifica degli eventi viene eliminata.  
  
 La transazione di evento che aveva avviato in origine la notifica non è influenzata dall'esito positivo o negativo della notifica degli eventi.  
  
 Gli errori che si verificano durante l'invio di una notifica degli eventi vengono registrati.  
  
## <a name="permissions"></a>Permissions  
 Per creare una notifica degli eventi con ambito database (ON DATABASE), è necessario disporre dell'autorizzazione CREATE DATABASE DDL EVENT NOTIFICATION per il database corrente.  
  
 Per creare una notifica degli eventi per un'istruzione DDL con ambito server (ON SERVER), è necessario disporre dell'autorizzazione CREATE DDL EVENT NOTIFICATION nel server.  
  
 Per creare una notifica degli eventi per un evento di traccia, è necessario disporre dell'autorizzazione CREATE TRACE EVENT NOTIFICATION nel server.  
  
 Per creare una notifica degli eventi con ambito coda, è necessario disporre dell'autorizzazione ALTER per la coda.  
  
## <a name="examples"></a>Esempi  
  
> [!NOTE]  
>  Negli Esempi A e B seguenti il GUID nella clausola `TO SERVICE 'NotifyService'` ('8140a771-3c4b-4479-8ac0-81008ab17984') è specifico del computer in cui è stato configurato l'esempio. Per tale istanza, su tratta del GUID per il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
>   
>  Per copiare ed eseguire questi esempi, è necessario sostituire il GUID con quello del computer e dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in uso. Come illustrato nella sezione argomenti precedente, è possibile acquisire il **'***broker_instance_specifier***'** eseguendo una query sulla colonna service_broker_guid di Sys. Databases vista del catalogo.  
  
### <a name="a-creating-an-event-notification-that-is-server-scoped"></a>A. Creazione di una notifica degli eventi con ambito server  
 Nell'esempio seguente vengono creati gli oggetti necessari per la configurazione di un servizio di destinazione con [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Il servizio di destinazione fa riferimento al tipo di messaggio e al contratto del servizio di inizializzazione per le notifiche degli eventi, quindi viene creata una notifica degli eventi per tale servizio di destinazione che invia una notifica ogni volta che si verifica un evento di traccia `Object_Created` nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
--Create a queue to receive messages.  
CREATE QUEUE NotifyQueue ;  
GO  
--Create a service on the queue that references  
--the event notifications contract.  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
([http://schemas.microsoft.com/SQL/Notifications/PostEventNotification]);  
GO  
--Create a route on the service to define the address   
--to which Service Broker sends messages for the service.  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
--Create the event notification.  
CREATE EVENT NOTIFICATION log_ddl1   
ON SERVER   
FOR Object_Created   
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
### <a name="b-creating-an-event-notification-that-is-database-scoped"></a>B. Creazione di una notifica degli eventi con ambito database  
 Nell'esempio seguente viene creata una notifica degli eventi per lo stesso servizio di destinazione utilizzato nell'esempio precedente. La notifica degli eventi viene attivata dopo che si verifica un evento `ALTER_TABLE` nel database di esempio [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```tsql  
CREATE EVENT NOTIFICATION Notify_ALTER_T1  
ON DATABASE  
FOR ALTER_TABLE  
TO SERVICE 'NotifyService',  
    '8140a771-3c4b-4479-8ac0-81008ab17984';  
```  
  
### <a name="c-getting-information-about-an-event-notification-that-is-server-scoped"></a>C. Recupero di informazioni su una notifica degli eventi con ambito server  
 Nell'esempio seguente viene eseguita una query sulla vista del catalogo `sys.server_event_notifications` per recuperare metadati sulla notifica degli eventi `log_ddl1` definita a livello di ambito del server.  
  
```  
SELECT * FROM sys.server_event_notifications  
WHERE name = 'log_ddl1';  
```  
  
### <a name="d-getting-information-about-an-event-notification-that-is-database-scoped"></a>D. Recupero di informazioni su una notifica degli eventi con ambito database  
 Nell'esempio seguente viene eseguita una query sulla vista del catalogo `sys.event_notifications` per recuperare metadati sulla notifica degli eventi `Notify_ALTER_T1` definita a livello di ambito del database.  
  
```tsql  
SELECT * FROM sys.event_notifications  
WHERE name = 'Notify_ALTER_T1';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Notifiche degli eventi](../../relational-databases/service-broker/event-notifications.md)   
 [DROP EVENT NOTIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-event-notification-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Sys. event_notifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)   
 [server_event_notifications &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)   
 [Sys. Events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-events-transact-sql.md)   
 [Sys. server_events &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-events-transact-sql.md)  
  
  

