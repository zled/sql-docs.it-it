---
title: Replica con Istanza gestita di database SQL | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: d55aea5d50d9ea434aabb392d0c6b53573c0199e
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559571"
---
# <a name="replication-with-sql-database-managed-instance"></a>Replica con Istanza gestita di database SQL

[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Istanza gestita di database SQL di Azure (anteprima) supporta la replica transazionale. Istanza gestita può ospitare i database di pubblicazione, di distribuzione e sottoscrittore.

## <a name="common-configurations"></a>Configurazioni comuni

In generale, il database di pubblicazione e il database di distribuzione devono essere entrambi nel cloud o in locale. Sono supportate le configurazioni seguenti:

- **Database di pubblicazione con database di distribuzione locale in istanza gestita**

   ![Replication-with-azure-sql-db-single-managed-instance-publisher-distributor](./media/replication-with-sql-database-managed-instance/01-single-instance-asdbmi-pubdist.png)

   I database di pubblicazione e di distribuzione sono configurati in una singola istanza gestita.

- **Database di pubblicazione con database di distribuzione remoto in istanza gestita**

   ![Replication-with-azure-sql-db-separate-managed-instances-publisher-distributor](./media/replication-with-sql-database-managed-instance/02-separate-instances-asdbmi-pubdist.png)

   Il database di pubblicazione e il database di distribuzione sono configurati in due istanze gestite. In questa configurazione:

  - Entrambe le istanze gestite sono nella stessa rete virtuale.

  - Entrambe le istanze gestite sono nella stessa posizione.

- **Database di pubblicazione e database di distribuzione in locale con database di sottoscrizione in istanza gestita**

   ![Replication-from-on-premises-to-azure-sql-db-subscriber](./media/replication-with-sql-database-managed-instance/03-azure-sql-db-subscriber.png)

   In questa configurazione, il database SQL di Azure è un sottoscrittore. Questa configurazione supporta la migrazione da locale ad Azure. Nel ruolo di sottoscrittore, il database SQL non richiede un'istanza gestita, ma è possibile usare Istanza gestita di database SQL come passaggio per la migrazione da locale ad Azure. Per altre informazioni sui sottoscrittori di database SQL di Azure, vedere [Replica nel database SQL](replication-to-sql-database.md).

## <a name="requirements"></a>Requisiti

Per i database di pubblicazione e di distribuzione in database SQL di Azure sono previsti i requisiti seguenti:

- Istanza gestita di database SQL di Azure.

   >[!NOTE]
   >I database SQL di Azure non configurati con Istanza gestita possono essere solo sottoscrittori.

- Tutte le istanze di SQL Server devono essere nella stessa rete virtuale.

- Per la connettività viene usata l'autenticazione di SQL tra i partecipanti alla replica.

- Una condivisione di account di archiviazione di Azure per la directory di lavoro di replica.

## <a name="features"></a>Funzionalità

Supporto:

- Combinazione di replica transazionale e snapshot di istanze locali e di Istanza gestita di database SQL di Azure.

- I sottoscrittori possono essere in locale, nel database SQL di Azure o in pool elastici.

- Replica unidirezionale o bidirezionale

## <a name="configure-publishing-and-distribution-example"></a>Esempio di configurazione di pubblicazione e distribuzione

1. [Creare un'istanza gestita di database SQL di Azure](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-create-tutorial-portal) nel portale.

1. [Creare un account di archiviazione di Azure](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account) per la directory di lavoro. Assicurarsi di copiare le chiavi di archiviazione. Vedere [Gestire le chiavi di accesso alle risorse di archiviazione](http://docs.microsoft.com/azure/storage/common/storage-create-storage-account#manage-your-storage-access-keys).

1. Creare un database per il server di pubblicazione.

   Negli script di esempio seguenti sostituire `<Publishing_DB>` con il nome di questo database.

1. Creare un utente del database con l'autenticazione SQL per il server di distribuzione. Vedere [Creazione degli utenti del database](http://docs.microsoft.com/azure/sql-database/sql-database-security-tutorial#creating-database-users). Usare una password sicura.

   Negli script di esempio seguenti usare `<SQL_USER>` e `<PASSWORD>` con questa combinazione di utente e password del database dell'account di SQL Server.

1. [Connettersi a Istanza gestita di database SQL](http://docs.microsoft.com/azure/sql-database/sql-database-connect-query-ssms).

1. Eseguire la query seguente per aggiungere il server di distribuzione e il database di distribuzione.

   ```sql
   USE [master]
   GO
   EXEC sp_adddistributor @distributor = @@ServerName;
   EXEC sp_adddistributiondb @database = N'distribution';
   ```

1. Per configurare un server di pubblicazione per l'uso di un database di distribuzione specificato, aggiornare ed eseguire la query seguente.

   Sostituire `<SQL_USER>` e `<PASSWORD>` con l'account e la password di SQL Server.

   Sostituire `\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>` con il valore per l'account di archiviazione. 

   Sostituire `<STORAGE_CONNECTION_STRING>` con il valore per le chiavi di accesso.

   Dopo aver aggiornato la query seguente, eseguirla. 

   ```sql
   USE [master]
   EXEC sp_adddistpublisher @publisher = @@ServerName,
                @distribution_db = N'distribution',
                @security_mode = 0,
                @login = N'<SQL_USER>',
                @password = N'<PASSWORD>',
                @working_directory = N'\\<STORAGE_ACCOUNT>.file.core.windows.net\<SHARE>',
                @storage_connection_string = N'<STORAGE_CONNECTION_STRING>';
   GO
   ```

1. Configurare il database di pubblicazione per la replica. 

    Nella query seguente sostituire `<Publishing_DB>` con il nome del database di pubblicazione.

    Sostituire `<Publication_Name>` con il nome della pubblicazione.

    Sostituire `<SQL_USER>` e `<PASSWORD>` con l'account e la password di SQL Server.

    Dopo aver aggiornato la query, eseguirla per creare la pubblicazione.

   ```sql
   USE [<Publishing_DB>]
   EXEC sp_replicationdboption @dbname = N'<Publishing_DB>',
                @optname = N'publish',
                @value = N'true';

   EXEC sp_addpublication @publication = N'<Publication_Name>',
                @status = N'active';

   EXEC sp_changelogreader_agent @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>';

   EXEC sp_addpublication_snapshot @publication = N'<Publication_Name>',
                @frequency_type = 1,
                @publisher_security_mode = 0,
                @publisher_login = N'<SQL_USER>',
                @publisher_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>',
                @job_password = N'<PASSWORD>'
   ```

1. Aggiungere l'articolo, la sottoscrizione e l'agente di sottoscrizione push. 

   Per aggiungere questi oggetti, aggiornare lo script seguente.

   Sostituire `<Object_Name>` con il nome dell'oggetto pubblicazione.

   Sostituire `<Object_Schema>` con il nome dello schema di origine. 

   Sostituire gli altri parametri tra parentesi angolari `<>` in modo che corrispondano ai valori negli script precedenti. 

   ```sql
   EXEC sp_addarticle @publication = N'<Publication_Name>',
                @type = N'logbased',
                @article = N'<Object_Name>',
                @source_object = N'<Object_Name>',
                @source_owner = N'<Object_Schema>'

   EXEC sp_addsubscription @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @destination_db = N'<Subscribing_DB>',
                @subscription_type = N'Push'

   EXEC sp_addpushsubscription_agent @publication = N'<Publication_Name>',
                @subscriber = @@ServerName,
                @subscriber_db = N'<Subscribing_DB>',
                @subscriber_security_mode = 0,
                @subscriber_login = N'<SQL_USER>',
                @subscriber_password = N'<PASSWORD>',
                @job_login = N'<SQL_USER>', 
                @job_password = N'<PASSWORD>'
   GO
   ```

## <a name="limitations"></a>Limitazioni

Le funzionalità seguenti non sono supportate:

- Sottoscrizioni aggiornabili

- Replica geografica attiva

## <a name="see-also"></a>Vedere anche

- [Informazioni su Istanza gestita (anteprima)](http://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)
