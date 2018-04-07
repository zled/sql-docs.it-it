---
title: Attività di gestione del carico di lavoro
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/12/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.openlocfilehash: 0a9c3ffd4768d78a4063ad40f7903dfe00b647e5
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="workload-management-tasks"></a>Attività di gestione del carico di lavoro

## <a name="view-login-members-of-each-resource-class"></a>Visualizzare i membri di account di accesso di ogni classe di risorse
Viene descritto come visualizzare i membri di account di accesso di ogni ruolo del server di classe di risorse in SQL Server PDW. Utilizzare questa query per individuare la classe di risorse per le richieste inviate da ogni account di accesso è consentito.  
  
Per descrizioni classe di risorse, vedere [del carico di lavoro](workload-management.md).  
  
Questa query consente di visualizzare l'elenco di appartenenze per ogni classe di risorse. Esistono tre classi di risorse, mediumrc, largerc e xlargerc.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  ( l.[type] = 'S' OR l.[type] = 'U' OR l.[type] = 'G' )  
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
```  
  
Se un account di accesso non è presente nell'elenco, le richieste riceverà le risorse predefinite. Se un account di accesso è un membro di più di una classe di risorse, la classe più grande ha la precedenza.  
  
Le allocazioni di risorsa sono elencate nel [del carico di lavoro](workload-management.md) argomento.  
  
## <a name="change-the-system-resources-allocated-to-a-request"></a>Le risorse di sistema allocate a una richiesta di modifica
Viene descritto come individuare la risorsa di classe in cui è in esecuzione una richiesta di SQL Server PDW e come modificare le risorse di sistema per tale richiesta. Modificare le risorse per una richiesta, è necessario modificare l'appartenenza di classe di risorse dell'account di accesso di invio della richiesta, tramite il [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md) istruzione.  
  
### <a name="step-1-determine-the-resource-class-for-the-login-running-the-request"></a>Passaggio 1: Determinare la classe di risorse per l'esecuzione della richiesta di accesso.  
Questa query consente di visualizzare gli account di accesso che sono membri delle appartenenze al ruolo di server di classe di risorse. Esistono tre classi di risorse, **mediumrc**, **largerc**, e **xlargerc**.  
  
> [!IMPORTANT]  
> Questa query deve essere eseguita da un account di accesso con **CONTROL SERVER** autorizzazione. Se eseguito da un account di accesso senza **CONTROL SERVER** autorizzazione, questa query restituisce solo le appartenenze al ruolo per l'account di accesso corrente.  
  
```sql  
SELECT l.name AS [member], r.name AS [server role]  
FROM sys.server_role_members AS rm  
JOIN sys.server_principals AS l  
  ON l.principal_id = rm.member_principal_id  
JOIN  
  sys.server_principals AS r  
  ON r.principal_id = rm.role_principal_id  
WHERE  
  l.[type] = 'S'   
  AND r.[type] = 'R'  
  AND r.[name] in ('mediumrc', 'largerc', 'xlargerc');  
