1. **In tutte le istanze di SQL Server creare un account di accesso server per Pacemaker**. Il codice Transact-SQL seguente crea un account di accesso:

   ```Transact-SQL
   USE [master]
   GO
   CREATE LOGIN [pacemakerLogin] with PASSWORD= N'ComplexP@$$w0rd!'
    
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [pacemakerLogin]
   ```

   In alternativa, è possibile impostare le autorizzazioni a un livello più granulare. L'account di accesso Pacemaker richiede l'autorizzazione ALTER, CONTROL e VIEW DEFINITION per gestire il gruppo di disponibilità. Richiede anche l'autorizzazione VIEW SERVER STATE perché l'account di accesso possa eseguire sp_server_diagnostics. Per altre informazioni, vedere [GRANT, autorizzazioni del gruppo di disponibilità (Transact-SQL)](http://msdn.microsoft.com/library/hh968934.aspx) e le autorizzazioni [sp_server_diagnostic](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql#permissions).

   Il codice Transact-SQL seguente concede solo le autorizzazioni necessarie per l'account di accesso di Pacemaker. Nell'istruzione seguente "ag1" è il nome del gruppo di disponibilità che verrà aggiunto come risorsa cluster.

   ```Transact-SQL
   GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::ag1 TO pacemakerLogin
   GRANT VIEW SERVER STATE TO pacemakerLogin
   ```

1. **In tutte le istanze di SQL Server salvare le credenziali per l'account di accesso di SQL Server**.

   ```bash
   echo 'pacemakerLogin' >> ~/pacemaker-passwd
   echo 'ComplexP@$$w0rd!' >> ~/pacemaker-passwd
   sudo mv ~/pacemaker-passwd /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd
   sudo chmod 400 /var/opt/mssql/secrets/passwd # Only readable by root
   ```
