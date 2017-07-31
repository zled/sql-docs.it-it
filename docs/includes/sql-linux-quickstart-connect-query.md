## <a name="connect-locally"></a>Eseguire la connessione in locale

Nella procedura seguente viene usato **sqlcmd** per connettersi in locale alla nuova istanza di SQL Server.

1. Eseguire **sqlcmd** con i parametri per il nome di Server SQL (-S), il nome utente (-U) e la password (-P). In questa esercitazione la connessione viene eseguita in locale, pertanto il nome del server è `localhost`. Il nome utente è `SA` e la password è quella specificata per l'account SA durante la configurazione.

   ```bash
   sqlcmd -S localhost -U SA -P '<YourPassword>'
   ```

   > [!TIP]
   > È possibile omettere la password nella riga di comanda perché sia richiesto di essere immessa.

   > [!TIP]
   > Se successivamente si decide di connettersi da remoto, specificare il nome del computer o l'indirizzo IP per il parametro **-S** e assicurarsi che la porta 1433 sia aperta nel firewall.

1. Se la connessione viene eseguita correttamente, il prompt dei comandi **sqlcmd** sarà: `1>`.

1. Se si verifica un errore di connessione, provare a diagnosticare il problema dal messaggio di errore. Rivedere poi i [consigli per la risoluzione dei problemi di connessione](../linux/sql-server-linux-troubleshooting-guide.md#connection).

## <a name="create-and-query-data"></a>Creare i dati della query
Nelle sezioni seguenti viene descritto l'uso di **sqlcmd** e Transact-SQL per creare un nuovo database, aggiungere dati ed eseguire una query semplice.

### <a name="create-a-new-database"></a>Creare un nuovo database

La seguente procedura consente di creare un nuovo database denominato `TestDB`.

1. Dal prompt dei comandi **sqlcmd** incollare il comando seguente di Transact-SQL per creare un database di test:

   ```sql
   CREATE DATABASE TestDB
   ```

1. Nella riga successiva scrivere una query perché vengano restituiti i nomi di tutti database nel server:

   ```sql
   SELECT Name from sys.Databases
   ```

1. I due comandi precedenti non sono stati eseguiti immediatamente. È necessario digitare `GO` in una nuova riga per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="insert-data"></a>Inserire i dati

Creare poi una nuova tabella `Inventory` e inserire due nuove righe.

1. Dal prompt dei comandi **sqlcmd** spostare il contesto nel nuovo database `TestDB`:

   ```sql
   USE TestDB
   ```

1. Creare una nuova tabella denominata `Inventory`:

   ```sql
   CREATE TABLE Inventory (id INT, name NVARCHAR(50), quantity INT)
   ```

1. Inserire i dati nella nuova tabella:

   ```sql
   INSERT INTO Inventory VALUES (1, 'banana', 150); INSERT INTO Inventory VALUES (2, 'orange', 154);
   ```

1. Digitare `GO` per eseguire i comandi precedenti:

   ```sql
   GO
   ```

### <a name="select-data"></a>Selezionare i dati

A questo punto, eseguire una query per restituire i dati della tabella `Inventory`.

1. Dal prompt dei comandi **sqlcmd** immettere una query che restituisca le righe della tabella `Inventory` che ne contiene oltre 152:

   ```sql
   SELECT * FROM Inventory WHERE quantity > 152;
   ```

1. Eseguire il comando:

   ```sql
   GO
   ```

### <a name="exit-the-sqlcmd-command-prompt"></a>Uscire dal prompt dei comandi sqlcmd

Per terminare la sessione **sqlcmd**, digitare `QUIT`:

```sql
QUIT
```

## <a name="connect-from-windows"></a>Eseguire la connessione da Windows

È importante notare che gli strumenti di SQL Server in Windows consentono di connettersi alle istanze di SQL Server in Linux nello stesso modo in cui si connettono a qualsiasi istanza remota di SQL Server.

Se si usa un computer Windows con possibilità di connessione al computer Linux, seguire la stessa procedura descritta in questo argomento, usando il prompt dei comandi di Windows che esegue **sqlcmd**. Verificare però che si stiano usando il nome del computer Linux e l'indirizzo IP di destinazione anziché il localhost. Assicurarsi anche che la porta TCP 1433 sia aperta. Nel caso di problemi di connessione da Windows, vedere i [consigli per la risoluzione dei problemi di connessione](../linux/sql-server-linux-troubleshooting-guide.md#connection).

Per altri strumenti che vengono eseguiti in Windows, ma si connettono a SQL Server in Linux, vedere:

- [SQL Server Management Studio (SSMS)](../linux/sql-server-linux-develop-use-ssms.md)
- [Windows PowerShell](../linux/sql-server-linux-manage-powershell.md)
- [SQL Server Data Tools (SSDT)](../linux/sql-server-linux-develop-use-ssdt.md)

## <a name="next-steps"></a>Passaggi successivi

Se non si ha familiarità con T-SQL, vedere [Tutorial: Writing Transact-SQL Statements](../t-sql/tutorial-writing-transact-sql-statements.md) (Esercitazione: Scrittura di istruzioni Transact-SQL) e [Transact-SQL Reference (Database Engine)](../t-sql/language-reference.md) (Guida di riferimento a Transact-SQL (Motore di database)).

Per esaminare altri modi per connettersi e gestire SQL Server, vedere [Visusal Studio Code](../linux/sql-server-linux-develop-use-vscode.md) (Codice di Visual Studio) e [SQL Server Management Studio](../linux/sql-server-linux-develop-use-ssms.md).