GO  
```  
  
Se sono non presenti Nessun account di accesso che sono membri di un ruolo del server di classe di risorse, la tabella risultante sarà vuota. In questo caso, se la query restituisce un account di accesso denominato Ching, quindi quando Ching invia una richiesta, la richiesta riceverà le risorse di sistema predefinite, che è minore di risorse di sistema di classe di risorse. Se un account di accesso è un membro di più di una classe di risorse, la classe più grande ha la precedenza.  
  
Per un elenco delle assegnazioni delle risorse per ogni classe di risorse, vedere [del carico di lavoro](workload-management.md) argomento.  
  
### <a name="step-2-run-the-request-under-a-login-with-different-resource-class-membership"></a>Passaggio 2: Eseguire la richiesta in un account di accesso con l'appartenenza alla classe di risorse diverso  
Esistono due modi per eseguire una richiesta con risorse maggiori o minori di sistema:  
  
-   Eseguire la richiesta in un diverso account di accesso che è un membro di una classe di risorse maggiore o minore.  
  
-   Aggiungere l'account di accesso necessarie per uno dei ruoli di classe di risorse. Scegliere questa opzione con cautela. la classe di risorse per l'accesso verrà modifica il livello di risorse di sistema per tutte le richieste inviate dall'account di accesso.  
  
Si supponga che Ching è un membro del ruolo del server largerc. Nell'esempio seguente viene illustrato come aggiungere l'account di accesso Ching al ruolo del server xlargerc.  
  
```sql  
ALTER SERVER ROLE xlargerc ADD MEMBER Ching;  
```  
  
Ching è ora un membro di largerc e i ruoli del server xlargerc. Quando Ching invia le richieste, le richieste ricevono le risorse di sistema xlargerc.  
  
Nell'esempio seguente riporta Ching al ruolo del server mediumrc.  A tale scopo, lei deve essere rimosso da xlargerc e i ruoli del server largerc e aggiunto al ruolo del server mediumrc.  
  
```sql  
-- Move login Ching back to using medium system resources for requests.  
ALTER SERVER ROLE xlargerc DROP MEMBER Ching;  
ALTER SERVER ROLE largerc DROP MEMBER Ching;  
ALTER SERVER ROLE mediumrc ADD MEMBER Ching;  
```  
  
Ching è ora un membro del ruolo del server mediumrc.  L'esempio seguente modifica Ching per le risorse di sistema predefinito per le richieste di sua.  
  
```sql  
-- Move login Ching to use the default system resources for requests.  
ALTER SERVER ROLE mediumrc DROP MEMBER Ching;  
```  
  
Per ulteriori informazioni sulla modifica appartenenza al ruolo di classe di risorse, vedere [ALTER SERVER ROLE](../t-sql/statements/alter-server-role-transact-sql.md).  

## <a name="change-a-login-to-the-default-system-resources-for-its-requests"></a>Modificare un account di accesso alle risorse di sistema predefinito per le richieste
Viene descritto come modificare le allocazioni di risorse di sistema assegnate a un account di accesso di SQL Server PDW agli importi predefinito. Questo problema riguarda le risorse di sistema SQL Server PDW assegna alle richieste inviate dall'account di accesso.  
  
Per le descrizioni classe di risorse, vedere [gestione del carico di lavoro](workload-management.md)  
  
Quando un account di accesso non è un membro di qualsiasi ruolo di server di classe di risorse, le richieste inviate dall'account di accesso riceverà la quantità di risorse di sistema predefinita.  
  
Si supponga che l'account di accesso Matt è attualmente un membro di tutti i ruoli server classe di risorse e desidera tornare a con le richieste di ricevere solo le risorse predefinite.  Nell'esempio seguente assegna le risorse predefinite per le richieste di Matt eliminando l'appartenenza a da tutti i ruoli server classe tre risorse.  
  
```sql  
--Give the requests submitted by Matt the default system resources   
--by dropping Matt from all resource class server roles.  
ALTER SERVER ROLE XLargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE LargeRC DROP MEMBER Matt;  
ALTER SERVER ROLE MediumRC DROP MEMBER Matt;  
```  
  
## <a name="display-the-number-of-concurrency-slots-needed-for-a-waiting-request"></a>Visualizza che il numero di slot concorrenza necessari per un tipo di attesa richiesta
Viene descritto come determinare il numero di concorrenza sono necessari spazi da una richiesta che è in attesa di esecuzione in SQL Server PDW.  
  
Per ulteriori informazioni, vedere [del carico di lavoro](workload-management.md).  
  
Una richiesta potrebbe essere in attesa troppo a lungo senza essere eseguito. Uno dei modi per risolvere questo problema è necessario esaminare il numero di slot concorrenza che la richiesta è necessario.  Nell'esempio seguente mostra il numero di slot concorrenza necessari per ogni richiesta in attesa.  
  
```sql  
--Display the number of concurrency slots required   
--for each request that is waiting to run.  
SELECT request_id, concurrency_slots_used AS [Slots Needed], resource_class AS [Resource Class]  
FROM sys.dm_pdw_resource_waits;  
```  
  
  
## <a name="see-also"></a>Vedere anche  
[Gestione del carico di lavoro](workload-management.md)  
  
