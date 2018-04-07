---
title: Comportamento di blocco (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c55c636e-b767-4a0c-8184-be991a10801f
caps.latest.revision: 27
ms.openlocfilehash: db8b05abe5d3eea3a927cdf410e7aa8df5ed2032
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="locking-behavior"></a>Comportamento di blocco
SQL Server PDW vengono utilizzati i blocchi per garantire l'integrità delle transazioni e mantenere la coerenza dei database quando più utenti accedono ai dati nello stesso momento.  
  
## <a name="Basics"></a>Nozioni fondamentali di blocchi  
**Modalità**  
  
SQL Server PDW supporta quattro modalità di blocco:  
  
Exclusive  
Il blocco esclusivo impedisce di scrittura o lettura dall'oggetto bloccato fino a quando la transazione che contiene che il blocco esclusivo viene completata. Nessun altri blocchi di qualsiasi modalità sono consentite mentre è in corso di un blocco esclusivo. Ad esempio, DROP TABLE e CREATE DATABASE utilizzare un blocco esclusivo.  
  
Origine dati  
Il blocco condiviso impedisce l'avvio di un blocco esclusivo sull'oggetto interessato, ma consente tutte le altre modalità di blocco. Ad esempio, l'istruzione SELECT inizia un blocco condiviso e pertanto consente di accedere ai dati selezionati contemporaneamente più query, ma impedisce gli aggiornamenti per i record da leggere, fino al completamento dell'istruzione SELECT.  
  
ExclusiveUpdate  
Il blocco ExclusiveUpdate impedisce la scrittura dell'oggetto bloccato, ma consente la lettura tramite il blocco condiviso. Altri blocchi non sono consentite mentre il blocco ExclusiveUpdate è valido. Ad esempio, il DATABASE di BACKUP e RESTORE DATABASE usare un blocco esclusivo-aggiornamento.  
  
SharedUpdate  
Il blocco SharedUpdate impedisce la modalità di blocco esclusivo ed ExclusiveUpdate e consente di modalità di blocco SharedUpdate e condiviso per l'oggetto. SharedUpdate modifica un oggetto, ma non limitare l'accesso in lettura ad esso durante la modifica. Ad esempio, inserire e aggiornamento di utilizzare un blocco SharedUpdate.  
  
**Classi di risorse**  
  
I blocchi vengono mantenuti per le classi di oggetti seguenti: DATABASE, SCHEMA, oggetto (tabella, vista o stored procedure), l'applicazione (utilizzato internamente), EXTERNALDATASOURCE, EXTERNALFILEFORMAT e SCHEMARESOLUTION (livello di database possono bloccare eseguito durante la creazione, modifica, o eliminazione di oggetti dello schema o gli utenti del database). Queste classi di oggetti possono essere visualizzati nella colonna object_type [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md).  
  
## <a name="Remarks"></a>Osservazioni generali  
Per i database, tabelle o viste, è possono utilizzare i blocchi.  
  
SQL Server PDW non implementa i livelli di isolamento configurabile. Supporta il livello di isolamento READ_UNCOMMITTED come definito per lo standard ANSI. Tuttavia, poiché le operazioni vengono eseguite in READ_UNCOMMITTED di lettura, pochissime operazioni di blocco effettivamente verificano o provocare contesa nel sistema.  
  
SQL Server PDW si basa sul motore di SQL Server sottostante per implementare il controllo di blocco e concorrenza. Se le operazioni di causare un deadlock di SQL Server sottostante nello stesso nodo, SQL Server PDW sfrutta la funzionalità di rilevamento di deadlock di SQL Server e consente di terminare una delle istruzioni di blocco.  
  
> [!NOTE]  
> SQL Server non consente le istruzioni che sono in attesa di blocchi vengano bloccate da richieste di blocco più recente. SQL Server PDW non è completamente implementato questo processo. In SQL Server PDW, continua richieste di nuovi blocchi condivisi possono a volte bloccare una richiesta precedente (ma in attesa) per un blocco esclusivo. Ad esempio, un **aggiornamento** istruzione (che richiedono un blocco esclusivo) può essere bloccata da blocchi condivisi che vengono concesse per serie di **selezionare** istruzioni. Per risolvere un processo bloccato (identificato esaminando il [sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md) DVM), arrestare l'invio di richieste di nuovo fino a quando non è stati soddisfatti il blocco esclusivo.  
  
## <a name="lock-definition-table"></a>Tabella di definizione di blocco  
SQL Server supporta i seguenti tipi di blocchi. Non tutti i tipi di blocco sono disponibili sul nodo del controllo, ma può verificarsi nei nodi di calcolo.  
  
-   Sch-S (stabilità Schema). Impedisce che un elemento dello schema, ad esempio una tabella o un indice, venga eliminato mentre in una sessione viene mantenuto attivo un blocco di stabilità dello schema su tale elemento.  
  
-   SCH-M (modifica dello Schema). Deve essere impostato in tutte le sessioni in cui si desidera modificare lo schema della risorsa specificata. Assicura che nessun'altra sessione faccia riferimento all'oggetto specificato.  
  
-   S (condiviso). La sessione attiva dispone dell'accesso condiviso alla risorsa.  
  
-   U (aggiornamento). Indica un blocco di aggiornamento acquisito su risorse che potrebbero essere aggiornate. Viene utilizzato per evitare una forma comune di deadlock che si verifica quando in più sessioni vengono bloccate risorse che potrebbero essere aggiornate in futuro.  
  
-   X (esclusivo). La sessione attiva dispone dell'accesso esclusivo alla risorsa.  
  
-   IS (preventivo condiviso). Indica l'intenzione di impostare blocchi condivisi (S) su alcune risorse subordinate nella gerarchia dei blocchi.  
  
-   IU (preventivo aggiornamento). Indica l'intenzione di impostare blocchi di aggiornamento (U) su alcune risorse subordinate nella gerarchia dei blocchi.  
  
-   IX (preventivo esclusivo). Indica l'intenzione di impostare blocchi esclusivi (X) su alcune risorse subordinate nella gerarchia dei blocchi.  
  
-   SIU (condiviso preventivo aggiornamento). Indica l'accesso condiviso a una risorsa con l'intenzione di acquisire blocchi di aggiornamento su risorse subordinate nella gerarchia dei blocchi.  
  
-   SEI (condiviso preventivo esclusivo). Indica l'accesso condiviso a una risorsa con l'intenzione di acquisire blocchi esclusivi su risorse subordinate nella gerarchia dei blocchi.  
  
-   UIX (aggiornamento preventivo esclusivo). Indica un blocco di aggiornamento attivato su una risorsa con l'intenzione di acquisire blocchi esclusivi su risorse subordinate nella gerarchia dei blocchi.  
  
-   BU. Utilizzato dalle operazioni bulk.  
  
-   RangeS_S (blocco condiviso intervalli di chiavi e risorsa). Indica un'analisi di intervallo serializzabile.  
  
-   RangeS_U (blocco condiviso intervalli di chiavi e aggiornamento risorsa). Indica un'analisi di aggiornamento serializzabile.  
  
-   RangeI_N (blocco inserimento intervalli di chiavi e risorsa Null). Utilizzato per verificare gli intervalli prima di inserire una nuova chiave in un indice.  
  
-   RangeI_S. Blocco conversione intervalli di chiavi, creato da una sovrapposizione di blocchi RangeI_N e S.  
  
-   RangeI_U. Blocco conversione intervalli di chiavi, creato da una sovrapposizione di blocchi RangeI_N e U.  
  
-   RangeI_X. Blocco conversione intervalli di chiavi, creato da una sovrapposizione di blocchi RangeI_N e X.  
  
-   RangeX_S. Blocco conversione intervalli di chiavi, creato da una sovrapposizione di blocchi RangeI_N e RangeS_S.  
  
-   RangeX_U. Blocco conversione intervalli di chiavi, creato da una sovrapposizione di blocchi RangeI_N e RangeS_U.  
  
-   RangeX_X (blocco esclusivo intervalli di chiavi e risorsa). Si tratta di un blocco di conversione utilizzato quando viene aggiornata una chiave in un intervallo.  
  
## <a name="see-also"></a>Vedere anche  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[sys.dm_pdw_waits](../relational-databases/system-dynamic-management-views/sys-dm-pdw-waits-transact-sql.md)  
  
