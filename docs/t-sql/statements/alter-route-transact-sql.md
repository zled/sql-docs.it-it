---
title: ALTER ROUTE (Transact-SQL) | Documenti Microsoft
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
- ALTER_ROUTE_TSQL
- ALTER ROUTE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER ROUTE statement
- dropping routes
- modifying routes
- removing routes
- routes [Service Broker], modifying
ms.assetid: 8dfb7b16-3dac-4e1e-8c97-adf2aad07830
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 39e39b8688e2350d27e664b4a1517584c11df941
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="alter-route-transact-sql"></a>ALTER ROUTE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica le informazioni relative a una route esistente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ALTER ROUTE route_name  
WITH    
  [ SERVICE_NAME = 'service_name' [ , ] ]  
  [ BROKER_INSTANCE = 'broker_instance' [ , ] ]  
  [ LIFETIME = route_lifetime [ , ] ]  
  [ ADDRESS =  'next_hop_address' [ , ] ]  
  [ MIRROR_ADDRESS = 'next_hop_mirror_address' ]  
[ ; ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *route_name*  
 Nome della route da modificare. Non è possibile specificare i nomi del server, del database e dello schema.  
  
 con  
 Introduce le clausole che definiscono la route da modificare.  
  
 SERVICE_NAME **='***service_name***'**  
 Specifica il nome del servizio remoto a cui la route fa riferimento. Il *service_name* deve corrispondere esattamente utilizza il nome del servizio remoto. [!INCLUDE[ssSB](../../includes/sssb-md.md)]utilizza un confronto byte per byte per trovare la corrispondenza di *service_name*. In altre parole, nel confronto viene fatta distinzione tra maiuscole e minuscole e non vengono considerate le regole di confronto correnti. Una route con un nome di servizio **' SQL/ServiceBroker/BrokerConfiguration'** sia una route a un servizio Broker Configuration Notice. Per una route per questo servizio non è necessario specificare un'istanza di Service Broker.  
  
 Se la clausola SERVICE_NAME viene omessa, il nome del servizio per la route rimane invariato.  
  
 BROKER_INSTANCE **='***broker_instance***'**  
 Specifica il database che ospita il servizio di destinazione. Il *broker_instance* parametro deve essere l'identificatore di istanza di Service broker per il database remoto, che può essere ottenuto eseguendo la query seguente nel database selezionato:  
  
```  
SELECT service_broker_guid  
FROM sys.databases  
WHERE database_id = DB_ID();  
```  
  
 Se la clausola BROKER_NAME viene omessa, l'istanza di Service Broker per la route rimane invariata.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 DURATA  **=**  *route_lifetime*  
 Specifica per quanti secondi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mantiene la route nella tabella di routing. Al termine di questo periodo di tempo, la route scade e non viene più presa in considerazione da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per la scelta della route per una nuova conversazione. Se questa clausola viene omessa, la durata della route rimane invariata.  
  
 INDIRIZZO **='***next_hop_address'*  
 Specifica l'indirizzo di rete per la route. Il *next_hop_address* specifica un indirizzo TCP/IP nel formato seguente:  
  
 **TCP: / /** { *dns_name* | *nome_NetBIOS* |*indirizzo_IP* } **:**  *numero_porta*  
  
 Specificato *numero_porta* deve corrispondere al numero di porta per il [!INCLUDE[ssSB](../../includes/sssb-md.md)] endpoint di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel computer specificato. Per ottenere tale valore, eseguire la query seguente nel database selezionato:  
  
```  
SELECT tcpe.port  
FROM sys.tcp_endpoints AS tcpe  
INNER JOIN sys.service_broker_endpoints AS ssbe  
   ON ssbe.endpoint_id = tcpe.endpoint_id  
WHERE ssbe.name = N'MyServiceBrokerEndpoint';  
```  
  
 Quando una route specifica **'LOCAL'** per il *next_hop_address*, il messaggio viene recapitato a un servizio all'interno dell'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando una route specifica **'TRANSPORT'** per il *next_hop_address*, l'indirizzo di rete viene determinato in base all'indirizzo di rete nel nome del servizio. Una route che specifica **'TRANSPORT'** possibile specificare un'istanza del nome o del gestore di servizio.  
  
 Quando il *next_hop_address* è il server principale per un database mirror, è necessario specificare anche l'indirizzo MIRROR_ADDRESS per il server mirror. In caso contrario non può venire eseguito il failover automatico della route al server mirror.  
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
 Valore di MIRROR_ADDRESS **='***next_hop_mirror_address***'**  
 Specifica l'indirizzo di rete per il server mirror di una coppia con mirroring di cui il server principale si trova il *next_hop_address*. Il *next_hop_mirror_address* specifica un indirizzo TCP/IP nel formato seguente:  
  
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
  
> [!NOTE]  
>  Questa opzione non è disponibile in un database indipendente.  
  
## <a name="remarks"></a>Osservazioni  
 La tabella di routing che archivia le route è una tabella di metadati che può essere letta tramite la **Routes** vista del catalogo. e aggiornata esclusivamente utilizzando le istruzioni CREATE ROUTE, ALTER ROUTE e DROP ROUTE.  
  
 Le clausole che non sono specificate nel comando ALTER ROUTE rimangono invariate. Non è possibile pertanto eseguire il comando ALTER per specificare che la route non scade, che corrisponde a un nome di servizio o che corrisponde a un'istanza di Service Broker. Per modificare queste caratteristiche di una route è necessario eliminare la route esistente e creare una nuova route con le nuove informazioni.  
  
 Quando una route specifica **'TRANSPORT'** per il *next_hop_address*, l'indirizzo di rete viene determinato in base al nome del servizio. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]può elaborare correttamente i nomi di servizio che iniziano con un indirizzo di rete in un formato non valido per un *next_hop_address*. I servizi con nomi che contengono indirizzi di rete validi verranno indirizzati all'indirizzo di rete indicato nel nome del servizio.  
  
 La tabella di routing può includere qualsiasi numero di route che specificano lo stesso servizio, indirizzo di rete e/o identificatore dell'istanza di Service Broker. In questo caso, [!INCLUDE[ssSB](../../includes/sssb-md.md)] sceglie una route utilizzando una procedura progettata in modo da individuare la corrispondenza più esatta tra le informazioni specificate nella conversazione e le informazioni della tabella di routing.  
  
 Per modificare il parametro AUTHORIZATION per un servizio, utilizzare l'istruzione ALTER AUTHORIZATION.  
  
## <a name="permissions"></a>Permissions  
 L'autorizzazione per modificare una route per impostazione predefinita al proprietario della route, ai membri del **db_ddladmin** o **db_owner** fissa ruoli del database e i membri del **sysadmin** fissa ruolo del server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-service-for-a-route"></a>A. Modifica del servizio per una route  
 Nell'esempio seguente viene modificata la route `ExpenseRoute` in modo da puntare al servizio remoto `//Adventure-Works.com/Expenses`.  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     SERVICE_NAME = '//Adventure-Works.com/Expenses';  
```  
  
### <a name="b-changing-the-target-database-for-a-route"></a>B. Modifica del database di destinazione per una route  
 Nell'esempio seguente il database di destinazione per la route `ExpenseRoute` viene modificato e impostato sul database identificato dall'ID univoco `D8D4D268-00A3-4C62-8F91-634B89B1E317.`  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317';  
```  
  
### <a name="c-changing-the-address-for-a-route"></a>C. Modifica dell'indirizzo per una route  
 Nell'esempio seguente l'indirizzo di rete per la route `ExpenseRoute` viene modificato e impostato sulla porta TCP `1234` nell'host con indirizzo IP `10.2.19.72`.  
  
```  
ALTER ROUTE ExpenseRoute   
   WITH   
     ADDRESS = 'TCP://10.2.19.72:1234';  
```  
  
### <a name="d-changing-the-database-and-address-for-a-route"></a>D. Modifica del database e dell'indirizzo per una route  
 Nell'esempio seguente l'indirizzo di rete per la route `ExpenseRoute` viene modificato e impostato sulla porta TCP `1234` nell'host con nome DNS `www.Adventure-Works.com`. Viene inoltre modificato il database di destinazione, che viene impostato sul database identificato dall'identificatore univoco `D8D4D268-00A3-4C62-8F91-634B89B1E317`.  
  
```  
ALTER ROUTE ExpenseRoute  
   WITH   
     BROKER_INSTANCE = 'D8D4D268-00A3-4C62-8F91-634B89B1E317',  
     ADDRESS = 'TCP://www.Adventure-Works.com:1234';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE ROUTE &#40;Transact-SQL&#41;](../../t-sql/statements/create-route-transact-sql.md)   
 [DROP ROUTE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-route-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  

