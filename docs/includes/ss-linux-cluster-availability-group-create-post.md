
## <a name="add-a-database-to-the-availability-group"></a>Aggiungere un database al gruppo di disponibilità

Verificare che il database a cui che aggiungere il gruppo di disponibilità è in modalità di recupero con registrazione completa e dispone di un backup del log valido. Se si tratta di un database di prova o di un database appena creato, eseguire un backup del database. Nel Server SQL primario, eseguire lo script di Transact-SQL seguente per creare ed eseguire il backup di un database denominato `db1`:

```sql
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Nella replica primaria di SQL Server, eseguire lo script di Transact-SQL seguente per aggiungere un database denominato `db1` a un gruppo di disponibilità denominato `ag1`:

```sql
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Verificare che il database sia creato nei server secondari

In ogni replica secondaria di SQL Server, eseguire la query seguente per verificare se il `db1` database è stato creato e sincronizzazione:

```sql
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
