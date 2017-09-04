
## <a name="add-a-database-to-the-availability-group"></a>Aggiungere un database al gruppo di disponibilità

Verificare che il database che si aggiunge al gruppo di disponibilità sia in modalità di ripristino completa e disponga di un backup del log valido. Se si tratta di un database di prova o di un database nuovo creato, eseguire un backup del database. Nell'istanza primaria di SQL Server, eseguire lo script di Transact-SQL seguente per creare ed eseguire il backup di un database denominato `db1`.

```Transact-SQL
CREATE DATABASE [db1];
ALTER DATABASE [db1] SET RECOVERY FULL;
BACKUP DATABASE [db1] 
   TO DISK = N'/var/opt/mssql/data/db1.bak';
```

Nella replica primaria di SQL Server, eseguire lo script di Transact-SQL seguente per aggiungere un database denominato `db1` a un gruppo di disponibilità denominato `ag1`.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] ADD DATABASE [db1];
```

### <a name="verify-that-the-database-is-created-on-the-secondary-servers"></a>Verificare che il database sia creato nei server secondari

In ogni replica secondaria di SQL Server, eseguire la query seguente per verificare che sia stato creato il database `db1` e sia sincronizzato.

```Transact-SQL
SELECT * FROM sys.databases WHERE name = 'db1';
GO
SELECT DB_NAME(database_id) AS 'database', synchronization_state_desc FROM sys.dm_hadr_database_replica_states;
```
