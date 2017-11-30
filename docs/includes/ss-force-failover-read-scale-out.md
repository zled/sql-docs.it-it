Ogni gruppo di disponibilità include solo una replica primaria, che consente operazioni di lettura e scrittura. Per modificare la replica primaria, è possibile eseguire il failover. In un gruppo di disponibilità per disponibilità elevata, il processo di failover è automatizzato da Gestione cluster. In un gruppo di disponibilità con scalabilità in lettura, il processo di failover è invece manuale. 

Esistono due modi per eseguire il failover la replica primaria in un gruppo di disponibilità a livello di lettura:

- Failover manuale forzato con perdita di dati
- Failover manuale senza perdita di dati

### <a name="forced-manual-failover-with-data-loss"></a>Failover manuale forzato con perdita di dati

Utilizzare questo metodo quando la replica primaria non è disponibile e non può essere recuperata. 

Per forzare il failover con perdita di dati, connettersi all'istanza di SQL Server che ospita la replica secondaria di destinazione ed eseguire:

```SQL
ALTER AVAILABILITY GROUP [ag1] FORCE_FAILOVER_ALLOW_DATA_LOSS;
```

### <a name="manual-failover-without-data-loss"></a>Failover manuale senza perdita di dati

Usare questo metodo quando la replica primaria è disponibile, ma è necessario modificare temporaneamente o definitivamente la configurazione e l'istanza SQL Server che ospita la replica primaria. Prima di eseguire il failover manuale, assicurarsi che la replica secondaria di destinazione viene aggiornata per evitare la perdita di dati. 

Per eseguire manualmente il failover senza perdita di dati:

1. Verificare la replica secondaria di destinazione `SYNCHRONOUS_COMMIT`.

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        MODIFY REPLICA ON N'**<node2>*' 
        WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);
   ```

2. Eseguire la query seguente per identificare che le transazioni attive vengano eseguito il commit per la replica primaria e almeno una replica secondaria asincrona: 

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

3. Aggiornamento `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1.

   Lo script seguente imposta `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` su 1 in un gruppo di disponibilità denominato `ag1`. Prima di eseguire lo script seguente, sostituire `ag1` con il nome del gruppo di disponibilità:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = 1;
   ```

   Questa impostazione assicura che ogni transazione attiva viene eseguito il commit per la replica primaria e almeno una replica secondaria asincrona. 

4. Abbassare di livello la replica primaria a una replica secondaria. Dopo la replica primaria viene abbassato di livello, è in sola lettura. Eseguire questo comando nell'istanza di SQL Server che ospita la replica primaria per aggiornare il ruolo `SECONDARY`:

   ```SQL
   ALTER AVAILABILITY GROUP [ag1] 
        SET (ROLE = SECONDARY); 
   ```

5. Alzare il livello della replica secondaria di destinazione a replica primaria. 

   ```SQL
   ALTER AVAILABILITY GROUP ag1 FORCE_FAILOVER_ALLOW_DATA_LOSS; 
   ```  

   > [!NOTE] 
   > Per eliminare un gruppo di disponibilità, utilizzare [DROP AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/drop-availability-group-transact-sql). Per un gruppo di disponibilità creato con CLUSTER_TYPE NONE o esterno, il comando deve essere eseguito in tutte le repliche che fanno parte del gruppo di disponibilità.