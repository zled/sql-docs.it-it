---
title: Failover forzato di SQL Server per il gruppo di disponibilità
description: Failover forzato per il gruppo di disponibilità con tipo di cluster NONE
services: ''
author: MikeRayMSFT
ms.topic: include
ms.date: 02/05/2018
ms.author: mikeray
ms.custom: include file
ms.openlocfilehash: f5655e73481d830c848aea34c4a4f49613be0913
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
Ogni gruppo di disponibilità ha soltanto una replica primaria, che consente operazioni di lettura e scrittura. Per modificare la replica primaria, è possibile effettuare il failover. In un gruppo di disponibilità per disponibilità elevata, il processo di failover è automatizzato da Gestione cluster. In un gruppo di disponibilità con tipo di cluster NONE, il processo di failover è manuale. 

Esistono due modi per effettuare il failover della replica primaria in un gruppo di disponibilità con tipo di cluster NONE:

- Failover manuale forzato con perdita di dati
- Failover manuale senza perdita di dati

### <a name="forced-manual-failover-with-data-loss"></a>Failover manuale forzato con perdita di dati

Usare questo metodo quando la replica primaria non è disponibile e non può essere recuperata. 

Per forzare il failover con perdita di dati, connettersi all'istanza di SQL Server che ospita la replica secondaria di destinazione ed eseguire il comando seguente:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>Failover manuale senza perdita di dati

Usare questo metodo quando la replica primaria è disponibile, ma è necessario modificare temporaneamente o definitivamente la configurazione e l'istanza SQL Server che ospita la replica primaria. Prima di effettuare il failover manuale, verificare che la replica secondaria di destinazione sia aggiornata per evitare una potenziale perdita di dati. 

Per effettuare il failover manuale senza perdita di dati:

1. Trasformare la replica secondaria di destinazione in `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'<node2>' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Eseguire la query seguente per verificare che per le transazioni attive sia eseguito il commit della replica primaria e di almeno una replica secondaria sincrona: 

   ```SQL
   SELECT ag.name, 
      drs.database_id, 
      drs.group_id, 
      drs.replica_id, 
      drs.synchronization_state_desc, 
      ag.sequence_number
   FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
   WHERE drs.group_id = ag.group_id; 
   ```

   La replica secondaria è sincronizzata quando `synchronization_state_desc` è `SYNCHRONIZED`.

3. Aggiornare `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1.

   Lo script seguente imposta `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1 in un gruppo di disponibilità denominato `ag1`. Prima di eseguire lo script seguente, sostituire `ag1` con il nome del gruppo di disponibilità:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Questa impostazione assicura che per ogni transazione attiva venga eseguito il commit della replica primaria e di almeno una replica secondaria sincrona. 

4. Abbassare il livello della replica primaria a replica secondaria. Dopo aver abbassato di livello la replica primaria, la replica è in sola lettura. Eseguire questo comando nell'istanza di SQL Server che ospita la replica primaria per aggiornare il ruolo in `SECONDARY`:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. Alzare il livello della replica secondaria di destinazione a replica primaria. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Per eliminare un gruppo di disponibilità, usare [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Per un gruppo di disponibilità creato con il tipo di cluster NONE o EXTERNAL, il comando deve essere eseguito in tutte le replica che fanno parte del gruppo di disponibilità.