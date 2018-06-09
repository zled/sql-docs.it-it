---
title: Errori di script R in SQL Server Machine Learning e R Services | Documenti Microsoft
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 0b695111849b234f6ca38fc89c538e905f187fb6
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34709102"
---
# <a name="r-scripting-errors-in-sql-server"></a>Errori di script R in SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Questo articolo sono descritti diversi scriptin gerrors durante l'esecuzione di codice R in SQL Server. L'elenco non è completa. Esistono molti pacchetti e gli errori possono variare tra le versioni dello stesso pacchetto. Si consiglia di errori di script di registrazione di [forum di Machine Learning Server](https://social.msdn.microsoft.com/Forums/home?category=MicrosoftR), che offre un supporto di machine learning componenti usati in R Services (In-Database), il Client R Microsoft e Microsoft R Server.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services


## <a name="valid-script-fails-in-t-sql-or-in-stored-procedures"></a>Script valido non riesce in T-SQL o stored procedure

Prima di wrapping del codice R in una stored procedure, è consigliabile eseguire il codice R in un IDE esterno o in uno degli strumenti di R, ad esempio RTerm o RGui. Usando questi metodi, eseguire il test e debug del codice utilizzando i messaggi di errore dettagliati restituiti da R.

Tuttavia, in alcuni casi il codice funzioni perfettamente in IDE o un'utilità esterna potrebbe non riuscire per l'esecuzione in una stored procedure o in un Server SQL contesto di calcolo. In questo caso, esistono una serie di problemi da cercare prima che si può presupporre che il pacchetto non funziona in SQL Server.

1. Verificare se finestra di avvio è in esecuzione.

2. Esaminare i messaggi per verificare se i dati di input o di dati di output contengono colonne con tipi di dati incompatibili o non supportato. Le query su un database SQL, ad esempio, restituiscono spesso GUID o rowguid, entrambi i quali non sono supportati. Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

3. Esaminare le pagine della Guida per le singole funzioni R determinare se tutti i parametri sono supportati per il contesto di calcolo di SQL Server. Per informazioni su ScaleR, utilizzare i comandi della Guida in linea R o vedere [riferimento pacchetto](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

Se il runtime di R è funzionante, ma lo script restituisce errori, è consigliabile provare il debug di script in un ambiente di sviluppo R dedicato, ad esempio strumenti R per Visual Studio.

È inoltre consigliabile esaminare e leggermente riscrivere lo script per risolvere eventuali problemi con i tipi di dati che potrebbero verificarsi quando si spostano dati tra R e il motore di database. Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

Inoltre, è possibile utilizzare il pacchetto sqlrutils per raggruppare script R in un formato più facilmente utilizzabile come una stored procedure. Per altre informazioni, vedere:
* [Generare una stored procedure per il codice R tramite il pacchetto sqlrutils](r/generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
* [Creare una stored procedure utilizzando sqlrutils](r/how-to-create-a-stored-procedure-using-sqlrutils.md)

## <a name="script-returns-inconsistent-results"></a>Script restituisce risultati incoerenti

Gli script R possono restituire valori diversi in un contesto di SQL Server, per diversi motivi:

- Conversione implicita del tipo viene eseguita automaticamente alcuni tipi di dati, quando i dati vengono passati tra il Server SQL e R. Per ulteriori informazioni, vedere [R librerie e tipi di dati](r/r-libraries-and-data-types.md).

- Determinare se al numero di bit è un fattore. Ad esempio, sono spesso le differenze nei risultati di operazioni matematiche per librerie di punto a virgola mobile a 32 e 64 bit.

- Determinare se NaN vengono generati in qualsiasi operazione. Questo può invalidare i risultati.

- Quando crei un reciproco di un numero prossimo a zero, è possano amplificate piccole differenze.

- Errori di arrotondamento accumulati possono provocare ad esempio i valori che sono minori di zero anziché zero.

## <a name="implied-authentication-for-remote-execution-via-odbc"></a>Autenticazione implicita per l'esecuzione remota tramite ODBC

Se ci si connette a di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dei comandi di computer per l'esecuzione di R usando il **RevoScaleR** funzioni, è possibile che venga visualizzato un errore quando si utilizzano chiamate ODBC di scrittura dei dati al server. Questo errore si verifica solo quando si utilizza l'autenticazione di Windows.

Il motivo è che gli account di lavoro che vengono creati per R Services non dispone dell'autorizzazione per connettersi al server. Pertanto, chiamate ODBC non possono essere eseguite per conto dell'utente. Il problema non viene eseguito con l'account di accesso SQL in quanto, con l'account di accesso SQL, le credenziali vengono passate in modo esplicito dal client R per l'istanza di SQL Server e quindi per ODBC. Tuttavia, utilizzando l'account di accesso SQL è anche meno sicura rispetto all'utilizzo di autenticazione di Windows.

Per abilitare le credenziali di Windows deve essere passato in modo sicuro da uno script che ha avviato in modalità remota, SQL Server deve emulare le credenziali. Questo processo è detto _autenticazione implicita_. Per ottenere questo risultato, il lavoro che eseguono gli script R o Python nel computer SQL Server devono disporre delle autorizzazioni corrette.

1. Aprire [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] come amministratore nell'istanza in cui si desidera eseguire il codice R.

2. Eseguire lo script seguente. Assicurarsi di modificare il nome del gruppo utente, se è stato modificato il valore predefinito e i nomi di computer e istanza.

    ```SQL
    USE [master]
    GO
    
    CREATE LOGIN [computername\\SQLRUserGroup] FROM WINDOWS WITH
    DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ```

## <a name="avoid-clearing-the-workspace-while-youre-running-r-in-a-sql-compute-context"></a>Non deselezionare l'area di lavoro durante l'esecuzione in un contesto di calcolo SQL R

Anche se l'area di lavoro di cancellazione è comune quando si lavora nella console di R, può avere conseguenze impreviste in un database SQL di contesto di calcolo.

`revoScriptConnection` è un oggetto in area di lavoro R che contiene informazioni su una sessione R che viene chiamata da SQL Server. Tuttavia, se il codice R include un comando per cancellare l'area di lavoro (ad esempio `rm(list=ls())`), tutte le informazioni sulla sessione e altri oggetti nell'area di lavoro R vengano deselezionate anche.

In alternativa, evitare di cancellazione indiscriminata di variabili e altri oggetti durante l'esecuzione R in SQL Server. È possibile eliminare variabili specifiche tramite la **rimuovere** funzione:

```R
remove('name1', 'name2', ...)
```

Se sono presenti più variabili da eliminare, è consigliabile salvare i nomi delle variabili temporanee per un elenco e quindi eseguire periodicamente operazioni di garbage collection nell'elenco.



## <a name="next-steps"></a>Passaggi successivi

[Problemi noti e risoluzione dei problemi di Machine Learning Services](machine-learning-troubleshooting-faq.md)

[Raccolta dei dati per la risoluzione dei problemi di apprendimento automatico](data-collection-ml-troubleshooting-process.md)

[Domande frequenti sull'installazione e sull'aggiornamento](r/upgrade-and-installation-faq-sql-server-r-services.md)

[Risolvere i problemi di connessioni al motore di database](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md)
