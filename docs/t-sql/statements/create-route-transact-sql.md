---
title: CREARE ROUTE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_ROUTE_TSQL
- ROUTE
- CREATE ROUTE
- ROUTE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- lifetimes [Service Broker]
- routes [Service Broker], creating
- forwarding brokers [SQL Server]
- service names [Service Broker]
- database mirroring [SQL Server], routing
- expired routes [SQL Server]
- activating routes
- CREATE ROUTE statement
ms.assetid: 7e695364-1a98-4cfd-8ebd-137ac5a425b3
caps.latest.revision: "42"
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 767be5069d65c11dad849a8fc32f5b15296a4eda
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-route-transact-sql"></a>CREATE ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge una nuova route alla tabella di routing per il database corrente. Per i messaggi in uscita, [!INCLUDE[ssSB](../../includes/sssb-md.md)] determina il routing controllando la tabella di routing nel database locale. Per i messaggi per le conversazioni che hanno origine in un'altra istanza, inclusi i messaggi da inoltrare, [!INCLUDE[ssSB](../../includes/sssb-md.md)] archivia le route **msdb**.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE ROUTE route_name  
[ AUTHORIZATION owner_name ]  
WITH    
   [ SERVICE_NAME = 'service_name', ]  
   [ BROKER_INSTANCE = 'broker_instance_identifier' , ]  
   [ LIFETIME = route_lifetime , ]  
   ADDRESS =  'next_hop_address'  
   [ , MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *route_name*  
 Nome della route da creare. La nuova route viene creata nel database corrente e diventa di proprietà dell'identità specificata nella clausola AUTHORIZATION. Non è possibile specificare i nomi del server, del database e dello schema. Il *route_name* deve essere un valore valido **sysname**.  
  
 AUTORIZZAZIONE *owner_name*  
 Imposta il proprietario della route sull'utente o il ruolo di database specificato. Il *owner_name* può essere il nome di qualsiasi utente o ruolo valido quando l'utente corrente è un membro di entrambi i **db_owner** ruolo predefinito del database o **sysadmin** ruolo predefinito del server. In caso contrario, *owner_name* deve essere il nome dell'utente corrente, il nome di un utente che l'utente corrente dispone dell'autorizzazione IMPERSONATE oppure il nome di un ruolo a cui appartiene l'utente corrente. Se la clausola viene omessa, la route appartiene all'utente corrente.  
  
 con  
 Introduce le clausole per la definizione della nuova route creata.  
  
 SERVICE_NAME = **'***service_name***'**  
 Specifica il nome del servizio remoto a cui la route fa riferimento. Il *service_name* deve corrispondere esattamente utilizza il nome del servizio remoto. [!INCLUDE[ssSB](../../includes/sssb-md.md)]utilizza un confronto byte per byte per trovare la corrispondenza di *service_name*. In altre parole, nel confronto viene fatta distinzione tra maiuscole e minuscole e non vengono considerate le regole di confronto correnti. Se la clausola SERVICE_NAME viene omessa, per la route viene utilizzato qualsiasi nome di servizio, ma in questo caso la route avrà una priorità di corrispondenza inferiore rispetto a una route per cui si specifica SERVICE_NAME. Una route con un nome di servizio **' SQL/ServiceBroker/BrokerConfiguration'** sia una route a un servizio Broker Configuration Notice. Per una route per questo servizio non è necessario specificare un'istanza di Service Broker.  
  
 BROKER_INSTANCE = **'***broker_instance_identifier***'**  
 Specifica il database che ospita il servizio di destinazione. Il *broker_instance_identifier* parametro deve essere l'identificatore di istanza di Service broker per il database remoto, che può essere ottenuto eseguendo la query seguente nel database selezionato:  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID()  
```  
  
 Se si omette la clausola BROKER_INSTANCE, per la route viene utilizzata qualsiasi istanza di Service Broker. Le route impostate per qualsiasi istanza di Service Broker hanno una priorità maggiore di corrispondenza rispetto alle route con un'istanza di Service Broker esplicita quando la conversazione non specifica un'istanza di Service Broker. Per le conversazioni che specificano un'istanza di Service Broker, invece, le route impostate per un'istanza specifica di Service Broker hanno una priorità maggiore rispetto a quelle impostate per qualsiasi istanza.  
  
 LIFETIME **=***route_lifetime*  
 Specifica per quanti secondi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene la route nella tabella di routing. Al termine di questo periodo di tempo, la route scade e non viene più presa in considerazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la scelta della route per una nuova conversazione. Se questa clausola viene omessa, il *route_lifetime* è NULL e la route non scade mai.  
  
 ADDRESS **='***next_hop_address***'**  
 Specifica l'indirizzo di rete per la route. Il *next_hop_address* specifica un indirizzo TCP/IP nel formato seguente:  
  
 **TCP: / /**{ *dns_name* | *nome_NetBIOS* | *indirizzo_IP* } **: * * * numero_porta*  
  
 Specificato *numero_porta* deve corrispondere al numero di porta per il [!INCLUDE[ssSB](../../includes/sssb-md.md)] endpoint di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer specificato. Per ottenere tale valore, eseguire la query seguente nel database selezionato:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Se il servizio è ospitato in un database con mirroring, è inoltre necessario specificare l'indirizzo MIRROR_ADDRESS per l'altra istanza che ospita un database con mirroring. In caso contrario, la route non eseguirà il failover sul mirror.  
  
 Quando una route specifica **'LOCAL'** per il *next_hop_address*, il messaggio viene recapitato a un servizio all'interno dell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando una route specifica **'TRANSPORT'** per il *next_hop_address*, l'indirizzo di rete viene determinato in base all'indirizzo di rete nel nome del servizio. Una route che specifica **'TRANSPORT'** non è necessario specificare un nome o del gestore di istanza del servizio.  
  
 MIRROR_ADDRESS **='***next_hop_mirror_address***'**  
 Specifica l'indirizzo di rete per un database con mirroring con un database con mirroring ospitato nel *next_hop_address*. Il *next_hop_mirror_address* specifica un indirizzo TCP/IP nel formato seguente:  
  
 **TCP: / /**{ *dns_name* | *nome_NetBIOS* | *indirizzo_IP* } **:**  *numero_porta*  
  
 Specificato *numero_porta* deve corrispondere al numero di porta per il [!INCLUDE[ssSB](../../includes/sssb-md.md)] endpoint di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer specificato. Per ottenere tale valore, eseguire la query seguente nel database selezionato:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Se si specifica MIRROR_ADDRESS, la route deve specificare la clausola SERVICE_NAME e la clausola BROKER_INSTANCE. Una route che specifica **'LOCAL'** o **'TRANSPORT'** per il *next_hop_address* non è necessario specificare un indirizzo mirror.  
  
## <a name="remarks"></a>Osservazioni  
 La tabella di routing che archivia le route è una tabella di metadati che può essere letta tramite la **Routes** vista del catalogo. È possibile aggiornare questa vista del catalogo solo tramite le istruzioni CREATE ROUTE, ALTER ROUTE e DROP ROUTE.  
  
 Per impostazione predefinita, la tabella di routing in ogni database utente contiene una sola route. Tale route è denominata **AutoCreatedLocal**. Specifica la route **'LOCAL'** per il *next_hop_address* e corrisponde a qualsiasi identificatore di istanza nome e il gestore del servizio.  
  
 Quando una route specifica **'TRANSPORT'** per il *next_hop_address*, l'indirizzo di rete viene determinato in base al nome del servizio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]può elaborare correttamente i nomi di servizio che iniziano con un indirizzo di rete in un formato non valido per un *next_hop_address*.  
  
 La tabella di routing può includere qualsiasi numero di route che specificano lo stesso servizio, indirizzo di rete e identificatore dell'istanza di Service Broker. In questo caso, [!INCLUDE[ssSB](../../includes/sssb-md.md)] sceglie una route utilizzando una procedura progettata in modo da individuare la corrispondenza più esatta tra le informazioni specificate nella conversazione e le informazioni della tabella di routing.  
  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] non rimuove le route scadute dalla tabella di routing. È possibile riattivare una route scaduta tramite l'istruzione ALTER ROUTE.  
  
 Una route non può essere un oggetto temporaneo. Nomi di route che iniziano con  **#**  sono consentiti, ma sono oggetti permanenti.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazione per la creazione di impostazioni predefinite per i membri di una route di **db_ddladmin** o **db_owner** ruoli predefiniti del database e **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-tcpip-route-by-using-a-dns-name"></a>A. Creazione di una route TCP/IP utilizzando un nome DNS  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/Expenses`. La route specifica che i messaggi per questo servizio verranno trasmessi tramite TCP alla porta `1234` nell'host identificato dal nome DNS `www.Adventure-Works.com`. All'arrivo, i messaggi verranno recapitati dal server di destinazione all'istanza di Service Broker identificata dall'ID univoco `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://www.Adventure-Works.com:1234' ;  
```  
  
### <a name="b-creating-a-tcpip-route-by-using-a-netbios-name"></a>B. Creazione di una route TCP/IP utilizzando un nome NetBIOS  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/Expenses`. La route specifica che i messaggi per questo servizio verranno trasmessi tramite TCP alla porta `1234` nell'host identificato dal nome NetBIOS `SERVER02`. All'arrivo, il messaggio verrà recapitato dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione all'istanza di database identificata dall'ID univoco `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH   
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://SERVER02:1234' ;  
```  
  
### <a name="c-creating-a-tcpip-route-by-using-an-ip-address"></a>C. Creazione di una route TCP/IP utilizzando un indirizzo IP  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/Expenses`. La route specifica che i messaggi per questo servizio verranno trasmessi tramite TCP alla porta `1234` nell'host all'indirizzo IP `192.168.10.2`. All'arrivo, il messaggio verrà recapitato dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di destinazione all'istanza di Service Broker identificata dall'ID univoco `D8D4D268-00A3-4C62-8F91-634B89C1E315`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89C1E315',  
    ADDRESS = 'TCP://192.168.10.2:1234' ;  
```  
  
### <a name="d-creating-a-route-to-a-forwarding-broker"></a>D. Creazione di una route per un'istanza di Service Broker di inoltro  
 Nell'esempio seguente viene creata una route per l'istanza di Service Broker di inoltro sul server `dispatch.Adventure-Works.com`. Poiché non vengono specificati il nome del servizio e l'identificatore dell'istanza di Service Broker, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza questa route per i servizi per cui non è definita nessun'altra route.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    ADDRESS = 'TCP://dispatch.Adventure-Works.com' ;   
```  
  
### <a name="e-creating-a-route-to-a-local-service"></a>E. Creazione di una route per un servizio locale  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/LogRequests` nella stessa istanza della route.  
  
```  
CREATE ROUTE LogRequests  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/LogRequests',  
    ADDRESS = 'LOCAL' ;  
```  
  
### <a name="f-creating-a-route-with-a-specified-lifetime"></a>F. Creazione di una route con una durata specifica  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/Expenses`. La durata della route è di `259200` secondi, equivalenti a 72 ore.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    LIFETIME = 259200,  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234' ;  
```  
  
### <a name="g-creating-a-route-to-a-mirrored-database"></a>G. Creazione di una route per un database con mirroring  
 Nell'esempio seguente viene creata una route per il servizio `//Adventure-Works.com/Expenses`. Il servizio è ospitato in un database con mirroring. Uno dei database con mirroring è disponibile all'indirizzo `services.Adventure-Works.com:1234`, mentre l'altro database si trova all'indirizzo `services-mirror.Adventure-Works.com:1234`.  
  
```  
CREATE ROUTE ExpenseRoute  
    WITH  
    SERVICE_NAME = '//Adventure-Works.com/Expenses',  
    BROKER_INSTANCE = '69fcc80c-2239-4700-8437-1001ecddf933',  
    ADDRESS = 'TCP://services.Adventure-Works.com:1234',   
    MIRROR_ADDRESS = 'TCP://services-mirror.Adventure-Works.com:1234' ;  
```  
  
### <a name="h-creating-a-route-that-uses-the-service-name-for-routing"></a>H. Creazione di una route che utilizza il nome del servizio per il routing  
 Nell'esempio seguente viene creata una route che utilizza il nome del servizio per determinare l'indirizzo di rete a cui inviare il messaggio. Si noti che una route con indirizzo di rete `'TRANSPORT'` ha una priorità di corrispondenza inferiore rispetto alle altre route.  
  
```  
CREATE ROUTE TransportRoute  
    WITH ADDRESS = 'TRANSPORT' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-route-transact-sql.md)   
 [DROP ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
